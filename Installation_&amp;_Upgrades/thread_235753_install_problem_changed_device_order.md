---
title: "install problem: changed device order"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by linuxone on 2006-08-13
Hi,

this weekend I installed Dapper, but unfortunately I had some big problems. So I did install Dapper 6.06/6.06.1 a few times until I found the reason for the problem.

Problem:
After a fresh install of Dapper Drake the system does NOT boot. No matter which version I installed (CD or DVD, 6.06 or 6.06.1), each time the same problem: no boot.

Reason:
The hard disc device name did change during boot process.

Solution:
Manually change fstab and menu.lst (grub) to the changed device names.


What happened? Explaining:
My system has several hard discs (2x IDE, 2x SATA and 1x SCSI). Main disc is the FIRST SATA device -> usually **sda**.

Booting from Dapper install medium (CD/DVD, 6.06/6.06.1) the device names and device order is correctly. The main drive is sda, sda1/sda5 were selected for installation and the entire install job runs fine without any error. Until I must reboot.

grub is loaded from hd0 (/dev/sda). Certainly. No other device has this new grub boot menu.

By loading initrd the devices did change. The Adaptec SCSI driver is loaded first. So the SCSI drive will become sda. Then the motherboard chipset driver is loaded, the onboard SATA controller and both connected SATA devices were found. My first SATA drive will become **sdb** now.

This must be a specific setting into the 2.6.15.x kernel. Because the same problem happens when installing Breezy and after doing a dist-upgrade to install Dapper. Booting the Breezy kernel (2.6.12.x) is possible, even after the dist-upgrade. Booting the new Dapper kernel will fail again.

A real nice trick. :confused: 

Thomas

---

### Post by n6mod on 2006-08-25
Gaaah. So I have the same problem, but I can't just changes the fstab, I don't think.

The issue in my case is that I have two drives running off the onboard SATA (sda and sdb, sata_via module). I just added a PCI SATA card and a removeable drive sled.

Again, the SATA card (sata_sil) card detects first.

Now, since the drive is removable (and thus might not always be there) I can't just change the fstab, can I?

I really need to rearrange the device order. But since the controller doesn't (I think?) have a device of its own, I don't know how to do that.

With ethernets I can put something like 

alias eth0 tulip

in modules.conf, but I don't know what to do with the SATA controllers.

Any suggestions?

---

### Post by Original Brownster on 2006-08-26
Hi,
I think the answer is UDEV. UDEV gets around the problem of changing device nodes that you get with USB for example, and all devices are named at boot time by a combination of kernel messages and UDEV interpreting them against the rules held in /etc/udev/rules.d/ Further events like hot plugging devices generate kernel messages too and therefore the rules are parsed again by udev.

In a nutshell I believe you can write a specific rule that identifies your removable sata drive, by a unique id. In this way you can constantly name it anything you like in /dev whenever it's plugged in or present at boot , so you could have it called /dev/ext_sata or whatever and not have it named 'sdx' 
looking at /etc/udev/rules.d/65-persistent-disk.rules you can see that if you had a drive plugged in at boot it will get named.
But If you create a rule in /etc/udev/rules.d/10-local.rules this will be identified and named first by your rule.
Check this [article]("http://www.reactivated.net/writing_udev_rules.html") out.

> **n6mod said:**
> Gaaah. So I have the same problem, but I can't just changes the fstab, I don't think.

The issue in my case is that I have two drives running off the onboard SATA (sda and sdb, sata_via module). I just added a PCI SATA card and a removeable drive sled.

Again, the SATA card (sata_sil) card detects first.

Now, since the drive is removable (and thus might not always be there) I can't just change the fstab, can I?

I really need to rearrange the device order. But since the controller doesn't (I think?) have a device of its own, I don't know how to do that.

With ethernets I can put something like 

alias eth0 tulip

in modules.conf, but I don't know what to do with the SATA controllers.

Any suggestions?

---

### Post by Fajer on 2006-08-26
I have three SATA drives and I have the same problem. Installer recognise my booting SATA drive as sdc but when grub  starts booting it fails becous it can't find directories - it see discs in other order...

When I disconnect my other two drives, Ubuntu works fine.

How I can create such rule You are talking about?

---

### Post by Original Brownster on 2006-08-28
Hi,
If your 3 SATA drives are permanently attached your problem is like the OP so the solution is to edit the menu.lst file that grub uses and the fstab file. This is because the drive names will remain constant for you despite the installer problem mentioned.
That is to say, if you get a grub menu and then an error  you can correct the problem this way. I would not write udev rules in this case.

Try comparing the name device that grub finds on boot to that used in the above files, check the posts about how grub numbers drives differently to linux in general, counting from 0.

At grub menu press 'c' for command line.

type: find /boot/grub/stage1

if you've not created a separate partition for boot you now know the drive number grub has found and should be used to load the kernel and initrd image.
compare to the contents of the menu.lst file,

type: cat /boot/grub/menu.lst

_example:_

title           Ubuntu, kernel 2.6.15-26-386
[COLOR="DarkOrange"]root [/COLOR]           (hd1,2)
kernel          /boot/vmlinuz-2.6.15-26-386 [COLOR="Red"]root=/dev/hdb3 [/COLOR]ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot



root should be set to this drive.

But I think at the end of the kernel line you may need to change the 'root=  ...' part. Because the way the kernel loads the drivers and discovers your sata disks this will most likely be part of the problem AND also be wrong in the fstab file too.

I don't know how you can discover the correct numbering without a bit of trial and error at this point, if you get the 'root=....' parameter wrong the os will stop at some point I expect because it'll mount the wrong partition. 
You can use a live cd to boot the system,mount your / partition then edit these files then reboot, 3 drives = 3 possibilities so shouldn't take too long!!!




> **Fajer said:**
> I have three SATA drives and I have the same problem. Installer recognise my booting SATA drive as sdc but when grub  starts booting it fails becous it can't find directories - it see discs in other order...

When I disconnect my other two drives, Ubuntu works fine.

How I can create such rule You are talking about?

---

