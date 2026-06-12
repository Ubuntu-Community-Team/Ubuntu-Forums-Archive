---
title: "How to upgrade from 32bit Ubuntu to 64bit Ubuntu?"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by stephanecharette on 2007-11-10
I currently have 32 bit Ubuntu 7.10 working just fine on my system.

I tried the 64 bit Live CD, and saw that I do indeed have a 64 bit processor.  I would like to use the 64 bit version so I have access to all 4GB of ram.  Is there a way to upgrade "in-place" from 32 bit to 64 bit?  Or would I have to completely re-install?

I tried in the install to select the manual partition setup and specified "/" as the mount point of my existing partition, but the installation app told me it would have to reformat that partition, which isn't what I want.

Stéphane Charette

---

### Post by rsambuca on 2007-11-10
You need to do a complete re-install.  Back up your sensitive data files and install overtop.

---

### Post by taisao on 2007-11-10
you can't use 4GB of ram with 32bit ubuntu?

---

### Post by stephanecharette on 2007-11-10
> **taisao said:**
> you can't use 4GB of ram with 32bit ubuntu?

My understanding is that all 32-bit OS (Windows, Linux, etc) can only directly address 3GB of memory space.  The other gig is not directly addressable.  With 64-bit addressing, this is not a problem.

Stéphane Charette

---

### Post by stephanecharette on 2007-11-10
Thanks rsambuca.

Related question:  If I use the 64-bit version of Ubuntu 7.10, can I still install and use the same set of 32-bit applications widely available?  Or can I only use applications that have been recompiled for 64-bit?

Stéphane Charette

---

### Post by rsambuca on 2007-11-10
The repositories between 32 and 64 bit are almost identical, so you may as well use the 64bit native versions.  Some 32bit apps can be force installed to work with the 64bit.  

To which apps were you referring?

---

### Post by stephanecharette on 2007-11-10
> **rsambuca said:**
> To which apps were you referring?

None in particular.  I was just curious to know if I'd be stuck with just 0.1% of the apps I normally have access to from Synaptic.  Or if all apps are made available in both 32-bit and 64-bit flavours.  Or if I can run 32-bit apps from within a 64-bit OS.

---

### Post by ptn107 on 2007-11-11
I run all my pcs with 64 bit ubuntu.  The software you can install is identical to 32 bit.  You'll notice that it is a little bit faster on 64 though (though not by much with some software).

---

### Post by recto on 2007-11-11
Hi, I have the same situation with my 64bit AMD Athlon +5000 with 2gb. I was using the Ubuntu 7,40 32bit ver. I tried to upgrade using the Update anager but it only upgraded to 7,10 still on a 32bit platform. I tried with the livecd 64bit 7,10 ver but theres no other way to upgrade, I guess a re-install would be the best thing. You can mirror a copy of your current setup with GHOST - wouldnt hurt to have a copy in case things dont go as planned.

Cheers.

---

