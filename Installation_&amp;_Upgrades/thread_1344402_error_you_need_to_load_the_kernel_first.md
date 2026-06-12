---
title: "error: you need to load the kernel first"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by root45 on 2009-12-02
I recently upgraded 9.04 to 9.10. The biggest problem with this was that the 2.6.31-302ec kernel wouldn't boot. I'd get the GRUB boot menu and select this kernel and get the message:

error: you need to load the kernel first

Trying to boot into other kernels didn't work either, although I later found out that this was a display problem. Eventually I gave up and reinstalled 9.10. To my dismay, I still get the error about needing to load the kernel when I try to boot 2.6.31-302ec.

I can now boot 2.6.31-15 though, so at the very least I have a somewhat working setup. The problem now is that 2.6.31-15 has a module problem. When I run sudo modprobe rt61pci (my wireless driver) to start wireless, I get the following error:

FATAL: Could not load /lib/modules/2.6.31-15-generic/modules.dep: No such file or directory

So basically, I would really like to get 2.6.31-302ec working, which I'm pretty sure is just a GRUB problem. But I also have no real way of getting files onto my computer. I can't access the internet and I can't transfer packages using an external drive because the file-type modules won't load.

My drive setup is:

/dev/sda1        HPFS/NTFS
/dev/sda2        W95 Ext'd (LBA)
/dev/sda5        Linux
/dev/sda6        Linux
/dev/sda7        Linux swap / Solaris

The first two are a Windows XP install, the third is a separate /home partition and the fourth is the karmic install. I'm not quite sure what else to post, but any help getting this working is appreciated.

---

### Post by u.b.u.n.t.u on 2009-12-02
Perhaps reinstall 9.04, as that apparently didn't cause these problems, check that everything is working and then start with 9.10 again, taking careful note?

---

### Post by root45 on 2009-12-03
Okay. I reinstalled 9.10 again, this time telling the installer to format the drive before while installing. I guess the Ubunutu installer won't actually delete old files unless you tell it to. So the old GRUB menu was still installed when I reinstalled the first time. Formatting the drive erased everything and did a true "clean" install of karmic.

So I think everything is working now. The only real problem I see is that I no longer have a 2.6.31-302ec kernel. I can boot from -14 or -15 though, and both of those load fine with all the modules. I don't really know much about what this means, but if it's problem, let me know. Otherwise, thanks for your help.

---

### Post by u.b.u.n.t.u on 2009-12-03
Sounds like you have it working. Well done!

---

