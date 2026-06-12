---
title: "dual boot ubuntu reinstall"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by jenningsdl on 2009-11-18
Hi 
I have had ubuntu installed (dual boot with vista) for about a year - now it died and wont recover. I want to reinstall Ubuntu, but not disturb the windows partition.  not sure exactly where to start. Downloading the new version fine, but with the CD, what is next step?

Thanks

Don

---

### Post by shababhsiddique on 2009-11-18
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)    read this. And if you are afraid of loosing XP try Hiren...(it can backup entire partotion).

---

### Post by darkod on 2009-11-18
If you are happy with the partitioning you had with the old version, even better.
Boot with the CD, select Install Ubuntu, then I think it's step 4 when it asks where to install select Manual Partitioning.
You will be able to see your disk partitions and all your old partitions should be there. Select them one by one, where it says "do not use..." select the filesystem (ext4 or ext3 if you prefer), check the Format box and select the mount point (probably same mount points you had before).
If you want to keep your /home and if you had it as separate partition, you leave Format box empty and it should pick it up. If the older version was too old, not sure how that would work out though.

If you want to change partitions then you need the Manual method again, only you will delete the old ones and create new ones as per your liking.

That should be it. :)

PS. My post is if you want to install the newest version, as you said, not if you just want to restore grub.

---

### Post by shababhsiddique on 2009-11-18
> **darkod said:**
> If you are happy with the partitioning you had with the old version, even better.
Boot with the CD, select Install Ubuntu, then I think it's step 4 when it asks where to install select Manual Partitioning.
You will be able to see your disk partitions and all your old partitions should be there. Select them one by one, where it says "do not use..." select the filesystem (ext4 or ext3 if you prefer), check the Format box and select the mount point (probably same mount points you had before).
If you want to keep your /home and if you had it as separate partition, you leave Format box empty and it should pick it up. If the older version was too old, not sure how that would work out though.

If you want to change partitions then you need the Manual method again, only you will delete the old ones and create new ones as per your liking.

That should be it. :)

PS. My post is if you want to install the newest version, as you said, not if you just want to restore grub.

You shall find it step by step here
 [http://ubuntu50mg.blogspot.com/2009/11/installing-ubuntu-besides-windows-dual.html](http://ubuntu50mg.blogspot.com/2009/11/installing-ubuntu-besides-windows-dual.html)

---

### Post by jenningsdl on 2009-11-19
I should have asked this the first time, but I have a 64 bit desktop.  Do I use the server edition of ubuntu?  thanks

---

### Post by Ginsu543 on 2009-11-19
You should use the 64-bit version of the Desktop edition, not the Server. At the Ubuntu download page, if you click on the "**[Alternative download options, including Ubuntu installer for Windows]("http://www.ubuntu.com/getubuntu/download#")**" link, it will give you the option to download the 64-bit version. I recommend, however, you use Bit Torrent to download the LiveCD as it is much faster (just click on this "[ubuntu-9.10-desktop-amd64.iso.torrent]("http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent")" link).

---

