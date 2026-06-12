---
title: "Additional ubuntu install on secondary hard drive."
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by LinuxView on 2008-12-02
I had one of my machine die...motherboard meltdown. Fortunately, the hard drive has no damage. The machine had 8.04. I have an another machine which has 8.10. I would like to add that 8.04 install to the grub on this new machine to start of that 8.04 install so I can grab all the installed application list, backup mysql databases, etc etc. Both computers had the same graphics card so there shouldn't be any driver issues (I just need to login once and grab everything). My guess is that I would have to mess with the current grub but I'm wondering if its possible to put an additional grub on a floppy drive so I don't damage the current grub in any way. Here's the disk -l output:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc25760bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       17165   137877831    7  HPFS/NTFS
/dev/sda2   *       17166       29857   101948490   83  Linux
/dev/sda3           29858       30401     4369680    5  Extended
/dev/sda5           29858       30401     4369648+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2ddf2dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         505     4056381   83  Linux
/dev/sdb2             506       30515   241055325    5  Extended
/dev/sdb5             506       30141   238051138+  83  Linux
/dev/sdb6           30142       30515     3004123+  82  Linux swap / Solaris

```

/dev/sda2 is that 8.04 install. That ntfs /dev/sda1 is not a windows install ... it's just space I created for backup. /dev/sdb1 is the current 8.10 install. Any help would be apprenticed ;)

---

### Post by caljohnsmith on 2008-12-02
When you say 8.02, do you mean 8.04 (Hardy) I assume? Are you currently booting the 8.10 sdb drive on start up? If that's the case, how about when you get the Grub menu on start up, press "c" to get the command line, and enter:
```
grub> rootnoverify (hd1)
grub> chainloader +1
grub> boot
```
And that should boot your sda drive, which I assume still has Grub in the MBR (Master Boot Record), so you should get 8.04's Grub menu if all goes well. Let me know if that works, or if it doesn't, let me know what happens when you try it. :)

---

### Post by LinuxView on 2008-12-02
yes sorry I meant 8.04 (edited in the first post)
yes i am booting the 8.10 on sdb drive on startup.

I tried ur suggestion and I got the following output when i hit enter after typing boot:

> grub> boot
Starting up ...

Error loading operating system

I believe grub was on the other hard drive on that 8.04 machine which did not survive the meltdown (wouldn't power on .. controller burnout?) I had nothing much on that 20gb hard drive ... just an xp install for testing and I guess the grub got install on that drive. So i will have to rebuild grub for this drive somehow without effecting the current 8.10 grub?

:-({|=

---

### Post by caljohnsmith on 2008-12-02
OK, how installing Grub to the MBR of your sda drive to see if that will make it bootable; open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
And please post the output of the above commands. Next reboot, but before you try the steps I gave in my previous post, also do:
```
grub> geometry (hd0)
```
And let me know if that command shows the first partition is type "0x7" or "0x83"; that will make it clear which drive you are booting from. Then do the Grub commands from my previous post to try and boot the sda drive again. Let me know exactly what happens and we can work from there. :)

---

### Post by LinuxView on 2008-12-02
John, i really apprentice you helping me out here, Thank you ;)

I did that root (hd0,1) and setup (hd0) in the terminal .. i dropped the output to a notepad and forgot to save it lol .. it said something like 16 embedded then at the end it said succeeded. 

Then I rebooted and entered command line using the "c" key during grub.

Output of grub> geometry (hd0)

```

drive 0x80: C/H/S = 1024/255/63, The number of sectors = 490234752, LBA

Partition num 0, filesystem type is ext2fs, partition type 0x83

Partition num 4, filesystem type is ext2fs, partition type 0x83

Partition num 5, filesystem type is unknown, partition type 0x82

```

The command in your other post booted the old grub :) But when I select the 8.04 version, it proceeded to the loading bar screen and the orange bar is just going right and left. After like 3-5 minutes, it loads this busybox with a command line.

---

### Post by LinuxView on 2008-12-02
So I just booted using the ubuntu 8.04 recovery option from the new grub and it stops on this part for about 2-5: 

> [   53.371923] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6.2:USB HID core driver

Then after 2-5, the following gets printed

> 
Done. 
       Check root= bootarg cat /proc/cmdline
       or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist,. Dropping to a shell!

(The x's are substituted for the hard drive real uuid.)


And then it goes back to the BusyBox command line. Please help :popcorn:

---

### Post by caljohnsmith on 2008-12-02
Great, we're making progress. How about booting the 8.04 drive again, but this time when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add:
```
rootdelay=130 acpi=off
```
Then press enter to save the change, and finally "b" to boot. See if that gets you any further, or if not, let me know what happens. :)

---

### Post by LinuxView on 2008-12-02
Nope, doesn't look like it did anything :( I also added that to the recovery line just to see whats happening and everything is still the same. And the uuid in kernel line in grub mataches that uuid in the alert message.

---

### Post by LinuxView on 2008-12-02
Got it working!

I did some googling and someone suggested that I delete ONLY the "quiet splash --" and add all_generic_ide to the kernel line. I tried it and it did the trick :)

John, thanks for your help .. couldn't have done with without you :guitar:

---

### Post by caljohnsmith on 2008-12-02
That's great news, glad you found a solution. Cheers and hope everything else runs smoothly. :)

---

