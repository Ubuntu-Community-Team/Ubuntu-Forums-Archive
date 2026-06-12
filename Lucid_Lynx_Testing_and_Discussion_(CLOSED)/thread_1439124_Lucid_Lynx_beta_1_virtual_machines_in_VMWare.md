---
title: "Lucid Lynx beta 1 virtual machines in VMWare?"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by taylorkh on 2010-03-25
This evening I built both 32 bit and 64 bit virtual machines using VMWare Player 3.0 on a Ubuntu 9.10 64 bit host.  I can access the virtual machines with the mouse (e.g. to click my name to login) however, the keyboard is not functional.  I cannot enter the password.

Has anyone else seen this issue?  I had tested alpha 1, 2 and 3 64 bit on the same host with no problems.  I will try again tomorrow and build the VMs with VMWare workstation instead of player and report what happens.

Ken

---

### Post by matt.nz on 2010-03-25
Same thing here. No keyboard action.

---

### Post by lavinog on 2010-03-26
I have been using kvm-qemu through out the testing phase.
beta-1 works, but there is no acceleration, and moving the mouse causes cpu spikes.

I found something a couple of days ago that there a patch was pulled from the kernel during beta-1 and this might be why vm's are acting up.

---

### Post by taylorkh on 2010-03-26
Good news - again - from VMWare.  Player 3.0.1 and Workstation 7.0.1 seem to have addressed the Lucid issues.  With WS 7.0.1 and Player 3.0.1 on 9.10 64 bit I have run the following combinations with no problem.

Workstatin with 64 bit guest
Player with Lucid 32 bit guest

Ken

---

### Post by taylorkh on 2010-03-26
Bad news - the VMs worked until I installed the available updates.  I can no longer access the VMs with the keyboard.

Ken

---

