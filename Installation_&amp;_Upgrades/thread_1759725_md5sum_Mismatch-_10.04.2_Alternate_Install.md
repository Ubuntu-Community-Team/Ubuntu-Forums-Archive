---
title: "md5sum Mismatch- 10.04.2 Alternate Install"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by Digital_Resistance on 2011-05-16
Hello,

I downloaded the **Xubuntu 10.04.2 *Alternate Install*** CD ISO file from    
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/)

When I checked the md5sum of the downloaded file, however, there was a mismatch. 

The md5sum given at both  
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/MD5SUMS](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/MD5SUMS)  
as well as
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) 
is **209cfc88be17ededb373b601e8defdee *xubuntu-10.04.2-alternate-i386.iso**
but running the command, 
```
md5sum xubuntu-10.04.2-alternate-i386.iso
```generated the following, obviously different checksum for me:
  
**098674ad5a59f0115030c5c0c3973899  xubuntu-10.04.2-alternate-i386.iso**

(It also took unusually long to generate the checksum- around thirty minutes.)

Is it possible that the file was corrupted or tampered with on the server?

---

### Post by Plueonic on 2011-05-16
That means you have a corrupt download..You'll need to re-download the image and while doing so,  its a better choice to use the torrent or zsync as it would minimize such corruption

---

### Post by sourchier on 2011-05-16
I think that your download did not completely finish. Flaky network connections--and overburdened servers--can contribute to this. You can try to rescue the incomplete iso using wget.

Code:

cd /path/to/iso

wget -c -4 http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.04/release/xubuntu-10.04.2-alternate-i386.iso

And see if the download completes.

---

### Post by Digital_Resistance on 2011-05-25
Thanks for the replies.

I'm pretty sure the file size matched what it was supposed to be but I suppose that indication could be off, especially since rounding is probably involved.

I was afraid that maybe the server had been compromised with a tainted file but I suppose that had such a thing occurred, it most likely would have been discovered much sooner.

---

