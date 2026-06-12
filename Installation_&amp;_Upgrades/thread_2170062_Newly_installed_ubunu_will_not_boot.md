---
title: "Newly installed ubunu will not boot"
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by amalgamateguitar on 2013-08-24
lets see...

When I boot the system it says "device not found" with some other stuff. I can retry and get some details but while I have ubuntu running off the CD I thought I would post. I read about bootinfoscript and I downloaded it, ran it, and am posting the results here.

And the version I installed is... 12.04 LTS

It is a 64 bit system.

Thanks in advance for any help you can privide.

I installed it along side a windows 7 system running on an HP laptop. I hope to maintain the windows sytem as well.

-John

---

### Post by amalgamateguitar on 2013-08-24
OK so some details: when I try to boot the system, the following two lines appear:

ERROR: no such device 68c1a7f6-a096-47b9-a5ae-d0fd4b70a712.
grub rescue>

---

### Post by amalgamateguitar on 2013-08-24
Any thoughts about this link:?[ http://www.tavisonline.com/2011/10/fix-broken-grub/]("http://www.tavisonline.com/2011/10/fix-broken-grub/") does it apply to me? it seems close.

---

### Post by Quackers on 2013-08-24
There is no sign of an Ubuntu installation on the Results.txt but you do have grub2 installed in the MBR of the drive. I take it that Windows won't now boot?
Where did you install Ubuntu? On what partition?
As you already appear to have 4 primary partitions (assuming you are not using GUID partition table) it would be a mistake to try and create a 5th partition without deleting a primary partition first. 
The first thing I would do is to run your Windows installation or repair disc and repair the MBR of the drive by using the repair installation utility. You may need to run this just once or you may need to run it up to 3 times. Once that is done Windows should then boot.

---

### Post by amalgamateguitar on 2013-08-24
One partition is windows, One is the factory installed winsows back up. one is the windows user created back up. the other was created by ubuntu while installing.... as far as I know. who knows which partition the ubuntu installer went to, but it worked twice before it stopped working.

---

### Post by Quackers on 2013-08-24
Nevertheless it would appear that there is no Ubuntu system nor ext4 partition on your 500GB hard drive.
There are 4 partitions
1) NTFS partition with Windows boot files on it
2) NTFS partition with Windows operating system on it
3) NTFS partition with (possibly) HP Tools?
4) VFAT partition with (possibly) Windows recovery system?

EDIT it may sound a bit odd but did you have a second hard drive attached when you installed Ubuntu?

---

### Post by SweetAurora on 2013-08-24
Also, by any chance is this a WUBI install? Did you download Ubuntu and hit the Wubi install in Windows?

---

