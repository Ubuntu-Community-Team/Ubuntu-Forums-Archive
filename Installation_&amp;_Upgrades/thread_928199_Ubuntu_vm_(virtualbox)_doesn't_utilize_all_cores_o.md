---
title: "Ubuntu vm (virtualbox) doesn't utilize all cores on Mac host"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2008-09-23
Ubuntu vm (virtualbox) doesn't utilize all cores on Mac host.

I installed Ubuntu as a virtual machine using virtualbox on a
multicore Mac host. I find the Ubuntu vm does utilize all the processor cores available on the host machine. 

Is there a solution ?

---

### Post by Physicist on 2008-09-25
Any comments ?

---

### Post by Linteg on 2008-09-25
The number of cores available to the guest in a virtual machine is usually controlled in the VM's settings. Are you sure you have enabled all cores in virtualbox?

---

### Post by Physicist on 2008-09-25
When is this setting configured?

Is it during the creation of the guest ? Or, after it is already created, can I still set the number of processors used by guest OS ?

---

### Post by Physicist on 2008-09-26
I checked again the process of installing a new guest Ubuntu OS in Virtualbox, there is no place you are asked to set up how many processors you want to use for the guest OS. Could it be set up in some other way ?

---

