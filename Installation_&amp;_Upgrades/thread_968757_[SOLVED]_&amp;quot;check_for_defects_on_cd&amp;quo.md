---
title: "[SOLVED] &amp;quot;check for defects on cd&amp;quot; shows no error, but I have a md5sum mismatch."
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by mempman on 2008-11-02
I recently downloaded a copy of intrepid ibex.  The downloaded image has the correct md5sum: 24ea1163ea6c9f5dae77de8c49ee7c03.

However, after I burnt this image onto a dvdr, I had the following md5sum:
f9ee46aa0b38e433d311aae2109ccacf  /dev/cdrom

When I booted off this newly burned dvd, I selected "check cd for errors" and I found no errors.

Now does this mean that there are some erros in the dvd that I burnt, but the errors are not significant enough to be detected by ubuntu's on-cd error detector?

---

### Post by mempman on 2008-11-03
bump bump bump...

---

### Post by ad_267 on 2008-11-03
I think that's normal. The md5 of the disc will be different to that of the image.

---

### Post by mempman on 2008-11-03
actually, I burnt the *.iso of ubuntu 8.10 3 times.  The first 2 times, I got a md5sum mismatch; however, for each of these cds, when I ran "check cd for defect" I got no errors.


Upon burning the *.iso image to a dvd the third time, I got exact same value for md5sum.  I am pretty sure that the "check cd for errors" program is not as accurate as md5sum.  

Anyways, I have concluded that k3b sucks for burning accurate images.  

I know I'm being neurotic about the md5sum match, but I just want to make sure that the burnt cd has exactly what I want on it.

---

### Post by ad_267 on 2008-11-03
Ok you're right, I just checked my disc which matches the iso. I was basing that on this thread: [http://ubuntuforums.org/showthread.php?t=493683](http://ubuntuforums.org/showthread.php?t=493683)

I burnt mine with brasero without any issues.

---

### Post by pavel123 on 2008-12-06
Everithing is fine with the accuracy and md5 sums.

Check sums differs because of the DVD format itself. It requires additional information to be writlen together with the original data.
That's why we get unmached md5 sum after CD image is burned to a DVD media.

To compute "true" md5 sum of a DVD (or DVD-image), use [rawread shell script]("http://www.troubleshooters.com/linux/coasterless.htm#rawread") (ex. rawread /dev/cdrom | md5sum).

---

