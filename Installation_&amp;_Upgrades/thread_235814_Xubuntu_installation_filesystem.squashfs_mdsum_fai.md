---
title: "Xubuntu installation filesystem.squashfs mdsum failed"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by noumaan on 2006-08-13
While booting from the xubuntu CD that I downloaded. I see this error:

[4294832.597000] SQUASHFS error: zlib_fs returned unexpected result 0xfffffffd
[4294832.603000] SQUASHFS error: unable to read page block 44d173a, size 7954

This error would appear with numbers changing in the square brackets. and installation halts and I am left at ubuntu@ubuntu$ prompt 

I rebooted again and checked the md5sum and found that filesystem.squashfs failed the test. 

I don't know whats wrong but I would really like to get this CD fixed without installing the entire CD again. :( is this possible?

---

### Post by dolby on 2006-08-14
only if md5sum of the iso passes

---

### Post by orb9220 on 2006-08-14
nope it means the iso is corrupted and you will need to download the iso again.

And I recommend that it only be downloaded from here, [http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

---

### Post by Carl H on 2006-08-14
> **orb9220 said:**
> And I recommend that it only be downloaded from here, [http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

Why only from there? Are there problems with ISOs downloaded from other places?

I've had 5 or 6 attempts at burning an AMD64 ISO. (See [here]("http://www.ubuntuforums.org/showthread.php?t=234348"))The last two both failed on the squashfs checksum.

---

### Post by orb9220 on 2006-08-14
Because I have downloaded from a known source. And never had problems with a failed checksum.

Download from other sources such as torrent sites, and You have no way of knowing if the iso is good and who posted it. I have always had a higher failure rate downing iso's from torrent sites then hosted servers that have the iso's.

---

### Post by MaximusToo on 2006-08-28
Similar problem with ubuntu-6.06.1-desktop-i386.iso image. MD5 checksum passes on the ISO file after it is downloaded. Checks out with the MD5 checksums posted [here]("http://ftp.wayne.edu/linux_distributions/ubuntu/6.06/MD5SUMS"). Once transfered to the disk using [ISORecorder v2]("http://isorecorder.alexfeinman.com/v2.htm") in Windows XP the boot checksum fails for *squashfs*. Two different CD's used, same issue. Would appear to be a problem with the ISO recording - either software or hardware. Although, i have used this ISO recorder for other succesful transfers.

---

### Post by Carl H on 2006-09-05
I have had multiple attempts at downloading and burning the AMD64 Ubuntu ISO, and it always fails on this checksum. 

I ordered a CD from Ship-It, and that also fails the checksum! I've tried it in two different drives with the same result, so it seems reasonable to assume that the disc itself is corrupt. 

I'm at a total loss as to what to do now. I have a brand new 64 bit PC at home with no OS, that's just gathering dust.

---

### Post by Cas07 on 2006-09-05
sorry if im missing something but does it not suggest that if a downloaded iso passes md5 checksums then the problem lies with either the cd/dvd-rom drive, defects in the physical discs or the software used to burn the discs?

To burn images in windows i use ImgBurn [ImgBurn]("http://www.imgburn.com/") and try lower burning  speeds to prevent write errors and ensure no scratches or dirt on discs.

If you are having problems with downloads, using bittorrent is a much safer option as error checking is part of it.

I dont know if pimping other distos is allowed on ubuntu forums  :-k but i run on my AMD64 work laptop SuSE 10.1 x86_64 and that was a dvd download using bittorrent.

---

### Post by Carl H on 2006-09-22
In my case, the disc doesn't pass the checksums. 

I am now seriously looking for another distro, as I have given up with Ubuntu before I even got started.

---

### Post by Carl H on 2006-09-28
I take it all back. The PC won't install any OS! Think I've got some duff hardware somewhere.

---

