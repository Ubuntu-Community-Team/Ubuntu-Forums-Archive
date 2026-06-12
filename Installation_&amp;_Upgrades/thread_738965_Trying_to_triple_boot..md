---
title: "Trying to triple boot."
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by Mortifix on 2008-03-29
I have 2 harddrives on my computer.

HDD 1: Windows XP Pro and Ubuntu
hDD 2: Windows Vista

I am trying to configure GRUB so that I can select from all three OS's with having to load up Vista's boot loader. I have been reading around and I keep seeing mixed answers that this is possible or not. If it is possible, getting the help to do this would be greatly appreciated. Thanks.

---

### Post by el_ricardo on 2008-03-29
take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=54149")

post #4 explains one way of reconfiguring GRUB that's worked for me in the past

---

### Post by Pumalite on 2008-03-29
Who owns the boot loader at the moment? How are you booting your computer? In what order did you install the OS's?Did you disconnect a drive at any time to install a different OS?
From Ubuntu, post
sudo fdisk -lu

---

### Post by Pumalite on 2008-03-29
[http://users.bigpond.net.au/hermanzone/p15.htm#Ope%20rating_System_Entries_for_Multiple_Booting_More_Li%20nux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Ope%20rating_System_Entries_for_Multiple_Booting_More_Li%20nux_Systems)

---

### Post by Mortifix on 2008-03-29
I didn't disconnect any drives, I installed Ubuntu, Vista, then XP. Not sure what you mean by the other two questions.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43524352

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   536024789   268012363+   7  HPFS/NTFS
/dev/sda2       536024790   625137344    44556277+   f  W95 Ext'd (LBA)
/dev/sda5       536024853   552411089     8193118+  83  Linux
/dev/sda6       552411153   556507664     2048256   82  Linux swap / Solaris
/dev/sda7       556507728   579046859    11269566    7  HPFS/NTFS
/dev/sda8       579046923   625137344    23045211    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0ed80de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156312449    78156193+   7  HPFS/NTFS

---

### Post by Pumalite on 2008-03-29
The order of installation should be 1st Vista in sda1, next XP; Ubuntu last in order to have a bootable triple boot. Consult that 2nd link I gave you from Hermanzone.

---

### Post by Mortifix on 2008-03-29
So will I have to reinstall everything? I actually just installed Vista and XP tonight in that order. should I just reinstall Ubuntu too?

---

### Post by Pumalite on 2008-03-29
Read the link I gave you and follow it to the letter.

---

### Post by Mortifix on 2008-03-29
Well is there a way that I can just get Vista working again. Its like 7 in the morning and I need to have Vista back for when people get on it.

---

### Post by Pumalite on 2008-03-29
Get Super Gub and restore it's MBR: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by Mortifix on 2008-03-29
Ok no matter what I do, I can't get Vista to load. It always loads XP. If I do that map thing it doesn't load at all. What am I doing wrong? I have tried about every option in Super Grub.

---

### Post by Pumalite on 2008-03-29
Do you have an Installation Disk for Vista?.There must be a 'Recovery Option' there.

---

### Post by Mortifix on 2008-03-29
There wasn't any recovery tool. I did have this program called Vista Boot Manager, but I don't think I could screwed anything up with that.

---

### Post by Pumalite on 2008-03-29
Stick to Super Grub. Read carefully the instructions. Super Grub boots anything bootable. So, unless you screwed your Vista, Super Grub should be able to boot it.

---

### Post by Mortifix on 2008-03-29
Well I changed up something and I got 2 windows xp professional OS's too appear, but the second (my vista I think) says File Missing Windows Root>\system32\hal.dll. I never deleted any file though.

Ok forget that....that is something else. I have tried every option in Super Grub and it still brings me back to the XP and not Vista. Its driving me crazy. I went to boot partition and this option should boot any OS that is on that current partition correct?



Ok nevermind, I got did something and I can get onto Vista so im gonna leave it at that. :) Now I can finally go to bed. Thanks so much for helping me and putting up with me lol.

---

