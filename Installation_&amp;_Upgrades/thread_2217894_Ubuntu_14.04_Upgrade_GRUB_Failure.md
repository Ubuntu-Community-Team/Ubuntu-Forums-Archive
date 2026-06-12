---
title: "Ubuntu 14.04 Upgrade GRUB Failure"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Harley_Lorenzo on 2014-04-18
First, let me post my current setup:

>64 bit Windows 8.1 running on UEFI firmware (smartboot and fast boot are turned off)
>Did have Ubuntu 13.10 running with absolutely no problems until lately
>Decided to upgrade to 14.04 as soon as possible
>Upgrade seemed to go without a hitch
>Boot and GRUB did not load, instead, Windows 8.1 loads immediately (perhaps GRUB did not install right)
>Thinking about doing these in order:
  1) Run bootrepair from a Live USB to try to fix GRUB, and if that doesn't work
  2) Reinstall Ubuntu 14.04

I would prefer the former as I have no separate /home/ partition and I don't want to backup my data first.

So, how my questions are:

What happened?
What should I do with bootrepair to fix this?
Was it a upgrade failure? Is this common? How come this hasn't happened to me before?
Was this Windows being greedy and hogging up the bootloader? If so, how do I fix this?
If none of this works, is it worth it to switch to Debian for the time being to see if that works?

Thank you in advance. (I know there are already a ton of threads popping up about errors and bugs in this new upgrade.)

---

### Post by kc1di on 2014-04-18
I would run boot-repair first, pay particular attention to and uefi information dialogues it spit out and follow them exactly. 
uefi or I should say secure boot and GPT partitioning is still a pain and is not always detected correctly by the installer. 

run boot-repair when it's finished make sure you get the web page for the report in case it does not work. and post the output here. 

Good luck ;)

---

### Post by Harley_Lorenzo on 2014-04-18
Will do! I will report what happens and the link as soon as I can.

Just let me create a LiveUSB real quick and write down the repositories I need to install Boot-repair.

---

### Post by oldfred on 2014-04-18
There is not a trusty ppa yet for Boot-Repair. 
Several work arounds.

       ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)

But I just installed ppa like normal but changed trusty to saucy and that worked.

 Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)
gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'

---

### Post by ubfan1 on 2014-04-19
The UEFI bootloaders are just sitting in a FAT filesystem on the EFI partition.  Ubuntu's bootloaders (shim.efi and/or grubx64.efi) should be sitting in /EFI/ubuntu on that partition.  If the ubuntu directory got corrupted and nothing is readable, you will need to repair it (see bug 1090829 ?)  If things look OK, try to select ubuntu from the efi boot menu (some function key at power on usually gives the choices of things to boot, maybe you have to select a hard disk first, then ubuntu).  Does that work?  If so, the problem may be just the boot order, which may be altered with the efibootmgr program (or just continue to use the efi boot menu).

---

### Post by Harley_Lorenzo on 2014-04-19
ubfan1, my UEFI setup page is setup just like a traditional BIOS, with only normal BIOS options (bootorder, USB Mouse Emulation, etc.) in there and has no option to change the bootloader from within.

Today, though, I will explore my UEFI partition to see if my bootloaders are intact and also explore my original mountpoint for Ubuntu to see if the data in there is also readable.

---

### Post by Luke M on 2014-04-19
This is a good tool to have handy when dealing with EFI:

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

Download the rEFInd .iso and put it on a CD or extract to USB.

---

### Post by dpiros on 2014-04-20
I had this same issue. I've tried boot repair from a live USB several times, and it doesn't seem to have done anything. I've also tried installing Ubuntu 14.04 to a new partition (to see if that might do it). No luck. I tried manually replacing bootx64.efi with grubx64.efi. Still no luck. It still booted into Windows.

Eventually, I realized I wasn't sure which bootloader the system was using (or even which partition it was on, I have two partitions with EFI boot structure for some reason), so I backed up the EFI System Partition, then deleted everything from it, and rebooted (so I could at confirm that the bootloader is on that partition). No operating system found, which is better than booting Windows. I then booted from the Ubuntu USB, and restored everything in the EFI partition except for EFI/Microsoft and EFI/Boot. Surprisingly, the next reboot gave me GRUB. It was the wrong GRUB (from my Mint install), but I managed to boot into Mint, restore EFI/Microsoft folder, and run boot-repair. After another reboot, I now get my Ubuntu GRUB. Both Ubuntu and Mint load. Windows does not, but I never use it, anyway, so I can figure that out later. I had a few defective Windows GRUB entries before, and now there's just one Windows entry, so I think I may have just lost the one that worked or something.

Still don't understand exactly what happened, but my system pretty much works now, so I'm good. If boot-repair from  USB doesn't work for you, try this (making sure to back things up), and see if it works. If not, you can just restore the backup.

My theory is that Ubuntu removed its entry from the EFI system, added it back, but put it at the end of the list, so the system found Windows first, and booted that. Remove Windows and the next entry (Mint) is booted. After that, it seems that boot-repair works better when you actually booted from the drive you want fixed.

---

