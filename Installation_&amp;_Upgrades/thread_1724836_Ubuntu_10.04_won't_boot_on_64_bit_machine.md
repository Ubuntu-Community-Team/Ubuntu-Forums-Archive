---
title: "Ubuntu 10.04 won't boot on 64 bit machine"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by jhouse59 on 2011-04-08
I've tried two Ubuntu 10.04 (64 bit) disk. From two different sources. Neither one will boot on my computer. It has a AMD Phenom II X6 six-core processor, 8GB PC3-10600 DDR3 SDRAM, and a ATI Radeon HD 5570 graphics. It will get to the Ubuntu splash screen with the dots under it. Stays there till my monitor goes to sleep. I've used two other Linux disk Mint and Zorin. Both of them will boot from their disk.
I've tried to install Ubuntu without booting into the live DVD. Same thing happens. I was wondering if there was something I could do to get it installed on my computer?

---

### Post by PCNetSpec on 2011-04-08
Try this...

Boot from the 10.04 LiveCD - 
At the very first screen, the one with just the rectangle (it&#8217;s meant to be a keyboard) and a human figure, press any key - spacebar will do.

Then choose your language.

Then make sure you have &#8220;Try Ubuntu without any changes&#8221; selected, and then press F6

Remove this from the end of the command line:

**quiet splash**

and replace it with

**radeon.modeset=0 xforcevesa**

Install Ubuntu... when you restart, you'll need to enter this once more... once booted, go to **System>Administration>Hardware Drivers** and activate the ATI proprietary driver (fglrx).

Other links:
[http://ubuntuforums.org/showthread.php?t=1467690](http://ubuntuforums.org/showthread.php?t=1467690)
(post #9)
and
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jhouse59 on 2011-04-09
> **PCNetSpec said:**
> Try this...

Boot from the 10.04 LiveCD - 
At the very first screen, the one with just the rectangle (it’s meant to be a keyboard) and a human figure, press any key - spacebar will do.

Then choose your language.

Then make sure you have “Try Ubuntu without any changes” selected, and then press F6

Remove this from the end of the command line:

**quiet splash**

and replace it with

**radeon.modeset=0 xforcevesa**

Install Ubuntu... when you restart, you'll need to enter this once more... once booted, go to **System>Administration>Hardware Drivers** and activate the ATI proprietary driver (fglrx).

Other links:
[http://ubuntuforums.org/showthread.php?t=1467690](http://ubuntuforums.org/showthread.php?t=1467690)
(post #9)
and
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I got Ubuntu installed. When I restarted. The only thing I got was a black screen and a flashing line in the upper left hand corner. It doesn't give me a choice between Windows or Ubuntu. Can someone help me?

---

### Post by Dutch70 on 2011-04-10
Boot up your live cd and select "Try Ubuntu".

Run the following command in a terminal, and post the output between ```
[ /CODE] tags using the "#" symbol in the toolbar.
That's a lower case "L"
[CODE]sudo fdisk -l
```

---

### Post by jhouse59 on 2011-04-10
> **Dutch70 said:**
> Boot up your live cd and select "Try Ubuntu".

Run the following command in a terminal, and post the output between ```
[ /CODE] tags using the "#" symbol in the toolbar.
That's a lower case "L"
[CODE]sudo fdisk -l
```

Here it is. I've got my computer so I can boot back into Windows. Had to go into the BIOs to change back to the hard drive that had Windows on it.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xad1c6678

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      120021   963957760    7  HPFS/NTFS
/dev/sda3          120021      121602    12699648    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015205

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       62395      182402   963957760    7  HPFS/NTFS
/dev/sdb2               1       62394   501179743    5  Extended
/dev/sdb5               1        2444    19631367   83  Linux
/dev/sdb6           61375       62394     8193118+  82  Linux swap / Solaris
/dev/sdb7            2445       61374   473355193+  83  Linux

Partition table entries are not in disk order
```

---

### Post by Dutch70 on 2011-04-10
You may want to try some of these settings.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

If it doesn't work, I would focus on your graphics card. I understand ATI graphics cards are kind of buggy.

---

### Post by jhouse59 on 2011-04-10
> **Dutch70 said:**
> You may want to try some of these settings.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

If it doesn't work, I would focus on your graphics card. I understand ATI graphics cards are kind of buggy.

That's the graphics cards that came with the computer. I tried to edit the grub file. But, I couldn't find one on the partion. The one that came up was. I think off of the DVD (not sure). Because it let me save it.
In the home folder there is just one folder. Seems like when I had Ubuntu 10.04 installed on my 32 bit computer. It installed more folders.
What is the code for edit the grub file from the DVD? This is the code I typed gksudo gedit /etc/default/grub.

---

### Post by PCNetSpec on 2011-04-11
What did you do to get Ubuntu installed ?

---

### Post by jhouse59 on 2011-04-12
> **PCNetSpec said:**
> What did you do to get Ubuntu installed ?

 Just put the DVD in the tray. Then done this.
> Then make sure you have &#8220;Try Ubuntu without any changes&#8221; selected, and then press F6

Remove this from the end of the command line:

quiet splash

and replace it with

radeon.modeset=0 xforcevesa

Answered the questions. Waited about 30 or 40 minutes. It said it was done. When I rebooted got a black screen with a flashing line in the upper left hand corner. Then had to go into BIOs and choose the hard drive with the Windows 7 on it to get it to boot. When I get timeI'm going to try and re-install it. I noticed when I installed it on my XP machine it had done something similar.

---

### Post by PCNetSpec on 2011-04-12
Did you miss this part ?

Install Ubuntu... when you restart, **you'll need to enter this once more**... once booted, go to System>Administration>Hardware Drivers and activate the ATI proprietary driver (fglrx).

OK, maybe I should have explained a bit bettter, as the way you enter the:
radeon.modeset=0 xforcevesa
kernel boot option is slightly different when booting from the hard drive.

As soon as your BIOS POST screen disappears, and you see:

[center][img]http://linuxforums.org.uk/MGalleryItem.php?id=1122[/img][/center]

Press the **SHIFT** key, you will be presented with the GRUB menu

Select the 'Default' Ubuntu kernel (usually the top one), and rather than pressing enter, press **E** to edit.

You will be presented with a screen like this:

[center][img]http://linuxforums.org.uk/MGalleryItem.php?id=1152[/img][/center]

Press the **DOWN ARROW** key until you get to the line that starts with:

> **linux /boot**

Press the **END** key to position the cursor at the end of the that line... it *usually* ends with &#8220;**quiet splash**&#8221;. 

Now you can enter additional kernel boot options... the nomodeset option has been added in the above screenshot... but you need to add **radeon.modeset=0 xforcevesa** in its place, so make the end of that line read:

> **quiet splash radeon.modeset=0 xforcevesa**
(doesn't matter if it moves down a line, as long as there is a space between splash and radeon.modeset=0 xforcevesa)

Now hit **Ctrl+X** to boot.

If that doesn't work, try "replacing" **quiet splash** with **radeon.modeset=0 xforcevesa** as you did the first time.

Once booted, install the proprietary fglrx driver from:
**System>Administration>Hardware Drivers**

Hopefully the proprietary drivers won't need any boot options, and things will "just work" after a reboot ;)

---

### Post by jhouse59 on 2011-04-16
Thanks.Everyone for the help. I finally got Ubuntu 10.04 to install. Had to do a re-install. But, it's up and running.

---

