---
title: "After Lucid Install, windows XP reboots"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lucky.developer on 2010-04-11
Hi,

After I installed Lucid Lynx beta 1, everything was perfect. But when I select windows XP from grub menu, the windows XP screen comes up and then the machine starts rebooting.

Here is my fdisk -l output

```
Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        6374    10241406+   f  W95 Ext'd (LBA)
/dev/sda3            6375        9536    25390080   83  Linux
/dev/sda4            9536        9730     1565696   82  Linux swap / Solaris
/dev/sda5            5100        6374    10241406    7  HPFS/NTFS

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders
Units = cylinders of 320 * 512 = 163840 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48948     7831512    b  W95 FAT32

```

Please help, I need to boot into windows as well.. for my job

---

### Post by wilee-nilee on 2010-04-11
Have you run sudo update-grub in Lucid?
Also did you resize XP for this install if so how? and did you run XP after resizing before installing Lucid?

I just noticed that sdb has a boot flag, run this bootscript and post it.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I would run this boot script before doing anything being that the boot is on 2 partitions.

---

### Post by lucky.developer on 2010-04-11
> **wilee-nilee said:**
> Have you run sudo update-grub in Lucid?
Also did you resize XP for this install if so how? and did you run XP after resizing before installing Lucid?

I just noticed that sdb has a boot flag, run this bootscript and post it.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I didnt resize the windows XP partition. XP was initially there in a primary partition. There was addition extended to be used with windows xp

I had around 27 GB of unallocated space in my disk before I installed Lucid Lynx. So i created 26GB root mount partition and kept the remaining for SWAP. Then i installed the lucid lynx in that 27GB space

No, I didnt run update-grub in Lucid after the install. Should i do it ?


I have attached the results of the script you told me to run. It is in RESULTS.txt

---

### Post by k3lt01 on 2010-04-11
Have you used the "Search" function of the forum to find if anyone else has posted the exact same, or even a similar, thing in the Lucid Lynx forum?

---

### Post by wilee-nilee on 2010-04-11
It looks like you have a fixable situation everything is there and your description of the install makes sense, and should have left XP intact. This is a little beyond my help with the sda and sdb, but that boot script will be what gets you help. There are a handful of regulars on here who are very good at getting this stuff worked out.

---

### Post by lucky.developer on 2010-04-11
where else should i ask about this problem.. i need to boot into windows xp. Where else will i get help on this ??

---

### Post by k3lt01 on 2010-04-11
> **lucky.developer said:**
> where else should i ask about this problem.. i need to boot into windows xp. Where else will i get help on this ??Don't go starting a new thread to ask the same question. Instead go and take a look at the [Lucid Lynx forum]("http://ubuntuforums.org/forumdisplay.php?f=377") and see if anyone there has had a similar issue.

---

### Post by wilee-nilee on 2010-04-11
In my experience this forum will get the quickest results. That doesn't mean don't look around. It has only been a 1/2 hour since you posted all the information needed to help you, you have posted, if it was me I would wait for somebody who knows the definitive answer in order to not mess it up. Just chill if you can.

---

### Post by k3lt01 on 2010-04-11
> **wilee-nilee said:**
>  if it was me I would wait for somebody who knows the definitive answer in order to not mess it up. Just chill if you can.The definitive answer is to go to the Lucid Lynx forum, it was created for people using Lucid Lynx so that is where this question should have been put in the 1st place.

Can a mod please move this to the appropriate place before mr developer creates a duplicate thread on the exact same issue.

---

### Post by lisati on 2010-04-11
> **k3lt01 said:**
> Can a mod please move this to the appropriate place before mr developer creates a duplicate thread on the exact same issue.

Done, on the basis of a possibiliy, no matter how unlikely, that there might be some kind of connection between the install of Lucid.

I'd spotted the thread earlier. I had something similar happen to me once, probably unrelated. Long story short: I installed XP SP3, rebooted, tried to install Ubuntu as dual boot and something went wrong. Went to restart XP, but XP wouldn't start properly & ended up in a reboot loop. Turned out that the machine needed a patch for SP3 to work properly.

---

### Post by wilee-nilee on 2010-04-11
> **lisati said:**
> Done, on the basis of a possibiliy, no matter how unlikely, that there might be some kind of connection between the install of Lucid.

I'd spotted the thread earlier. I had something similar happen to me once, probably unrelated. Long story short: I installed XP SP3, rebooted, tried to install Ubuntu as dual boot and something went wrong. Went to restart XP, but XP wouldn't start properly & ended up in a reboot loop. Turned out that the machine needed a patch for SP3 to work properly.

The boot script shows the XP boot on sdb and grub is on sda if I read it correctly, I think this is a easy fix I just don't have a definitive answer. The good thing is, OP is if we post we bump you onto the main postings.

---

### Post by k3lt01 on 2010-04-11
Can you boot into Windows Safe Mode? If you can have you tried regular Windows fixes like scandisk? defragment?

---

### Post by wilee-nilee on 2010-04-11
Bump

---

### Post by nanog on 2010-04-11
i would use the windows recovery console to run chkdsk. you could also use gparted or palimpset to check your disk in ubuntu. if your mbr or partition table on sdb is corrupt i strongly recommend  bootit ng -- a brilliant trialware application for fixing  mbr or partition tables. the open source alternative is testdisk but its not easy to use. if the disk is not the problem then you should try repairing in recovery console or with a system disk. 

also, if you want to access your files you can just mount the drive in ubuntu (but i'm assuming you know that).

---

### Post by psyke83 on 2010-04-11
Some advice:

[LIST=1]
[*]Boot into the Ubuntu installation.
[*] Update all packages (may be helpful if any newer grub packages contain fixes to your particular issue).
[*] Mount your Windows partition and do a quick check to ensure that the files are intact (i.e., check if you can at least see the "Documents and Settings", "Program Files" and "WINDOWS" folders).
[*] Reboot the machine, highlight the Windows XP entry in GRUB, and as soon as you press the return key, immediately and repeatedly press the F8 key on your keyboard - this will bring up the Windows Advanced Options Menu.
[*] Choose "Safe Mode" and pay attention to any errors on screen during the verbose boot process.
[*] (Assuming that you can successfully enter Safe Mode) Run a disk check: open a Command Prompt and type "chkdsk C: /F", and confirm the prompts.
[*] Reboot, choose Windows in the GRUB menu and allow the disk check to run without interruption.
[*] When the machine reboots, choose Windows in the GRUB menu and attempt a normal boot.
[/LIST]

---

