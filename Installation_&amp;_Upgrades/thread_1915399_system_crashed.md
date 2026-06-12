---
title: "system crashed"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by vishnugt on 2012-01-26
Hi,

My system got crashed due to un-expected power failure.
I think the OS got crashed.
I want to recover my system in the previous state. Please help me to do this activity..

Thanks&Regards,
vishnu gt

---

### Post by nipunshakya on 2012-01-26
I don't think unexpected power failure will crash your OS unless your terminal was busy in running some vital activity on it...Doesn't your machine boot up?
Your problem is understood, but your machine's specifications aren't....mind describing about your machine?

---

### Post by vishnugt on 2012-01-26
my system is not booting, after this incident.

i m using Compaq 3500
os:  ubuntu 11.04
memory : 1.4 GB
disk : 120 GB
while starting the system, i m getting like this::

Busybox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

---

### Post by ajgreeny on 2012-01-26
Use a live CD or USB and then run ```
sudo e2fsck /dev/sdx#
```where sdx# is your root partition, probably sda1 if ubuntu is the only OS on the machine.  That may sort out the file system problems.

---

### Post by vishnugt on 2012-01-26
somebody provide me some solution . i have some critical data in my system......

---

### Post by nipunshakya on 2012-01-26
it seems that you have a damaged filesystem..but unfortunately i don't have a solution to this...u might want to wait for someone to reply you back.

---

