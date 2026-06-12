---
title: "Another Plymouth question..."
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by whalogreg on 2010-05-08
So I've searched high and low to find something on my Plymouth problem, but mine seems to be a little bit different from everything I've found. I AM getting a plymouth screen, and it IS in the proper resolution, which seems to be the problem with most people. My problem is, my plymouth screen only shows up for about a half a second after about 30 seconds of a blank screen with a white cursor at the top, and then goes right to the login screen. Not a huge problem, but if possible I'd like to fix this. 

I'm running a gateway md7818u with Intel Graphics Media Accelerator (GMA) 4500MHD. Intel Core 2 Duo T6400. 4gb ram. Not sure what other info anyone might need...

On a side note, I've read that plymouth is supposed to help in terms of boot speed. I have not noticed this, in fact my 10.04 might be four or five seconds slower to an idle desktop than my previous 9.10 install... What about it is supposed to be faster?

---

### Post by whalogreg on 2010-05-08
bump

---

### Post by whalogreg on 2010-05-10
::bump::

---

### Post by chadwick359 on 2010-05-10
I'm gonna confirm this, 10.4 x64, Intel GMA 4500hd, and plymouth only flashing on for a second before GDM loads, still poking around for a why, but just letting you know there are other folk out there looking too.

---

### Post by ronparent on 2010-05-10
I'm seeing the same problem. An improvement over prior problems, so, I am leaving well enough alone. Not to say it shouldm't be fixed.

---

### Post by whalogreg on 2010-05-10
> **ronparent said:**
> I'm seeing the same problem. An improvement over prior problems, so, I am leaving well enough alone. Not to say it shouldm't be fixed.

I don't know if I've seen an improvement over prior problems. I personally never had any problems with GRUB/upsplash or booting in general. This is mostly aesthetic, but like I said above, my 10.04 boots about five seconds slower than my 9.10 install did...

---

### Post by davidmohammed on 2010-05-10
have you tried this trick as root (sudo su)

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

---

### Post by whalogreg on 2010-05-11
> **davidmohammed said:**
> have you tried this trick as root (sudo su)

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u



That seemed to do the trick! Thanks!

---

