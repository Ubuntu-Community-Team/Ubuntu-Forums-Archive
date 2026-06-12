---
title: "Installation from ISO"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by asai on 2010-08-04
Hi,

I am trying to install Ubuntu without burning a CD from a downloaded ISO file.
I have /home on it's own partition.
I start with executing these commands:
```
cd /home
sudo mount -o loop hardy-server-i386.iso /media/cdrom0
sudo cp /media/cdrom0/install/vmlinuz .
sudo cp /media/cdrom0/install/initrd.gz .
```
Then I edit the grub configuration file /boot/grub/menu.lst, Adding this item:
```
title Install Ubuntu
root (hd0,4)
kernel /vmlinuz boot=casper iso-scan/filename=/hardy-server-i386.iso
initrd /initrd.gz 
```
The installer starts fine, however it stops with error missing CD. This means that kernel and initrd files are ok, but it doesn't read the ISO.
Whats missing in the configuration?

---

### Post by jocko on 2010-08-04
> **asai said:**
> 
```
title Install Ubuntu
root (hd0,4)
kernel /vmlinuz boot=casper [COLOR=Red]iso-scan/filename=/hardy-server-i386.iso[/COLOR]
initrd /initrd.gz 
```The installer starts fine, however it stops with error missing CD. This means that kernel and initrd files are ok, but it doesn't read the ISO.
Whats missing in the configuration?
Don't you need to give the full path to the .iso?
Did you follow some instructions to do this? Why not link to those instructions to allow people to try to find what you missed?
Edit: Sorry... I see now that you actually did use the full path to the iso, as the iso is on the root of your /home partition...

---

### Post by asai on 2010-08-05
Thanks for your reply.
The ISO, vmlinuz and initrd.gz files are all in root of the partition (hd0,4)

I should of course linked the source. Sorry about that.
Here it is: [http://deepbluespaces.blogspot.com/2008/07/install-ubuntu-804-from-hard-disk.html]("http://deepbluespaces.blogspot.com/2008/07/install-ubuntu-804-from-hard-disk.html")

---

### Post by asai on 2010-08-09
Did not get this to work.
However I installed the system over Internet. :D

---

