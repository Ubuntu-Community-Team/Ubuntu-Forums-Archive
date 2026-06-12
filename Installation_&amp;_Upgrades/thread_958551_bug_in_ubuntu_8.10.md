---
title: "bug in ubuntu 8.10?"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by alkat on 2008-10-25
Hi,
I think I've found a bug in Ubuntu 8.10. I've installed the RC last night and I've noticed that the log messages keep on growing until they eat up all my disk space.

This happens with kernel, system and messages logs. Here's what I can read in the syslog:

> Oct 25 20:12:32 ubuntolo kernel: [ 8165.938993] 
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939299] bad: scheduling from the idle thread!
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939301] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939303] 
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939303] Call Trace:
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939306]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939307]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939309]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939312]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Oct 25 20:12:32 ubuntolo kernel: [ 8165.939314]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10


How can I report this "bug" or find a solution?

---

### Post by cariboo on 2008-10-25
To create a bug report go here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

You will have to create an account in order to report bugs.

Jim

---

### Post by xnid on 2008-10-31
I have exactly the same problem. Have you found the cause of the problem? Or better, any solution? :)

---

### Post by flashcat on 2008-10-31
My problem too. Login and no desktop environment. I can ssh into it from another box so if there is something I need to change, I would sure like to know.
:guitar:

---

### Post by xnid on 2008-10-31
> **flashcat said:**
> My problem too. Login and no desktop environment. I can ssh into it from another box so if there is something I need to change, I would sure like to know.
:guitar:

Weird. I can use my computer, but the CPU is working at 100%. From top I can see that it is dd and klogd working, so it is probably connected to the flooding of my dmesg. I get a lot of messages repeating alkat's problem.

---

### Post by lavinog on 2008-10-31
Can you provide information about your setup? Ubuntu 64bit or 32? Video card/System memory/ Processor...etc

---

### Post by xnid on 2008-10-31
> **lavinog said:**
> Can you provide information about your setup? Ubuntu 64bit or 32? Video card/System memory/ Processor...etc

I have a fresh installed Ubuntu 8.10 64-bit. Running on a Dell XPS M1530 with Intel Core 2 Duo processor, 4GB of ram, Nvidia Geforce 8600 GT (I'm using the proprietary driver version 177), and a Intel PRO/Wireless 4965 card.

I don't know if it is related, but my Wireless LED is constantly flashing.

---

### Post by flashcat on 2008-10-31
> **lavinog said:**
> Can you provide information about your setup? Ubuntu 64bit or 32? Video card/System memory/ Processor...etc

Thanks for the reply! Attached is a copy of the entire setup via dmesg.

---

### Post by xnid on 2008-10-31
Check out: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285")

After installed linux-backports-modules-2.6.27-7-generic and rebooting as suggested in the bug discussion, it seem to have fixed the problem, but I will not say for sure before my computer has been on for a while.

---

### Post by flashcat on 2008-10-31
> **xnid said:**
> Check out: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285")

After installed linux-backports-modules-2.6.27-7-generic and rebooting as suggested in the bug discussion, it seem to have fixed the problem, but I will not say for sure before my computer has been on for a while.

Thanks very much. I installed the above package and rebooted. Initially the problem still existed. However, when I selected Gnome for the default session all is well.

---

