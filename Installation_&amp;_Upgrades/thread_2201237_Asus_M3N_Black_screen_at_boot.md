---
title: "Asus M3N: Black screen at boot"
date: 2014-01-23
forum: Installation &amp; Upgrades
---

### Post by simone3 on 2014-01-23
Hi!

I got an old laptop Asus M3N pentium CentrinoM 1.3Ghz

I reached the goal to install xubuntu 12.04, it was all fine just with the only option nolapic.

The boot is black from the Grub 1.99 loader.
The rescue mode start and it suddenly stop at this row:
acpi: 2 blocks of module-level excutable AML code

the Grub version is very spartan but it is very full of commands and I donno how to use it at all.
I would like to try the nolapic option again, but how do it?

What I can do?
Thanks

---

### Post by mörgæs on 2014-01-23
Hi, welcome to the fora.
Does this help?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by simone3 on 2014-01-23
yep, it is started!!!
I'm going to fix the most difficult step, so, the solution I found (but I don't understand perfectly its meaning) it was to add the nolapic option to the the line that is calling the image of the system.
So, nest step: Why it nolapic instead other options? then how to make it permanent by default?
Do you have other useful link for me about this nolapic option and other like this one?

Next step: how to fix the grub into just one layer and not like chinese dollies?
now it is like this:
Grub Xubuntu
Grub Win7
Grub WinXP

However, I'm going to erase XP and I hope it will be very soon

Thanks for now

---

### Post by mörgæs on 2014-01-24
The link above also describes how to make boot options permanent. 
I don't know anything specific about nolapic, sorry. I can only point you to Google. 

If you want advice with dual/triple boot it's best to post a screenshot from Gparted.

---

