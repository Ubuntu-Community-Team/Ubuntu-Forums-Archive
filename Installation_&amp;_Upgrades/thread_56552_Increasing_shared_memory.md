---
title: "Increasing shared memory"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by arlie on 2005-08-12
I was trying to install Sybase ASE Express Edition and had some shared memory problems.

I was advised by Sybase Asia Pacific that:

"It looks like ASE could not get 40MB shared memory.

The operating system shared memory default of most Linux releases is 32MB. The minimum required by Adaptive Server is 64MB for a default Server with 2K pages. You must increase the amount of shared memory if you plan to increase the total memory of Adaptive Server."

So how I increase Ubuntu shared memory to 64MB?

Please help...

---

### Post by ape on 2005-08-13
You will want to edit your /etc/sysctl.conf and add the following line:

     kernel.shmmax = 67108864

  After adding this you should probably reboot the system.  To verify that the change took, issue the following command:

     `sysctl -a | grep shmmax` and you should see the value that you entered in your /etc/sysctl.conf.

---

### Post by arlie on 2005-08-15
[QUOTE=ape]You will want to edit your /etc/sysctl.conf and add the following line:

     kernel.shmmax = 67108864

  After adding this you should probably reboot the system.  To verify that the change took, issue the following command:

     `sysctl -a | grep shmmax` and you should see the value that you entered in your /etc/sysctl.conf.[/QUOTE]
 Thanks.

---

