---
title: "Cannot boot after Hardy Install"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by robertjlee on 2008-06-28
I am having booting problems. When I boot, I get the normal BIOS messages, then text-mode with a flashing cursor in the top-left corner. No GRUB menu appears.

My new Ori-series desktop ([http://efficientpc.co.uk/desktops/ori/](http://efficientpc.co.uk/desktops/ori/)) came pre-loaded with Ubuntu 8.04.

As shipped, I had problems booting with my PS/2 mouse plugged in. But after unplugging it, everything worked and the system would boot straight in every time. The seller (Efficient PC, a Canonical approved vendor) only used the first hard disk and didn't set up software RAID or encryption, so I chose to re-install.

I installed from the Alternate CD, and set up a RAID-1 (mirrored) array for the /boot partition (at the start of each disk), and RAID-5 for an encrypted / partition (I forgot to include swap). This eventually installed, but the process proved to be a rather buggy one (ie if I made one mistake I had to reboot and start again).

Having finally got the OS set up, I found I could only get the system to boot by booting from the install CD and selecting "boot from first hard disk". I tried installing grub onto the MBR of (hd0), and it made no difference; I could boot fine through the CD but not directly from the hard disk.

As an experiment, I ran ```
apt-get install mbr
``` and used that to install a new MBR boot-loader to chain the grub boot-loader installed on (hd0,0). This made no difference when telling the BIOS to boot from the hard disk. When booting from the CD, and chaining via the "boot from first hard disk" option, I got the boot-loader prompt asking me which partition to boot from; **A** selected advanced mode but no other keys (**1** or **Enter**) had any visible effect (even though the grub boot-loader seemed to be installed on (hd0,0) successfully).

My attempts to re-install grub on (hd0) fail with warnings about ext3_stage1_5 not being found when I run setup from the grub prompt, and give a "not found" error when trying to select any option. So I guess I'm looking at yet another reinstall just to fix the MBR, but I doubt that will avoid the need to boot from a CD.

If it wasn't for the fact that this is a brand-new machine that booted straight into Hardy when I first got it, I'd say this was a straight-forward BIOS problem.

Does anyone know how I can diagnose this problem?

Edit: Forgot to say that, to make it boot from an encrypted RAID disk, I had to fix the crypttab ([http://wiki.debian.org/DebianInstaller/RAIDvsCrypto](http://wiki.debian.org/DebianInstaller/RAIDvsCrypto)), but I don't think it's even getting that far.

---

### Post by mindedc on 2008-06-29
I have had similar problems. My system is a fairly new core 2 duo box with an ASUS motherboard with onboard intel SATA ports, a "jmicron" onboard controller with one pata and one sata port. I was running 7.10 with a CF to IDE adapter with a 256 meg CF card in the PATA port which was set in the bios as the boot disk and mounted as /boot. I then had two seagate baracuda PATA drives mirrored in a RAID 0 on a hotpoint IDE card. I then had three SATA 1Tb drives in a raid 5 on the motherboard SATA ports. I have a 3ware controller in there I have not used yet.

I wanted to go to 8.04 and 64 bit and get rid of those old baracudas, so I downloaded the 8.04 server install iso and burned it to a disk. I re-configured the hardware such that the CF adapter was in the hotpoint controller, two new SATA drives were on the motherboard intel SATA ports. I moved the CF adapter so I could put the DVD drive in the motherboard pata port and boot from it.

I pulled the raid 5 set for safety reasons. I put a new CF card in the CF adapter and installed 8.04. It let me make a new md0 on the two sata drives and install the OS. It automatically installs grub without any sort of prompting and reboots the system. From there I cannot boot into ubuntu. I have tried every permutation of moving the drives around as well as changing the grub parameters and what disk its installed on. Grub consistently gets an error 17. 

I am quite familiar with configuring grub manually and altering the maping file etc... Unfortunately it seems if you use a modern "enthusiast" motherboard it's hell to get grub to boot the system and I go through something like this every time I do a linux upgrade. My desktop system won't run an ubuntu install disk unless I pull my 25-in-one flash card reader that is built into the case off the usb.. go figure.

I spent two days doing different installs and configurations. Every time I was able to put the 7.10 CF card in and boot off the two old drives. With 8.04 I have never seen grub get to the command line using my CF disk or one of the sata drives as the boot disk. The only way to get it to work was to hang the drives off the 3ware controller and set them up as a hardware raid. I really wanted to get those hanging off different PCIe lanes on the motherboard controller as I prefer to have my data on different disks from the OS (and I run several VMs on the mirrored drives as well...). 

BTW, all of the patitions were xfs except the /boot which was ext2 since grub historically doesn't like xfs sometimes.

---

### Post by robertjlee on 2008-06-29
Hi mindedc,

I don't think we have the same problem, because I'm not getting an error 17. I'm not even getting as far as grub loading stage 1.5, and I don't think that stage 1 is loading either.

There are some useful links on possible booting problems here: 
[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

The big problem I have is that I don't get an error message, so the above guide isn't much use to me. But perhaps you'll find it helpful?

---

### Post by mindedc on 2008-06-30
Thanks for the link. I've already been there and tried all of the recomended solutions. I have also had the blinking cursor issue without grub even loading. I can't remember where and in what permutation of it I had that. It's moot for now as I appear to have cooked the chipset on my motherboard running the system with the case off while I was running on the old drives.... 

Hopefully I can get a replacement tomorrow and the CPU and memory are ok... I'm getting random segfaults in 7.10 which was rock solid before.... I put my hand on the cpu and it was ok, the heatsinks on the VRMs were warm but ok, memory temp was ok, chipset was hot enough to burn your hand. Of course it has a pathetic heat sink...go figure....

---

### Post by robertjlee on 2008-07-01
Well, my problem is solved thanks to the people at Efficient finally getting back to me.

What was happening was that the BIOS and GRUB had different ideas about which hard disk they were supposed to be booting from. 

Since my BIOS won't let me change the boot order, the proposed solution was to set up grub on the MBR of each hard disk:
```
sudo grub
grub> device (hd0) /dev/sda
grub> root (hd0,0)
grub> setup (hd0)
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> device (hd0) /dev/sdc
grub> root (hd0,0)
grub> setup (hd0)
grub> device (hd0) /dev/sdd
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

This worked, insofar as GRUB would start, but I still got an error 15: File Not Found.

I then had a brainstorm, and tried editing the option before I booted it, and removing the /boot prefix, which cleared that error and the system booted!

Rather than mess around any more with the OS-installed grub boot files, I figured the easiest permanent fix to the error 15 was to create a symbolic link from /boot/boot to /boot (so the paths would be right when booting from grub).

Rebooted and all worked as it was supposed to!

A week to install an OS, but I am now happy again.

Hope that helps someone else,

—Robert J Lee

---

