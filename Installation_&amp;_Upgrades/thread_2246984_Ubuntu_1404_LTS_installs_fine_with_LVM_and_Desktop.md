---
title: "Ubuntu 14:04 LTS installs fine with LVM and Desktop, fails with LVM and Serv"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by delleske on 2014-10-04
On a new HP Proliant N54L, I've (accidentally) installed Ubuntu Desktop 14.04 LTS 64 bit via an USB stick without any problem, harddisk has been erased, "normal" installation using the entire disk but with LVM.

But as I wanted Ubuntu 14.04 LTS 64 bit Server, I reflashed the USB-stick and started the non-graphical installer, which worked fine (guided partitioning, using entire disk, with LVM) until I got

"busybox-initramfs kann nicht installiert werden" also known as "unable to install busybox-initramfs". (I mention the German version so others may profit from it)

I even went back to install an English minimal system: Same.

I read "apt-install or in-target already running" in the console, ends with 

"in-target: Unexpected: Command not executed" and then a command that tries to install busybox-initramfs.

Sigh.

And I thought a six month old Ubuntu Server runs on hundredthousands of servers?!?

Where did I go wrong?

---

### Post by gordintoronto on 2014-10-05
What is your hard drive configuration which requires LVM?

---

### Post by 8YNpG6L on 2014-10-14
I am having the same issue installing 14.04.1 LTS using LVM ...

---

