---
title: "edgy-dvd md5sum mismatch"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by tuxfun on 2006-10-28
Hello Every Buddy,
  
The downloaded edgy-dvd-i386.iso's md5sum mismatches with the source URL.


 (Source URL)
 [http://cdimages.ubuntu.com/dvd/current/MD5SUMS](http://cdimages.ubuntu.com/dvd/current/MD5SUMS)

 (md5sum)
 e246727e80bc212d297c41888a73d9ab  edgy-dvd-i386.iso

 (Destination, i.e on my Hard disk)
 037cb3eb867e1fdfe10d17264dbd3761 *edgy-dvd-i386.iso


[B] I downloaded this iso using 'GWGET' the gnome-downloader, which actually couldn't stop downloading even after it was 100 % (dunno why!!)
and have burnt it using GnomeBaker. 

Now when I try to install a software from this burnt dvd , synaptic gives the following error messages :
[/B]

<ermess>

 W: Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Daily Build i386 (20061007)]/pool/main/libv/libvorbis/libvorbisfile3_1.1.2-1ubuntu1_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Daily Build i386 (20061007)]/pool/main/l/lua50/liblua50_5.0.2-6_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Daily Build i386 (20061007)]/pool/main/l/lua50/liblualib50_5.0.2-6_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Daily Build i386 (20061007)]/pool/main/o/openexr/libopenexr2c2a_1.2.2-4.3_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Daily Build i386 (20061007)]/pool/main/p/pcre3/libpcre3_6.4-2ubuntu1_i386.deb
  MD5Sum mismatch

</ermess>  ( ....there are more)
 
 
[B]Kindly help me in fixing this as it took me more than a week to download the whole dvd.

I really would like to fix this, and burn an other dvd with correct md5sum settings.
[/B]


Thanks in Advance,
Arjun.

---

