---
title: "Installing new kernel from local files"
date: 2006-05-10
forum: Installation &amp; Upgrades
---

### Post by knerr on 2006-05-10
Hi there.  I'm quite new at Linux, but am relatively computer literate.  I have installed breezy on a Dual 600 Mhz PIII system and am trying to install the 686-smp kernel to make use of both proc.  I realize apt-get would be the easiest solution for me, but I only have a dialup connection, and I haven't gotten the running yet.  I've read that dialup can be difficult
 w/ Ubuntu.  I did try to get it running, but I don't think my modem is supported.  I've been trying to install the kernel manually, by DLing the files on my mac and transefering them w/ a USB drive, then installing via the terminal, but all the dependencies are kicking my butt.  Is there a simpler way to do this?  
Can someone give me a list of the files I really need to install, and let me know what order to install them?  
Or, would my time be better spent trying to get my dialup working?  Would it be possible to use a shared internet connection on a mac running OS X?
Thanks a lot for any help.  
knerr ](*,)

---

### Post by joft on 2006-05-11
Hi,

for a 686 SMP machine I would use this package:

[http://packages.ubuntu.com/breezy/base/linux-image-2.6.12-10-686-smp](http://packages.ubuntu.com/breezy/base/linux-image-2.6.12-10-686-smp)

As you can see, it depends on 3 packages (red dots), and in fact by looking at the names of them, I would say, you already have them ...

About what packages does dpkg complain? (I assume you did "dpkg -i <packagename.deb>".)

---

### Post by knerr on 2006-05-11
Well, for starters, I think I was using the packages for Hoary.  Yeah, I'm stupid.  I think I linked to them from an old forum posting.  
I think I do have all the dependencies for that package, but I started with [linux-686-smp]("http://packages.ubuntu.com/breezy/base/linux-686-smp") which is dependent on linux-image-686-smp (which is dependent on the package you linked) and linux-restricted-modules-686-smp.  Do I not need those other packages?

Thanks a lot for your help.

---

### Post by joft on 2006-05-11
In fact, you don't need these other packages. They are just there for convenience as soon as it comes to kernel package updates. Read the description of the packages, there will be a note, that they are only empty packages which just depend on the newest "real" linux-image packages.

---

