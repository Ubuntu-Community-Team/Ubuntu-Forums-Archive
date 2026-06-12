---
title: "Error loading operating system"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by Lightgod86 on 2007-11-07
I have an XP box, of which i just put in a sata drive (all of my drives are sata) and tried to install Gutsy. After battling the APIC errors, i finally got it to install. and on the first reboot it goes to windows (no grub).  So i try to boot to the other drive (Ubuntu) and i get an "error loading operating system".  When i installed it i chose to install it on the 2nd clean drive.  I have yet to see the grub menu when booting for either drive.

What do i need to to so that i can see the GRUB menu and boot to both OS's which are on different drives?  :confused:

And yes i have searched but have yet to find a solution to this precise problem.

---

### Post by Doggles on 2007-11-07
hmmmmm

maybe your "error loading operating system" is coming from changing the boot order of your drives, or maybe it's because you're not finding an appropriate master boot record for Ubuntu. We should be able to get you through this one though I hope...

I tried this out a while ago (having XP on one drive and Ubuntu on another) - I was paranoid about destroying my XP drive, so I unplugged it from the mobo, then installed Ubuntu with only the one disk plugged in - at this point I installed Grub to the MBR when prompted. When I was happy that Ubuntu was running OK, I plugged my XP drive back in. Now I found that if I changed the boot order in the BIOS, I could successfully boot from either the Windows or the Ubuntu drive. This is OK to start with but it isn't a very elegant way to dual boot. You might want to try this to start with though so that you can at least get into Ubuntu and have a poke around.

To get grub working properly so you don't need to go into the BIOS all the time, you then set the Ubuntu drive as drive 1, then edit your grub menu and add a couple of lines to include your XP drive. On a two-disk dual boot, you need to remap the drives so that Windows thinks it is on the primary drive. Have a look on the forums for this and if you can't find it then give me a shout and I'll dig out my old backed up menu.lst file and try to find the correct commands. Then when you reboot grub should allow you to boot either OS.

Note - I was using SATA drives on an Asus P4P800 mobo - so should be a similar situation to you. - you're not using RAID by the way are you?

Best of luck with this - let me know how you get on

Doggles :)

---

### Post by bulldog on 2007-11-07
> **Lightgod86 said:**
> I have an XP box, of which i just put in a sata drive (all of my drives are sata) and tried to install Gutsy. After battling the APIC errors, i finally got it to install. and on the first reboot it goes to windows (no grub).  So i try to boot to the other drive (Ubuntu) and i get an "error loading operating system".  When i installed it i chose to install it on the 2nd clean drive.  I have yet to see the grub menu when booting for either drive.

What do i need to to so that i can see the GRUB menu and boot to both OS's which are on different drives?  :confused:

And yes i have searched but have yet to find a solution to this precise problem.

Did you install ubuntu with both drives connected?
Which hdd is set as the master boot device in the BIOS?

You can boot windows so grub isn't on that hdd :)
So it must be on the other one.
You can reinstall grub with the live cd but be sure you put it on the right hdd.
The best thing to do is set the ubuntu hdd as first boot device in the BIOS and the windows hdd as the second one.
Now reinstall grub:
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr **but be carefull here,if the find command returned (hd1,?) the setup should be on (hd1) not (hd0)**
```
setup (hd0)
```
Exit the grub shell
```
quit
```

If this is going well without errors grub will be installed to the proper hdd.
Now we need to put windows in the menu.lst so you can boot it from the grub menu.
But first try to boot ubuntu and if that is going well we are going to setup the menu.lst.

---

### Post by Lightgod86 on 2007-11-07
OK! Sorry for the delay...

I did the above and have now seen the grub menu when i boot to the Ubuntu HD.  It lists windows as well...But 2 more problems...

When i select Ubuntu from GRUB i get an ERROR 17: Cannot mount selected partition.

After that i tried to boot to windows from GRUB and it gave me a "NTLDR is missing"

Switching the boot order back to my windows HD booted up windows just fine...

So where do i go from here to get Ubuntu up, and windows to boot from the Grub?

Thanks for all the help so far!

---

### Post by bulldog on 2007-11-07
In order to set the right boot options I need you to perform [live cd] in a terminal ```
sudo fdisk -l
``` small L not a one.
So we can see on which hdd ubuntu is installed,because it points to the wrong partition right now,just as the windows partition.

---

### Post by Lightgod86 on 2007-11-07
Ok, on Live CD now... Here is the output:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ac15ad4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabe0c1a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19452   156248158+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x560c2a8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29644   238115398+  83  Linux
/dev/sdc2           29645       30401     6080602+   5  Extended
/dev/sdc5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c22a487

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60791   488303676    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1171d5af

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60791   488303676    7  HPFS/NTFS



I am off to work now, but will check my email...but have no access to my computer...So i will try what you reply with tonight...

and THANKS for the quick help!!

---

### Post by Lightgod86 on 2007-11-07
And if you cant tell...Ubuntu is on the 250 gig HD, windows is on the 160 gig HD...the others are storage, and not to be bothered =)

---

### Post by bulldog on 2007-11-07
Device Boot Start End Blocks Id System
/dev/sdc1 * 1 29644 238115398+ 83 Linux
/dev/sdc2 29645 30401 6080602+ 5 Extended
/dev/sdc5 29645 30401 6080571 82 Linux swap / Solaris

Let's start with this one.
To start ubuntu select the line in grub menu and hit the e to edit it.
Remove what is listed and replace it with (hd2,0) hit the b to boot and see what happens.
It should boot into your ubuntu.

Your windows....hmm..I see two of them :confused:
We'll get to this to morrow but you can start windows by setting it as first boot device in the BIOS.

If you can boot in ubuntu I want you to copy your menu.lst to the forum so I can have a look and change things like they should be.
Open a terminal and make a backup first```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
Now copy the menu.lst to the forum [copy/paste]

Remember when you changed to bootline in grub it's not permanent,only for that  boot,we have to change the menu.lst to make it permanent.
And when you change the bootorder in the BIOS things will be mixed up again so be carefull and make a note on the settings.
It's nice to have so many hdd's,but it can complicate things :)

---

### Post by Lightgod86 on 2007-11-08
OK again sorry for the delay...

I tried replacing (hd4,0) to (hd2,0) but that didnt work...so i tried all of the other ones...And i did get (hd0,0) to work!

So anyways here is the menu.lst from ubuntu, which by the way im on now!

What do i need to do for windows?

Thanks again!


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd4,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6baccfb-61bb-4632-b746-10a8753f5486 ro quiet splash noapic nolapic
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd4,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6baccfb-61bb-4632-b746-10a8753f5486 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd4,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

---

### Post by bulldog on 2007-11-08
Nice to hear you get it going.
All depends on how your disks are aranged and how ubuntu list them.```
cat /boot/grub/device.map
```

You have the ubuntu hdd as the first boot device (hd0) so your fdisk is telling another story.
So we have to take a look at the device.map too.

But we have a start :)```
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d6baccfb-61bb-4632-b746-10a8753f5486 ro quiet splash noapic nolapic
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d6baccfb-61bb-4632-b746-10a8753f5486 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title Microsoft Windows XP Professional
root (hd3,0)
savedefault
makeactive
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1
```

Windows can be on any hdd as far as I know so you have to go by trial and error if you want to get it going.
Change the root line the same way as you did with ubuntu on startup  but you have to start with (hd1,0) and you have to change the mapping line as well to ,map (hd0) (hd1) till you find the hdd which boot windows for you.
Then change your menu.lst with the found hdd ,save the file and you're good to go.

The menu.lst can be changed with```
gksu gedit /boot/grub/menu.lst
``` save it when done!

I think you have a general idea what we are doing and how to make things work,but if you have questions,just ask.

Good luck and enjoy your ubuntu :)

---

### Post by Lightgod86 on 2007-11-08
Cool, everything works now...

Windows was on (hd1,0) so i just replaced all the 3's with 1's and grub worked on loading both after the changes without a hitch!

I must say i am amazed on the great support this community gives, and I just wanna say THANKS one more time!

---

### Post by Doggles on 2007-11-09
Nice one Bulldog - that was starting to confuse me so I stopped posting in case I made matters worse!

---

### Post by bulldog on 2007-11-09
Thank you. :)

---

