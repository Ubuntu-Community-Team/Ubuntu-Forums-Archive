---
title: "Problem with dual boot Ubuntu 10.10 and Win 7 x64"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by billlagr on 2010-10-25
Hi All
I attempted to install Ubuntu 10.10 along side a pre-existing Win 7 x64 installation, I resized the Win 7 partition and created a new one for Ubuntu, no problems there.
The installation itself went fine, however, it seems that Win 7 hoses the boot record.
Immediately after the install, on the first reboot, the usual GRUB menu appears with the options to boot to Ubuntu, or Win7 etc. If I boot to Ubuntu, then restart, it all boots normally again (GRUB menu). As long as I boot to Ubuntu, all is fine. However if I boot to Win 7, then restart, I get an error - I can't remember exactly what sorry i misplaced my bit of paper - but something about 'extent offsets'. If I use FixMBR in Windows, I then get the 'Missing Bootmgr.exe' error.
For now I have had to remove Ubuntu and fix the Win installation with the Win 7 recovery disc.
Anyone have any ideas?
Thanks
 
(Laptop - Dell Studio 1558, 4Gb RAM, 640Gb HDD)

---

### Post by danieln on 2010-11-12
i am facing the same problem here.

it just seems like ubuntu 10.10 does not work along with win 7

i have win 7, and after installing ubuntu 10.10 and writing the grub in /dev/sda, i am not able to boot to win 7 anymore!

i tried to reinstall win 7 all over to get win 7 up, then reinstall gru as on this guide -> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Then again, win 7 is gone!

anyone manage to get ubuntu 10.10 and win 7 64bit working together? really need some help here as this did not happen in the earlier versions

---

### Post by Rubi1200 on 2010-11-12
Firstly, hi and welcome to the forums :)

There are problems that can occur in these types of situations, especially if the computer in question has a recovery partition or Dell DataSafe partition etc.

I suggest posting either screenshots of your current setups (from within Windows) or if there is an Ubuntu install you can get into, running the following command and posting the results:

```
sudo fdisk -l
```(lowercase L not 1).

The terminal is accessed via Applications > Accessories.

Also, it is important that you run chkdsk after resizing Windows partitions, make sure also there are no more than 4 primary partitions, and, if possible, run the boot info script linked at the bottom of my post and post the results back here (this can be done either from a LiveCD or from within an Ubuntu install).

Feel free to ask any questions you want and also do an advanced search on the forums (there are other users who have experienced similar problems; there are also solutions).

---

