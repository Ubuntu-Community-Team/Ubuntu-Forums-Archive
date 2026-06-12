---
title: "Help accessing different partitions"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by VelocityDwarf on 2011-03-01
Hello everyone, I'm new to this forum and to Ubuntu.

A couple hours ago I downloaded the Ubuntu 10.10 netbook edition so I could install it on my sony vaio netbook.
The installation went fine, and I selected the option of installing Ubuntu alongside my other operative system (win 7). I chose 160 gb (320 gb hard drive) to the left partition which I think said "files" or something like that (had a folder icon) and 160 gb to the right side partition (had the ubuntu icon).
Again, installation went fine. But when I tried to enter windows again, I couldn't boot it. I don't know how to access BIOS, and when I acces GRUB (by pressing f8) the only options I get are 2 ubuntus (with their respectively safe modes) and 2 memory tests.

How can I access win 7 again. I mean, of course I can install it again (I backed up the important files) but there is a homework I finished last night that I couldn't back up.

Can you please help me? I'm relatively new to Ubuntu.

---

### Post by tommcd on 2011-03-01
Open a terminal on Ubuntu and post the output of:
```
sudo fdisk -l
```
This will list all of the partitions that Ubutnu sees. This will tell us where Windows is on your hard drive.
Also from the terminal, try running:
```
sudo update-grub
```
This should hopefully update grub so that it will give you the option to boot Windows. You will then need to reboot to boot into Windows.
If this does not fix the problem, download and run the *bootinfo script*.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
 Post the output of the bootinfo script here
This will provide the info that is needed to properly diagnose the problem.

---

### Post by Hedgehog1 on 2011-03-02
Hi All!

This is a duplicate post of: 

[http://ubuntuforums.org/showthread.php?t=1698147]("http://ubuntuforums.org/showthread.php?t=1698147")

Sadly, the install overwrote the Windows partition.

---

