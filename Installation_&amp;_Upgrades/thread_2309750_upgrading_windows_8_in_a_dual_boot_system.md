---
title: "upgrading windows 8 in a dual boot system"
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by vishal18 on 2016-01-13
I use windows 8 and ubuntu dual boot. I want to upgrade windows 8 to 10. I just wanted to know whether windows will wipeout my ubuntu partition during upgrading. I know it will replace grub and there are lot of threads to fix it. So my question is specifically about whether my ubuntu system will be untouched during windows upgrade. (My computer has 4 partitions already created by windows(C:, D:, E:, F:) and 1 more i created when installing ubuntu).

---

### Post by partagas150 on 2016-01-13
Take my word for it.... Win10 WILL wipe your entire hard drive in order to install. One good thing to do, is IF possible, make a back up of everything on Ubuntu, then proceed with 10, then, make your USB stick, and reinstall Ubuntu. ...(note, once win10 is installed, you can make that partition smaller, in order to have enough space on "C" drive to install Ubuntu.

hope this helps

---

### Post by siepo on 2016-01-13
Not my experience. The installer will ask you how much you want to keep. I chose just my personal files. The ubuntu partitions remained untouched. W10 did make a small additional partition, but it was taken out of the original w8.1 partition. Btw, since then I have reverted to w8.1, and the extra partition is gone.

This was an UEFI system. If your system was bought with w8 then it is probably UEFI too. Otherwise I would not know what to expect.

I did have some trouble with grub, but that was probably only because at the time I was sticking to numbered partitions rather than uuids. The trouble got resolved without major surgery.

My advice if you have an uefi system: of course back up everything important first because you never know. If you cannot boot ubuntu afterwards, try Boot Repair.

---

### Post by oldfred on 2016-01-13
I have one system with Windows only for TV, only because of Comcast, HBO Go & similar require the DRM and will not work with Linux. I just upgraded in place from 8.1 to Windows 10. It took forever, was not sure what was going on for quite a while. Many reboots.

System now gives me out of memory errors with only one application running, its new browser & I have 4GB of RAM. I changed some settings today, so we will see if that helps.
 Once you get past the top level screens the detail screens are not really different than what I remember from XP. Have not run any other Windows versions.

My Ubuntu install was still there and from UEFI boot menu was able to choose it to boot. Windows had set itself as first in boot order as expected, but did not cause any other issues.

If you have a BIOS install, Windows will delete Ubuntu logical partition(s) from partition table. Best to back up partition table and have an Ubuntu repair flash drive handy for parted rescue, testdisk & reinstalling grub.

---

### Post by vishal18 on 2016-01-15
guess i'll probably stick with windows 8 and not upgrade it. thanks for your advice.

---

### Post by oldfred on 2016-01-15
I increased cache size & removed a few start up apps. Did not have any issues with Windows 10 last night on too much memory use. 

But only running one app should not have issue and should not be using cache with 4GB of RAM.

---

