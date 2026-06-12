---
title: "Hard Disk partition question"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by keithk50 on 2007-03-14
Using Gparted within the Ubuntu live CD have managed to take some HD free space from the Windows NTFS partition as I wanted to add it to Linux. (Originally I let the Live CD install Ubuntu onto my laptop in automatic mode).  I now have an unallocated space of 3.42GB.   The GParted details look like this:


Partition                Filesystem            Size            Used         Unused           Flags
/dev/hda1               fat32                   4.01GB          .........           .........          Hidden                 
/devhda2                nfts                     13.32GB         10.64          2.62
Unallocated            Unallocated          3.42GB
/dev/hda3               Ext3                      6.87GB           3.73GB    3.14GB
/dev/hda4               Extended           337.31MB
/dev/hda5               Linux Swap         337.27MB

Being a novice with Ubuntu (and HDs) I previously asked how to add this 3.42GB to my Linux (hda3).   The answer (obvious to me now) was to format the unallocated space to ext3 and add it to hda3.   Using the Ubuntu live CD (which I am doing now) I opened GParted and clicked on the unallocated line within the box but when I then click partition in the top menu line all options apart from information are greyed out!. Would love some assistance/guidance as I really would like to add the spare to my Ubuntu hda3.   On a final point am I correct in saying that the fat32 (hda1) should be left alone?.      Any help appreciated.

---

### Post by buuntuu! on 2007-03-15
simply right-click partition hda3, select "grow/resize" and grow it over the unallocated space!
why should you have to leave alone your fat-partition? (unless there is an OS installed there...)

---

### Post by keithk50 on 2007-03-15
Thanks so much for the reply.   Was beginning to lose heart.    When you say "grow it over the uallocated space" do you mean just add it to the 'New Size (MiB) in the Resize/Move window?.
Sorry for being such a NooB but I never even worked with HD partitions with XP or Mac OSX!
No I dont think there is an OS on the fat32 partition but the word 'hidden' frightened me off a bit.   Could they be files required by XP (ie; the part missing from my original 30GB)   Thought, probably wrongly, that was why the HD is only showing up as 27GB!.    Many thanks again.

---

### Post by buuntuu! on 2007-03-15
when selecting "resize/move" you should see the unallocated space to the left of hda3, just grab hda3s left border and drag. i did that quite some time ago, so don't panic if it doesn't work right away... you might want to try the [gparted]("http://gparted.sourceforge.net/") live cd, it is only a small download. ubuntus version is a bit dated, being up to date always helps.

don't be afraid about your hiddne partition, if your pc came preinstalled with window$ you probably didn't receive a ninstall-cd right? the hidden partition should be where it is stored (so the company earned a few extra bucks on your expense). i have a thinkpad and after burning all my recovery cds for xp i deleted the hidden partition, no problem there...

---

