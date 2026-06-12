---
title: "linux 2.6.27-5.8"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BCurtisWX on 2008-10-02
i386 build of linux 2.6.27-5.8 in ubuntu intrepid RELEASE

in the builds for intrepid..

I didn't know we were up to -5, aren't we at -4.7?

---

### Post by wilsong on 2008-10-02
My DMESG 

states Linux version 2.6.27-4-generic

---

### Post by wgrant on 2008-10-02
Perhaps because -5 was published less than an hour ago...

---

### Post by waspbr on 2008-10-03
2.6.27-5.8 can't come soon enough to ubuntu, it should fix the problem I have and finally allow me to boot my Desktop

---

### Post by wilsong on 2008-10-03
I installed the alpha 6 from the iso, and have all the updates so technically im using the beta, and my kernel is 4 ... should i have 5?

---

### Post by wgrant on 2008-10-03
> **wilsong said:**
> I installed the alpha 6 from the iso, and have all the updates so technically im using the beta, and my kernel is 4 ... should i have 5?

No - it's still in the NEW queue.

---

### Post by plun on 2008-10-03
All facts about this new kernel which will arrive when its ready.

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/007852.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/007852.html)

.

---

### Post by plun on 2008-10-05
It took some time for a meta package, now its out.

I have had no problem with this kernel.

5.5, 5.8..:confused:

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/007977.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/007977.html)

---

### Post by dabl on 2008-10-05
It's working great here -- fixed the %*&^#@&@ ethernet e1000e module problem.

[http://ubuntuforums.org/showthread.php?t=927943&page=8](http://ubuntuforums.org/showthread.php?t=927943&page=8)

---

### Post by Nullack on 2008-10-05
Me too, its working nicely. Albeit still for the lack of other framebuffer resolutions on boot.

---

### Post by ronacc on 2008-10-05
ok here on 64bit

---

### Post by Perpetual on 2008-10-05
Where would I find out what packages are in the [daily builds]("http://cdimage.ubuntu.com/daily-live/current/")?  I would like to watch for this kernel to show up in the builds but I can't seem to figure out where the information is.

Thanks.

---

### Post by ShirishAg75 on 2008-10-05
Perpetual, 
       there is something called [list]("http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.list") which has the info. that you need :)

---

### Post by Perpetual on 2008-10-05
> **ShirishAg75 said:**
> Perpetual, 
       there is something called [list]("http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.list") which has the info. that you need :)

I saw that but unless I can't read, I don't see where it lists the kernel there.

---

### Post by wgrant on 2008-10-05
> **Perpetual said:**
> I saw that but unless I can't read, I don't see where it lists the kernel there.

The list is fine for the alternate or server CDs, but you need [the manifest](http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.manifest) for desktop CDs. linux-image-2.6.XX-Y-FLAVOUR is what you're looking for.

---

### Post by gtdaqua on 2008-10-06
upgrading to 2.6.27-5 (today) reverts to [this error]("http://ubuntuforums.org/showthread.php?t=913771").

---

### Post by nanog on 2008-10-06
rock solid on 2 laptops and 1 dev box. am thinking about moving to ibex for all desktop installs!

---

### Post by Perpetual on 2008-10-06
> **wgrant said:**
> The list is fine for the alternate or server CDs, but you need [the manifest](http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.manifest) for desktop CDs. linux-image-2.6.XX-Y-FLAVOUR is what you're looking for.

Thanks.

---

### Post by gtdaqua on 2008-10-08
> **gtdaqua said:**
> upgrading to 2.6.27-5 (today) reverts to [this error]("http://ubuntuforums.org/showthread.php?t=913771").

Upgrading to 2.6.27-6 still throws the [same]("http://ubuntuforums.org/showthread.php?t=913771") error.

---

