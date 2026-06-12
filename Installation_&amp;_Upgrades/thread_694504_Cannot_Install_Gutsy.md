---
title: "Cannot Install Gutsy"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by mudora on 2008-02-12
Hi,

Ok, so I have been using ubuntu for 2 months now, with dual boot (XP). After failing to boot XP one day, I decided to format and reinstall everything. So I proceeded this way: I installed XP, deleting my ubuntu partitions at the same time, I suppose ubuntu data still exists. I made only one partiton on my HDD (Sata drive) with the rest unpartitioned. 

I was now ready to install ubuntu, however, when I choose start/install from the menu (livecd), it hangs at the progress bar. I deleted quiet & splash and first I got "I/O error, dev fd0, sector 0". After reading online, I disabled my Floppy Drive (I don't have one). I tried installing again, and same thing happens, this time I get "'/sbin/modprobe' abnormal exit".

Any idea anyone? Please, I'm really fond of ubuntu and I wouldn't go back to using XP only, which I only need for certain programs/games). I miss the stability and speed of ubuntu already!

Thank you for any help!

EDIT: BTW, I am using the new cd I received from Canonical, not a downloaded version. I also tried my Feisty cd from last year and it does not work (same problem). My previous installation was 7.04, had to upgrade to 7.10 online.

---

### Post by Pumalite on 2008-02-12
I suggest you get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete everything in your harddrive. Make new large partition of your whole HH, formated ntfs. Install XP. Boot Gparted again; this time right click on XP and choose 'resize' from the menu. In the space just obtained, make the following partitions:
10 GB for '/'
1 GB for /swap
The rest for /home
Install Ubuntu; go Manual and use the partitions already created.

---

### Post by zxscooby on 2008-02-12
try downloading and burning the alternate install cd.

---

### Post by mudora on 2008-02-12
Thanks for the suggestions! I'll try Gparted. I got a slow internet connection and downloading the alternate cd will take hours! If nothing works, I'll try it though.

Thanks again. I will post an update from ubuntu hopefully soon! ;)

UPDATE: I succeeded in dual booting both OS once again! However, instead of re-formatting the whole HDD (too lazy to re-install XP software), I tried formatting the rest of the HDD (apart from XP). This time the installation worked flawlessly! :)

Thank you for all the help!

---

