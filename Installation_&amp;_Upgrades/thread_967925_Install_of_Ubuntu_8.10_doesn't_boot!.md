---
title: "Install of Ubuntu 8.10 doesn't boot!"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by ciube on 2008-11-02
Hi everybody, I'm new user and I have a big problem...

since yesterday I'm triing to install Ubuntu 8.10 but unsuccessfully.

When I boot from cd it say to me:

[B]Loading please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/B]


I tried to unplug the optical unite, the hard drives, the ram module, but nothing...it doesn't want to start!

Please help me!

---

### Post by taurus on 2008-11-02
How fast did you burn the ISO image to a CD?  Also, did you remember to check the integrity of the ISO image with checksum before you burnt it?

---

### Post by ciube on 2008-11-02
> **taurus said:**
> How fast did you burn the ISO image to a CD?  Also, did you remember to check the integrity of the ISO image with checksum before you burnt it?

Yes I checked it. The ISO is good.
4x burning speed.

---

### Post by taurus on 2008-11-02
Do you have another machine that you can check to see if you can boot from that CD?

---

### Post by ciube on 2008-11-02
> **taurus said:**
> Do you have another machine that you can check to see if you can boot from that CD?

Now I try it...thanks!

---

### Post by ciube on 2008-11-02
I tried it in an other machine: it works perfectly. There's not the problem I have in my desktop.

---

### Post by taurus on 2008-11-02
What's the spec of the machine that wouldn't boot Ubuntu CD?

---

### Post by ciube on 2008-11-02
> **taurus said:**
> What's the spec of the machine that wouldn't boot Ubuntu CD?

It's a Pentium 4 2.67 Ghz
Main board: Via P4PB 400
RAM: 512 (2 x 256)
HD 1: 60 GB Maxtor
HD 2: 150 GB Seagate

I have already installed Ubuntu distro in the past and util yesterday Ubuntu 8.04 were installed on tha machine.

---

### Post by horned0wl93 on 2008-11-02
I'm getting the same thing.  Your video drivers aren't installed/loading.  See [Intrepid Video Installation Drill-Down]("http://ubuntuforums.org/showthread.php?p=6088755#post6088755").

Cheers;
the0wl

---

### Post by ciube on 2008-11-02
I saw your tutorial, interesting... but I don't know how install driver packages: I can't arrive in a terminal!
My system doesn't boot even whit live session!

---

### Post by ciube on 2008-11-02
I also try to change my graphic card,
I try to reset bios configuration, but the problem still exist.

---

### Post by bl00d666 on 2008-11-02
what kind of memory do you have. ddr or ddr2. cause i got similar problem and i solve it by replacing my ddr2 memory with my old ddr. i post on another thread there . maybe the problem is the same. [http://ubuntuforums.org/showthread.php?t=947298&highlight=ddr2+problem&page=2](http://ubuntuforums.org/showthread.php?t=947298&highlight=ddr2+problem&page=2)

---

### Post by ciube on 2008-11-02
I have 2 ddr modules. It's an old PC...4 years ago...

And this configuration work perfectly with Ubuntu 8.04!!!

---

### Post by ciube on 2008-11-02
I succeed to boot the installation by putting "acpi=off" in the boot configuration, now I'm installing Ubuntu 8.10...
I'll say you something later...thank you for your assistance!

---

### Post by ciube on 2008-11-02
I have installed Ubuntu succesfully, but the problem retorned when I restarted the machine. What can I do?

---

### Post by ciube on 2008-11-02
I resolved completely the problem.
To make the boot of ubuntu I edit grub configuration by adding "acpi=off" in the kernel row:
/boot/grub/menu.lst

---

### Post by dannyboy676 on 2008-11-02
Hi all, i am new to these forums because i want to learn and use ubuntu more, i have the same problem, can someone please explain how to solve this problem in simple terms please as i haven't had much interacting with Linux, here's is my spec,

Intel E8400
Asus P5Q Pro
4GB of DDR2 RAM
8800GT GFX card
750GB HDD

Thank you all
Dan
:)

---

