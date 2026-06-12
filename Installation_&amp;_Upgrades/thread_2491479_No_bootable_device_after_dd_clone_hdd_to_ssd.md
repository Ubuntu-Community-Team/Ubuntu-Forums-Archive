---
title: "No bootable device after dd clone hdd to ssd"
date: 2023-10-10
forum: Installation &amp; Upgrades
---

### Post by wakingsleeper on 2023-10-10
Hello, 

I run a small media server and decided it was a great idea to upgrade to a SSD.  100G HDD -> 500G SSD.   Booted to a live usb and DD'd to clone, shutdown removed the original drive and on startup bios is telling me no bootable drives.  I found ubuntu boot-repair and gave it a shot but didn't identify anything wrong on its own. Added the output in paste bin below

Any help greatly appreciated.

[https://paste.ubuntu.com/p/XWVK75tV5d/](https://paste.ubuntu.com/p/XWVK75tV5d/)

---

### Post by oldfred on 2023-10-10
I typically suggest new clean install & restore from backup. Becomes good test that backup has everything while you still have old drive.

What does this show, if flash drive is sda & new drive is sdb.
sudo gdisk -l /dev/sdb

You may have gpt's backup partition table in middle of drive when it has to be at the end of the drive. You can use gdisk to fix that, if that is the issue.

---

### Post by sudodus on 2023-10-11
If a GUID partition table, you need an extra step to restore the backup partition table at the tail end of the new drive. You can fix it after cloning with **[FONT=Courier New]gdisk[/FONT]** or easier with **[FONT=Courier New]gpt-fix[/FONT]** according to [this link](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix).

That kind of fix is built into the cloning tools [Clonezilla](https://clonezilla.org) and [mkusb](https://help.ubuntu.com/community/mkusb), but when you clone with **[FONT=Courier New]dd[/FONT]**, you must fix it as a separate operation afterwards.

---

### Post by wakingsleeper on 2023-10-11
Thank you both, I ended up reinstalling the HDD to get it back up and running for the day.  I guess I need to read up more on GPT... I will try the gpt-fix to see if that corrects the issue, but might end up re-cloning with Clonezilla since there will be database updates from today.   Hopefully I'll have time to mess around with it tonight, and I will post again with results.

---

### Post by oldfred on 2023-10-11
One disadvantage of dd is that it also copies all the empty space which makes it very slow.

I install each new release, but keep LTS versions as main working install.

I can install from RAM using toram parameter, so install is from RAM to SSD. That install takes about 10 to 12 minutes.
I have lots of partitions, so finding partitions on my drives, seems to be the longest part of the install process.

Using rsync to restore /home, running a configuration script for some things that are not in /home and reinstalling all the apps which can take a bit if you have added lots of apps.
Or in about an hour I have a new clean install without all the cruft left over from previous install.

---

### Post by SeijiSensei on 2023-10-11
I use GNU ddrescue for this task. Cloned a drive just the other day. Booted just fine.
```

sudo apt update
sudo apt install gddrescue
sudo ddrescue /dev/sdc /dev/sdd
```

---

### Post by wakingsleeper on 2023-10-12
I tried the GPT-FIX, GDISK -l looked fine (i didn't copy the output but it was GPT:present MBR:protective). Gave up on fixing it and cloned via Clonezilla, same issue no boot. 
 
I put the SSD in another Computer and it booted past bios, so it is an issue with my BIOS/Hardware, I am running this on a Proliant ML10 and some googling shows other have issues booting from SSD as well. There may be a fix, something about a SPP update ill have to figure that. 

Thank you all for the suggestions and help.

---

