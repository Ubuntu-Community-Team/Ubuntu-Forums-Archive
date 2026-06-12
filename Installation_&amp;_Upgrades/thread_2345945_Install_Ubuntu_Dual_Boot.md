---
title: "Install Ubuntu Dual Boot"
date: 2016-12-09
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2016-12-09
Hello, I am about to install ubuntu 16.10 with windows 10 on a new HP laptop, I have resized the partition from windows allowing space for ubuntu to be installed, turned off fast boot and secure boot is there anything else that I need to do before I begin the install?

I did run the live version last night and it worked great until I got the blank screen that people have been getting when they use AMD graphics but I hope once ubuntu is installed and I upgrade to the 4.9 kernel it will fix that, at least the AMDGPU driver was used and it worked good until the blank screen.
Thanks

---

### Post by oldfred on 2016-12-09
Do not know much about AMD graphics, other than they are in the middle of conversion from older proprietary driver that now does not work with newer kernels to open source or partially proprietary driver.

But for UEFI install see link in my signature.
I prefer to partition in advance & use Something Else.
Be sure to reboot Windows after resize so it can run chkdsk. Make doubly sure that fast start up or hibernation is off. If partitions shown in Something Else then you should be ok. You also need to have Secure boot off.

HP's are not Linux friendly, you have to do a work around on the UEFI boot.
HP violates UEFI standard that says NOT to use description as part of boot and only valid description is "Windows Boot Manager". But many work arounds. If dual booting most can use the fallback or hard drive boot entry. HP may already have a fallback entry in UEFI that uses /EFI/Boot/bootx64.efi which is just a copy of Window own .efi boot file.  Boot-Repair will automatically copy shimx64.efi to bootx64.efi and if you have UEFI entry it should work.

Some HP do allows other systems, but settings are buried pretty deep.
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 

Older threads, users had to manually copy shim to bootx64.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by wildmanne39 on 2016-12-09
Looks like I do have a little more work to do before I try to install ubuntu, I am glad I asked first, I thought I had read that HP's were harder to install ubuntu on then other laptops.
Thank You very much!:)

---

### Post by RobGoss on 2016-12-09
I think **Fred **pointed out some good tips as far as installing Ubuntu on that HP, I have one HP machine and is was not easy to get Ubuntu installed on it I still don't have the machine dual booting correctly and I had to use** refind** [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) to get the machine to choose which OS I wanted to boot but it's doing just fine now so I wont make any changes right now

---

### Post by tea for one on 2016-12-10
> **wildmanne39 said:**
> Hello, I am about to install ubuntu 16.10 with windows 10 on a new HP laptop, I have resized the partition from windows allowing space for ubuntu to be installed, turned off fast boot and secure boot is there anything else that I need to do before I begin the install?

I purchased a HP Stream 11.6 netbook approx 6 months ago.
I left Widows 10 intact and used the Windows partition tool to allow space for Xubuntu core.

I agree with oldfred, HP have organised UEFI in their own distinct way.

My main obstacle was "grub-efi amd64 signed package failed to install"

I got round this eventually by **turning off the secure boot in the UEFI settings** and reinstalling. I expected to find that Windows 10 would refuse to load but to my surprise it loaded with secure boot disabled - who really knows how these HP UEFI devices function?

Secure boot is disabled and legacy boot is enabled and both Xubuntu Core and Windows 10 boot and function adequately.

When I turn the power on, **grub does not apppear automagically like a pre UEFI machine,** I have to press F9 to choose the boot device and then grub will appear (depending on you personal grub configuration settings). If I do not press F9, Windows 10 will load due to some priority(?) bulit into the UEFI by HP.

In effect, I have two boot loaders:-

Windows OS Boot Manager loads automatically when I turn on the PC (without pressing F9)
When I press F9, I can see all alternative bootable devices including Windows Boot Manager, Notebook Hard Drive and USB sticks (if they are inserted before power on)

In essence, it's a bit more complicated than pre UEFI, but manageable. However, my suspicious nature leads me to believe that not all HP laptops will be identical in their UEFI settings and my solution may be different from yours.

Please let us know how if your Ubuntu installation was successful.

Kind regards

---

### Post by wildmanne39 on 2016-12-10
Oldfred I am at the screen to install the boot loader since I have windows 10 does it just go into the sda partition or do I need to put it some where else, and I have not used something else in a few years so do you have a recommendation for partitions, I think you like to have a data partition that is large and keep a home partition kind of small but I do not know for sure.

I appreciate any suggestion you have, I only want to do this one time and the last time I installed I let ubuntu set them up and with in a week I was out of space in the root directory.
Thanks

---

### Post by oldfred on 2016-12-10
I have multiple 25GB or so partitions on both SSD & HDD for Ubuntu installs. One LTS version on SSD is my main working system. Others are to test or experiment with.

I do keep /home inside my / (root). But have a large data partition on HDD for all my data including some of the normally hidden folders with lots of data like Firefox profile & Thunderbird profile.

With UEFI it does not matter what you say about where to install grub. I have tried with sdb & full installs to flash drive, but every time it overwrites my /EFI/ubuntu folder in the ESP on sda. I quickly learned to back that up. But all it really changes is /EFI/ubuntu/grub.cfg in ESP which is just a configfile entry of 3 lines to chain load to full grub.cfg in the install. 

Grub will end up in the same ESP - efi system partition as Windows in a different folder. Grub install should add an UEFI boot entry that you can then directly boot from UEFI. But HP  does not let you boot that.
Many with HP use the fallback or hard drive entry that still works for most. That is /EFI/Boot/bootx64.efi which on flash drive is what is used to boot. But it also works for internal drives. We copy shimx64.efi from /EFI/ubuntu to /EFI/Boot and rename shimx64.efi to bootx64.efi. Boot-Repair can do all the copy, if you check/tick the 'use the standard efi file' option in advanced mode.

I have seen others use rEFInd. Have not tried that, but have not had any issues on my own built desktops and one Dell with Windows. They all boot the ubuntu entry without issue.

If only one hard drive you can have /, swap & /home. If knowledgeable on mounting a partition with fstab, setting ownership & permissions, and linking you can use data partition(s). Back with XP, I had both a NTFS data partition and a Linux formatted data partition. Partitioning is personal, even my own optimal partition scheme is changed with a new drive or new system.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by wildmanne39 on 2016-12-10
I got ubuntu 16.10 installed without issue with your help oldfred.

I installed grub to windows boot menu which I know you said ubuntu would put it there anyway, I did not have to do any thing extra to get ubuntu to boot on the new hp laptop they must have changed their UEFI setup, for the first time since the new bios system came about I get the ubuntu boot screen with a windows boot option and all I have to do is click the one I want to boot and it actually works.

I am having a graphic card driver issue that may make me install ubuntu 14.04.1 but I hope not.
Thanks for the help.

---

### Post by oldfred on 2016-12-10
Glad you got it working. :)

Have seen a lot of threads on the change in AMD drivers. But do not know what is correct or best currently.
 AMDGPU & Radeon DDX Updated - Better 2D Performance, Tear Free, DRI3 Default Nov 2016
Also needs  X.Org Server 1.19
[http://www.phoronix.com/scan.php?page=news_item&px=Radeon-AMDGPU-1.19-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Radeon-AMDGPU-1.19-Updates)
Ubuntu 16.04 How-To Install/Uninstall AMD Radeon&#8482; Software AMDGPU-PRO Driver
[https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx) 


       AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)
[http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075)

---

### Post by wildmanne39 on 2016-12-11
Thanks for the links for the amd cards I will read them when I am fresh in the morning.
:D

---

