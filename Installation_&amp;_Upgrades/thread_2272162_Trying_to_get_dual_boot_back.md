---
title: "Trying to get dual boot back"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by davehenry7 on 2015-04-04
I had 14.04 working with win8.  Now boot menu disappeared, and only Windows loads. I tried Boot-Repair-Disk several times.
Can someone please help me by looking at my pastebin  page?:

[http://paste.ubuntu.com/10737556/](http://paste.ubuntu.com/10737556/)

I don't know enough about grub, grub2, efi etc.

It looks like it should work, though? What am I missing?
 BTW, I tried the suggested bcdedit command in Windows, and was not allowed, even under admin.
I tried turning off secure boot.

Also, is it OK to use my 13.10 disk to update grub even tho Ubuntu is upgraded to 14.04?
Thanks for your help.

---

### Post by oldfred on 2015-04-04
Does Windows boot ok?

I do not understand as I thought this was drive 2 in UEFI not first drive. And it should work if Toshiba followed UEFI spec. But they modify UEFI to only boot Windows by description.
```
BootOrder: 0001,2001,0000,2003,2002
Boot0000* Windows Boot Manager    HD([COLOR=#ff0000]2[/COLOR],200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD([COLOR=#ff0000]2[/COLOR],200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(EFIubuntugrubx64.efi)
```

But perhaps UEFI is like grub and also searches for the GUID (also in entry above) to find correct partition.

Boot-Repair should not download into 13.10 as it is obsolete. Always best to have current version repair CD/DVD/flash for every system you have installed. Or a current Windows 8 repair flash drive and Ubuntu's installer on a flash drive.

Many with Toshiba have copied grub to the /EFI/Boot folder and renamed bootx64.efi. Then a hard drive boot entry works. Not sure if it auto creates entry or you have to still create it.

       Backup entire efi partition before making changes.

   A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot

   Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi Then boot harddrive entry in UEFI menu.
Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)

   From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.

   sudo mount /dev/sda1 /mnt

   only if /EFI/Boot not already existing, run the mkdir command,
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot

   If new folder created, the bootx64.efi will not exist, skip backup command

   sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup

   make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.

   sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

   More examples of users who manually moved efi files
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)


 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)

---

### Post by davehenry7 on 2015-04-05
Oh my goodness, that is a lot.  Thank you, oldFred for all that.  It is a little daunting for me to accomplish this now, and so I did a new re-install of 14.04.1 LTS into an empty partition that I had. It loaded, but did not boot.  It did not give me booting options -- only Windows still boots.  I had a fleeting glimpse on booting that '/boot/EFI/'something' could not be found.

I do not understand the instruction:
   Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and  name it bootx64.efi Then boot harddrive entry in UEFI menu.
What do I rename it to?    And, 'boot harddrive entry'???  I'm too much of a newby to understand that.
I guess I am beyond help, but wanted to thank you for your efforts, oldFred.

(I cannot even have success with a command like:  grub> find  /boot/grub/stage2  (File not found)
So I don't even know whether grub should be at sda2,sda1,sda6.
Plus the EFI is totally baffling.  I did try BIOS secure boot on and off -- no diff.)

---

### Post by davehenry7 on 2015-04-05
Good news everyone.
My new installation revealed itself when I pressed F12 while booting, and revealing the boot menu.  Now i see where the Ubuntu boot options can be seen.  I have working installations of my old 13 and new 14 Ubuntu versions running .
This happenned after running Boot-Repair-Disk again after a fresh install. and using the Recommended tab. 
I have yet to make the menu appear automatically, but this works for now.

NOT!  I just tried it again, and ubuntu menus do not appear when pressing F12 in boot menu.  Just a temp fix from B-R-Disk, I guess.

---

### Post by oldfred on 2015-04-05
UEFI has a one time boot and that seems to be what is happening.

I tried to explain what was going to be done.
I then posted all the detail commands you need to run, but you need to know if your efi partition is sda1 or some other partition, example uses sda1.

---

### Post by davehenry7 on 2015-04-05
OK, I'm reading it more carefully now, with a little more knowledge, and it's starting to make a little sense.
Thanks.

---

### Post by davehenry7 on 2015-04-12
Had to finish my taxes before continuing...thanks to oldFred, I got Ubuntu coming up in the Boot menu --  as in from the computer's boot device selection.  Grub still does not automatically load upon starting the computer.  So I press F12 upon startup, HDD, then I have ubuntu or win options.
What are the final steps to having Grub menu appear upon start up?
I followed the directions for replacing bootx64.efi with grubx64.efi as described in the previous post by oldFred. But I can't say I get it all yet.
Happy to have gotten over this hurdle. Not quite 'solved'.
Thanks again.
It is interesting that I have two ubuntu options in HDD boot menu , and each takes me to version 14, eventhough I kept version 13 on another partition.
Grub does allow me previous ubuntu version(s) though.

---

### Post by oldfred on 2015-04-12
You may have both shim(grub for secure boot) & grub as UEFI boot options. If you turn secure boot on then shim may be only option.
Can you set a hard drive boot option as default or first in boot order. That should be the copy of grub that was copied to bootx64.efi.

---

### Post by davehenry7 on 2015-04-16
Halleluia.
I can now mark this case Solved.
The final step was getting the bcdedit command to work in Win8. At first, access was denied.
I needed to Start/cmd/ and right click on cmd and "Run as administrator" . That's all it needed.
Thanks oldFred,  you've done it again.
Couldn't do it without you.

---

