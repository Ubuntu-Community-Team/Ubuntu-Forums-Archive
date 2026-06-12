---
title: "Unable to boot Ubuntu 12.04.4 from second SSD"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by Nartus on 2014-05-27
Hello all.
I am new to Linux and I am currently on a robotics team at my university. We are using ROS Hydro for the programming environment. So I must use 12.04.X to use it.

My problem is that I can not seem to boot into linux at all. I was able to install it to my second 320GB SSD i recently purchased. I have been using EasyBCD to try and modify the Windows Boot Loader. After I get to the selection screen and select Ubuntu, it says that a key file is missing, the .mbr file. It is strange that this is not working at all. I did notice that the second hard drive does not show up on Windows explorer but shows up in Disk Management and I can not add a path or a letter to it. I am thinking this is a standard occurrence with the drive.

I do know I have linux on there as EasyBCD sees it in the Add Entry section. It just can't seem to find the required file.

My thinking is leading me to believe that I installed Linux wrong. I did a Swap at 32GB (I have 32GB of ram on my computer) and a /(root). I had read that a /home is recommended above 30GB.

Any advice would be greatly appreciated.

My System:

Alienware M17xR4 
Primary OS: Windows 8.1

---

### Post by oldfred on 2014-05-27
Windows will not read Linux formatted partitions.
Windows boot loader is really only to boot Windows, and with two hard drives you just install grub to the MBR (if BIOS) of the second drive.

If a full drive install, often better to have 20 or 25GB for / (root). Unless editing videos you should not need swap that large. You will probably never use swap, but have 2 or 3GB just to have some. Then use rest of drive as /home or data partition(s). Ubuntu can read NTFS partitions, so if you want to share data have a NTFS data partition on either the Windows or Linux drive. Do not set Windows system partition or c: drive as read/write, just as read only to avoid issues.

Install grub to the MBR of the second drive. Do not use any autofix if you run  repairs in Boot-Repair as will will install grub to both drives. But use advanced mode and choose system and drive to install boot loader.

Best to see details, post link to BootInfo report:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Nartus on 2014-05-27
How would I go about installing GRUB on the MBR on the second drive? I am unable to get to Linux at all via boot menu. I am using UEFI since Windows 8 forces that on me. Maybe boot into the legacy ROM options and go from there? I can't change the order the drives are booted either. and for the NTFS, I would have to reinstall for that? I was thinking of getting a 3rd drive eventually for sharing. I was just curious about that.

---

### Post by oldfred on 2014-05-27
If you are using UEFI, then you really should install Ubuntu in UEFI boot mode on second drive. But you then have to use gpt partitioning. 
Ubuntu will boot from a gpt partitioned drive with either UEFI or BIOS, but if you installed in BIOS/CSM mode then you may have MBR(msdos) partitioning.
Best to see BootInfo report to know what you have.
More info on two drive UEFI installs in link in my signature.

---

### Post by Nartus on 2014-05-27
So here is the url boot repair gives me: [http://paste.ubuntu.com/7350798](http://paste.ubuntu.com/7350798) 

The only way I was able to install ubuntu was to go into legacy mode. The UEFI boot menu never displayed the cd drive nor a USB. So I am assuming the hard drive is in the old BIOS format. If that is the case would I have to reformat the drive and reinstall?

---

### Post by oldfred on 2014-05-27
You are only showing one 200GB drive.  And you now have grub2's boot loader in the MBR. Does it boot Ubuntu. and grub menu shows Vista as your Windows?

Both Windows & Ubuntu are in BIOS mode. Even is system is UEFI capable you should not change. It looks like it probably is too old to even have UEFI.

If installing Ubuntu on another drive, and that drive will only have Ubuntu you can use gpt partitioning. Windows only boots from gpt with UEFI, but Ubuntu can boot from gpt drive with BIOS or UEFI. With my old system that is only BIOS I boot two drives as gpt.

---

### Post by Nartus on 2014-05-27
Well I know for one I have two drives. When I am in legacy mode I can't boot into windows but I can into linux and vica versa for UEFI. So is there something else I messed up? I can see two drives in Windows 8.1 Disk manager.

Oh and I have no idea why it is showing vista as my windows os it is windows 8 otherwise

---

### Post by oldfred on 2014-05-27
If you overinstalled Windows 8 over Vista, it may still look like Vista to the script.
Does BIOS show two drives?

Is that really your link? It does not seem to match anything that you are explaining?

---

### Post by Nartus on 2014-05-27
Well thats the link. I copied it straight from boot repair. I have been using Easy BCD. In one guide it said to go to BCD deployment and choose "Install the Windows 7/vista bootloader MBR" I gave that a go and nothing happened. Maybe thats causing the issue there. But as I said I have two hard drives and in the legecy boot rom in the boot menu (after enabling it in the UEFI) I can see network, hard disk, second hard disk, and CD/DVD Drive. If i was in UEFI only with legacy boot rom disabled I can not boot into the second drive.

P.S. I can run another boot loader log if you would like.

---

### Post by Nartus on 2014-05-27
OK I think I might have figured it out. Not sure though. Novice mistake I guess. I went back to UEFI boot menu and put my disc with 12.04.4 and now it sees it. Guess I have to uninstall and reformat the ssd and try again. If there is a safe way to do that I'd like to know lol. Man that might be my issue.

---

### Post by oldfred on 2014-05-27
What is on SSD?
Do not use any auto install as that erases entire drive in many cases. Much safer to use Something Else or manual install. But then you have to select sizes for all partitions you want.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Nartus on 2014-05-27
On the SSD is only linux nothing more. It was blank before Linux was installed on it.

I did use "Something Else" on the first install. Can I just do that again? I have no data what so ever on the linux side.

---

### Post by oldfred on 2014-05-27
Sure, is partitions are the sizes you want just choose them again and select mount & format.

I am just reusing partitions. An install overwriting an older install on my sdc drive. And a install to my gpt partitioned SSD that has two versions of Ubuntu.

---

### Post by Nartus on 2014-05-28
Well here is a new one. I try loading the disc and I get the error "No device is set" and then I get a screen that is just pixels all jumbled up. Is the iso bad or something? It is 12.04.4 so it should work. It does show up in Uefi boot menu

---

### Post by oldfred on 2014-05-28
Is this dual video?
And do you set which video Intel or Intel you boot with?
nVidia needs nomodeset.
Intel may need different settings, but kernel, support software & video drivers have been updated with each major release of Ubuntu, so 14.04 may work a bit better.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Nartus on 2014-05-28
It is duel video card with intel. So that is causing a problem? anyway to tell it to look at a specific card?

---

### Post by oldfred on 2014-05-28
Some BIOS have settings to control which video is used.

I only have nVidia so do not know latest details on dual video. My understanding is the latest nVidia driver does work.

Some links for more info:
       Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
[http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319](http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319)

---

