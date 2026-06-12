---
title: "win7 to 10 upgrade wiped out whole Ubuntu partition?"
date: 2015-07-31
forum: Installation &amp; Upgrades
---

### Post by m3esha on 2015-07-31
Hi.

Yesterday I started Windows7 to 10 upgrade. I was kind of busy so I just left it going (stupid me). This morning I saw on the monitor:
```
error: no sush partition.
Entering rescue mode...
grub rescue> _
```
I tried reinstalling grub but failed. I've also tried using boot-repair - didn't help.

Here is URL from boot-repair: [http://paste.ubuntu.com/11972035/](http://paste.ubuntu.com/11972035/).

---

### Post by Simon_Tomoko on 2015-07-31
I suppose if this was my PC, I would grab my Linux Live CD and boot Linux and see what there is to see on the HDD. Running the "Try It" option will give you the ability to poke around and view what is readable on the HDD. 

Sorry I couldn't be more help.

---

### Post by oldfred on 2015-07-31
You need to use testdisk.

Windows is nortorious (we have seen many posts) where major updates where it rewrites partition table leaves off the ext4 partition in an extended partition. But I see it did leave your /boot, but you still have the large gap where another partition was. And grub says you boot from sda7, but do not have a sda7.

You need to make sure you restore all your current partitions, but then include another ext4. Testdisk may show many partitions that were deleted, but that is from all the changes. You need to find a set of partitions that keeps all your current ones & adds just the one missing. 

Partition should be between the start of the extended & start of sda5. But testdisk still uses the old CHS values.

```
 /dev/sdb4       267214846   488396799   110590977    5  Extended
/dev/sdb5       462526464   478148607     7811072   83  Linux


```

You also can try parted rescue. It does use sectors, but you have to put in correct value.
 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

---

### Post by NoWayWin8 on 2015-07-31
It's still there, Windows seems to have overwritten the preious EFI partition though. Check if SecureBoot is enabled in BIOS, or in Windows open an elevated command prompt or powershell and run this command:
```
Confirm-SecureBootUEFI
```
If it returns "True" then you need to disable SecureBoot or else install an Ubuntu version newer than 12.04 (which you should do anyway).

---

### Post by m3esha on 2015-07-31
Thanks a lot for answers.

Of course I did use Live USB to see what's there, the problem is there was nothing ;) (I mean there was no partition with files from my Ubuntu partition).

I will try to use testdisk. I hope I won't break my disk more...

I'll check SecureBoot in BIOS but I can't run any commands in Windows - I can't boot any system (meesage from my first post appears).

I had installed Ubuntu 14.04 and I'd probably install it again but I don't want to - then it forces me to format partition and I don't want to lose all the data I had there.

---

### Post by m3esha on 2015-07-31
Running testdisk gave me this.

---

### Post by m3esha on 2015-07-31
And using parted seems to have helped!

Awesome, thank you very much, oldfred.

Windows is back to upgrading but I hope nothing is going to happen this time (or at least nothing new...).

---

### Post by oldfred on 2015-07-31
Glad that worked. :)

I think testdisk would have worked. You needed to keep sda1 as * or flagged as bootable. And recovered one of the 5 deleted partitions. But because it uses CHS not sectors it is difficult to tell which would be the correct one to choose. It would have to be after the end of the NTFS partition and before the first other logical partition and set as logical. Cannot see enough detail in screen shot to tell, but not always easy. 
Glad parted worked.

Please change to solved so others that search forum can find an answer that works.

---

### Post by m3esha on 2015-07-31
Windows at 37% told me my PC doesn't fulfill requirements (it totally does) and tried to revert to previous version but failed. Now when I try to boot it, it tells there's an error and I should use install DVD. But when I do (using Windows 7 install disc) and try running repairing system, it tells me it's wrong version :/

Well, but that's the topic for different forum ;) Thanks again. Marking as SOLVED.

---

