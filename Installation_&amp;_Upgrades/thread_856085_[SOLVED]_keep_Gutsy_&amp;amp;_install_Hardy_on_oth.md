---
title: "[SOLVED] keep Gutsy &amp;amp; install Hardy on other drive; Will Grub get confused?"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2008-07-11
Hi!
I've asked related questions and waited some time, since I want my first  re-install of Ubuntu Studio to go smoothly hopefully...
I want to keep Gutsy for a while which is on my huge IDE drive that has a /boot /swap partition, data and a Suse variant as well.  I have 11 Gigs left on a SCSI drive which is shared with XP.  I also have another blank SCSI drive with almost 10 Gigs which I will put /home.   Thanks to my bios settings, the IDE drive was seen as primary or Sda during Gutsy manual install and it planted the MBR on that drive and I put grub in the designated /boot partition, flagged it bootable and all my OS can load nicely.

  But now I read that having gutsy and hardy on 2 drives can have the same IUD # or something and grub can get confused and worse try to run the new kernel with older version...?! 
Should I worry, will having grub on the SDa IDE drive but Hardy on Sdb and Sdc drives create any problems?  I have to back up windows again, that's for sure!  I keep reading info but my scenario is so particular I can't figure out for sure what will work... Have to say, still greatly enjoying and learning with linux! 


:confused:        :lolflag:

---

### Post by logos34 on 2008-07-12
No, the UUIDs are precisely what prevent system confusion.

When you install Hardy on the other drives, it should detect gutsy and windows--it would probably be best to let it overwrite the existing grub with a new one, so you will have a selection of the other OSs when you reboot to the grub menu.

Either that or copy the hardy kernel images to the /boot and add entries to the current menu.lst. in which case you want to to be sure during installation to write grub to the hardy root partition ('/dev/sdxy') rather than the default

---

### Post by streamsanddragonflies on 2008-07-12
Thanks logos34, I reread the thread and the person had same uuid for his 1st and 2cnd partitions on hda and hdb, but that wasn't a problem anyways.  Actually he found out later that he inadvertedly switched the 2 drives boot order in the bios e.c.t...so   I just got confused for nothing! Things should go smooth esp. with a separate /boot partition.  If ever an error occurs with the new grub install, is it recovery disk and then use menu.lst. backup? 

In passing, any experience with a LVM setup?  It could help my /home and /usr by enabling them to span 2 disks if needed (since those drives are small) but it supposedly can get tricky when upgrading...

---

### Post by logos34 on 2008-07-12
> **streamsanddragonflies said:**
> f ever an error occurs with the new grub install, is it recovery disk and then use menu.lst. backup?

To reinstall, use [this guide]("http://ubuntuforums.org/showthread.php?t=224351").

If you need to edit menu.lst from the live cd, just click on root volume in nautilus side pane to mount, then

gksudo gedit /media/disk/boot/grub/menu.lst

---

