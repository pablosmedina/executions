executions
==========

An abstraction layer on top of the Executors framework to simplify common patterns of parallel tasks executions

Callable<SomeTaskResult> oneSecondTask = ...
Callable<SomeTaskResult> twoSecondsTask = ...
Callable<SomeTaskResult> tenSecondsTask = ...

Collection<SomeTaskResult> results =  Executions.newExecution().withTask(oneSecondTask)
                                								               .withTask(twoSecondsTask)
                                								               .withTask(tenSecondsTask)
                                								               .withTimeout(5,TimeUnit.SECONDS)
                                								               .withExecutor(Executors.newFixedThreadPool(4))
                                								               .execute();
                        								               
results.size(); //It returns 2
