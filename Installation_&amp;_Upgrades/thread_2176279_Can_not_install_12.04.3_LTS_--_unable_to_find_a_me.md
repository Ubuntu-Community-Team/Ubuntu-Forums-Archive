---
title: "Can not install 12.04.3 LTS -- unable to find a medium containing a live filesystem"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by KenF on 2013-09-23
1.  From some forum searches, I noted the closed thread [http://ubuntuforums.org/showthread.php?t=1692832&highlight=unable+find+medium+live+filesystem](http://ubuntuforums.org/showthread.php?t=1692832&highlight=unable+find+medium+live+filesystem) , but nothing there helps.

2.  When trying to boot into a live image of 12.04.3, I get this message ( "unable to find a medium containing a live filesystem") and the boot sequence stops.

a.  Image on a DVD.

I have both a DVD read/write drive and a CD-ROM drive.  This is the first time I've tried to boot a live image from a DVD rather than a CD-ROM.  I've gone into the BIOS and tried every order of boot sequence.

dmesg indicates that it finds the two drives  (/dev/sr0 and /dev/sr1).   The error message is from initramfs and says it can not find a live image.


b.  Image on a USB key.

I created the image using my current install (10.04) "Startup Disk Creator".

In the boot-up process it dumps out again into busy box with the same error message (unable to find a medium containing a live filesystem).

I was able to figure out that the image is on /dev/sdb1 and was able to mount that.  However, I can not figure out how to continue the boot-up process or get it to realize that the image is there.

c.  When 12.04 first came out and fit on a CD ROM, I was able to boot that.  However, I didn't install it at the time.

3.  Additional Information:

The image I'm using is ubuntu-12.04.3-desktop-i386.iso .    I verified the MD5 hash.


Any help/pointers?

---

### Post by Kirboosy on 2013-09-23
You may want to try Unetbootin to create your USB key. That might create the key properly.

However, you mentioned on point "C" that you burned a CD intitially and it worked just fine. You can download the original 12.04 release from the link below.

[Ubuntu 12.04 LTS]("http://old-releases.ubuntu.com/releases/12.04.0/")

Hope that helps!
~Caboose

---

### Post by KenF on 2013-09-23
1.  Regarding the USB key.

a.  I tried using unetbootin.  Same thing.

b.  I found out a bit more about what's going wrong with the USB key.  I don't have a solution, but it has to do with slow setup of the /dev area.  Either the key is somehow too slow or udevd is acting odd.

--  When it first drops into busybox with the error message, I should note that an "ls /dev/sd*" does *not* show /dev/sdb.

--  casper.log show's it is trying to read the live filesystem from /dev/sdc, /dev/sdd, ...   but not /dev/sdb

--  After a minute, /dev/sdb shows up.  After another 30 seconds /dev/sdb1 shows up.  This can be mounted, etc.

--  After a few more minutes there is a (repeated) error message to the console:

udevd[235]: timeout: killing "/sbin/blkid -o udev -p /dev/sdb"  [  ]


--  After all of this occurs, I'm fairly certain I could continue the boot/load process.  However, I'm not sure what to do.  I tried "./init 0" ... which progressed for a while.  It mounted /root and such ... but died out somehow without establishing a path for /bin, etc.

2.  I was able to write the 12.04.0 release to a CD.  It worked fine.

Thanks!!!

KenF


Thanks,

Ken

---

### Post by jayrod on 2013-10-28
I had the same exact problem, and I created the USB key using both the startup disk creator and the universal USB installer.  12.04.2 works, but 12.04.3 does not.

---

### Post by xu.walker on 2013-11-12
It turns out it would be related with USB stick type.

I used a 4G USB stick, it didn't work for a few ways I tried.

When I used an old 1G USB stick, it worked just fine.

---

