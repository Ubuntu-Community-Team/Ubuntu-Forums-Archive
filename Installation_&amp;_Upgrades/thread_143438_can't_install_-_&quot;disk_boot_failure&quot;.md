---
title: "can't install - &quot;disk boot failure&quot;"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by hmLyons on 2006-03-12
I'm trying to install Ubuntu (2.6.12-9-386) but I always get the following message after completing the installer "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

I've tried
-another hard drive (6gb IDE, which I had sucessfully run Vector Linux on before)
-letting the installer partition my drive
-disconnecting the CD drive (leaving only the hard drive, set as master)
-changing the disk to LBA mode in my bios (saw a post that recommended this)
-loading failsafe defaults in bios
-clearing CMOS with a jumper
-flashing my bios to most recent vesion
-getting angry (didn't help)
-installing Fedora Core 4 (same problem)

Some system info
DFI K8M800-MLVF
Western Digital 200gb IDE (WD2000JB-00FUA0) (first channel, master) I've run Fedora Core 3 on this drive before without issue. Altough I'd actually installed FC3 on that drive when it was inside another computer.

I was able to boot Ubuntu with grub installed on a USB stick, although I wasn't sure what to do once I was at the shell.

I'm able to run Knoppix from CD (that's how I'm writing this).

Perhaps relevant, after the installer is done and it says "Rebooting System" (or something) the system never reboots, after waiting a few minutes, I just pressed the reset button.

Any suggestions on what I can try next?

Thanks,
HM

---

### Post by FredSambo on 2006-03-12
at the risk of sounding condescending, what is the boot configuration in the BIOS?

---

### Post by hmLyons on 2006-03-12
It's set to;
First Boot Device: HDD-0
Second Boot Device: HDD-1
Third Boot Device: CDROM
Boot Other Devices: Enabled

---

### Post by FredSambo on 2006-03-12
did you try disabling 'boot other devices?'

---

### Post by hmLyons on 2006-03-12
Just tried that now. No luck.

---

### Post by FredSambo on 2006-03-12
nvm...

---

### Post by uscfan on 2006-03-12
The error message you are recieving is one sent by the BIOS notifying you that there are no bootable devices. Try setting your CD drive to the first boot device.

---

### Post by hmLyons on 2006-03-13
I'll try that when I get home, but I'm a little confused. How will that help me boot off the hard drive I've just installed Ubuntu on?

---

### Post by hmLyons on 2006-03-14
That didn't work :(

---

### Post by hmLyons on 2006-03-14
Success! I chanced upon the solution. I removed the jumper from my hard drive and voila! Strange, I don't know why this is the case - this drive was previosly booting Fedora Core 3 fine... but it works now anyways!

Thanks for everyone!

HM

---

### Post by rookie_yu on 2006-03-14
U got 2 hard drives on same channel? Maybe jumper was on cable select position. It works sometimes on single drive configuration, but not if U connect another drive.

---

### Post by hmLyons on 2006-03-15
Nope. HHD was on ide channel 1 and CD was connected to ide channel 2 on  the mobo.

---

### Post by mozetti on 2006-03-15
Newer motherboards sometimes don't like master/slave settings, preferring "cable select." I'm guessing this may have been your issue, since you said the working FC3 was when the HDD was in another box.

---

### Post by leon-1 on 2006-03-15
[QUOTE=rookie_yu]U got 2 hard drives on same channel? Maybe jumper was on cable select position. It works sometimes on single drive configuration, but not if U connect another drive.[/QUOTE]

That isn't a bad idea, except I would say that the drive was already set to cable select. There is a possibility that the control lines on the cable that are used when the cable select function is used are damaged, hence when you tell the machine to boot it is unsure where the drive is, the bios throws a wobbler and says you have no drive.

Take out the jumper the drive now becomes a slave or master, the cable select control line is no longer required, BIOS is happy and all seems to work.

There is a possibility that the cable has degraded or is degrading, it may be worth changing the IDE cable.

---

### Post by Kurt` on 2006-03-19
I had this EXACT same problem, EXACT same setup, and resolved it the EXACT same way just now...

However, this machine was quite old. It's a Compaq from 1998 :p

---

### Post by hmLyons on 2006-03-19
I had actually tried swapping the IDE cable with one I had lying around just before I tried the jumper thing, didn't seem to make a difference.

Glad I got it working. Ubuntu rocks!

---

### Post by mirko2 on 2006-04-27
[QUOTE=mozetti]Newer motherboards sometimes don't like master/slave settings, preferring "cable select." I'm guessing this may have been your issue, since you said the working FC3 was when the HDD was in another box.[/QUOTE]

Something like this must be the problem, because I just had this same problem. I tried different disks and operating systems etc., but the disk was always set as Master (No other devices on the primary bus.)

Strange or not, Ubuntu Live CD and Installer CD booted just ok from a DVD-drive set as Master on secondary bus. 

The only thing that did not boot from the disk set as Master was Ubuntu 5.10, but now with Cable Select the problem is solved.

Thanks.

---

