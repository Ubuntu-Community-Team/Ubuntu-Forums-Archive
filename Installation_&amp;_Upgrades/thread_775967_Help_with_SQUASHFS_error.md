---
title: "Help with SQUASHFS error"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by TuckLive on 2008-04-30
I'm trying to install Hardy, but even before it loads I get a "SQUASHFS error:  Unable to read page" that just scrolls forever.  When I check the cd for error I get 13, but I checked the same cd in my laptop and it says 0 errors and loads fine so it's not a bad cd.  I tried my old 7.10 cd and I get the same error.  Anybody else seen this?

---

### Post by jdholifield on 2008-04-30
Tuck, I saw the same thing with my installation last night.

Fortunately I was able to press the reset button on the computer and after a cold boot it started right up normally as it should and I've had no problems with it since.

---

### Post by TuckLive on 2008-04-30
I haven't been so lucky.  I've pushed the reset button dozens of times hoping to get lucky.  I had Windows Server 03 running perfectly with it.  I believe the problem to be hardware, but I can't think of what.

---

### Post by TuckLive on 2008-04-30
to give more information, 7.10 server ed. works just fine.  I also burned another cd at the lowest speed and still same results.  The problem must reside in hardware, but not in the cd player.  Anybody know a workaround or something I could possibly change in the bios?

---

### Post by Nidding on 2008-05-01
I have the exact same problem except that the cd doesn't show any errors when I check it.
As I was convinced that the cds were the problem, after 5-6 different cd/DVD and maybe 20 runs of the installation, I actually got it past this point of the install (I changed the installer language to Danish instead og English at this point so maybe that had something to do with it). But I've still only managed to get it to the basic install, so I can now boot the console. As I'm a rookie when it comes to linux, I don't know what to do from here, so if anybody can come up with a workaround, it would be quite nice.

---

### Post by digitaldoug on 2008-05-01
I got the same problem.  It turns out that ubuntu-8.04-desktop-i386
iso image is too big for many CD-R (733,079,552 bytes) and this
truncates the squashfs.filesystem file on the CD-R.  I tried copying it to a DVD-R, but am still having problems.

I don't know why Ubuntu has not pulled this .iso from its 
distribution yet.

digitaldoug

---

### Post by devliljohn on 2008-05-06
i was having the same error and after reading this thread i trie dburning the .iso to a dvd and it worked. w00t w00t

---

### Post by aks19 on 2011-02-02
I also faced the same problem and it got resolved when I the downloaded the iso image file again.

For me the problem was the corrupt iso image. I used md5 checker and realized that I was not getting the expected md5 sum on existing iso image file.

I downloaded the file again and checked md5. This time I got the expected md5 sum and was able to successfully install the OS.

Hope this helps someone.

Cheers.

---

