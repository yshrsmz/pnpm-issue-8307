# pnpm-issue-8307

https://github.com/pnpm/pnpm/issues/8307

## how to reproduce

### without the issue

1. checkout the `main` branch(with pnpm@9.5.0-beta.0)
2. `pnpm i`
3. `pnpm --recursive build`
4. check `packages/app/node_modules`
   - you will see `@types/node`, `fastify`, `lib`, `typescript`
5 `pnpm prune --prod`
4. re-check `packages/app/node_modules`
   - you will see `fastify`, `lib`

### with the issue

1. update `packageManger` field in `./pacakge.json` to `pnpm@9.5.0-beta.1`
   - Or the latest pnpm(9.11.0)
2. `pnpm i`
3. `pnpm --recursive build`
4. check `packages/app/node_modules`
   - you will see `@types/node`, `fastify`, `lib`, `typescript`
5 `pnpm prune --prod`
4. re-check `packages/app/node_modules`
   - nothing inside the directory. There should be `fastify` and `lib`
