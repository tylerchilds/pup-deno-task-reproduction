# Context

There seems to be interplay between pup and deno with regards to `deno task`

# Reproduction

Install pup:

```
deno run -Ar jsr:@pup/pup@1.0.0-rc.39 setup --channel prerelease
```

Run `deno task start` with pup.

```
pup run --autostart --cmd "deno task start"
```

expected console output:
```
Hello World
```

actual console output:
```
tychi@yourlovedones:~/SourceCode/pup-deno-task-reproduction$ pup run --autostart --cmd "deno task start"
2024-05-13T20:15:44.994Z [LOG] [core:processes] Process 'task' loaded
2024-05-13T20:15:44.995Z [LOG] [task:starting] Process starting, reason: autostart
2024-05-13T20:15:45.006Z [ERROR] [task:stderr] ⚠️  The `--unstable` flag is deprecated and will be removed in Deno 2.0. Use granular `--unstable-*` flags instead.
2024-05-13T20:15:45.006Z [ERROR] [task:stderr] Learn more at: https://docs.deno.com/runtime/manual/tools/unstable_flags
2024-05-13T20:15:45.027Z [ERROR] [task:stderr] error: 
2024-05-13T20:15:45.027Z [ERROR] [task:stderr] Module not found "file:///home/tychi/SourceCode/pup-deno-task-reproduction/task".
2024-05-13T20:15:45.028Z [LOG] [task:errored] Process exited with error: Error: Exited with code: 1
^C2024-05-13T20:15:47.515Z [LOG] [core:terminate] Termination requested
2024-05-13T20:15:47.515Z [LOG] [task:block] Process blocked, reason: terminating
```
