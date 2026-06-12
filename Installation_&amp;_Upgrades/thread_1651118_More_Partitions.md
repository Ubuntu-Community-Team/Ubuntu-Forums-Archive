---
title: "More Partitions"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by YoSniper on 2010-12-22
Hello everybody,

This isn't a huge problem, but it is starting to annoy me. Pretty much every time my computer updates while under the Ubuntu platform, it creates a new partition in my hard disk for that version. So every time I want to restart my computer, rather than simply choosing between Windows and Linux, I have to choose which version of Linux or Windows.

Is there an easy way (in Windows or Linux) to merge these partitions or delete the old ones without losing data?

I'd rather not have 20 options to choose from on every boot.

Thanks.

---

### Post by CraigThomas on 2010-12-23
I'm bit of noob but I'm pretty sure what you are talking about are not new partitions, but different kernel versions.
I'm not sure what version you are running so I'm assuming the latest 10.10 which normally uses grub2, which is the bootloader presenting you with the options.
What you need to do is remove the older kernel versions (the advice of cautious people is to generally leave this version and the one before, but I tend leave only the latest, highest numbered) this can be done from synaptic assuming you know which versions to remove.
Feel free to do a search yourself for this topic but one the first helpful links I came across was this one:
[http://ulyssesonline.com/2010/07/25/remove-old-kernel-in-ubuntu-and-grub2/](http://ulyssesonline.com/2010/07/25/remove-old-kernel-in-ubuntu-and-grub2/)

Hope this helps,
Craig

---

### Post by sikander3786 on 2010-12-23
The solution has been presented by *CraigThomas* already :-)

Those are not partitions they are just the newer kernels. And it is strongly recommended that you keep at least one older kernel so if something wicked happens with the current one, you've the option to boot the older and can diagnose/fix the problem.

How to remove older kernels courtesy of forum member *drs305*
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

