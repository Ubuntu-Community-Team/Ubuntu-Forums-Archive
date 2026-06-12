---
title: "Wanting to dual boot"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by AJLChase on 2011-01-11
I'm wanting to dual boot Ubuntu with my Windows 7 machine. I have 2 1tb HD's and would like a diff OS on each HD. When I get to the install portion for partioning I am confused as to what I am suppose to do. It seems as though Ubuntu is only recognizing the two hard drives as 1. Giving me a total of 2Tbs to partition. I am afraid to partition it as I don't know how it will do so over the original OS? Any help or guides to link me to? Thanks!

---

### Post by pbpersson on 2011-01-11
You were wise to stop when you did.

Here is a [graphical installation guide]("https://help.ubuntu.com/community/GraphicalInstall")

I would suggest that you use the "specify partitions manually (advanced)" because then you can guide Ubuntu as to where you want it to install and make sure it does not touch your Windows partitions.

Let's say for instance that your second hard drive is called sdb.  Assuming you have a 1TB drive, You might do something like:

sdb1    500 GB   /
sdb2    490 GB   /home
sdb3     10 GB   swap

There are a limitless number of ways to do this, if you ask 20 people you might get 20 different answers.  It partially depends upon what you will be doing with your machine.

---

### Post by pbpersson on 2011-01-11
Please note that in this image it is not showing you two hard drives, it is showing you two different scenarios for sda which is your first hard drive.

That might be what is confusing you

---

### Post by Rubi1200 on 2011-01-11
Before you start the installer, go to Applications > Accessories > Terminal and run this command.

```
sudo parted -l
```
(lowercase L not 1)

Paste the output here so we can get a better idea of what you are dealing with.

---

