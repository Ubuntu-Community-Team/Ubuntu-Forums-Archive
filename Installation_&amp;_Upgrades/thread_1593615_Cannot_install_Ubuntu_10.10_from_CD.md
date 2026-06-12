---
title: "Cannot install Ubuntu 10.10 from CD"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by shubhkarman on 2010-10-11
Whenever I boot up my PC from the CD, it starts shows the Ubuntu logo with the loading sign and then gives me this error:

"Can not mount /dev/loop0(/cdrom/casper/filesystem/squashfs) om //filesystem squashfs"

I tried downloading and burning the ISO again but I got the same problem. I also tried using a Ubuntu 10.04 Lucid Lynx CD but it shows the same error too. By the way, my pc has 512 mb of ram..

---

### Post by molnarb14 on 2010-10-12
Hello,

i am faceing the same problem, but i don't think it's caused by lack of memory, because i have 2 gig's of ram...
If somebody has any idea please reply.

Thanks,
B

---

### Post by or1onas on 2010-10-12
I had the same problem and re-downloaded and burned the .iso at a slow speed (16x)

---

### Post by shubhkarman on 2010-10-12
I tried this on some other computers and it still doesn't work. Please help me....

---

### Post by mörgæs on 2010-10-12
If the CD does not work, you could try creating a USB stick with Unetbootin.

---

### Post by shubhkarman on 2010-10-13
Can anyone help me???

---

### Post by incanus1 on 2010-10-28
It happens to me as well.
I'm getting the following error message during the installations:

Errno 5 Input/Output error /rofs/usr/share/perl/5.10.1/unicore/namelist.txt


Ubuntu kernel 447.791849 Squashfs error unable to read inode 0x3f2d21fcc

this happens when I'm trying to install from CD and also from USB stick.

any idea what is the problem?

---

### Post by mörgæs on 2010-10-28
Again, was the USB stick made with the latest release of Unetbootin?
Does it work using the alternate installer?

---

### Post by Gralgrathor on 2010-11-12
> **mörgæs said:**
> Again, was the USB stick made with the latest release of Unetbootin?
Does it work using the alternate installer?

The same problem occurs with UnetBootin. It appears to be exactly what it is: an I/O error due to corrupted install media. However, I haven't found a way to get around it yet.

I am trying to install the Ubuntu 10.10 64bits desktop edition on a standard PC. The message I get is:

```
[ 104.800436] EXT4-fs (loop2): mounted filesystem with ordered data mode
[ 288.909464] SQUASHFS error: zlib_inflate error, data probably corrupt
[ 288.909481] SQUASHFS error: squashfs_read_data failed to read block 0x11b3773e
[ 288.909490] SQUASHFS error: Unable to read data cache entry [11b3773e]
```(The numbers might be off; copy pasted this from another bugreport. The messages are exactly the same.)

Might it be that the compressed volume contains an error at the *source*? Perhaps a rebuild by Ubuntu of the ISO image is in order? I don't know.

If and when I can get 10.10 to work, I'll post an update.


_**UPDATE:**_

I got past the error. Didn't change anything; just flashed the 10.10 amd64 desktop edition to the same USB key as before, using UnetBootin, then chose install from the boot menu. Currently installing. No news is good news.

**_ADDENDUM:_**
Another thread I read (lost the link) suggested it might have something to do with inbuilt support of Ubuntu for various types, models, brands of media. You might try fiddling with the boot options of your kernel before booting from CD or USB. Here's a HowTo: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by azertyh on 2010-11-12
> **shubhkarman said:**
> Whenever I boot up my PC from the CD, it starts shows the Ubuntu logo with the loading sign and then gives me this error:

"Can not mount /dev/loop0(/cdrom/casper/filesystem/squashfs) om //filesystem squashfs"

I tried downloading and burning the ISO again but I got the same problem. I also tried using a Ubuntu 10.04 Lucid Lynx CD but it shows the same error too. By the way, my pc has 512 mb of ram..

i have read that you got this message if you have a bad CD.
an alternative is to install ubuntu from USB, using UnetBootin as mörgaes suggested.

---

