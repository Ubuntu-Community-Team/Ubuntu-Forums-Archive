---
title: "Karmic ISO image fails test but MD5 checksum hash matches"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by kumarldh on 2009-12-14
I downloaded an ISO (ubuntu-9.10-alternate-i386.iso) using torrents and burned a CD to setup one of my laptop. When I tried to use the CD to boot it failed. I checked the CD on 2 other systems and it didn't work. I used unetbootin to create a USB startup disc but it also failed. I checked the hash and compared it with [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and didnt find any difference. Still, I again downloaded the torrent and repeated the process and failed :(. This happened 2nd time with me and with Karmic only.
Am I doing something wrong?

---

### Post by phillw on 2009-12-14
> **kumarldh said:**
> I downloaded an ISO (ubuntu-9.10-alternate-i386.iso) using torrents and burned a CD to setup one of my laptop. When I tried to use the CD to boot it failed. I checked the CD on 2 other systems and it didn't work. I used unetbootin to create a USB startup disc but it also failed. I checked the hash and compared it with [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and didnt find any difference. Still, I again downloaded the torrent and repeated the process and failed :(. This happened 2nd time with me and with Karmic only.
Am I doing something wrong?

Hi and Welcome to the Forums,

If you're having problems via the torrents, to rule anything out - it is okay to use the main registry.

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

Just ensure you choose both the format (in your case, alternate) and a country from somewhere near you. This helps reduce the load on the servers. However, they should be taking a bit of a well earned rest after the madness of earlier last month.

Make sure you burn a cd at no higher speed than 4X -- If you cannot select this low a speed, the above thread has alternative burning options.

Regards,

Phill.

---

### Post by kumarldh on 2009-12-14
Hey Phil,

Thanks a ton for your time and reply. Point to be noted here is, I downloaded the torrent from [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download). I used brasero and simply burned the CD. I have done the same for 9.04 and 8.04 and even for 7.10. I never faced any issue and interesting fact is that first time when I downloaded the ISO I was in San Jose, CA and 2nd time I was in Delhi, India and both ISOs have same issue. I tried to create a USB startup disk using these ISOs but none worked. 
For now, I have installed 9.04 on the laptop and have setup upgrade to 9.1.

---

### Post by efflandt on 2009-12-14
Once you burn the CD, eject and remount it, cd to the CD and do **md5sum -c md5sum.txt** to check if the files on the CD match the md5sums in md5sum.txt.  Although, I don't know if that reveals anything about the El Torito end of booting the CD (does it get as far as asking you what language, or if you want to test or install it?).

---

### Post by kumarldh on 2009-12-15
The CD boots and lets me install the system but fails around 14% at "Choose and install softwares", I skipped it, then I tried to install Grub and it failed, I installed LILO. This worked but installation was pretty lame...

---

