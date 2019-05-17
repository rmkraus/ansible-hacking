# Complex Nested Loops

```bash
ansible-playbook main.yml
```

This is an example that requires a complex nested loop. The new looping mechanisms are very powerful and can accommodate most situations. However, there are still situations that require more complex logic than a single `loop` command can realistically service.

In this example, we are creating virtual machines. For each "type" of virtual machine (srv or desktop), we want to create multiple identical instances (specified by `qty`). Since the number of instances can change for each machine type, we cannot easily collapse this into a single list suitable for the `loop` mechanism.

To accomplish this, we will do a nested loop. There is an outer loop that calls the `include_tasks` module to run an inner loop. The outer loop will loop over the items in the `vms` dictionary while the inner loop repeats the number of times specified by qty. Instead of actually creating a vm, we run a debug command to see the vm's name.
