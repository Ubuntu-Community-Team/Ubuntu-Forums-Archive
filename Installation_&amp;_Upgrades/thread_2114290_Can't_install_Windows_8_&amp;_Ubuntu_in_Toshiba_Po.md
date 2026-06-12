---
title: "Can't install Windows 8 &amp; Ubuntu in Toshiba Portege Z930"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by Abrx on 2013-02-09
Hello,

I'm trying to install an Ubuntu 12.10 64bit in my z930 alongside a pre-installed windows 8, but Grub menu won't even show.

My pre-installed distribution comes with the following partitions:

/dev/sda1 - a Windows system recovery
/dev/sda2 - a UEFI partition
/dev/sda3 - a Windows system partition
/dev/sda4 - Windows 8 main partition
/dev/sda5 - Toshiba's windows 8 recovery partition (I delete this one to make space for Ubuntu)

Here is what I've done:

[LIST=1]
[*]Resized the windows 8 partition using windows 8 disk management tool.
[*]Create a partition using windows 8 disk management tool.
[*]Disable "Intel fast boot" in the UEFI
[*]Boot my live Ubuntu 12.10 64bit from a USB drive
[*]I noticed Ubuntu installed doesn't detect the pre-installed windows 8, so I choose "do something else".
[*]Select /dev/sda5 as root partition and select Btrfs as file system
[*]Install & reboot
[/LIST]
The laptop boot directly into Windows 8, without showing Grub's boot menu, so I reboot from my USB ubuntu installation again and:

[LIST=1]
[*]Install and launch boot-repair
[*]I notice that, in advanced options, there are no Grub options (appear light grey)
[*]I run the recommended fix and I get this URL: [http://paste.ubuntu.com/1630627/](http://paste.ubuntu.com/1630627/)
[*]Reboot
[/LIST]
This time my system tries to boot directly into windows 8 again, but it gets stuck in a loop showing the small "loading" windows 8's logo (the one with the 6 little circles dancing around).


I tried overwriting Windows 8's UEFI boot with grub's one, but it's all the same (the fix is suggested here: [http://askubuntu.com/questions/235567/windows-8-removes-grub-as-default-boot-manager](http://askubuntu.com/questions/235567/windows-8-removes-grub-as-default-boot-manager)).


I don't know what else to do, can somebody help me?


Thank you.

---

### Post by oldfred on 2013-02-09
With gpt partitioning all partitions are primary. Do not delete vendor supplied partitions. Some systems will not boot without them. Did you do a full system back and make the set of DVDs to reinstall. We are seeing too many users totally overwrite the hard drive and not have Windows at all.

I would not use btrfs.
       BTRFS, not ready for prime time
            Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

You have two efi partitions. With UEFI and gpt you can only have one efi partition. And the "boot" flag in gpt is what makes an efi partition efi. You never with gpt set a boot flag on any other partition like with BIOS/MBR.

---

### Post by Abrx on 2013-02-09
> **oldfred said:**
> With gpt partitioning all partitions are primary. Do not delete vendor supplied partitions. Some systems will not boot without them. Did you do a full system back and make the set of DVDs to reinstall. We are seeing too many users totally overwrite the hard drive and not have Windows at all.

I would not use btrfs.
       BTRFS, not ready for prime time
            Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

You have two efi partitions. With UEFI and gpt you can only have one efi partition. And the "boot" flag in gpt is what makes an efi partition efi. You never with gpt set a boot flag on any other partition like with BIOS/MBR.

I have a backup and I restored it already, but I don't know how a set of DVDs will help me (I don't have an external drive, so it could be a problem if I really need them). The partition I delete is not needed by windows, and in fact windows does boot after I remove it; as I said, I built the Ubuntu partition using windows. The recovery partition is 9 GB, it's right after the windows partition (which occupies almost the whole  disk) and it's followed by a 8.5 GB sixth  partition (unused), so I need to remove it to make space for Ubuntu if I don't want to loose a significant part of my hard drive.

Also, I don't have two UEFI partition, just the one (sda2) and both Ubuntu and Windows detect it. 

Regarding Btrfs, I chose this FS after reading a few articles about SSD-ready file systems and several performance comparisons. It might not be ready for large production systems, but it is good enough for me, so I'd rather keep it that way.

---

### Post by oldfred on 2013-02-09
Another thread on those using btrfs.
[http://ubuntuforums.org/showthread.php?t=2112829](http://ubuntuforums.org/showthread.php?t=2112829)

Did you just backup Windows or all the other partitions?

```
Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       923,647       921,600 Windows Recovery Environment (Windows)
/dev/sda2         923,648     1,456,127       532,480 [COLOR=Red]EFI System partition[/COLOR]
/dev/sda3       1,456,128     1,718,271       262,144 Microsoft Reserved Partition (Windows)
[COLOR=Red]/dev/sda4 [/COLOR]      1,718,272   124,598,271   122,880,000 [COLOR=Red]EFI System partition[/COLOR]
/dev/sda5     124,598,272   250,066,943   125,468,672 Data partition (Windows/Linux)
``` Somehow your sda4 which probably is your main install is showing as an efi partition. Remove boot flag using gparted.

---

### Post by Abrx on 2013-02-10
I backed up the whole disk (dd if=/dev/sda of=sda.img), so I can restore it as it was before I did anything at all (I've done this twice already :sad:).

I don't know why the report shows that, if you go a look at parted's report you can see the only partition with boot flag is sda2.

I'll see what I can do about Windows partition showing as EFI partition, maybe that's the source of the whole problem.

BTW: After my first failed installation with btrfs, I did a second installation with ext4 and experienced the exact same problems. I just paste my last report after many many hours of frustration, I'd be surprised if that has anything to do with my problems, but I'll switch to ext4 just to be sure.

Thank you for your answers, I really appreciate them. I'll post my results as soon as I get them.

---

### Post by Abrx on 2013-02-10
Ok, so I checked my partition table with gparted and nothing out of the ordinary there, so I went on installing Ubuntu with ext4. Didn't show grub menu so I just booted from my USB drive and run boot-repair. This time I do see grub options, and the proposed repair is different from the previous one, so that's one thing. Also, the boot-repair report doesn't show two EFI partitions at any point this time (which is good, I guess...).

Btw, windows 8 was not detected by grub nor Ubuntu installer.

Now, after the boot-repair, my laptop doesn't go pass the "TOSHIBA" starting screen. If I insert my USB drive, it jumps to my second boot option (USB) and boots Ubuntu live.

I don't really understand why this is happening, it makes no sense. I'm going to repair the mess and see if I can fix the UEFI manually or using another loader. Still, I'd like to know why this happening.

This is my report after I boot to Ubuntu live: [http://paste.ubuntu.com/1632834](http://paste.ubuntu.com/1632834)

---

### Post by Abrx on 2013-02-10
A second boot-repair fixed the UEFI and then the laptop booted directly to windows 8 again. I installed Easy BCD and fixed the UEFI so that a menu would show up and I can choose between Ubuntu and Windows 8. While Windows 8 boot works perfectly, I get an error with Ubuntu boot. It says some files are missing and it cannot boot.

I don't know what to do, really. This is all very weird. I think I'll try installing Grub in /dev/sda5 instead of /dev/sda and see if Easy BCD can load it from there...

---

### Post by oldfred on 2013-02-10
I do not know how Easy BCD works. With UEFI you should not need it as both Windows &  Ubuntu have boot files in efi paritition to boot.

Some systems only will boot the Windows boot file. For those systems Boot_Repair backs up Windows boot file and renames the grub file to the Windows name. Then from grub it chain loads to the backup Windows file to boot Windows.

       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

    
Grub also has a bug on creating the Windows chain load entries. It still creates the old BIOS entries.
       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
    
       [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
If you get to a grub menu, then you may be into video or other boot parameters.
What video chip/card do you have?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

            [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
If you get grub menu press e so you can edit boot stanza.
try to boot with acpi=off or nomodeset in place of splash quiet on the linux line

---

### Post by Abrx on 2013-02-10
> **oldfred said:**
> I do not know how Easy BCD works. With UEFI you should not need it as both Windows &  Ubuntu have boot files in efi paritition to boot.

I think Easy BCD manipulates Windows boot loader. Anyway, Easy BCD didn't fix my problem, the only system it boots correctly is Windows 8 :-( 

> 
Some systems only will boot the Windows boot file. For those systems Boot_Repair backs up Windows boot file and renames the grub file to the Windows name. Then from grub it chain loads to the backup Windows file to boot Windows.I know, and it's the first fix I tried. I did it automatically with boot-repair and then by hand; didn't work at all :-(

    > If you get to a grub menu, then you may be into video or other boot parameters.
What video chip/card do you have?It is an Intel HD4000, but I don't even get to the Grub menu, I'm far from that point...

I've tried with and without Secure Boot but it is all the same, I don't get past the base installation. I install ubuntu 12.10 with no apparent problem but I'm totally uncapable of booting it.

I'm quite familiar with Grub and Linux (I've been using Debian for almost 15 years), if I get to Grub I can do whatever I want even by hand, but alas, I don't get that far...

I'll keep trying but I'm about to give up :-/

---

### Post by oldfred on 2013-02-10
Some systems particularly Samsung have major issues.
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)

Above also briefly mentions some Toshiba.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by Abrx on 2013-02-10
Somehow I managed to get to a Grub. Apparently, boot-repair do and undo changes in successive runs, and some of my changes were undone while I was trying for boot-repair to do some other changes.

What I did:

[LIST=1]
[*]Install Ubuntu
[*]Boot from live USB
[*]Mount uefi partition
[*]Backup Boot/bootx64.efi and Microsoft/Boot/bootmgfw.efi
[*]Overwrite them with ubuntu/grubx64.efi
[/LIST]
This way, first I get Secure Boot problems. I disable Secure Boot and run into graphics problems (flickering, a solid purple screen, then a black screen and that's all). I run boot-repair to install a grub with nomodeset, I followed in-screen instructions and everything worked perfectly. This time boot-repair undid my manual changes too, but I was prepared so I redid them. FINALLY I got into an operating Grub menu and I can boot windows from there (both, from bootx64.efi and from bootmgfw.efi) but here's another problem... Ubuntu doesn't boot! It stalls at the loading screen (the one with the four horizontal dots). It fills the four dots once and the stalls there. If I push the power button, the shutdown sequence is shown and the laptop turns off, but I don't get to login screen.


It's not working yet, but I made a significant progress this time. Any ideas?

---

### Post by oldfred on 2013-02-10
I believe boot repair renames grubx64.efi for non-secure boot but renames the shim.efi file for secure boot as that has the Microsoft key.

Do not force shutdown, that often corrupts system. Best to remember elephants.
       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Depending on far it booted, it may accept REISUB. I think order is not critical as long as R is first and B is last.

When it stops does an alt f1 or alt f2 get you to terminal?

Video issues after grub menu depend on what video chip. 

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    Boot-Repair also has these options.
       Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply

       Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)

    Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Some systems need other boot parameters also, some to try if above suggestions do not work.
       UEFI or Intel new systems:
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset
pci=nomsi 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w

---

### Post by Abrx on 2013-02-11
Ok. After trying almost every combination of options, I begun to remove quite, splash and vt.handoff. I repeated all option combinations and I kept seeing (or I though I saw, it was all too fast; I have confirmed this later, looking into the logs) a kernel panic at some point and then a complete stall. When I was about to give up and return the laptop, I removed the only option a kept: nomodeset. All of a sudden, no more panics and boot right to desktop login.

So here's what I did:


[LIST=1]
[*]Install ubuntu normally (take into account that boot-repair doesn't work with Btrfs).
[*]Disable Secure Boot (for some reason, Toshiba's secure boot doesn't like signed grub efi).
[*]Run boot-repair (it will backup boot/bootx64.efi and microsoft/boot/bootmgfw.efi and replace them with ubuntu/boot/grubx64.efi; toshiba doesn't comply with EFI standard; you do this by hand, if you wish)
[*]I also let boot-repair reinstall grub. It will detect Windows efis and add working entries to grub.
[*]When the grub menu shows up, edit the Ubuntu entry and remove every option after the "ro". I.e.: quiet, splash, $vt_handoff. I guess you could keep the "quiet" option, but you have to remove splash and vt handoff.
[/LIST]


This is how I got to boot a Toshiba Portègè z930.


There's still some issues: I can't change backlight luminosity, and mouse lock key doesn't work either. Everything else seems to be running smoothly.


I hope this help other people experiencing difficulties with their newest laptops. And thank your for your help, Oldfred, I really appreciate it :)

---

### Post by oldfred on 2013-02-11
Glad you got it working. And thanks for update on what finally worked.

I will add this thead to my list of links with success and some users do search forum for info and may find this thead and that should help them.

---

### Post by rodriguez27 on 2013-06-12
Abrx,
Thank you for your efforts! I've got Ubuntu 12.04 running on my new Toshiba Satellite Z930 01E by following the steps you performed (including dd'ing the drive before hand just in case...).
The only difference was that I didn't need to edit the grub items after boot-repair finished. For boot-repair I chose the "Recommended repair" option, and did everything it told me to do.

Afterwards, I was also not able to change the screen brightness; neither in the settings GUI or with the keyboard function keys -- the keyboard function keys displayed an updated overlay bar though (but brightness did not change).

Not sure if you (or anyone else out there) is still having this issue, but here is what I did to fix this:

1. Edit **/etc/default/grub**
2. Change the **GRUB_CMDLINE_LINUX** line to: **GRUB_CMDLINE_LINUX="quiet splash pcie_aspm=force i915.i915_enable_rc6=1 i915.lvds_downclock=1 acpi_osi=Linux acpi_backlight=vendor elevator=noop"**
3. Run **update-grub**
4. Restart

This page explains the settings: [http://www.linlap.com/acer_aspire_s3](http://www.linlap.com/acer_aspire_s3)
and this page is where I got the commands from [http://www.gaggl.com/2012/05/intel-ultrabook-tweaks-on-ubuntu-12-04/](http://www.gaggl.com/2012/05/intel-ultrabook-tweaks-on-ubuntu-12-04/)
which I found from a link on this page: [http://yltechblog.blogspot.com.au/2012/09/installing-ubuntu-1204-to-toshiba-z930.html](http://yltechblog.blogspot.com.au/2012/09/installing-ubuntu-1204-to-toshiba-z930.html)

My whole experience was relatively painless. I resized the Windows 8 partition (/dev/sda4/) to 80GB and filled the rest of the drive with Ubuntu. I may re-adjust this at some stage though. I intend to use Windows 8 mainly to watch movies on (and other light usage) while travelling if the battery life is significantly better than for Ubuntu. I was actually quite impressed with Windows 8 in the short time that I used it, I didn't do much though. My main use for this machine is as a very portable development rig, where I'd be relying on A/C power for longer sessions anyway.

Enjoy!

---

