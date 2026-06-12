---
title: "Can't resize Partition in GParted (yellow warning besides unmounted partition)"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by The Thunder Chimp on 2010-06-22
Hello,

I have a USB Multiboot created with [pendrivelinux.com](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/). I have tried to install Ubuntu 10.04 on a small laptop, but I get the problem that the installer wants to either:

1) Partition my USB key and install it there
2) Install it on my drive and destroy the Windows Partition
4) Install it on my key and destroy everything on it.
3) Manually setup the partitions

When manually setting up partitions, I cannot resize the windows partition. 
GParted can't resize that partition (there is a triangular ! yellow warning sign, similar to this thread's icon, but yellow). GParted on the USB (GParted Environment) has the same problem as GParted in Ubuntu. It seems to be locked, even though I am in root and I have every hard drive partition unmounted.

I will post screenshots of the error message in the following hour.

---

### Post by macstar on 2010-06-22
> **The Thunder Chimp said:**
> Hello,

I have a USB Multiboot created with [pendrivelinux.com]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/"). I have tried to install Ubuntu 10.04 on a small laptop, but I get the problem that the installer wants to either:

1) Partition my USB key and install it there
2) Install it on my drive and destroy the Windows Partition
4) Install it on my key and destroy everything on it.
3) Manually setup the partitions

When manually setting up partitions, I cannot resize the windows partition. 
GParted can't resize that partition (there is a triangular ! yellow warning sign, similar to this thread's icon, but yellow). GParted on the USB (GParted Environment) has the same problem as GParted in Ubuntu. It seems to be locked, even though I am in root and I have every hard drive partition unmounted.

I will post screenshots of the error message in the following hour.

i think you wont have any chance to do it with gparted. especially not, if the windows parition is in ntfs file format. 
and, booting gparted live from dvd, might let you move/mod your windows partition but i can ONLY WARN YOU: DONT DO IT. gparted might hang up and your partition is kinda lost then. i faced the same problem a few days ago.

the best and savest solution is to boot windows and resize the partitions from there.

---

### Post by darkod on 2010-06-22
Run Gparted from ubuntu cd for example, and try rught-click, Check on the partition.

On the other hand, if that's the windows system partition, without even bothering with Gparted first try to boot windows and in command prompt do:

chkdsk c: /r /f

See if any of that helped. The Check option of Gparted will probably say to run chkdsk anyway.

---

### Post by darkod on 2010-06-22
> **macstar said:**
> i think you wont have any chance to do it with gparted. especially not, if the windows parition is in ntfs file format. 


This is not true. There is some error on the partition (which might not be serious at all) and simply Gparted doesn't want to touch it. Sometimes bad sectors do this, even when windows might ignore them.

However, because windows is picky, it's better to resize using windows Disk Management in vista or 7. The tool is not present in XP so your only choice is third party windows app, or Gparted or similar. Gparted comes free.

---

### Post by darkod on 2010-06-22
PS. For the record, I have resized vista system partition with Gparted Live and after it did the check which started automatically first time I tried to boot it, it was fine.

However, usually it's better to resize with Disk Management. On the other hand, because of windows idiotic unmovable files, Disk Management might end up telling you you can shrink a whole 10-20MB when you have 100GB unused on the partition and you need to shrink more.
That was the reason I was using Gparted on vista partition.

---

### Post by The Thunder Chimp on 2010-06-22
Here are the Screenshots I promised upon first post, the last post gives you some error information. Thanks for your time man.

EDIT: How can you resize partitions in Windows on the Hard Drive if the Drive is mounted??

---

### Post by darkod on 2010-06-22
The first 4 screenshots are pointless. If you need to resize /dev/sda3 you DO NOT do it with the installer, not at the same time when installing.
You do it in advance.

Did you read any of my posts about running chkdsk from windows? Basically the same as that message on image 5 is telling you.

Windows doesn't use "mounting", not as linux. In vista and 7 it allows resizing a partition, in XP not. It will not resize it immediately anyway, if that's confusing you. It will just schedule it, ask for a restart, and do it in sort of DOS mode.

---

### Post by macstar on 2010-06-22
> **darkod said:**
> This is not true. There is some error on the partition (which might not be serious at all) and simply Gparted doesn't want to touch it. Sometimes bad sectors do this, even when windows might ignore them.

However, because windows is picky, it's better to resize using windows Disk Management in vista or 7. The tool is not present in XP so your only choice is third party windows app, or Gparted or similar. Gparted comes free.

then gpart has a mal-function or behaviour after detecting failures on partitions is bad implemented.

why cant gparted just check the partition first and if there is a problem on the partition - send a warning and ask the user to cancel?

as i can confirm gparted doesnt check for failures automatically and tries to resize ntfs partition. then it will hang up and you wont have access to your ntfs partition anymore. not fixable with gparted. 
all you can do is boot in windows and try it there.

i would not trust gparted on ntfs partitions. i thought it was as solid as partition-magic but i was wrong.

---

### Post by darkod on 2010-06-22
> **macstar said:**
> then gpart has a mal-function or behaviour after detecting failures on partitions is bad implemented.

why cant gparted just check the partition first and if there is a problem on the partition - send a warning and ask the user to cancel?

as i can confirm gparted doesnt check for failures automatically and tries to resize ntfs partition. then it will hang up and you wont have access to your ntfs partition anymore. not fixable with gparted. 
all you can do is boot in windows and try it there.

i would not trust gparted on ntfs partitions. i thought it was as solid as partition-magic but i was wrong.

What are you talking about? I don't know what happened to you, but it doesn't help to lie to all people who will read this for help.
Read carefully again the first post of the OP, which you obviously didn't, where he/she clearly says that there is a triangle warning mark and Gparted doesn't even want to START resizing the partition. According to you his computer would have been messed up already because a resize was tried. But Gparted refused it because of the detected errors.

Yes, unfortunately things can get messed up when using any partitioning tool, not just Gparted. But saying that Gparted can't resize ntfs partitions is a flat out lie.

---

### Post by macstar on 2010-06-22
> **darkod said:**
> What are you talking about? I don't know what happened to you, 


this:
[http://ubuntuforums.org/showthread.php?t=1514085](http://ubuntuforums.org/showthread.php?t=1514085)

i know it might not happen to all people - but as i experienced that problem i'd say to the op: better save than sorry! 

and why should someone mess arround with gparted and risk to lose ntfs partition, when there is a possibility to use windows partition tool? ;)

---

### Post by oldfred on 2010-06-22
If you have a NTFS partition you need to have windows tools to repair it. It would be better to stop using NTFS if you do not have windows anymore to repair it.Testdisk also recovers partitions including NTFS and often can repair them even when chkdsk does not work.

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by efflandt on 2010-06-22
I have never had any problems resizing WinXP ntfs partitions with gparted.  However, you should disable virtual memory first in WinXP first and reboot for that to take effect if you want the best chance at shrinking a partition to minimize immovable files.  The first time I resized my 200 GB partition in 2004 I had not done that and could only free up about 24 GB.  But more recently when I first installed Ubuntu 9.04 (a week before 9.10 was released) by disabling WinXP virtual memory I could have shrunk the XP ntfs partition to the size of actual use, but I just freed up 66 GB for a couple of Linux versions and swap.  After resizing and rebooting Windows (which will check the disk) you can re-enable virtual RAM.  I have also used gparted since then to resize WinXP ntfs partitions on several laptops without any issues.

But for Vista or Win7 it is recommended that you use Windows own admin tools to shrink partitions.  Then you can use gparted to create you Linux partitions.  I did that on a Win7 laptop I had temporarily while setting it up for someone (I put grub2 on the primary Linux partition).  Although, after removing Ubuntu 9.10 and setting the Win7 partition as boot, I had to used the Win7 disk a couple of times to restore boot because it could not find bootldr.  After restoring Win7 boot I resized the partition from Win7 to fill the disk.

---

### Post by wilee-nilee on 2010-06-22
> **efflandt said:**
> I have never had any problems resizing WinXP ntfs partitions with gparted.  However, you should disable virtual memory first in WinXP first and reboot for that to take effect if you want the best chance at shrinking a partition to minimize immovable files.  The first time I resized my 200 GB partition in 2004 I had not done that and could only free up about 24 GB.  But more recently when I first installed Ubuntu 9.04 (a week before 9.10 was released) by disabling WinXP virtual memory I could have shrunk the XP ntfs partition to the size of actual use, but I just freed up 66 GB for a couple of Linux versions and swap.  After resizing and rebooting Windows (which will check the disk) you can re-enable virtual RAM.  I have also used gparted since then to resize WinXP ntfs partitions on several laptops without any issues.

But for Vista or Win7 it is recommended that you use Windows own admin tools to shrink partitions.  Then you can use gparted to create you Linux partitions.  I did that on a Win7 laptop I had temporarily while setting it up for someone (I put grub2 on the primary Linux partition).  Although, after removing Ubuntu 9.10 and setting the Win7 partition as boot, I had to used the Win7 disk a couple of times to restore boot because it could not find bootldr.  After restoring Win7 boot I resized the partition from Win7 to fill the disk.

Thanks for sharing but your preaching to the choir.;)

---

### Post by The Thunder Chimp on 2010-06-22
Wow, thanks a lot guys, but my simple solution was to use the partitioning tools that come with Windows 7.

I was wondering too, when I use the shutdown button, Ubuntu logs off, then it almost shuts down, the screen turns blank (like if it was down), but the hard-drive still spins forever, and the green light is still there. Running ```
sudo shutdown -h now
``` works perfectly fine. Is there a way to configure the shutdown button so it can run the working command? Thanks again for your help!

---

