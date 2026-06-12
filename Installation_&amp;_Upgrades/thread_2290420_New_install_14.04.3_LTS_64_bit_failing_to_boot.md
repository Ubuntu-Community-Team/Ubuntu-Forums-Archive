---
title: "New install 14.04.3 LTS 64 bit failing to boot"
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by richard130 on 2015-08-12
Hi,


I have a work computer which shipped with Windows 7 enterprise and I'm trying to put ubuntu 14.04.3 LTS 64bit on it as a dual boot. I go through all the installation fine, but when I select ubuntu from the boot loader I get


```

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT ! /Dev/disk/by-uuid/xxx does not exist. Dropping to a shell


BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
enter 'help' for a list of built-in commands.
 
(initramfs)

```

and it ends up in a shell


(note I don't have the uuid to hand)


I have had a thorough search of google to try to fix this and I come up with nothing that works. There is no encryption or RAID set up or anything like that.


I have tried:
1. reinstalling grub loader using [these]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") instructions
2. updating initramfs using 

```
[COLOR=#000000][FONT=HelveticaNeue]sudo mount /dev/sda5 /mnt[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]sudo mount --bind /dev /mnt/dev[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]sudo mount --bind /proc /mnt/proc[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]sudo mount --bind /sys /mnt/sys[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]sudo chroot /mnt[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]update-initramfs -u[/FONT][/COLOR]
```

a bit like [here]("http://askubuntu.com/questions/456903/ubuntu-14-04-not-booting-update-initramfs-nothing-to-do-exiting")

3. Following the instructions [here]("http://www.proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/")

And so far nothing works.

In all of the above I've been mounting sda5 as on my system after the install sda1 and sda2 are small windows partitions (booting or whatever) sda3 is the main windows partition, sda 4 is the extended ubuntu partition consisting of sda5 as OS and sda6 as swap space. Am I right in doing this?

I'm installing from a bootable USB drive which works fine. I have verified the checksum on both the ubuntu iso and the utility (from pendrivelinux.com) which put it on the usb stick. Although if I use the check disk utility on the live USB it claims two files have issues but doesn't let me view them or do anything other than reboot. This prompted redownloading the iso and usb utility, reinstalling everything and verifying the checksums.

I'm sort of coming to my wits end on this one. Having done a few installs in my time (but still a newb really) I've never had so much trouble and have tried far more complicated partition arrangements in the past with success. It's sort of not good enough considering how Ubuntu is positioning itself; this is a completely vanilla dual boot of a LTS release on a bog standard Dell windows 7. [Rant over].

Any help would be much appreciated.

Thanks,

Rich.

---

### Post by dino99 on 2015-08-12
As it is a dual boot with w7, a few questions about the config first:
- is it a bios or uefi ? is there a gpt windows installation ?
- is the hdd(s) normmally used ? or set as 'raid' 'lvm' ?
- where have you install grub ? (the bootloader) (usually set into /dev/sda)

for explaining the different cases, that have been already explained many times, please search & read the posts/threads of 'oldfred' which usually answer about such config
[http://ubuntuforums.org/showthread.php?t=2289736&highlight=oldfred](http://ubuntuforums.org/showthread.php?t=2289736&highlight=oldfred)

---

### Post by nijil on 2015-08-12
busybox problem
please help

---

### Post by oldfred on 2015-08-12
It sounds like you have done several of the regular fixes & it should be bootable.

Lets see lots of detail, but not sure what it may show?
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Another way to boot is Supergrub.
       
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by richard130 on 2015-08-12
Ok, let's see what I have here:

According to [this]("http://kb.parallels.com/en/115815") the boot is via BIOS not UEFI.
According to the instructions [here]("http://www.tomshardware.com/forum/268934-32-disk") the disk is MBR. Yep the drive is just used normally.
Here is the boot info output: [http://paste.ubuntu.com/12067336/](http://paste.ubuntu.com/12067336/)

Let me know if there's anything else I can provide which is helpful.

Thanks,

Rich.

---

### Post by oldfred on 2015-08-12
I am not seeing anything specifically wrong.

And your chroot should have fixed a initramfs issue, if that is all it is.

Is UEFI/BIOS set for AHCI for drives?
Is system UEFI, but you elected to install in BIOS mode? Or an older system?

You could use Boot-Repair to do the full uninstall/reinstall of grub and reinstall newest kernel. That is like another chroot.

You can also try booting with SuperGrub and then may be able to run repairs from inside install instead of chrooting.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by richard130 on 2015-08-12
So,

I have also tried reinstalling over the existing install, with no joy, it decided to swap the ext4 and swap partitions around in sequence this time, that is sda5 is now swap and sda6 is ext4, although they look to be in the same place according to the Windows disk utility tool.

I have tried doing boot-repair as found [here]("https://help.ubuntu.com/community/Boot-Repair"), with output: [http://paste.ubuntu.com/12068055/](http://paste.ubuntu.com/12068055/)

No joy, but it also has had the side effect that in grub there 'appears' to be 2 windows installs under sda2 and sda3, there was only sda3 before. And now the sda2 100Mb partition is navigable from windows as the D: drive. All this wasn't the way it was before.

I'm starting to think that the boot partitions on the machine are now an unholy mess and I might get IT support to do a clean install of Windows on the machine and try starting over (though I suspect I may have similar issues as I would just be doing what I did before).

Rich.

---

### Post by richard130 on 2015-08-12
> [COLOR=#000000]Is UEFI/BIOS set for AHCI for drives?[/COLOR]
[COLOR=#000000]Is system UEFI, but you elected to install in BIOS mode? Or an older system?[/COLOR]

I really don't know to be honest. How would I find out? This is a brand new system, I haven't elected to do anything (AFAIK), just factory installed Windows and then plonked a live USB on it. I guess it might be and have had it overwritten to BIOS at some point with all my tinkering, but I haven't explicitly seen that option.

Would ms-sys have done that?

Might look into supergrub, but I think I might just try starting from scratch...

Rich.

---

### Post by oldfred on 2015-08-12
Your Windows boot partition is sda2 as the 100MB NTFS partition with the boot flag.
Boot-Repair now copies bootmgr & BCD from Boot partition to main install. Many users did not know the normally hidden 100MB partition was vital for Windows boot and delete it. And there is no easy way to recover boot files if user did not create a separate Windows repairCD or flash drive. 

Boot-Repair cannot install Windows boot files.
But then grub2's os-prober sees two bootable partitions as it looks for boot files not just the boot flash that Windows uses.

---

### Post by richard130 on 2015-08-13
Sure, that makes sense, if a little OTT perhaps. Any ideas though? Sorry...

---

### Post by richard130 on 2015-08-13
UPDATE: I installed 15.04 over 14.04.3 LTS and it boots fine.

BUT I really didn't want to do this, I want the LTS, it seems as though a fix is needed.

As if to prove my concerns valid with 15.04 the screen gets garbled on the inbuilt display (not on external monitors) when I log in/log out and generally isn't stable (desktop being tiled and translated seemingly at random).

Is this a known bug?

Does anybody have any ideas what I should do?

I attempted Linux mint 17.2 as it has LTS, but it refuses to connect to the PEAP wifi security at my work...

---

### Post by oldfred on 2015-08-13
Often a lot of issues are related to video. 
What video card/chip does your system have?
What brand/model system?

---

### Post by richard130 on 2015-08-14
Dell E7450, core i7 5600U, Intel HD5500 (broadwell GT2)

---

### Post by oldfred on 2015-08-14
With Broadwell that is a very new system which needs newest kernel, support software & video drivers. But I thought that 14.04.3 updated to the same kernel as 15.04 which is 3.19.

 Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)

Often you have to tell the driver what screen size to use.


 Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

You add boot parameter like nomodeset:
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

     
 

If it works then you can add it to grub configuration to make it permanent.

---

