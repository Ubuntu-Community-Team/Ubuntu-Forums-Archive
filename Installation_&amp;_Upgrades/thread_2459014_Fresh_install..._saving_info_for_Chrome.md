---
title: "Fresh install... saving info for Chrome"
date: 2021-03-08
forum: Installation &amp; Upgrades
---

### Post by acefromspace on 2021-03-08
Doing a fresh install (Ubuntu 20.04 LTS) Backing everything up on a USB flash drive. Need to create a bootable USB drive with Ubuntu iso (a separate USB drive) First, it's a brand new USB flash drive (SanDisk) Do I need to format it first (just to backup data)?
I assume the other flash drive will get formatted as part of the process of creating a bootable drive with the Ubuntu iso. I backed up bookmarks for Chrome (export bookmarks) Is there a way to backup saved passwords? This isn't my computer (personally I don't allow saved passwords) but my mother likes to stay logged into things like her Gmail.

---

### Post by CelticWarrior on 2021-03-08
> [COLOR=#000000]Do I need to format it first (just to backup data)?[/COLOR]
It depends.
If it has a supported file system and you're comfortable with it then I would say no, you don't.

> [COLOR=#000000]I assume the other flash drive will get formatted as part of the process of creating a bootable drive with the Ubuntu iso.[/COLOR]
Correct.

> [COLOR=#000000]I backed up bookmarks for Chrome (export bookmarks) Is there a way to backup saved passwords? This isn't my computer (personally I don't allow saved passwords) but my mother likes to stay logged into things like her Gmail.[/COLOR]
If she's using one Google service - any will do - then all she needs is to login in the newly installed Chrome: [https://support.google.com/chrome/answer/165139?co=GENIE.Platform%3DDesktop&hl=en](https://support.google.com/chrome/answer/165139?co=GENIE.Platform%3DDesktop&hl=en)

---

### Post by acefromspace on 2021-03-08
The file I have is ubuntu 20.04.2.0 desktop-amd 64.iso Not sure if this the correct one to use. I's a Dell desktop with CPU Intel Core i5-4440

---

### Post by CelticWarrior on 2021-03-08
> [COLOR=#000000]I's a Dell desktop with CPU Intel Core i5-4440[/COLOR]
Yes, your file is correct. It's for any 64-bit machine, AMD or Intel.

---

### Post by acefromspace on 2021-03-08
Thank you so much. It's been awhile... out of practice (I'm 60 years old) but it's all coming back to me now.
Had to re-learn how to change the boot order in BIOS but got it now. I'll go ahead and create the bootable USB iso and start backing up data. All seems well with Google... logged in and sync.
This computer had Windows on it so my son set up dual boot... don't need that anymore (will only install Ubuntu.) The only thing I'm not sure about is it shows "Dell Utility Partition 1" Do I need to save that? I'd rather just tell the Ubuntu install to use the entire hard disk.

---

### Post by acefromspace on 2021-03-08
All data backed up. Bootable startup disc created. Feeling good about this. Done for today but good to know everything is ready to go.
Just to be sure, going to test the startup disc in my old laptop (just run it "live"... make sure it boots up)

---

### Post by yancek on 2021-03-09
My understanding is that partition is for hardware diagnostics.  There are plenty of hardware diagnostic tools available for Ubuntu so you may not need it.  I've never used Dell, so if this partition is small compared to the entire hard drive it might be better to leave it.  You would need to get into the BIOS to boot it for your diagnostics

---

### Post by acefromspace on 2021-03-09
That's what I thought.. don't really need it (ubuntu has stuff) and I already have a hardware utilities disk.

---

### Post by acefromspace on 2021-03-11
Fresh install went fine. Did update after (I just prefer to do that... doesn't really matter) I can't seem to find ubuntu restricted extras (usually the first thing I do next) Did I make a mistake not checking "install third party...") during install?
How do I fix that (if that's an issue)
Also, how do I view the file system? 
I installed chromium and imported bookmarks. Logged in but can't seem to restore saved passwords. Should I download Chrome (that's what we used before)?
Now the fun part... teaching mom to use unity (my son had it setup with the old gnome style before)

---

### Post by tea for one on 2021-03-11
> **acefromspace said:**
>  I can't seem to find ubuntu restricted extras (usually the first thing I do next) Did I make a mistake not checking "install third party...") during install?
How do I fix that (if that's an issue)

Not a mistake - open a terminal and enter:-
```
sudo apt install ubuntu-restricted-extras
```

---

### Post by acefromspace on 2021-03-11
ubuntu-restricted-extras... done. Thank you.

---

### Post by TheFu on 2021-03-11
If you don't setup a separate data partition, anything installed into the live-boot of the Try Ubuntu setup won't be saved.  Every time you boot, you'll need to reinstall and reconfigure all those programs.

There is a tool, mkusb, which will let you boot from an ISO and install programs and keep data in an "overlay" file system so it is retained.  But you can't update the kernel.  ISO files are read-only by design. They cannot be updated.

In general, Ubuntu files need to be stored on Linux file systems, not NTFS and NOT FAT32 or exFAT.  That's because Linux expects to control permissions and have expected file system capabilities work which aren't supported by MSFT file systems.  For flash storage, the f2fs file system is probably the best choice today for a Linux system.  Create a 10G partition on the data flash drive and try it out. You can format the other part of that flash drive as exFAT if you want to share it on Windows. If it will never be plugged into Windows, there is no need to have any exFAT or FAT32 or NTFS. Those will just confuse any issues you have.

Linux cares about file systems, permissions, owners, groups, ACLs and xattrs. MSFT file systems don't support all of those in the expect way.

---

### Post by acefromspace on 2021-03-11
TheFu, I sort of understand but didn't have any issues with the data files I stored on the flash drive. Everything seems fine. I would like to learn more though so will read this again later.
When I first used the flash drive, it showed filesystem as DOS (I'm guessing FAT32) Thanks for the "heads up". I am busy celebrating... just got the new printer to work (posted another thread on that) so everything is working great.

---

