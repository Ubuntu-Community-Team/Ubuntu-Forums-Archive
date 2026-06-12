---
title: "Ubuntu and Win7 paralel install, problem: windows don't see entire HDD"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by antonic on 2010-05-24
hi. 

I have installed win7 and Ubuntu on acer emachines E430. Had some problems with boot but have fixed those with help from here. 
The problem I didn't see is that when I am in Windows file manager only show half of hdd. I can see the entire one in ubuntu.  I dont even see Ubuntu through win. But through Ubuntu I can see win folder. (why this doesn't surprise me?)

Can this be fixed at all?
Thx

---

### Post by darkod on 2010-05-24
There is nothing to fix. Windows can't see linux partitions, not by default. There are some ways to make it see linux partitions but I'm not sure how safe they are. You are probably risking windows to break your ubuntu.

Is there any particular reason you want to see the ubuntu partition from windows?

If you need to share files you would usually create a data partition formatted as ntfs and both OSs can see it. Also you can use usb stick or usb hdd for moving files between them if needed sometimes.

Besides, ubuntu can read ntfs and can copy any file from the windows partition that you might need in ubuntu too.

---

### Post by julio_cortez on 2010-05-24
> **darkod said:**
> If you need to share files you would usually create a data partition formatted as ntfs and both OSs can see it. Also you can use usb stick or usb hdd for moving files between them if needed sometimes.
Exactly. Ubuntu can read/write NTFS partitions (you can also automount them by editing the **/etc/fstab** file with kate for example) but Windows as far as I know isn't even aware that ext4 partitions can be read.
And this is a good thing in my opinion.

If you want to share data between the two OSs (maybe you want to download things with Ubuntu and then use them in Windows) the best solution is indeed to create a NTFS partition and automount it in Ubuntu by adding its entry in the **/etc/fstab** file.

---

### Post by antonic on 2010-05-24
Yup this is the reason. Thanks for help guys.

---

### Post by dino99 on 2010-05-24
mountmanager is the easy way

---

### Post by ToFue on 2010-05-24
> **antonic said:**
> hi. 

I have installed win7 and Ubuntu on acer emachines E430. Had some problems with boot but have fixed those with help from here. 
The problem I didn't see is that when I am in Windows file manager only show half of hdd. I can see the entire one in ubuntu.  I dont even see Ubuntu through win. But through Ubuntu I can see win folder. (why this doesn't surprise me?)

Can this be fixed at all?
Thx

you can install an ext2/ext3 reader on windows.. check out [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

or search for ext2.dll .. some have reported read only for ext3 fs, but should give you some insight..

also check out [http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)  for a general understanding.

hope this helps!

---

