---
title: "Cannot install Ubuntu on HP Pavillion X360 13-a220nw"
date: 2017-04-24
forum: Installation &amp; Upgrades
---

### Post by borys123 on 2017-04-24
Hello,
I'm starting a new thread as I haven't found anything related to my problem, all threads about my notebook describe different problems than mine.

I am trying to install Ubuntu (I've also tried other distros with the same results) on my HP Pavillion X360 13-a220nw, using a bootable image on USB. 
After disabling secure boot in BIOS I am able to enter the GRUB but after selecting whichever option (compatible, even oem install) all I get is blank black screen.
Tried using nogui, to no avail. Only once (without any specific changes to the options) was I able to enter the system, with GUI, but after installing it, I was not able to boot into the system, only the GRUB was working. After deleting that partition, I was never able to boot to any linux system again.

I'm not a Linux expert, any suggestions I can try to solve my problem? After reading different forums I see that people have problems with Linux on my model but they either cannot get the BIOS to run the USB or have no sound after booting.

---

### Post by oldfred on 2017-04-24
What are specs of system?
And what video card/chip?

If you have Ubuntu installed:
       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

But almost all HP have required various work arounds.
       
 Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 

 Most older systems users had to manually copy files. Boot-Repair's advanced mode with 'Use the standard EFI file'  will auto copy files.
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by borys123 on 2017-04-25
Core i5 5200U CPU, integrated Intel HD 5000 graphics.
Thanks for your suggestions, I will try them today in the evening :)

Edit: Your advices mostly mention setting the UEFI boot, do they really apply to my problem if I have already found the way to boot into the GRUB but after hitting enter at whichever entry the only thing I get is blank screen? As I previously said I'm not an expert but I'm not sure if it's worth to tamper with the partitions on the USB stick.

As for the BootInfo, I cannot get any Linux distro to work at the moment.

It boots into grub when the pendrive is partitioned MBR, no secure boot and only in USB 2.0 port.

---

