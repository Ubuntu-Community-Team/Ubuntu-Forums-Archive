---
title: "Gnome 17.04 won't boot into OS again"
date: 2017-10-26
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2017-10-26
After a successful install if Ubuntu gnome 17.04 (I thought) I started my newer HP laptop this morning after a successful log off last night and was meet by a black screen that went through this check of some kind and ended with this.
Of course none of this made any scene to me so here I am.
This also happened on a previous install when it dimmed the screen and would not wake. I hard booted and this was the same outcome.
Here's two screen shots (and I mean screen pictures <g>) of the out put.
BTW this happened with any version install after 16.04.1. I can't seem to upgrade!
Thanks in advance for any help in being able to use future upgrades.
Bob.

---

### Post by Bashing-om on 2017-10-26
bob brazie; Ouch !

That says that the file system is corrupt, we take the system's advise and run that "manual" file system repair.

Must be conducted from a liveUSB(DVD) !

Verify the target partition:
```

sudo parted -l

```
#From liveDVD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```

Fingers crossed it is not a hardware fault !

[INDENT][INDENT]a step in the right direction
[/INDENT][/INDENT]

---

### Post by bob brazie on 2017-10-26
Wow! That's a lot to type. Thanks for the timely reply.
Do I type these commands in a terminal from the live USB?
I can't try your suggestions just yet as I tried to re-install gnome 17.04 three times and now I get a message saying: "The Grub-efi-amd64-signed package failed to install into 1target1."
I reinstalled Ubuntu 16.04.1 and it is running fine but I would like to try the new versions. And can't as I stated that all new versions past 16.04.1 result in the same failure after installation. I even tried upgrading 16.04.1 to the new 17.04 with the same result.
You mention something about maybe a hardware fault. Is there a way to check for that?

---

### Post by Bashing-om on 2017-10-26
bob brazie; Hummm ....

> 
Do I type these commands in a terminal from the live USB?

Answer: Yes

> 
You mention something about maybe a hardware fault. Is there a way to check for that?

Answer: There is the linux tool "smartctl" to run a SMART check on the hard drive to check its status.
```

sudo smartctl -a /dev/sda

```
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335) <-How to read output of smartctl
again make sure of the target device - here the 1st had drive that the system recognizes as "sda" . Adjust to suit your needs.

> 
 "The Grub-efi-amd64-signed package failed to install into 1target1."


Be aware I have no experience with the newer EFI systems . Here the errors to me indicate a trust issue .
This "should" not happen as the kernel is signed to enable installing the software .

What you might try is to temporarily disable secure boot in the firmware and update/upgrade the present install.
```

sudo apt update
sudo apt full-upgrade

```
With the thought that you have nvidia graphics, and in order to install the proprietary driver for the card - as you trust the source - you must disable secure boot to allow the software installation.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by bob brazie on 2017-10-26
"What you might try is to temporarily disable secure boot in the firmware and update/upgrade the present install."

Is it possible that this is causing the problem of not finding/booting into the installed OS?

---

### Post by Bashing-om on 2017-10-26
bob brazie' Well ..

A lot of factors to consider in booting up .
Did you verify the .iso file ? did you verify the copy to the install medium ? did you check the box in the install to also install updates while installing ?

[INDENT][INDENT]many times I do wonder
[/INDENT][/INDENT]

---

### Post by bob brazie on 2017-10-30
Here is the output. I don't know how to make it see the drive.
I have tried re-installing gnome 17.04 two times and on re-boot I get the same errors and it will not boot. I tried enabling legacy support and disabling secure boot.
I cannot boot into recovery mode for some reason and when I reinstall it shows the installation is there. I tried re-installing and that did not work any better than a clean install.
This is a shame as ubuntu is supposed to be easy to install and use. I have been a user since 9.04 and would really enjoy using the gnome version. This has been the case since 16.04.1. Any version higher then that causes the same errors. Not sure what changed since then that would cause this to happen.

ubuntu-gnome@ubuntu-gnome:~$ sudo parted -l
Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? i                                                          
Model: Lexar USB Flash Drive (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      43.3MB  45.7MB  2359kB               EFI


Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1000GB  1000GB  ext2


ubuntu-gnome@ubuntu-gnome:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
/dev/sda1 is in use.
e2fsck: Cannot continue, aborting.


ubuntu-gnome@ubuntu-gnome:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.43.4 (31-Jan-2017)
/dev/sda1 is in use.
e2fsck: Cannot continue, aborting.


ubuntu-gnome@ubuntu-gnome:~$

---

