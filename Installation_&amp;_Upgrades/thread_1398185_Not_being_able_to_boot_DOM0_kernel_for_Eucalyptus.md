---
title: "Not being able to boot DOM0 kernel for Eucalyptus"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by tej.sarup on 2010-02-04
I have downloaded and installed the Debian DOM0 Xen kernel and the modules on my Ubuntu Jaunty machine.

The necessary changes were made in the menu.lst and I can see the entry in the GRUB menu when the system boots.

On selecting the Xen kernel there is some information which I guess comes from XEN but then I see messages like 
(XEN) is relinquishing control VGA Console etc.
and then the GRUB menu shows up again? In which case I can choose the Ubuntu Jaunty installation and begin in work in that

I am new to ubuntu and technically what I understand is supposed to happen is that i should boot the DOM0 kernel and be able to login right? as opposed to landing up at the GRUB menu?

1. The GRUB menu should not show up again right?
2. A more basic question, i am just using the Debian DOM0 kernel so after the kernel boots what should happen?

---

### Post by yogeshg1987 on 2010-02-04
Don't know much about it. 

But this should point you somewhere: [http://ubuntuforums.org/showthread.php?p=6230287](http://ubuntuforums.org/showthread.php?p=6230287)

Oh forgot, and this should be of help too: [http://lists.xensource.com/archives/html/xen-devel/2008-05/msg00873.html](http://lists.xensource.com/archives/html/xen-devel/2008-05/msg00873.html)

---

### Post by tej.sarup on 2010-02-04
Thanks!
It just seems that to get Xen working on Ubuntu now is just about implementing workarounds one after the other. So i would probably have to explore the KVM route now !

---

