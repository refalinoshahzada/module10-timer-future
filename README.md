### Understanding How it Works

![SS](img/cargo_run.png)

In asynchronous programming, instructions don't necessarily run in the order they're written. In this example, the `main()` function starts by creating an executor and a spawner. It then uses the spawner to launch an asynchronous task using `spawn`, but this doesn't execute the task right away—it merely schedules it. After spawning the task, `main()` prints "Spawner has been called, task will run asynchronously." to indicate the task is queued. It then immediately prints "hey hey". The asynchronous task doesn't begin until the executor is run at the end of `main()`, at which point it picks up the task. The task then waits two seconds, prints "howdy!", and finally prints "done!". This sequence happens because the executor is responsible for running the asynchronous task, while the rest of `main()` runs without waiting for it.
