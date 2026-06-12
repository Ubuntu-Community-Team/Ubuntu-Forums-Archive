---
title: "Boot repair and broken grub"
date: 2022-02-15
forum: Installation &amp; Upgrades
---

### Post by dushyantsahoo on 2022-02-15
I'm trying to fix grub from a USB drive. I am not sure why the problem happened. I was running Ubuntu 20.04 and restarted normally and on the restart, I get grub-rescue screen. I don't have windows installed, just the Ubuntu. I am currently using usb to fix it. I ran Boot-repair but got below error 

    Error detected in grub_mkconfig

After rebooting, I was taken to grub screen. I am trying solutions of 
[https://unix.stackexchange.com/questions/52726/after-bios-splash-will-not-boot-asked-to-select-os-but-cant/52790#52790](https://unix.stackexchange.com/questions/52726/after-bios-splash-will-not-boot-asked-to-select-os-but-cant/52790#52790), [https://unix.stackexchange.com/questions/96977/grub-probe-error-failed-to-get-canonical-path-of-cow](https://unix.stackexchange.com/questions/96977/grub-probe-error-failed-to-get-canonical-path-of-cow), [https://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow](https://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow) and [https://askubuntu.com/questions/1262733/install-grub-on-mounted-filesystem](https://askubuntu.com/questions/1262733/install-grub-on-mounted-filesystem), but nothing worked. I run the following:

    sudo mount /dev/sda1 /mnt
    sudo grub-install --root-directory=/mnt /dev/sda
I get the following error:

    grub-probe: error: failed to get canonical path of /cow.
Even when running

    sudo grub-mkconfig > /boot/grub/grub.cfg

or

    update-grub

in chroot, I get the same error. Pastebin link: [https://paste.ubuntu.com/p/sT23JKdBr8/](https://paste.ubuntu.com/p/sT23JKdBr8/). Can someone explain the error, and explain how to solve it? 

This is the result of running sudo fdisk /dev/sda command

    Device     Boot      Start        End    Sectors   Size Id Type
    /dev/sda1  *          2048 1901873141 1901871094 906.9G 83 Linux
    /dev/sda2       1901875198 1953523711   51648514  24.6G  5 Extended
    /dev/sda5       1901875200 1937033215   35158016  16.8G 82 Linux swap / Solaris
    /dev/sda6       1937035264 1953523711   16488448   7.9G 83 Linux

---

### Post by oldfred on 2022-02-15
Cow is copy on write or the live installer. 
You were attempting to update grub on live installer.

On my system a sdf flash drive on reboot of system becomes the sda drive.
So you need to know which drive is live installer & which drive is your install.

Your fstab has a comment on a /boot partition, but no entry.
Did you have a separate /boot partition? And first attempt at reinstall removed /boot from fstab?

From Boot-Repair you can use advanced mode & do a full reinstall of grub & include the latest kernel. 
That would in-effect revert to /boot as a folder in / not a separate partition. A /boot partition is not normally required for desktop type installs.
If server install oo LVM with full drive encryption you may need a /boot partition.

---

### Post by dushyantsahoo on 2022-02-15
I did reinstall grub and kernel and it returned with an error -recheck exit code 1. Here is the pastebin of the result: [https://paste.ubuntu.com/p/nRf4Q29pfv/](https://paste.ubuntu.com/p/nRf4Q29pfv/)

---

### Post by oldfred on 2022-02-15
Not sure if Boot-Repair issue or your system.
You had 5.11.0.27.29~20.04.11 Kernel but it reinstalled  5.4.0-99.
The 5.4 is from original 20.04 or 20.04.1 which I have and have the -99 kernel.
But if you more recently installed or if you installed the enablement stack, you get newer kernels.

Not sure why it dumped all the kernels.

It is as if you changed permissions of / (root) and now nothing is working?

I might try a full chroot where you manually mount your partitions and do the kernel install, update system, houseclean old kernels, and reinstall grub. 

To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://ubuntuforums.org/showthread.php?t=1470597&p=9226662#post9226662](https://ubuntuforums.org/showthread.php?t=1470597&p=9226662#post9226662)
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by dushyantsahoo on 2022-02-16
I am not sure how it happened. I followed the suggested links but when I run update-grub, I get grub-probe: error: failed to get canonical path of /cow. When I restarted my laptop, I was taken to grub-rescue screen.

---

### Post by kevdog on 2022-02-16
Did you do a chroot?  Here is a video showing how to do this-- [https://www.youtube.com/watch?v=599BR1goYJg](https://www.youtube.com/watch?v=599BR1goYJg)

---

### Post by YannBuntu on 2022-02-16
hi dushyantsahoo,
there are several 'Read-only file system' in your boot-repair log, ie permissions on sda1 are incorrect. This aligns with the /cow error you had previously with grub-probe.
Also, you have used boot-repair after having done several manual operations (eg sda1 was already manually mounted on /mnt).
Please can you run boot-repair recommended repair from a fresh live session and indicate the new URL ?  this will show us if the permission error is permanent or was due to your initial repair attempts.

---

### Post by MAFoElffen on 2022-02-16
The meaning of a "fresh live session" is that you would need to reboot with the LiveCD and start over, so that nothing you have done in the previous session is remaining in memory... To let the scripts decide how to handle things without distractions...

---

### Post by dushyantsahoo on 2022-02-16
Yes, I tried that and got error "failed to get canonical path of /cow.". I wish everything went smoothly

---

### Post by dushyantsahoo on 2022-02-16
Hi, thanks for helping. Below is the pastebin of fresh attempt

[https://paste.ubuntu.com/p/TrvjRRTxqh/](https://paste.ubuntu.com/p/TrvjRRTxqh/)

---

### Post by dushyantsahoo on 2022-02-16
I might have missed a critical information here, sorry. I have 8gb SSD and one which I think I installed Ubuntu long ago (2017) because of which there might be some problem in boot repair?

---

### Post by dushyantsahoo on 2022-02-16
How can I correct it?

---

### Post by oldfred on 2022-02-16
It only shows sda & flash drive.

If a 8GB SSD, is that Intel RST, RAId or similar?
Microsoft was for a while requiring vendors to add small cache SSDs for Windows fast startup to make system boot faster, as Windows does not boot very quickly.
Usually the SSD was about the size of RAM, but some vendors did put larger SSD up to 32GB. If larger, we have seen users erase the Windows hibernation & Intel RST, and use SSD as Ubuntu / (root). But your 8GB is too small for anything.

You do need Intel RST/RAID off and AHCI on for drives for Ubuntu to work. Only if dual booting with Windows, then you need AHCI drivers in Windows. Check UEFI settings.

You have BIOS/MBR install, but system may be UEFI?
And you have nVidia GeForce GTX 960M which needs nVidia driver.

---

### Post by dushyantsahoo on 2022-02-16
I am not using windows on the laptop, it is just Ubuntu. Probably I might have mistaken about 8gb boot and that is not causing an issue here. Is there something else which is causing the issue in boot repair?

---

### Post by oldfred on 2022-02-16
Yann in post #7 is the author of Boot-Repair.
Did you make any of the changes he seems to say is the issue?

Are you able to chroot into system and install grub, or did other changes you must have made previously totally break system?
Often if it takes more than a couple of hours to debug & fix system, better to just reinstall & restore from backups.
I regularly install every 6 month release, often more than once just to see what is changing. And install to SSD is just over 10min, restore of data & updates, now mostly scripted takes less than an hour. Longest time is reinstalling apps from exported list from old install into new install.

---

### Post by dushyantsahoo on 2022-02-17
[SIZE=2][FONT=arial]Yes, I tried those changes and [https://paste.ubuntu.com/p/TrvjRRTxqh/](https://paste.ubuntu.com/p/TrvjRRTxqh/) is the new pastebin. But it does not seem to work, I have a new error- 
[/FONT][/SIZE][SIZE=2][FONT=arial]Error detected in grub_mkconfig

I did chroot into the system and installed grub, but I again get an error when I perform update-grub. 
I am scared to do reinstall, I am almost finishing up my PhD and I don't want to loose any information. So it would be great if I could resolve this issue otherwise I can do reinstall as you suggested[/FONT][/SIZE]

---

### Post by oldfred on 2022-02-17
We regularly report here that if your data is important, you must have backups. 
What if hard drive totally failed tomorrow? 
And see lines 17-23 in report, it may be hard drive.

From live installer and Disks (gnome-disks) in upper right corner is Smart Status.
All I know is whether it says drive is good or bad, but it can run tests to check for issues.

---

