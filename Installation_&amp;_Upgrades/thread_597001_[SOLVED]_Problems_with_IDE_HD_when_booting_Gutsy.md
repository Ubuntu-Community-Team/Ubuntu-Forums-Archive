---
title: "[SOLVED] Problems with IDE HD when booting Gutsy"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by cirorodrigues on 2007-10-30
I did a fresh install of Gutsy using the alternate CD. After some trouble with this install, mainly regarding to wifi and nvidia, I managed to solve most of the problems. 
The remaining one is not blocking the usage, but it's slowing down the boot process. During boot, I get four times the following message:
[INDENT][   37.064000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   37.064000] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x12 data 4096 in
[   37.064000]          res 40/00:02:00:7a:00/00:00:00:00:00/b0 Emask 0x4 (timeout)[/INDENT]
where the numbers between brackets change from one to another. I analysed dmesg output (attached) and I think the problem is a frustated tentative to set UDMA mode 5 (UDMA/100) to the HD (ata1.00), until finally change it to UDMA mode 4 (UDMA/66).
After booting, the system is running very stable, including wifi and nvidia proprietary drivers.
This problem didn't occurred with any of the previous versions (6.06, 7.04) I've installed and used last 18 months, and I did no hw changes at all.
Following some research, I tried hdparm changing info into /etc/hdparm and running update-rc.d, but seems the changes I did have no effect during boot. Does anyone know how to force UDMA/66 from the beginning, avoiding the wasteful tentatives?

---

### Post by N/A on 2007-10-31
I have the same problem

---

### Post by ruibernardo on 2007-11-01
Hi,

that was happening to me on a qemu VM and gutsy. To solve this enable the ide-generic module on boot.

Edit the file /etc/initramfs-tools/modules:
```
sudo nano /etc/initramfs-tools/modules
```add "ide-generic" to the file, save and exit.

Then update the kernel modules loaded on boot with
```
sudo update-initramfs -u
```and reboot.

---

### Post by aus1and3r on 2007-11-01
thank buddah that this thread is already here!
my former roomate left an ancient sotec laptop intel celery process with like 256 megs of ram yadda yadda...  anyway, i want this as a fool around computer, especially for having fun with linux. 
big problem though, i get this same message as I try and run/install xunbuntu.  i tried to use the code listed earlier but it seems as if i'm missing something. i get responses like /bin/sh: sudo:not found...
i figure im missing some kind of command.

help me!

---

### Post by N/A on 2007-11-01
It works :) thanks epimeteo

Now i have to figure out why is the splash screen working (not that is a bad thing but i got used to it not working) and why my wireless is active just for a few minutes after reboot. 

Seems nomatter what there's always a trade off :lolflag:

---

### Post by cirorodrigues on 2007-11-01
> **N/A said:**
> It works :) thanks epimeteo

Now i have to figure out why is the splash screen working (not that is a bad thing but i got used to it not working) and why my wireless is active just for a few minutes after reboot. 

Seems nomatter what there's always a trade off :lolflag:

About the splash screen, I don't know if it was the same problem I had before, but in my case I got no splash screen and LCD display shows "out of range...". 
I solved it:
[INDENT]sudo gedit /etc/usplash.conf[/INDENT]
change the information about resolution:
[INDENT]x=1024[/INDENT]
[INDENT]y=768[/INDENT]
or some resolution suitable to your specific monitor. After that, reboot. 

Problem was caused by the original configuration set for a widescreen monitor and mine can't support it. I think this is the cause of many complaints about Gutsy CD doesn't showing splash screen during boot.

About the IDE problem I'll test and I'll come back later.

---

### Post by cirorodrigues on 2007-11-01
Thanks a lot. It works.
Indeed, it's even better than before as now hdparm shows the HD is working with udma mode5 (UDMA/100) instead of previous mode4 (UDMA/66). I don't know why, but before these changes my HD was /dev/sda and now it's /dev/hda (as it was in Feisty).

---

### Post by spelingchampeon on 2007-11-02
I hope what happened here has something to do with what happened to me. I am off work for a month, and figured it would be a good time to try out Gutsy. I took my AMD2000+ and ran the upgrade from Fiesty. Everything was fine for the 1st couple of days, then my HD started to fail. I was getting a whole bunch of ata1 errors. I rebooted, and nothing.. sat there. I could not get into GRUB, or recover anything. I took the HD, and ran Western Digital diagnostics on it again, but it would not run ..failed immediately. I thought it was just the HD. 

I took another Western Digital HD (80gig), and ran the WD diagnostic, which passed fine. Then, for giggles, I fdisk'd it in DOS, and ran the DOS format. Clean. Installed Gutsy, and it failed. I retested the disk again, and with the WD utilities, wrote 0's to the drive...installed Gutsy again, and it worked for 2 days. Yesterday, I went to boot up, and I got nothing but Error 16's and 18's. I tried to recover with the LiveCD, but all I was getting was ata1 errors. 

Either I am doing something wrong, or something has 'linux-wise' eaten my HD to the point Linux thinks they are no good. Any clue's (aside from this post?).

---

### Post by cirorodrigues on 2007-11-05
Just one additional comment. After perform this correction, I have no more errors messages regarding the HD, but boot time it's not that better, and my DVD players seems to be slower. I'll try to confirm this.

---

