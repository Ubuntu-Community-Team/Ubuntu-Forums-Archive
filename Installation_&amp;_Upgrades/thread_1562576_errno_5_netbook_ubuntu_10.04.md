---
title: "errno 5 netbook ubuntu 10.04"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by Microsoft Hater on 2010-08-27
Hey all!

I'm trying to install ubuntu 10.04 to my netbook from usb:

It loads great from the usb, but when I try to install it to the harddrive I get the errno 5 problem at 54% time in and out.

My harddrive is fine, and I haven't been able to solve this problem from the forum searches I've done.

I have an acer zg5 netbook (SSD) that I'm trying to install to. 

I've tried reformatting the hd to a few different formats with no success. Any tips, advice, help, suggestions are greatly appreciated!!

---

### Post by Microsoft Hater on 2010-08-27
If there is any more information I can provide to help solve this problem, I am eager to submit it. Any help is greatly appreciated.

---

### Post by presence1960 on 2010-08-27
[http://ubuntuforums.org/showthread.php?t=1207755&page=2](http://ubuntuforums.org/showthread.php?t=1207755&page=2)

scroll down to #20.

There is a typo in #4. The command should read ```
ubiquity --no-migration-assistant
```

---

### Post by Microsoft Hater on 2010-08-27
Thanks for the reply Presence1960. :)

I have already tried the advice I found in the search engine:

I've tried these too:

[http://ubuntuforums.org/showthread.php?t=1545792](http://ubuntuforums.org/showthread.php?t=1545792)

But to no avail. Any ideas?

---

### Post by Microsoft Hater on 2010-08-28
Actually, if I just use Ubuntu from my USB that would probably suit me fine. Are there any problems with using my USB as a partition to run it from? Can I still use all of the plugins and whatnot and just install it to the usb?

---

### Post by Microsoft Hater on 2010-08-28
Is there just some bug in the 10.04 release?

---

### Post by Microsoft Hater on 2010-08-28
*UPDATE*

I've tried installing both the netbook Ubuntu 10.04 and the i386.iso for the regular desktop Ubuntu onto both my SSD and my mmc/sd drive, and both have the errno 5 at around 50%. No luck yet - tried the terminal install, the try ubuntu then install and the from bootup install.

---

### Post by Microsoft Hater on 2010-08-28
Still not having any luck - even after memory/disk checks... Any ideas??

---

### Post by Microsoft Hater on 2010-08-30
It was the USB drive. I tried a different one, same brand and size even, and it fixed it yesterday. 

So **to beat this errno 5 problem:**

1) Check that the md5 hash is the same.

2) Check that your CD is properly burnt (It didn't offer me the option to check my USB - that would've saved a lot of time) (Burn them as slow as possible, **avoid** CD/DVD-**RW**s, and *follow step one first.*

3) Try a different USB drive. Or two or 3.

4) Try both "Install now" and install after selecting the "Try Ubuntu without installing" functions.

5) Run the installer through the "ubiquity --no-migration-assistant" command in terminal

6) Try downloading the alternate.iso of the ubuntu you want: Repeat steps 1-5.

7) Try removing some ram sticks or replacing them. If all of these solutions don't work for you, you might need a new harddrive.

Hope this helps!

---

### Post by supermooshman on 2010-08-31
just had the same problem 

I solved it by booting the live cd and deleting all partitions with parted..


Should've found this thread earlier (would've saved me a lot of hairpulling :))

---

### Post by Microsoft Hater on 2010-09-04
7) Boot the live cd and delete all partitions with gparted.
8-->Try removing some ram sticks or replacing them. If all of these solutions don't work for you, you might need a new harddrive.
 
Thanks for the extra input supermooshman!
 
(PS I'm going to be in Brussels this fall! I hear the chocolate rocks!)

---

### Post by jimbo99 on 2010-09-15
I would agree to not assume that the source drive isn't faulty.  I've run into those issues a lot.  Though you worked it out I would really like to have the Linux maintainers work out more suitable error messages for display rather than some cryptic error number and then dumping additional info into some log file that new and even moderately knowledge users have no idea exists (or where it is if they did know).

---

