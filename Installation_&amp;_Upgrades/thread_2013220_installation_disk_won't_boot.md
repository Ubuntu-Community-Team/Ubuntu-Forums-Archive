---
title: "installation disk won't boot"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by somae on 2012-06-30
I've been trying to install ubuntu from a cd. I've been able to burn cds and boot from the cd (installed debian that way). I tried holding down the left shift key as the boot started, and also tried pressing it over and over. When the cd tries to boot it goes to a black screen and hangs.

Unfortunately, we've got the Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) graphics device - which is why I want to try ubuntu because I was unable to solve the problem with it in debian.

The computer is a dell dimension xps_r with about 2GHz cpu and 500M ram.

Help appreciated.

---

### Post by southerngeek on 2012-06-30
How far exactly are you getting in the boot process? Past the livecd boot options menu, or is it even getting that far?

---

### Post by somae on 2012-06-30
It doesn't get to anything but a black screen - (there is no livecd boot options menu).

---

### Post by southerngeek on 2012-06-30
Have you checked the CD (in another computer, or at least in the program that you used to burn the image with) to make sure it burned correctly?

There are known issues with that chip (as you probably already know..), if the CD checks out ok, you might try downloading one of the older version livecd iso's and see if one of them will work, just to test it out.

---

### Post by sudodus on 2012-06-30
You can also try ***Knoppix***, which is known for its good hardware detection. I have used the version 6.4.4 not only for live sessions but also to install an 'almost-debian' system on a computer older and smaller than yours.

In order to avoid running into adriane mode (for people with bad eyes) you should enter **knoppix** at the boot prompt (plus optional boot 'cheat codes' if necessary).

---

### Post by somae on 2012-06-30
I didn't try the cd in a different computer (but am going to). I always use "verify" when I burn cds.

Will give knoppix a try.

Thanks.

---

### Post by somae on 2012-06-30
Is there a way to verify that the file downloaded correctly? I used bit torrent and the file size was 217,702 kb.

---

### Post by sudodus on 2012-07-01
Usually you can find a checksum, for example md5sum at the web site, from where you select the download or torrent.

The output of ```
md5sum filename.iso
``` should match the md5sum at the web site.

For example, at this link, there are iso files and the corresponding md5sums

[[COLOR="Red"]_ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/_[/COLOR]]("ftp://ftp.uni-kl.de/pub/linux/knoppix-dvd/")

---

