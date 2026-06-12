---
title: "Lucid on late'09 iMac"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by janjokela on 2010-03-14
For those wanting to install Lucid on a late'09 iMac, be advised.

For some unknown reason, as of now, the installation destroys (literally) the GPT partitions table. So when you boot up you computer after installation, you'll get the no boot option icon flashing. Installing and  running rEFIt from a pen drive won't help you. Your partition tables are gone. 

So in order to re-install OS X, I had to reformat the hard drive since the EFI partition was probably broken and as such the hard drive wouldn't even show up as a possible drive for installing OS X. 

As a matter of fact, It might not even be an issue with grub2, given that even choosing to not install grub will result in a bricked EFI partition (or whatever the issue might be).

Late'09 iMac Core 2. ATI. 27inch display.
Tested alpha 3 and a bunch of daily builds.

Cheers,
Jan.

---

### Post by dyltman on 2010-03-14
> **6205 said:**
> I would have late '09 iMac with shiny Snow Leopard, i would never put on that HW some crappy open source s*it... I just hope it has not damaged your Mac.

You sir are boring.

---

### Post by QwUo173Hy on 2010-03-15
Thanks for the heads up.

---

