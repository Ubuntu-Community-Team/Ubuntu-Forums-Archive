---
title: "new install stuck in initramfs prompt after every boot"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by Budric on 2011-11-08
Hi,
 
I'm installing Ubuntu Server 11.10.  It's a fresh install where I repartition/format the whole disk.  After reboot the system gets stuck on (initramfs) prompt.  I can press CTRL + D, after which the system continues to boot and seems to work.  Network is up, SSH daemon is running and I can write to disk.
 
The dmesg I get just before the prompt is:
>  
[   36.055346] sd 2:1:0:0: Attached scsi generic sg3 type 0
[   36.055512] sd 2:1:0:0: [sda] 286523392 512-byte logical blocks: (146 GB/136$
[   36.056327] sd 2:1:0:0: [sda] Write Protect is off
[   36.056398] sd 2:1:0:0: [sda] Mode Sense: 03 00 00 08
[   36.056629] sd 2:1:0:0: [sda] Got wrong page
[   36.056694] sd 2:1:0:0: [sda] Assuming drive cache: write through
[   36.058067] sd 2:1:0:0: [sda] Got wrong page
[   36.058135] sd 2:1:0:0: [sda] Assuming drive cache: write through
[   36.068323]  sda: sda1 sda2 < sda5 >
[   36.069867] sd 2:1:0:0: [sda] Got wrong page
[   36.069934] sd 2:1:0:0: [sda] Assuming drive cache: write through
[   36.070003] sd 2:1:0:0: [sda] Attached SCSI disk
[   51.465262] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: null

 
I don't know if this error is related to my problem.
 
/dev/sda is a RAID-1 volume.  The hardware is Dell PowerEdge R610 which I believe should work with Ubuntu ([link]("http://www.ubuntu.com/certification/hardware/201003-5449"))
 
Anyone know what's going on and how I can fix this?
Thanks very much.

---

### Post by redknite on 2011-11-10
holy crap.  This is the same problem I'm having.  I have the same system too!  when you were doing the install what did you choose for partitioning?  I chose guided -entire disk.  I didn't do the LVM.  Did you?

---

### Post by redknite on 2011-11-10
also,  typing exit seems to load ubuntu also.

---

### Post by enc7yp7 on 2011-12-09
I too am seeing this issued on a dell 2950 - RAID 1 to a logical volume, Seagate drives, Ubuntu server 11.10 x64 bit.  I also chose guided -entire disk without the LVM.

---

### Post by Rubi1200 on 2011-12-10
Hi all,
post the results of the boot info script so we can get a better overview of what might be happening.

See the link at the bottom of my post with instructions.

---

### Post by Haninjapan on 2011-12-12
I have the same problem with my Ubuntu 11.10 install: after grub I am stuck at a purple splash screen . Behind it is the initramfs prompt waiting for something.
Typing "exit" works to successfully continue booting ubuntu.  Sometimes I can boot without problem. 

I do use two raid1 and 5 arrays for my home and media files. The rootfs is on a normal partition

I have used the boot_info_script.sh to generate the attached results file.

I hope it helps.

Greetings,

Han

---

### Post by megahertz on 2011-12-14
Did you install with ubuntu-11.10-alternate?
Is dmraid loaded?
I had the same problem. Try to remove Grub and install again. Than run sudo update-grub.

---

### Post by Haninjapan on 2011-12-14
I should have explained this before.
I arrived into this situation after upgrading from the normal Ubuntu 11.04 desktop version.
It is for me a not specific "ubuntu server" related problem 

I have read indeed that dmraid could give this kind of problems. I have removed the package I assume that I don't load this module anymore. But is should do a quick lsmod and scan dmesg to make sure.
But anyhow removing the package did not help.

Furthermore is the naming of my raid's a bit of a mess I use "/dev/md/name" but maybe I should fix it to /dev/md126 type of convention to make sure that it works more robust. 

I did not try to remove and reinstall grub.  How did you do this?   I am a bit hesitant to remove my bootloader; it could lock me out....
I will have a look at this as well...

Having to type "exit" on the purple screen is not making my wife very positive about Ubuntu. I am quite motivated to find a solution....

---

### Post by tomakCZ on 2011-12-16
the same problem on Dell R415, fresh install server 11.10, result.txt included

---

### Post by enc7yp7 on 2011-12-20
No intention to jump this thread to a new topic, but perhaps related...After having some issues with the networking service not starting, I noticed I am booting into runlevel 2.  I am new to the debian-based world and not sure if this is common for Ubuntu server builds.  Should the default be runlevel 3 and could this effect the grub process causing it to hang in single-user mode or initramfs?

Please let me know if my out-loud thinkings don't fit the mode for this forum and I will reel it in, lock it up, dial it down.

---

### Post by Skidd on 2012-01-31
Just an FYI to anybody else having this same problem.
Our R610 server, just like others here, would drop to the rescue prompt on every boot.  The fix was not obvious at first.  The alert message kept saying the disk was not found, yet I could see it in /dev  

The problem had something to do with how long it takes for the controller hardware to actually respond back with the correct devices.

The fix however is very very easy!!

edit the file "/etc/default/grub"
Find the variable LINE 
```
GRUB_CMDLINE_LINUX=""
```
change it to
```
GRUB_CMDLINE_LINUX="rootdelay=90 nomodeset" 
```
Save the file and run
```
update-grub
```

The "nomodeset" is not necessary, but I prefer not to go into any upscaled graphics mode on a server console.

Voila!!
If you check the contents of /boot/grub/grub.cfg
You'll see the addition of the above parameters on your kernel line.

Subsequent reboots "should" work now.

---

### Post by enxtur on 2012-08-16
hi, this success on me, ubuntu 12.04 LTS server on dell poweredge R710, tnx :guitar:

---

### Post by jaelcio on 2013-01-16
thankyou this success on me, ubuntu 12.04 LTS server on dell poweredge t300

---

### Post by thctlo on 2013-02-24
I bet you guys installed from usb stick. 
 
reinstall from cdrom and this problem is gone. 
 
i run multiple systems, dell server en own builds, debian and ubuntu
and i have seen this problem only when i install ubuntu from usbstick
 
i used pendrive en unetbooting for creating the stick. 
 
the drive /bootloader changes after the install with stick. 
for example at install stick is /dev/sda and disk are /dev/sdb 
after reboot disk are /dev/sda 
 
Why this works with debian and not ubuntu i dont know.

---

### Post by matt_symes on 2013-02-24
This is an old thread so closed.

---

