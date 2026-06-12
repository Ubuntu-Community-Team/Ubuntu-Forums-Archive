---
title: "Issues Booting From an External HDD"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by Tramx on 2012-10-30
Hi, I was attempting to install Xubuntu on my external HDD to make my Linux OS more portable. I successfully installed Xubuntu (32-bit) on my HDD with the desired ext4 filesystem and swap space and configured my BIOS (on my HP Pavilion dv6 series)  to boot from usb HDD first. Despite all this it will not boot from the HDD and gets stuck with a blank screen, and will not continue. (I require the OS to work on my main HP.)

I tried to plug the HDD to my Toshiba machine and it booted fine.
Please note that my HP machine is a 64-bit system as opposed to my Toshiba machine. Can there be an issue with the BIOS on my HP machine that is causing this problem OR should I try installing a 64-bit version Xubuntu?  :confused:

Guidance appreciated,
Thank you

---

### Post by oldfred on 2012-10-31
Do you have a very large / (root) partition? Some BIOS or grub issues cause boot issues with very large / partitions. 

Or it could be a video issue. If you hold shift key from BIOS do you get grub menu? The can you boot from recovery mode?

---

### Post by Tramx on 2012-10-31
Oh, yes my root partition is very large, it takes up all the space of my HDD that is not including swap (950GB is size). I tend to do this because I dislike to split partitions. Similarly configured, Windows on my internal HDD works fine. 

Regarding GRUB, true, it normally comes first always, but in my case there is just a blank screen and nothing comes up whatsoever even when pressing SHIFT (I can't see GRUB or get into recovery mode), which makes me doubt it is a video card issue. Installing from the live-cd GUI works fine though. Odd.

---

### Post by oldfred on 2012-10-31
If it works on your other computer, it has to be something unique to your HP. 

Some can also be BIOS settings.

 If you have Fastboot or Quickboot or similar turn that off. 
Is system in AHCI mode? 
BIOS & disable "Boot Sector Virus Protection"
Some BIOS do not boot from USB3 ports, but work from USB2.

---

### Post by coldraven on 2012-10-31
Make sure that you do not have any other USB media connected.
My laptop won't boot from external HDD if I forget to remove the SD card that is always in the card reader.

---

### Post by Tramx on 2012-10-31
Yes, I have realized that the BIOS will not boot from the USB 3.0 ports (it will skip straight to booting into my internal Windows HDD). It is when I boot from my 2.0 ports that the screen goes blank and seemingly hangs. I am unsure whether my system is in AHCI or not. Please show me how to disable this Quickboot, as I cannot find these options in the BIOS (it is a limited InsydeH20 BIOS).

@coldraven, I have disconnected all USB/SD devices (even the mouse) and the results are the same.

---

### Post by oldfred on 2012-10-31
If you have one of those really limited BIOS, you may not have many settings.

It can still be a video issue or a system needing other boot options. Boot options are often  unique to each vendor's system.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I always need nomodeset to boot first time until I install nVidia drivers. But if you want a system that boots multiple systems you should not install proprietary drivers although some have used scripts to switch drivers.

---

### Post by Tramx on 2012-10-31
Ok, I will try as you suggested and re-install Xubuntu, one slight issue with this though. I am using Xubuntu Desktop Live CD and will directly boot into GUI install, and there are no options to pre-config the GRUB menu isn't there? Do you know of a way I can accomplish this by getting into GRUB pre-installation? Also, do you recommend changing only NOMODSET or the acpi settings as well? As I said I am not certain, but I think my system is in acpi mode.

---

### Post by oldfred on 2012-10-31
Acpi is a seperate issue that used to be larger, and has to do more with power settings and saving power. 

You want AHCI which has to do with drive support. Alternative is Large, LBA (Large Block Allocation), but not IDE every BIOS varies on names.

Does your liveCD have the little accessibility  icons at the bottom of the screen for just a few seconds when you start to boot. Press any key to get a menu, then f6 to get boot options. You can add nomodeset.

---

### Post by Tramx on 2012-10-31
Pardon me! I've got the terms confused, ACPI is most likely not the issue here. I came across it once when installing kernel modules for power management. As mentioned earlier, my limited BIOS settings doesn't have options to switch between AHCI and IDE modes and I presume defaults to AHCI. I am also guessing that Linux installs these drivers by default which is good.

Yes, it does have accessibility options in Live-CD and I will proceed with installation. I will inform you if it works.
Thank you.

---

### Post by Tramx on 2012-10-31
The problem still persists... The computer hangs a while at the start-up (before BIOS) and then continues booting up into Windows. There is no sign of Xubuntu running whatsoever. :(

Edit: After some reading, is it beneficial if I installed a /boot partition as well? Is this the root cause of the problem?

---

### Post by oldfred on 2012-10-31
Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

We have seen some issues with either certain BIOS or grub2 bug that very large / (root) partitions will not boot. Solution has been a separate /boot  or smaller / (root) within the first 100GB of the hard drive. Only some users seem to have this issue and I do not think there is even a grub bug report as it is so inconsistent. But Boot-Repair reports it for those that may have issues. 

Did you check on the other BIOS settings. Many laptops do not have much of a BIOS or UEFI but some setting are not obvious that they may be an issue.

---

