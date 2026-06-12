---
title: "&quot;10 times faster&quot; patch in Linux 2.6.35-24?"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by TheCosmicFrog on 2010-12-23
Hi everyone,

Just a quick question. Does the latest Linux kernel update for Ubuntu (2.6.35-24) contain the infamous "10 times faster" patch?

This is the patch I'm referring to:
[http://www.pcworld.com/businesscenter/article/210966/tiny_linux_kernel_patch_delivers_huge_speed_boost.html](http://www.pcworld.com/businesscenter/article/210966/tiny_linux_kernel_patch_delivers_huge_speed_boost.html)

I know in the article it says we have to wait until 2.6.38, but since I'm very unfamiliar with Linux kernel development, I just thought I'd ask. 

If not, should I just go about updating myself? Or is it better to be safe and stick with the kernel version in the Ubuntu repositories?

Thanks and happy holidays,
Aaron

---

### Post by davidmohammed on 2010-12-23
best wait - saying that though - some people claim that [this alternative]("http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html") works as well.

---

### Post by TheCosmicFrog on 2010-12-23
> **davidmohammed said:**
> best wait - saying that though - some people claim that [this alternative]("http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html") works as well.

I read about that. It came from a Red Hat developer, correct? Apparently Linus gave him a pretty hard time for it - felt it was pretty uncalled for. 

Have you tried this yourself?

---

### Post by davidmohammed on 2010-12-23
no - I'm not convinced it will improve matters for me since I use a single processor.  I believe that the kernel patch and this patch is for dual cores and better.

Willing to be proved wrong though if someone can decipher those instructions.

---

### Post by TheCosmicFrog on 2010-12-23
Have a Core 2 Duo myself. A little weary of applying this non-kernel patch though. If something goes wrong and I want to remove it later I doubt it'll be too easy :/

---

### Post by oldos2er on 2010-12-23
You can try [https://launchpad.net/~chogydan/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~chogydan/+archive/ppa?field.series_filter=maverick)

---

