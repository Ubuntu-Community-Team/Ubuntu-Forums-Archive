---
title: "Grub menu not showing up after installation"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by Curbside Jimmy on 2014-10-28
I installed Ubuntu on two computers today. Each installation is on a unique ext4 partition. Windows is on a seperate one. In each case the grub menu doesn't come up and windows starts. This has never happened before. So, I don't have a way to get to the ubuntu os on eiter computer.

Oddly, a Grub Super Disk doesn't start when I try starting from the DVD drive.

Could I have missed a step in the installation dalog? Or, perhaps Microsoft is putting stuff in updates to keep Linux from loading.

Does anyone have any suggestions? I only use Windows 7 when there is  no other choice.

---

### Post by Curbside Jimmy on 2014-10-28
I just finished loading ubuntu onto two computers. Each installation was on a unique partition with an ext4 format, Each computer has Windows seven on a separate partition.

In both cases now Grub os menu doesn't load when I boot up. This has never happened before. I have a Grub 2 Super disk as well as the old version. Neither of these will load from the DVD on start up. 

Is there something on the installation dialog I may have done wrong? 

Or, perhaps Windows updates are now keeping Linux from loading?

Anyone have any ideas?

---

### Post by yancek on 2014-10-28
> Is there something on the installation dialog I may have done wrong? 

There are all kinds of things that could have gone wrong but since we don't know much about what you did, we are left to guess.
If you have windows 7, is it using the standard MBR method to boot?
Are you able to boot windows?
Did you use the "Something Else" manual option during the install of Ubuntu or the install alongside method?
Did you accept the default for Device for bootloader installation of sda?
Can you boot the Ubuntu installation medium?

---

### Post by grahammechanical on 2014-10-28
Why have posted the same question twice?

[http://ubuntuforums.org/showthread.php?t=2250457](http://ubuntuforums.org/showthread.php?t=2250457)

---

### Post by fantab on 2014-10-28
Are you able to boot Ubuntu?
Are you able to boot Windows?
If your computer boots directly to ubuntu directly then your Windows is not being detected by Grub. When there is only one OS then [Grub menu is hidden]("https://help.ubuntu.com/community/Grub2#Hidden"). Try holding the SHIFT key at boot.

Post the output of:
```
sudo parted -l
```

---

### Post by oldfred on 2014-10-29
We can really only work on one computer per thread. Pick one.

What is the brand, model system?
Is it a new UEFI based system or an older BIOS based system?
If newer did you install Ubuntu in UEFI boot mode?

May be best to see details.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Curbside Jimmy on 2014-10-29
I don't have a way to load ubuntu. Windows comes up automatically. Ubuntu is loaded, just not useable.

In the past I have often used a Super Grub disk to find all operating system but the disk is unrecognized, both Grub 2 and the old one.

---

### Post by oldfred on 2014-10-30
Duplicate threads merged.

Please do not create duplicate threads. We are all volunteers and need to know what has already been suggested so as not to duplicate efforts.

Use live installer that you used to install Ubuntu and run the summary report from Boot-Repair.

---

### Post by Curbside Jimmy on 2014-10-30
The biggest problem is an Acer AX1430-UD30P, Desktop.

Ubuntu is installed on a seperate partition from Windows 7. On every other occasion when I have installed Ubuntu this way, the Grub opperating system menu comes on when the machine is turned on. Grub does not come up. The CD rom does not load a Grub Super Disk. 
Pressing F2 , F8 or F10 brings up a menu but there is no option for booting from the CD Rom, at least not one I have found. If I could find a way to change the boot sequence, a Grub disk would probably work. I don't know many Linux or grub terms.

I have done about 10 Ubuntu installation without a problem. This has never happened before. The Ubuntu partition shows up on an easeus partition program.

---

### Post by yancek on 2014-10-30
Can you boot the installation medium for Ubuntu from a DVD or flash drive so you can run some commands and get some pertinent information?

If so, try:  sudo fdisk -l
               parted -l

Both commands, a Lower Case Letter L.  You could also google 'bootinfoscript' if you have an internet connection from the DVD/flash drive then download and run it.

---

### Post by oldfred on 2014-10-30
Acer have a few idiosyncrasies, not sure if your model is similar:

       Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)

---

### Post by Curbside Jimmy on 2014-10-30
yancek,
I will try to load Ubuntu from the DVD like you suggest. 
I don't know much code, but I recognize fdisk as part of msdos. 

Before I type in the code should it all be on one line like sudo fdisk -l parted -l?

or would it be two seperate commands like sudo fdisk and then sudo parted -1 on a seperate line?

---

### Post by yancek on 2014-10-30
> or would it be two seperate commands like sudo fdisk and then sudo parted -1 on a seperate line? 		

sudo fdisk -l, then hit the Enter key and post the output, repeat with parted -l, then hit enter and post output.

---

### Post by fantab on 2014-10-31
```
sudo parted -l
sudo fdisk -l
```

You can copy paste the above commands in Terminal. Those are two different commands and should be run separately.

---

### Post by Curbside Jimmy on 2014-10-31
Its time to close this thread. It turns out that on the Acer desk top F12 brings up a boot menu. So, the Grub Super Disk finds ubuntu and I can run it. 

ubuntu does not seem to run well on the Acer. I am going to try and figure that out and make another post if need be. Right I am going to re-install ubuntu and see of the second try works better.

Thanks Everybody

---

### Post by oldfred on 2014-10-31
It may depend on what version you are installing as this bug has been fixed but only in very new version(s).
Just to be safe only use Something Else to reinstall and make sure you have good backups.

       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

