---
title: "Can't boot back into ubuntu after windows 7 installation"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by jsd013 on 2010-05-12
Alright so I had a dual boot system with ubuntu 9.10 and vista installed on two separate partitions. I updated vista to 7 and found that I could no longer choose an operation system on boot up as I had been doing with vista/ubuntu. After many days of searching for answers I tried several things including a few programs like easyBCD but none of them helped and i now get to choose between linux and windows 7 at start up but if I choose linux it says no operating system installed.... 
    
    So I tried to do the livecd (ubuntu 10) method today and found out i cant even boot into a livecd session. Everytime i put in the disk and boot a loading screen comes up and after a while it turns into a screen with a black background and the following text:
"No init found. Try passing init= bootarg.
Busybox. v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)"

Ive tried to execute the fdisk command after finding it helped other people with a similiar error in forums ive read but i just get an error saying "/bin/sh: fdisk: not found" or for several other commands Ive seen suggested to users in a similar predicament, without any luck though. I cant do the bootinfo script either because well...i cant even boot from a live cd.

I realize i may have messed around with something completely beyond my understanding and that is why i need the help of someone who's understanding it is within. All i want is my working OS back and any help at all would be greatly appreciated.

EDIT
Sorry it turns out the livecd was corrupt and I am now using a valid one but still having a lot of trouble trying to fix this but here is the output of sudo sfdisk -l and ive noticed it is rather unusual compared to what ive seen other users post......can someone please help me fix this.....:
```
Device      Boot   Start      End       #cyls      #blocks            Id         System
/dev/sda1     *    0+         19319-    19320-    155186144      7     HPFS/NTFS
/dev/sda2          37533+   38912-    1360-    10919936         7     HPFS/NTFS
/dev/sda3          19320     37552     18233     146456572+    5     Extended
/dev/sda4          0               -           0             0                 0     Empty
/dev/sda5          19320+   36807     17488-    140472328+   83     Linux
/dev/sda6          36808+   37552       745-      5984181        82     Linux swap / Solaris
```And im sorry it looks so messed up i tried for half an hour and couldnt get it to look the way i wanted im a noob.....

---

### Post by Mark Phelps on 2010-05-12
Being a multi-booter for years, I've learned the hard way that the MS boot stuff is the harder to fix and the easiest to break ...

So, I would recommend you fix the Win7 boot first and deal with rebooting Ubuntu after you get that working.

Did you bother to use the Win7 Backup function to create and burn a Win7 Repair CD? I'm guessing probably not -- so go to the link below, download and burn the appropriate Win7 disk image, boot with it, and run  Startup Repair repeatedly until it no longer fails.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Once you get that working, come back ...

---

### Post by kansasnoob on 2010-05-12
It would be best if we could see the output of The Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Also please clarify, you can boot Windows but not Ubuntu, is that correct?

---

### Post by unisol on 2010-05-12
Reinstall Ubuntu Grub Bootloader After Windows Wipes it Out
If you run a dual-boot system with Linux and Windows, this has happened to you. You had to do your monthly reinstall of Windows, and now you don’t see the linux bootloader anymore, so you can’t boot into Ubuntu or whatever flavor of linux you prefer.

Here’s the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

sudo grub

> root (hd0,0)

> setup (hd0)

> exit

Reboot (removing the livecd), and your boot menu should be back.

---

### Post by kansasnoob on 2010-05-12
> **unisol said:**
> Reinstall Ubuntu Grub Bootloader After Windows Wipes it Out
If you run a dual-boot system with Linux and Windows, this has happened to you. You had to do your monthly reinstall of Windows, and now you don’t see the linux bootloader anymore, so you can’t boot into Ubuntu or whatever flavor of linux you prefer.

Here’s the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

sudo grub

> root (hd0,0)

> setup (hd0)

> exit

Reboot (removing the livecd), and your boot menu should be back.

How can you be sure this is legacy grub and not grub2?

---

