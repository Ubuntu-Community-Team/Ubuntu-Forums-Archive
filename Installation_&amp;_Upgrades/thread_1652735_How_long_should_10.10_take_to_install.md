---
title: "How long should 10.10 take to install?"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by nerwintheodd on 2010-12-25
I'm booted from the CD, and I'm on a 2ghz Celeron processor with a 160gb HDD.  I'm asking because the installer is hanging at the &quot;Preparing to Install:For Best Results&quot; screen for what seems to be an inappropriate period of time when I click the &quot;forward&quot; button.  I'm impatient, but unsure if this is typical for the installation process.

EDIT: While the display doesn't show any activity, besides keeping the window active, and spinning the loading cursor, the window seems to be dead.  It spins the CD drive every now and then, but I can't tell if that's just a product of the OS operating in the background, or if it's installing.

---

### Post by karthick87 on 2010-12-25
It depends upon your system configuration..For me it took just 15 minutes for a complete install..

---

### Post by nerwintheodd on 2010-12-25
Hmm... Did you experience any difficulty or hang time right after that "For Best Results" screen? Does it just begin installing directly after that window? I figured there would be more dialogue before it just dove straight into the installation process.

---

### Post by Rubi1200 on 2010-12-25
If you chose the options to download and install 3rd party software and perform updates during the installation process it could take quite some time.

Depends on your Internet connection as well as computer. 

I have seen some users report that it took up to 1/1.5 hours for the whole process to complete.

---

### Post by nerwintheodd on 2010-12-25
No, no updates/3rd parties. Would it make the process easier if I haven't already booted the OS from the CD when I begin installation?  To just select "Install" from the boot CD window?

EDIT: WAIT... So the installer isn't recognising my internet connectivity at the "For Best Results" screen. I figured that would just be required for the 3rd party stuff and updates, but are you saying that it's required for the install process to have an internet connection?

---

### Post by Rubi1200 on 2010-12-25
How far along in the process are you? Or did you stop the install?

And, no, I don't believe that would make a difference.

EDIT: As far as I know, I don't think an Internet connection is a requirement for the install unless you chose the options I mentioned previously.

---

### Post by nerwintheodd on 2010-12-25
Literally, I hit the "Forward" button at the "For Best Results" screen on the installer, the very first screen. After I click the button, the loading cursor just spins and spins, but the window remains active(buttons respond to hovering.)

---

### Post by nerwintheodd on 2010-12-25
&quot;ubi-partman failed with exit code 10&quot; Was the error message I got after sitting and letting it load for an hour. Here's the syslog for the event if it helps:  Dec 25 19:53:41 ubuntu kernel: [253846.048881] ata1.00: cmd 60/08:00:a0:9e:a1/00:00:12:00:00/40 tag 0 ncq 4096 in Dec 25 19:53:41 ubuntu kernel: [253846.048882]          res 41/40:08:a0:9e:a1/00:00:12:00:00/62 Emask 0x409 (media error)  Dec 25 19:53:41 ubuntu kernel: [253846.048884] ata1.00: status: { DRDY ERR } Dec 25 19:53:41 ubuntu kernel: [253846.048886] ata1.00: error: { UNC } Dec 2Dec 25 20:00:36 ubuntu kernel: [254261.379970] aufs au_xino_do_write:378:gconfd-2[4756]: I/O Error, write failed (4294967268) Dec 25 20:01:37 ubuntu kernel: [254322.378344] aufs au_xino_do_write:378:gconfd-2[4756]: I/O Error, write failed (4294967268) Dec 25 20:01:37 ubuntu kernel: [254322.378510] aufs au_xino_do_write:378:gconfd-2[4756]: I/O Error, write failed (4294967268) Dec 25 20:01:37 ubuntu kernel: [254322.378651] aufs au_xino_do_write:378:gconfd-2[4756]: I/O Error, write failed (4294967268) Dec 25 20:01:37 ubuntu kernel: [254322.378786] aufs au_xino_do_write:378:gconfd-2[4756]: I/O Error, write failed (4294967268) EDITED FOR FORMATTING

---

### Post by Rubi1200 on 2010-12-25
Could it be a dodgy CD or a bad burn?

Try downloading again and before you burn at the lowest speed check the MD5SUM:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The other thing I would ask you to do, if you are still on the LiveCD, is post the output of this command:
```
sudo parted -l
```Thanks.

EDIT: do you have a RAID array?

---

### Post by nerwintheodd on 2010-12-25
```
Model: ATA TOSHIBA MK1655GS (scsi) Disk /dev/sda: 160GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End    Size    Type      File system     Flags  1      1049kB  154GB  154GB   primary  2      154GB   160GB  6290MB  extended  5      154GB   160GB  6290MB  logical   linux-swap(v1)   Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only. 
``` I'm not sure if the formatting on this is as crappy as it appears on my browser, sorry.

---

### Post by Rubi1200 on 2010-12-25
Sorry, I am unable to read that. Copy/paste the entire output; or is this a blank drive waiting for something to be installed?

---

### Post by nerwintheodd on 2010-12-25
Model: ATA TOSHIBA MK1655GS (scsi) Disk /dev/sda: 160GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End    Size    Type      File system     Flags  1      1049kB  154GB  154GB   primary  2      154GB   160GB  6290MB  extended  5      154GB   160GB  6290MB  logical   linux-swap(v1)   Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.  Firefox is being a **** and the formatting of my posts is all off.  hopefully this looks better...      *EDIT* This is quite frustrating, but is an entire copypaste of the response I got to the command line.

---

### Post by Rubi1200 on 2010-12-25
> Model: ATA TOSHIBA MK1655GS (scsi) Disk /dev/sda: 160GB Sector size  (logical/physical): 512B/512B Partition Table: msdos  Number  Start    End    Size    Type      File system     Flags  1      1049kB  154GB   154GB   primary  2      154GB   160GB  6290MB  extended  5      154GB    160GB  6290MB  logical   linux-swap(v1) hmm.

I see an extended partition and swap, but where is the Ubuntu install.

Try this instead:

> sudo fdisk -lAgain, are you sure this was not a bad burn or a dodgy CD?

What about RAID?

This might also help:
[http://ubuntuforums.org/showthread.php?t=1498417](http://ubuntuforums.org/showthread.php?t=1498417)

---

### Post by mysteriousdarren on 2010-12-25
I would use a text install if you are having this much trouble, also in my experience go check the disk before installing.

---

