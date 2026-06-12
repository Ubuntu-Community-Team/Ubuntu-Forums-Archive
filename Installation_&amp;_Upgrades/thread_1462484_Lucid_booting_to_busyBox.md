---
title: "Lucid booting to busyBox"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by HeyOutThere on 2010-04-25
just upgraded to Lucid on a dell inspiron 1564 laptop with an i3 processor for compatibility with intel hardware, and installation went fine up until the reboot.

now i am booting up to busyBox and cannot get to the desktop.

it reads-
```
BusyBox v1.13.3 (Ubuntu 1:1,13,3-1ubuntu11) built -in shell (ash)
Enter 'help' for a list of built in commands.

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
-missing moduals (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/3bb4c07-5dea-40d5-896a-d361532a101f does not exist. Dropping to a shell!
```

Typing exit as some sources advised causes the above to be reiterated.  What should i do to fix this?
Mostly new to ubuntu, what should i do to fix this?

---

### Post by thirdspace on 2010-05-04
I just had a fresh lucid install on an old PC fail twice in a row with this message. Then I installed karmic on the same PC with no changes and it installed and booted successfully.

What this means is that the lucid system on the installer cd could access the disk drive, and so could grub2, for some reason the lucid system loaded from the disc drive could not access the partition on the disk where it expected to be able to mount "/", aka the root filesystem.

Unfortunately there are quite a few different things that can cause this. Because the previous release installed and booted correctly on the exact same hardware, I can say with fair confidence that I've found a "regression", a new bug (or unintentionally missing feature) in the new release compared to the previous one.:(

---

### Post by tsaowang on 2010-05-05
Hello,

My problem was that linux is not given the right UUID, you have to locate where you have linux installed (maybe /dev/sda1 or anything else depending on your configuration)

then in a terminal type :

**#sudo blkid**

- (Enter your password)

- Choose the right UUID from the list (mine was corresponding to /dev/sda1)

**#sudo gedit /boot/grub/grub.cfg**

Locate the following lines (I had to modify the UUID three times in grub.cfg):


***linux /boot/vmlinuz-2.6.31-21-generic root=UUID=[COLOR=Red]a026ae5a-4c0b-42cd-8b46-b57bfb433ac7[/COLOR] ro quiet splash***

Replace the UUID by the value the entry **#sudo blkid **gave you for your boot device and then save the file and do the following :

**#sudo update-grub**

Restart and you must now be OK

---

### Post by SiouxerBrewer on 2010-05-05
tsaowang how can we apply these settings when ubuntu won't boot?  Is it from a live cd?

---

### Post by thirdspace on 2010-05-06
On this computer there turned out to be a jumper setting on the hard drive that was making it take a long time to become responsive after a reset. So the "regression" seems to have been that lucid is less patient with a slow-to-wake-up boot drive.

> **thirdspace said:**
> I just had a fresh lucid install on an old PC fail twice in a row with this message. Then I installed karmic on the same PC with no changes and it installed and booted successfully.

What this means is that the lucid system on the installer cd could access the disk drive, and so could grub2, for some reason the lucid system loaded from the disc drive could not access the partition on the disk where it expected to be able to mount "/", aka the root filesystem.

Unfortunately there are quite a few different things that can cause this. Because the previous release installed and booted correctly on the exact same hardware, I can say with fair confidence that I've found a "regression", a new bug (or unintentionally missing feature) in the new release compared to the previous one.:(

---

### Post by thirdspace on 2010-05-06
/boot/grub/grub.cfg is not normally supposed to be edited, because it gets overwritten when you run update-grub, with settings from /etc/grub*. For booting once, I guess it would work to either boot some kind of rescue CD and use that to edit /boot/grub/grub.cfg. Or hold down SHIFT key starting right after power-on until grub menu appears and then follow onscreen prompts to edit command line.

> **tsaowang said:**
> Hello,

My problem was that linux is not given the right UUID, you have to locate where you have linux installed (maybe /dev/sda1 or anything else depending on your configuration)

then in a terminal type :

**#sudo blkid**

- (Enter your password)

- Choose the right UUID from the list (mine was corresponding to /dev/sda1)

**#sudo gedit /boot/grub/grub.cfg**

Locate the following lines (I had to modify the UUID three times in grub.cfg):


***linux /boot/vmlinuz-2.6.31-21-generic root=UUID=[COLOR=Red]a026ae5a-4c0b-42cd-8b46-b57bfb433ac7[/COLOR] ro quiet splash***

Replace the UUID by the value the entry **#sudo blkid **gave you for your boot device and then save the file and do the following :

**#sudo update-grub**

Restart and you must now be OK

---

### Post by thirdspace on 2010-05-06
> **SiouxerBrewer said:**
> tsaowang how can we apply these settings when ubuntu won't boot?  Is it from a live cd?

Hold down SHIFT while computer starts. You should get a "grub menu" screen with instructions for choosing a boot option or editing boot one. Edit the first choice and on the "linux" line, replace everything from root= up to the next space with the device name of your root partition. If you have only one hard drive the name will be /dev/sda? where ? is replace with some digit. If Ubuntu is the only OS on the drive, it is probably /dev/sda1.

---

### Post by SiouxerBrewer on 2010-05-08
> **thirdspace said:**
> Hold down SHIFT while computer starts. You should get a "grub menu" screen with instructions for choosing a boot option or editing boot one. Edit the first choice and on the "linux" line, replace everything from root= up to the next space with the device name of your root partition. If you have only one hard drive the name will be /dev/sda? where ? is replace with some digit. If Ubuntu is the only OS on the drive, it is probably /dev/sda1.

Thank you for your reply, however, this still delivers the same results.  Some background information:

-I have two hard drives 
-Sdb1 is my windows xp partition
-sdb2 is my linux partition
-sda is a NTFS files only (no software) hard drive with no extra partitions
When I use the live CD in order for linux to recognise SDA(1) I must add "pci=nomsi" to the boot script (f6).  I then install linux from the live cd. (I'm not sure if this has anything to do with the problem)
-Near the end of the installation parameters I go into advanced settings and select /dev/sdb2 for the boot device
-One thing to note.  Sometimes when I use the live CD it labels sda as sdb, then subsequently labels sdb1,2... as sda1,2...  when I installed linux sdb1,2...were labeled properly as well as sda

What am I missing?

---

