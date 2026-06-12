---
title: "Fails to boot after fresh 14.04 install"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by ColinBrough on 2014-04-24
Trying to install 14.04 as the sole OS on a Dell Inspiron 570 desktop. ISO ubuntu-14.04-desktop-amd64.iso burned to USB stick using unetbootin.

Ubuntu runs from the stick OK, and the install process appears to go OK, but when I try to boot the new installation I get the following error:

----------------
Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux Documentation/init.txt for guidance.
CPU: 2 PID: 1 Comm: swapper/0 not tainted 3.13.0-24-generic #46-Ubuntu
Hardware name: Dell Inc. Inspiron 570     /04GJJT, BIOS A00 10/19/2009
00000000 00000000 f74a3f78 c164b873 efcc332e f74a3f98 c16469ac c1826f5c
c1aa5c80 c1815698 efcc332e 00000000 c193ce80 f74a3fac c1641cec c1815b80
c1815688 fffffff8 f74a2000 c1659ab7 c1641bf0 00000000 00000000 00000000
Call Trace:
 [<c164b873>] dump_stack+0x41/0x52
 [<c16469ac>] panic+0x97/0x181
 [<c1641cec>] kernel_init+0xfc/0x100
 [<c1659ab7>] ret_from_kernel_thread+0x1b/0x28
 [<c1641nf0>] ? rest_init+0x70/0x70
---------------------

The system previously ran 12.04 and other versions before that, so the hardware should be OK... (with a slighly different partitioning scheme).

There are three disks in the system:

sda is a 640Gb SATA - previously this had three partitions (/, /home, and swap). Aim is to have this with /mnt/disk2 and swap.
sdb is a 120Gb SSD - previously this had /mnt/disk2 (23Gb) and /mnt/disk3 (96Gb), not used much. Aim is to have this with / (23Gb) and /home (96Gb).
sdc is a 2Tb SATA - previously this had /mnt/disk4, aim is to preserve this - mostly media files.

When installing at the partitioning stage I've selected "Something else" and set the partitions as above, formatting the ones on sda and sdb. I've tried putting the boot sector on both sda and sdb, and changing the boot order of the disks via the BIOS. I've also tried putting a small /boot at the start of sda (shrinking the /mnt/disk2 partition). Always the same result.

Any suggestions for things to check or try very welcome - never had much occasion to play with grub, so wouldn't know how to go through the stages that the installer is presumably doing and checking each step...

I have already successfully installed 14.04 (i386, not changing boot disk) on an HP Microserver and an Acer Aspire laptop that also previously ran 12.04.

Thanks

Colin

---

### Post by makkus on 2014-04-24
I've got the same problem, I don't think it's to do with how the hardrives are setup. I tried different ways of partitioning (one primary parttion, ubuntu suggested layout, lvm,...), nothing worked, always getting this error message. 

I'm using a Thinkpad x220t. Judging from searching Google, it seems a few people have the same issue. Doesn't seem to be 14.04 specific though, seems to happen only in new installs though, not upgrades. Looks like a regression that was introduced sometime after 12.04, but I'm not really sure.

---

### Post by oldfred on 2014-04-24
Are you installing grub to sdb and then booting in BIOS from sdb?

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

The 14.04 version of Boot-Repair is not yet available.

----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

 gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'

---

### Post by ColinBrough on 2014-04-25
Thanks, oldfred.

At the time of the original post I was indeed installing grub to sdb and then booting in BIOS from sdb.

One of the things I've tried since then (didn't change resulting failure) was swapping SATA cables on sda and sdb, so the drive I want to boot from is drive 0 as far as the BIOS is concerned. So in the boot info report below sda and sdb are swapped over - sda is the 120Gb SDD with / and /home, and sdb is the 640Gb HDD with /mnt/disk2...

[http://paste.ubuntu.com/7328674/](http://paste.ubuntu.com/7328674/)

(Used workaround 0 from your list...)

Other things I've checked or tried since first posting: boot flag is only set on sda (according to gparted), and I've tried dropping to the grub command line as the BIOS boots through grub, then manually setting kernel image etc and booting - grub's TAB completion "sees" the image files, but booting gives the same error as before.

Thanks

Colin

---

### Post by ronb19495 on 2014-04-25
I had a problem like this a while back I found if I ran the live disk as live ubuntu and installed while running live that problem was no longer

---

### Post by oldfred on 2014-04-25
I do not see any specific issue. And not familiar with your kernel panic error.

Grub does not use boot flag. But a few BIOS require a boot flag just to let you boot at all, so we still suggest one on a primary partition. Used by Windows to know what partition has its boot files. Also used by Lilo boot loader.

Some old BIOS would not boot from partitions over 137GB, but your system looks new enough not to have that issue. Is drive set for AHCI in BIOS? Some with IDE setting have the old boot issue.

Are you using the 32 bit or the 64 bit version? And how much RAM?

---

### Post by ColinBrough on 2014-04-25
Using the 64 bit ISO - its an AMD Phenom II processor, so the i386 ISO doesn't even boot!

There's 6Gb RAM in the machine.

It previously booted OK with 9.10 through to 12.04 on the 640Gb drive (partition with '/' on it was about 23Gb).

I'll check the AHCI thing, though I suspect that's not the issue. My local LUG mailing list suggested I try booting into the live USB, then doing a chroot into the installation on the disks (which mount OK when the live USB is running) and then maybe try 'aptitude update' or 'update-initramfs' and reboot... I'll check the AHCI thing, try unplugging the two HDDs and re-installing with just the SDD present, and try the chroot thing - all when I have a moment!!

Thanks again

Colin

---

### Post by oldfred on 2014-04-25
I think Boot-Repair's advance mode does a chroot for its purge & reinstall of grub. From that you probably can run other commands also, but I have not tried that.

Many with upgrades are having to run this:
 sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

But I agree that it seems more like initrd.img may not be correct and needs recreating with update-initramfs, see man page for options.

---

### Post by ColinBrough on 2014-04-27
Progress report:
 - unplugging the two HDD's and only installing onto the SDD doesn't change the behaviour
 - I tried the chroot thing as suggested by some LUG friends; couldn't get the chroot jail to "see" the internet, so couldn't update the system. 'sudo update-initramfs' ran OK, said it had updated initrd, but on reboot still have the same kernel panic and message.

Will try boot-repair's "repair installation" next, and also try one of the default partitioning schemes in the installer (rather than the custom, "Something else", that allows you to pick out partitions...).

Grrr!!

Colin

---

### Post by oldfred on 2014-04-27
Some other hardware suggestions in this thread.
But older kernel and different distribution.

[http://www.pclinuxos.com/forum/index.php?topic=100672.0](http://www.pclinuxos.com/forum/index.php?topic=100672.0)

---

### Post by ColinBrough on 2014-04-28
Neither boot-repair's "repair installation" nor allowing the Ubuntu installer to use default partitions rather manually selecting them made any difference. Beginning to wonder about the hardware thing, but it is so consistent and only started when I tried to install Ubuntu 14.04. Hummm....

Will perhaps try a different distro (debian or Fedora probably), or reinstall 12.04, and see whether either of those has any more success - might confirm or eliminate the hardware problem idea...

Colin

---

### Post by ColinBrough on 2014-04-28
And the answer is.... use "Startup Disk Creator" on one of the existing Ubuntu 14.04 installations to create the bootable USB, rather than unetbootin.......

(I've previously had more reliable results from unetbootin, hence my preference for it. And without reinstalling 12.04 to check, I think it needed to be the "Startup Disk Creator" in 14.04 rather than the one in 12.04...)

Thanks for all your help.

Colin

---

### Post by Lokesh_Jetty on 2014-05-01
> **ColinBrough said:**
> And the answer is.... use "Startup Disk Creator" on one of the existing Ubuntu 14.04 installations to create the bootable USB, rather than unetbootin.......

(I've previously had more reliable results from unetbootin, hence my preference for it. And without reinstalling 12.04 to check, I think it needed to be the "Startup Disk Creator" in 14.04 rather than the one in 12.04...)

Thanks for all your help.

Colin

Thanks for the solution. I faced the same problem last night while trying to install xubuntu. I can boot from the usb drive but not from hdd installation. but i don't have an existing Ubuntu 14.04 installation. is the Startup Disk Creator included in the iso? i'm thinking i can boot from usb first and use the Startup Disk Creator in the live system to create another bootable USB and install from that.

---

### Post by sudodus on 2014-05-02
I'm not sure about all flavours and versions of Ubuntu, but ***Startup Disk Creator*** is found in a menu or via Dash, and it can be run from a terminal window with either of the commands (kde in Kubuntu)

```
usb-creator-gtk
```
```
usb-creator-kde
```

*Edit*: See this link for more information about ***Startup Disk Creator*** and other tools to create USB boot drives.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by 2-tomi on 2014-05-06
> **oldfred said:**
> I think Boot-Repair's advance mode does a chroot for its purge & reinstall of grub. From that you probably can run other commands also, but I have not tried that.

Many with upgrades are having to run this:
 sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

But I agree that it seems more like initrd.img may not be correct and needs recreating with update-initramfs, see man page for options.

My experiences so far:
- Fresh install without upgrades worked. Manual upgrade + the fix above (sudo dpkg-reconfigure grub-pc) worked for a while. However new upgrades seemed to break it again. I get the same kernel panic after the latest upgrades (after running sudo dpkg-reconfigure grub-pc ). 

Currently waiting for new upgrades which would fix this. Does anyone else have any better ideas?

---

### Post by elnegrito on 2014-05-07
I had the same problem here. It was solved creating a bootable Ubuntu 14.04 USB Disc using UNetbootin. Booting to that drive and then creating a bootable Ubuntu 14.04 USB Disc, on another USB drive, using Startup Disk Creator.

---

