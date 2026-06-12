---
title: "Grub fails to load:stops at grup&gt;"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by calibre97 on 2008-06-12
(that should read grub> in the subject line of course. If it really was "grup" then I'd be in serious trouble)

I have an HP dv5035nr with XP MCE SP2, Kubuntu 8.04 and System Commander 9. XP is on the only primary partition, with everything else in an extended partition (data partition, TrueImage securezone, Kubuntu partition, swap partition).
Everything was working fine (famous last words!) with System Commander loading first, then when I chose Kubuntu, grub would load and I could get to Kubuntu. Because TrueImage was constantly hanging and taking forever, I decided to remove it and load Norton Ghost. I deleted the securezone and turned it into a normal NTFS partition.

When I boot, I still get System Commander first. When I select Windows, all is fine, as it loads. When I select Kubuntu, I see a brief flash of grub trying to load, then it halts with a note and a grub prompt. I loaded the Kubuntu Live CD and everything's there as it should be. Partitions are still the same, with Kubuntu on /dev/hda7. My menu.lst has the various kernel options at (hd0,7) which is the same as it was.

When I loaded gpartd, I saw that the Windows partition was flagged as hidden and the extended partition and Kubuntu partitions were both flagged boot. I removed the hidden flag on the Windows partition as it was visible before, and I removed the boot flag on the extended partition.

I've also tried booting from a SuperGrub disk, which did load my menu.lst file and displayed everything as expected, but each kernel item (there are three due to updates) resulted in a "cannot mount partition" error.

Is there something I can type at the grub> prompt, or should I try different numbers in menu.lst (such as moving it up to 8 or down to 6)? I sort of know what I'm doing and I've tried everything I can think of (short of the aforementioned renumbering, of course, which I'll try since I can live CD boot and see files) and I just can't get the partition to boot.

---

### Post by calibre97 on 2008-06-12
OK, I chickened out and just did a new Kubuntu install into the converted securezone partition. That loaded me up with a new menu.lst that included the points I wanted. Problem now is it fubar'd my Windows choice. Luckily when I booted into my previous Kubuntu, I ran grub-install /dev/hda7 so that once I get an MBR back so I can get into Windows, I will then be able to restore System Commander from within Windows and then everything should be everything.

---

### Post by calibre97 on 2008-06-12
OK, in case anyone stumbles upon this...
My partitions did get screwed up..specifically now it appears my XP partition loads hidden when I try to boot into Kubuntu so that throws off my partition numbering. In menu.lst, I used to be all about the hda,7. Well, now it's hda,6. Go figure.

So I fired up the live CD and went to my Kubuntu partition and edited menu.lst (after making a backup!!!!) to read hda,6.

Everytime I mess around with things, I wind up having to do this dance to get everything bootable again:
1. Get GRUB on the MBR so both Kubuntu and XP are bootable.
2. Boot into Kubuntu and run grub-install /dev/hdaN where N is the appropriate number.
3. Boot into XP from GRUB.
4. Reenable System Commander.
5. Boot into System Commander and select whatever.
=sometimes in this sequence I have to fix the MBR so it just boots Windows. Then I start at #4.

Bottom line folks: you wanna play with Windows and Kubuntu? Have a GAWLDANGED LIVE CD HANDY!!!! And a SuperGrub CD with GpartD so you can partition and fix your MBR and fix your GRUB or whatever.

Now, just when I have XP and Kubuntu running, I'm going to try Fedora Core 9 in that spare partition. Ain't this fun???

---

