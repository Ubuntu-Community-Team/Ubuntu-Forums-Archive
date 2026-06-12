---
title: "Error 17 can not mount selected partition"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by molykkutti on 2010-07-22
I 've reinstalled XP partition on my ubuntu system 8.10 ,After that i reinstalled grub using live CD ubuntu 9.04

with the following commands 

grub > find /boot/grub/stage1
       > root  (hd0,5)
      > setup (hd0)
     

but when i restarted the system i got the grub menu .. but when i select ubuntu 
i got the following error message 

" error 17 .. can not mount selected partition "

I don't know how to solve the problem pls help ...

---

### Post by kansasnoob on 2010-07-22
Could you please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can do so using the Live CD.

I am curious if you know that 8.10 is no longer supported?

---

