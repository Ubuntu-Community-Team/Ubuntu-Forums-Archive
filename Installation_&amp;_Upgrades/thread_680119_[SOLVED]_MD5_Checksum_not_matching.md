---
title: "[SOLVED] MD5 Checksum not matching"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by victor9098 on 2008-01-27
Hi All,

I have been trying to download Gutsy Gibbon and have tried downloading from 2 different locations but when I copy to CD I get the following checksum error:

keith@keith-sam:/cdrom$ md5sum -c md5sum.txt | grep -v 'OK$'
./casper/filesystem.squashfs: FAILED
md5sum: WARNING: 1 of 474 computed checksums did NOT match

Can anybody suggest why I am getting this? I have brought my CD writing speeds down from x6, x4 and now x2 in the latest but same error keeps coming up.

Thank you

---

### Post by zvacet on 2008-01-27
I hope that you still have iso on your comp.Download same iso with torrent and point download to the folder where your iso is.Torrent will just chek your iso and replace bad files with good ones.After that chek [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and if it´s O.K. burn iso on CD,chek Cd integrity and after that if all goes well install.

---

### Post by victor9098 on 2008-01-27
Yes, still have the iso.

Have not used torrent before. Is it in synaptic or must I get from elsewhere?

Thank you

---

### Post by victor9098 on 2008-01-27
Here is the result of running checksum on my iso, it matches with the Ubuntu checksum.

keith@keith-sam:~$ cd /home/keith/Desktop/7.10_Gutsy_Gibbon
keith@keith-sam:~/Desktop/7.10_Gutsy_Gibbon$ md5sum ubuntu-7.10-desktop-i386.iso97e47adf45c125ecdc89f5fa418a76d9  ubuntu-7.10-desktop-i386.iso

I downloaded via the Ubuntu website, just choose a local download location

EDIT:

N, my iso does not match, I am missing a "c" at the end. So how do I use torrent to fix this? My download location was: [http://www.mirrorservice.org/sites/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso](http://www.mirrorservice.org/sites/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso)

Thank you

---

### Post by victor9098 on 2008-01-27
OK!

Found bittorrent, found a .torrent of gutsy, downloaded the .torrent file to the folder where the original iso was located. Downloaded virtually straight away except for about 500kb! That was all it took to mess up my installation.

After that ran checksum got the all clear. Burned to CD (slowest speed possible). Verified the CD integrity. Got no errors. Commenced install.

All this has been posted from my brand new gutsy gibbon install!! Thank you very much for  pointing me in the right direction.

---

