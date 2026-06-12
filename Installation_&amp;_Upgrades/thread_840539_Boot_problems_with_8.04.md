---
title: "Boot problems with 8.04"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by aliusdragonfly on 2008-06-25
Hi all,

I'm yet another newbie at Ubuntu, and I'm having trouble getting my new install to boot. I wiped XP off of the drive and installed Ubuntu from the Live CD, and the install seemed to g o fine. However, now when I start up the computer it says "GRUB GRUB Loading stage1.5 ..." and then just sits there. I have left it overnight and it has not made any progress or displayed any other errors. I have tried some of the stuff in other threads, like the root (hd0,1) and setup (hd0) thing, and it has not helped. Anyone have any suggestions?

---

### Post by cpetercarter on 2008-06-25
When Grub first says "loading stage 1.5..", press escape. It may put you into the Grub menu where you may be able to boot in recovery mode.

---

### Post by aliusdragonfly on 2008-06-25
No response. It just sits there with the cursor blinking and doesn't do anything. There is no wait between when it shows "GRUB Loading stage1.5" and when it freezes up. What is stage 1.5?

---

### Post by VMC on 2008-06-25
> **aliusdragonfly said:**
> No response. It just sits there with the cursor blinking and doesn't do anything. There is no wait between when it shows "GRUB Loading stage1.5" and when it freezes up. What is stage 1.5?

output the following from a Terminal. Since you can't boot installed linux, boot from live cd.

```
sudo fdisk -l
```

---

### Post by aliusdragonfly on 2008-06-25
output of fdisk:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9118    73240303+  83  Linux
/dev/sda2            9119        9519     3221032+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System

anything useful there?

---

### Post by aliusdragonfly on 2008-06-26
anyone still with me here?

---

### Post by logos34 on 2008-06-26
check this out:
[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)

maybe you have a corrupt stage 1.5 file.

try herman's 'refresh' method (adjusted for your case).

-mount root:
[B]
sudo mkdir /media/sda1

sudo mount -t ext3 /dev/sda1 /media/sda1

cd /media/sda1[/B]  

> sudo cp /boot/grub/menu.lst .
                                       sudo rm /boot/grub/*
                                       sudo cp menu.lst /boot/grub
[B]
cd 

                                       sudo grub-install --root-directory=/media/sda1 /dev/sda[/B]

(I altered the last part just to make sure there's no confusion as to root dir when you run grub-install)

---

### Post by aliusdragonfly on 2008-06-26
So here's an odd problem. In the directory /boot, there is no subdirectory /grub. The terminal says it can't find /boot/grub/menu.lst.  However, if I do sudo grub and find /boot/grub/menu.lst, it says it is on (hd0,0). Where is my menu.lst? Why is it not where it belongs? and what can I do about it?

---

### Post by logos34 on 2008-06-26
Is root mounted and are you in the right directory?

mount it like above or just click on root volume in side pane of nautilus file browser to mount...navigate to boot/grub..what do you see?

---

### Post by aliusdragonfly on 2008-06-26
I have mounted as above, but when I navigate to /boot there is no /grub. There are the following: 

abi-2.6.24-16-generic
config-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak
vmlinuz-2.6.24-16-generic
memtest86+.bin
System.map-2.6.24-16-generic

no grub directory, no menu.lst.

---

### Post by logos34 on 2008-06-26
> **aliusdragonfly said:**
> I have mounted as above, but when I navigate to /boot there is no /grub. There are the following: 

abi-2.6.24-16-generic
config-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak
vmlinuz-2.6.24-16-generic
memtest86+.bin
System.map-2.6.24-16-generic

no grub directory, no menu.lst.

I don;t understand that, because when you ran 'find /boot...stage1' there was obviously a stage1 file in /boot/grub.  well, if you're sure there's nothing there, then just do:

[B] cd 

                                       sudo grub-install --root-directory=/media/sda1 /dev/sda

[/B](or '/media/**disk**' if you just clicked on root to mount)

---

### Post by aliusdragonfly on 2008-06-26
I have done so now, but it hasn't changed anything. And I don't understand why the find command is returning a location either. The new directory I made, /media/sda1, contains a /boot and a /grub of its own, with menu.lst ensuite, but the main /boot for the whole file system doesn't have a /grub. 

Anyway, still staring at GRUB GRUB loading stage1.5. Is stage 1.5 important? I read somewhere that it might be possible to bypass it somehow.

thanks for your patience and help with this.

---

### Post by logos34 on 2008-06-26
> **aliusdragonfly said:**
> I have done so now, but it hasn't changed anything. And I don't understand why the find command is returning a location either. **The new directory I made, /media/sda1, contains a /boot and a /grub of its own, with menu.lst ensuite,** but the main /boot for the whole file system doesn't have a /grub. 

Anyway, still staring at GRUB GRUB loading stage1.5. Is stage 1.5 important? I read somewhere that it might be possible to bypass it somehow.

Then it appears grub folder with files is still there....when you say 'main /boot' you must be looking in the one on the live cd (altogether different)

again, stage1 and/or the rest of the grub files may be corrupt...an educated guess at least.  so try refresh as desribed above

---

### Post by logos34 on 2008-06-26
was windows on the other drive?  

Maybe grub is seeing the other drive as (hd0).  Try switching the hard disk boot order in the BIOS

---

