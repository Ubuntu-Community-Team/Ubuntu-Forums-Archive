---
title: "Update from Wubi install to dual boot"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by blindape on 2009-12-06
Hi,

I've had Ubuntu 8.10 installed with wubi on my Acer Aspire laptop since February.  After several months of putting Ubuntu through it's paces and the fact that I now use Ubuntu over windows 95% I am convinced that I need to move to a dual boot system as it seems more robust (plus the fact that I can't update the wubi to 9.10).  However when I booted into windows to uninstall wubi, it couldn't read the partition that wubi was installed on.  When trying to access the D: drive the computer says that "the file or directory is corrupted and unreadable."  I tried running chkdsk on the D: drive but it found no problems.  so I tried accessing d: drive and got the same problem.

Next I rebooted the computer and selected to boot into Ubuntu which worked fine!  In fact from ubuntu I could read "all" of D drive without any problems.  Also when I booted from the live CD for 9.10 I can also access d-drive without any problems.  but I can't access it from windows to uninstall wubi.

So here is my question:

Is there a way to 'repair' things on windows so I can read D: drive and then uninstall wubi before installing ubuntu on the entire partition.  

or

can I just re-format the entire partition without uninstalling wubi before installing ubuntu 9.10.

The reason I as this is how will windows and the boot sequence be affected if wubi isn't properly uninstalled.  I don't want to be stuck without a working operating for any length of time as I need my computer for work, however wubi has reached the end of it's limits for me and needs to be upgraded to a full install.

Regards,

John Curwood

---

### Post by lidex on 2009-12-06
You should be able to reformat. I'm not sure how wubi affects the bootsector however you can boot with your windows cd after and in repair mode run fixmbr to reset windows boot. 

Have a look here:
[http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php")

BTW windows by default doesn't recognize linux file systems.

---

### Post by blindape on 2009-12-06
Thanks for the reply, I realise that windows doesn't read the linux file system by default, but D: drive is NTFS and most of the files on their were originally written to from windows apps.  the wubi install is 1 8GB file saved onto the D-drive.  Until the time I booted into windows and tried to uninstall wubi, windows was able to read all files on there fine.

I am leaning towards your suggestion, however my computer never came with an install/recover CD, so I want to be absolutely sure before I do anything.

Regards,

John Curwod

---

### Post by wilee-nilee on 2009-12-06
When I installed Karmic on my acer aspire one it had XP on it, the recovery partition was in grub, and it was a one click to overwrite the main XP operating partition, with no change to the MBR.

---

### Post by blindape on 2010-01-20
Hi, I know this reply is a bit late, but I bit the bullet and formatted the partition containing the wubi install.  When I started the computer after this it automatically booted to windows,  and I was able to install a dual boot version of Ubuntu without any issues when it came to booting to either ubuntu or windows.

Cheers,

John

---

