---
title: "Convert a 64-bit installation to a 32-bit"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Thorbjoern Ravn Andersen on 2010-01-14
I have an Ubuntu server vmware instance which accidentially have been installed with the 64-bit edition.  Now it needs to be moved to a 32-bit only host, and I'd rather avoid having to create a new, identical installation if it can be handled with a suitable amount of dpkg-fu.

I know it is relatively simple to switch the kernel in 32-bit mode to a PAE-version if needed (done that already), but can the whole "platform" be switched like this?

---

### Post by skymera on 2010-01-14
So Ubuntu is in the VM and is 64bit?
And it's moving to a 32bit Host, correct?

As far as i know, you'll need to reinstall, i don't think it's possible to convert 64bit to 32bit install.

---

### Post by Thorbjoern Ravn Andersen on 2010-01-14
> **skymera said:**
> So Ubuntu is in the VM and is 64bit?
And it's moving to a 32bit Host, correct?

As far as i know, you'll need to reinstall, i don't think it's possible to convert 64bit to 32bit install.

Yes, you are correct in both assumptions.  

Thank you for responding.  I'm still hoping, though :)

---

### Post by Sef on 2010-01-14
>      Quote:
                                                                      Originally Posted by **skymera**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8663338#post8663338")                 
                 [I]So Ubuntu is in the VM and is 64bit?
And it's moving to a 32bit Host, correct?

As far as i know, you'll need to reinstall, i don't think it's possible to convert 64bit to 32bit install.[/I]
                                 
Yes, you are correct in both assumptions.  

Thank you for responding.  I'm still hoping, though :smile:
Skymera is correct.  You would need to install ubuntu 32-bit.   To change from 64-bit to 32-bit (or vice-versa.)

---

