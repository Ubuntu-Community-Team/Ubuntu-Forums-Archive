---
title: "Dual-boot: Windows stops working after installing Linux"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by david_frey on 2008-05-21
I am trying to get a dual-boot system where I have Windows XP and Kubuntu 8.04 installed on the same hard drive.

I first installed Windows XP.  I created a 60GB partition and left the rest of the space unused.  The installation went fine and I was able to boot Windows.

Next I installed Kubuntu 8.04 from DVD.  In the partitioning screen, I chose the option that was something like "use the largest free space".  The Kubuntu installation went smoothly.

The problem is that after installing Kubuntu, I am no longer able to boot windows.  GRUB has a Windows XP option.  When I choose that, Windows begins booting then quickly blue screens with the error message "UNMOUNTABLE_ROOT_VOLUME"

What can I do to fix this?

```

$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8b9a8b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       91201   671131440    5  Extended
/dev/sda5            7650       89722   659251341   83  Linux
/dev/sda6           89723       91201    11880036   82  Linux swap / Solaris

```

---

### Post by Herman on 2008-05-21
:) Hello david_frey,
Try running a file system check in your Windows partition, as described in the following link, [http://forums.wincustomize.com/164526/get;1462212](http://forums.wincustomize.com/164526/get;1462212)

Here's another link just in case you want to read more, [NTFS and FAT32 file system repair and maintenance]("http://users.bigpond.net.au/hermanzone/p10.htm#NTFS_File_Fystem_Repair_and_Maintenance")

Regards, Herman :)

---

### Post by Eddie Wilson on 2008-05-21
Good Day Herman,
When I saw this thread I thought this could be the same problem that I have, but its not. I have dual booted Ubuntu and Xp for years. All I use Xp for is some games that I couldn't get to play in WINE. I did a clean install of Ubuntu 8.04 and expected no problems with my Windows install. I've never had any before. It showed up in my grub menu as always but when I select Windows XP the screen just goes blank and does nothing. I've checked my menu.lst and everything looks good. I can boot into xp using SuperGrub but I don't want to have to do that every time. I've tried everything I could find in the forums  but nothing helps. There are a few more things I may try but I was just wondering if you have heard of this problem and what your thoughts may be on the matter.
Thanks,
Eddie

---

### Post by david_frey on 2008-05-21
After trying everything I could find in google, I gave up and started over.

I installed Windows XP again, but this time, I installed all of the updates before I installed Kubuntu.

While installing Kubuntu, I chose the manual partitioning option instead of the use all remaining space option.

I am now able to boot both Kubuntu and Windows XP.

---

### Post by Herman on 2008-05-21
:) Hello Eddie,
> when I select Windows XP the screen just goes blank and does nothing
:confused: I haven't heard of this one before.
If Super Grub Disk can boot your Windows okay then that seems to indicate that the problem is somewhere in your GRUB and not in your Windows XP.

Normally you would see some feedback as GRUB runs through the commands, even if they only appear for an instant and then disappear again. For example, like[ this]("http://users.bigpond.net.au/hermanzone/p15.htm#Stuck_in_the_middle_Errors_and").

The output from 'sudo fdisk -lu' is often useful for solving booting problems.

You could try a few experiments or tests to try to learn more about the problem.
An easy way to begin would be to try pressing your 'c' key and booting Windows by typing the commands yourself at [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
Try these commands and observe what happens, _[Chainloading Windows the simple way]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way")_.

If you can chainload your Windows successfully from CLI mode GRUB, probably you need to take another look at your booting stanza for Windows in your /boot/grub/menu.lst file, there might be some syntax error in there that's hard to see, like a stray punctuation mark or a whitespace where there shouldn't be one or something else that's small and difficult to spot.
If you can't chainload your Windows installation from CLI mode GRUB, then hopefully you will be able to read the feedback after each command and that may provide more clues about what's going wrong.
If your operating system's GRUB does have some corruption, a file system check in your Ubuntu partition would be worth a try. [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").  A file system check is always a good thing to do, whether you need one or not.
If that doesn't fix it then maybe there's some kind of corruption in your GRUB files themselves, (rare but possible). 
The grub-install command can be used to refresh your GRUB files in /boot from your GRUB exectutable file in /usr/sbin. To make sure, you can delete all your GRUB files from /boot first, before running grub-install. You should make a backup of your /boot/grub/menu.lst file first, and remember to restore that again afterwards.
```
sudo grub-install /dev/sda
```Where: 'sda' is your Linux device name for your first hard disk (MBR), if not, try 'dev/hda' instead.

Regards, Herman :)

---

### Post by Herman on 2008-05-21
> After trying everything I could find in google, I gave up and started over.
I installed Windows XP again, but this time, I installed all of the updates before I installed Kubuntu.
While installing Kubuntu, I chose the manual partitioning option instead of the use all remaining space option.
I am now able to boot both Kubuntu and Windows XP.:) Okay, thanks for letting everyone know that you got it working, and I'm glad you got it fixed. 
Happy Kubuntuing!
Regards, Herman :)

---

