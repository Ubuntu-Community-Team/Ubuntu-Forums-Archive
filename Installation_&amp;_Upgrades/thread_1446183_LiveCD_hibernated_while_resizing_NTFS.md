---
title: "LiveCD hibernated while resizing NTFS"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by SwimDude0614 on 2010-04-03
Um... crap.
I was installing Ubuntu 9.10 side-by-side on a computer that had Windows XP Pro already on it. I told gparted to start shrinking the NTFS paritition, and about 5 minutes before the read-only test was finished, I shut the lid. Whoops... Forgot to change the power options.
Please, don't ask if I have backups. Wouldn't be here if I did.

I tell GParted to do a check disk, and gives me the following:

> 
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name     :/dev/sda1
NTFS volume version: 3.1
Cluster size    :4096 bytes
Current volume size: 108219970048 bytes (108220 MB)
Current device size: 108219966704 bytes (108220 MB)
Checking filesystem consistency...
Accounting clusters...
Cluster accounting failed at 65734 (0x100c6): extra cluster in $Bitmap


It then gives the same error for 65735-65743, and finishes with:

> 
Filesystem check failed! Totally 145771 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!


Windows of course won't boot, and I won't have access to a Windows XP install disk until Monday night, and there is no floppy drive on the laptop.

I appreciate any help you can give me.

---

### Post by SwimDude0614 on 2010-04-03
Oh yea, GParted is showing that it finished resizing the partition (which is odd since I only ever saw it go through the read-only test). I'm assuming though that I should not start creating the new ext4 and swap partitions, overwriting the old data, just yet?

---

### Post by Arand on 2010-04-03
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) has windows recovery disks available for download, use them to run checkdisk on the drive, hopefully this might help.

On another note, consider filing a bug requesting that gparted should block any powersaving features whilst operating.

- Arand

---

### Post by SwimDude0614 on 2010-04-03
well i've got the torrent going for the windows 7 32-bit disk, but no one is sending it right now.

---

### Post by SwimDude0614 on 2010-04-03
Got the windows 7 disk downloaded, burned, and loaded. As I feared, it did not recognize any OSes installed though. Perhaps that's because the disk was for 7 and the OS was XP, or perhaps the partition is just that screwed up? In any case, I'm burning a Win XP disk now that I finally got ahold of. I'll update when I have news from that.

-Update-
BSOD:
> 
A problem has been detected and Windows has been shut down to prevent damage to your computer.

blah blah blah... (I swear that's exactly what it says)

Technical information:

*** STOP: 0x0000007E (0xC0000005, 0xF748E0BF, 0xF78DA208, 0xF78D9F08 )

***       pci.sys - Address F748E0BF base at F7487000, DateStamp 3b7d855c


Possibly relevant info: The current install on the computer I *believe* has service pack 3. The disk I'm using is SP1.
The hardware is HP Elitebook 8510w:
CPU: T9600
Memory: 1 x 4 GB DDR2 800
HDD: 160 GB Toshiba 7200 SATA
Graphics: NVidia Quadro 770m

Any ideas are GREATLY appreciated.

-Update 2-
Just tried setting the HDD to IDE rather than SATA, still same problem.

---

### Post by Arand on 2010-04-03
From the recovery disk command prompt, I would try to run something like ```
chkdsk /RX c:
```- Arand

---

### Post by SwimDude0614 on 2010-04-03
Got to the command prompt. It started running chkdsk and theeenn....

683 large file records processed.
Errors found. CHKDSK cannot continue in read-only mode.
Failed to transfer logged messages to the event log with status 50.




So, any ideas how to get it out of read only mode?

Ideas greatly appreciated! Thanks all.

---

### Post by Arand on 2010-04-03
If you go through the menus choosing repair, you should get to a meny which offers a command prompt that allows these commands.

There should be plenty of guides on how to get there out there, even in MS:s sparse documentation.

Also note that the flags /RX should be CAPITAL, I was wrong in my first post.

These flags should take care of the read-only, /F being the basic one to force actually changing the filesystem

- Arand

---

### Post by SwimDude0614 on 2010-04-04
> **Arand said:**
> If you go through the menus choosing repair, you should get to a meny which offers a command prompt that allows these commands.

There should be plenty of guides on how to get there out there, even in MS:s sparse documentation.

Also note that the flags /RX should be CAPITAL, I was wrong in my first post.

These flags should take care of the read-only, /F being the basic one to force actually changing the filesystem

- Arand

thanks! that is working as we speak. i used only /f

At the moment, its sitting (and has been sitting for 10 minutes) at "Index verification completed."

Hopefully it gets past this stage someday... I'm off to go Google that phrase and see if anyone else is experiencing hang-ups at this point

---

