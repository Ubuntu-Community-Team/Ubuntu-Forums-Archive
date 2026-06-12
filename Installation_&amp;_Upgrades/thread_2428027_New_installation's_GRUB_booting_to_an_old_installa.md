---
title: "New installation's GRUB booting to an old installation?"
date: 2019-09-29
forum: Installation &amp; Upgrades
---

### Post by orthoducks on 2019-09-29
I'm having problems with a dual-boot installation of Windows 10 and Ubuntu 18.04. I'd like some assistance understanding what happened before I decide what to do next.

I'm trying to recover from an error which rendered both Windows and Ubuntu unbootable. Working on the same disk, I restored a disk image created when Window was working and Ubuntu was not yet installed. Then I installed Ubuntu. That should have created a dual boot disk with a working, fully customized Windows and a working, freshly installed Ubuntu. Instead, Windows worked and Ubuntu failed in exactly the same mode as the damaged system I'm trying to replace.

I booted a live DVD and examined the disk. I found *two* EXT4 partitions, and both appear to contain Linux.

Here's what I think happened: When I restored Windows it overlaid the disk's boot and Windows partitions, but did not touch the damaged Linux partition. Then the Ubuntu installer split the original Linux partition into two, installed a new Ubuntu in one, and left the original damaged Ubuntu in the other. Then it installed GRUB and configured it to boot the old damaged Linux partition instead of the new one.

My questions are: first, assuming that you who are trying to help me know more about GRUB and the installer than I do, does my theory sound reasonable? Second, if so, what is the best way to recover?

I've read about the GRUB configuration files before, but found them confusing. I now think this may be a good time to learn how they work and point them to the good Linux partition, then delete the bad one.

The other solutions would be to (1) copy the good one over the bad one -- assuming I can be sure which is which -- or (2) delete *all* of the disk's partitions and start over.

A final word to ensure that well-intentioned responders don't go off the rails: I haven't explained what happened to the original installation and what failure mode it caused, because that would be time consuming and would not help solve the current problem. Please take it on faith that (1) I know what I did wrong and how to avoid doing it again. (2) The failure mode could not plausibly be caused by anything else, e.g. a hardware error; therefore its occurrence is proof that GRUB is trying to boot the original damaged system or a new one that has been damaged in the same way. (3) Even if I were careless enough to damage the new system the same way I damaged the old one, it failed before I even had an opportunity to do so.

---

### Post by guiverc on 2019-09-29
I would not expect a partition to be split into two on an install, but I'd always install using 'something else' and select the partitions I want to install to. I also like & use the no-format options I have available there, and that it can auto-restore my previous programs post-install without touching my user data.  There is a 'install alongside' option so maybe you chose that, but you didn't say what method, nor what Ubuntu 18.04 LTS you installed (there are many options!  server, desktop, alternate let alone options once installer has started).

I would `fsck` your other partition & examine it (open it in a file manager, eg. `nautilus`), if it's valid why not `update-grub` to see if it's recognized & added to the existing grub (after `fsck` or file-system check). 

Grub consists of my stages; the first stage is the MBR or master-boot-record, which is the first 512 bytes on a disk. You can't provide much code in 512 bytes so it's little more than grub-rescue (very limited) & a pointer to the later stages. The later stages are located in /boot/grub/ which continue boot.

---

### Post by yancek on 2019-09-29
If you have not resolved this issue and need assistance, go to the boot repair site at the link below.  Use the 2nd option explained on the page to use the ppa to get it and then run it per instructions.  Make certain to select the Create Boot Info Summary option which will give you a link when it completes and you can post that here for members to view and hopefully help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

> When I restored Windows it overlaid the disk's boot and Windows partitions

Boot partition for what?  windows?  Ubuntu? or was this actually an EFI partition which would be standard on windows 10?  I would not expect the installer to split any partitions without user intervention either.  There are a number of possible scenarios which could cause the problems you have and hopefully, the output of boot repair will help someone help you to resolve the problem.

---

### Post by orthoducks on 2019-09-29
I won't have time to do much with the sick system until next weekend -- maybe no time at all -- but I'll respond to the comments so far to see if we can move this forward a bit.

You both said you would not expect Ubuntu to split a partition on install, which puzzles me. I've always installed it after installing Windows, so I've never seen it do anything else. If the disk has no unallocated space it *can't *do anything else except fail. This is the first time I've installed Ubuntu on a disk that already had an Ubuntu partition, so this is the first time I've seen it split an Ubuntu partition instead of the Windows partition. Maybe that's unusual; without experience I can't say.

Guiverc: I read about update-grub last night, but I didn't see anything about how to tell it what disk to operate on. I assume it operates on the disk you booted from, making it useless for repairing a disk that won't boot. Is that not right? If not, running update-grub from Live Ubuntu is probably the simplest way to fix the problem.

I've never tried the "something else" install option because I once tried "install third party graphics" and got an unbootable system. I decided then that plain-vanilla is the way to go. "Something else" sounds very useful, if it is safe when used as directed. I'll look into it, soon if I have to reinstall to fix this problem.

Yancek: "Boot partition for what?" Yes, for Windows. As I said, I was restoring a backup made after I installed and customized Windows but before I installed Ubuntu. The Windows boot partition was the only one on the disk. This is a fairly old motherboard that I use for hacking, and I'm pretty sure it has BIOS, not EFI. I once tried to find out, but the procedure I was following didn't work (it required me to select a Windows 10 option that didn't appear on my system).

---

### Post by yancek on 2019-09-29
> 
You both said you would not expect Ubuntu to split a partition on install

From your original post, the quote below indicating that it split the Linux/Ubuntu partition but what you refer to above is a totally different thing.  The standard method is to use the windows Disk Management tool to shrink the windows partition to create unallocated space on which to install Ubuntu.  You can also do this with the Ubuntu tools but changing windows partitions is best done with windows tools.

> Then the Ubuntu installer split the original Linux partition into two

If you already had an Ubuntu install, I would expect the installer to give you a choice of overwriting it or installing to another partition.  The Something Else option in Ubuntu is simply their name for a manual install which gives the user choices and more control over the installation.  If you still need help, you will need to get more info such as boot repair output.

Have you read the Ubuntu documentation on dual booting with windows 10?  The link below explains it and it also gives you a command you can use to determine if you have EFI or a Legacy install.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by rsteinmetz70112 on 2019-09-30
If you are seeing the GRUB menu there may be an option old partition. In the menu there should be a line called "Advanced Options" - under that menu you should see see options of booting the older kernels, recovery more or doing a number of other things. You might want to look and see what's there.

Running fsck on the Ubuntu partitions seems like a good first step. You can do this from a live DVD.

Also update-grub may find the older installation, but I'm not real familiar with dual boot installations so you probably want to rely on others advice before running it.

Finally it seems possible that the new install shrunk the windows partition again to create space for the Ubuntu install. How that works I'm speculating but may depend on how much space was available in the Windows partition. A little more information on the partitions would be helpful - like how big are they?

---

