---
title: "Upgrade from cd? How?"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by ruialexbarbosa on 2008-06-06
Hi,

trying to upgrade from 7.04 to 7.10 (on a mac powerbook g4, PPC version).

How do I do it from the cd? I have the cd in the slot... What now?

Thanks

---

### Post by briandu on 2008-06-06
u do not need to do that.

just open xterm and enter:

sudo apt-get upgrade 

and away you go

---

### Post by ruialexbarbosa on 2008-06-06
It just says there's nothing to add... :confused:

---

### Post by avtolle on 2008-06-06
> **ruialexbarbosa said:**
> Hi,

trying to upgrade from 7.04 to 7.10 (on a mac powerbook g4, PPC version).

How do I do it from the cd? I have the cd in the slot... What now?

Thanks
With the CD in the slot, reboot; when the chime sounds, hold down the "c" key, and the Mac should boot from the CD.

Which CD are you using? Desktop or Alternate? Reason I ask is that many of us with G4s can only install, it seems, from the Alternate.

BTW, I think you should join us on the Apple Users Forum for more responses to ppc related questions. 

I want to warn you about one more thing; when/if you are successful in booting from the 7.10 CD, you may find yourself dropped into Busy Box. If this happens to you, then at the prompt ```
sudo modprobe ide-core
```which will hopefully allow the boot process to continue.

---

### Post by ruialexbarbosa on 2008-06-06
Yes, yes, you guys (apple forum) are the ones I'm looking for!!!

Here's my story:

7.04 and 8.04 boot with live cd (I'm on a g4 12" 512ram 1.33), 7.10 will not boot.

I heard that to use MOL I can't use 8.04, but 7.04 doesn't give me wifi.

Which version should I use? Where do I start? Is there a "all you need to know about installing ubuntu on a g4 powerbook"?

I had many succesfull installs with vaios and toshibas since 6.06, but new (ish) to Mac.

Thanks again

---

### Post by avtolle on 2008-06-06
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=328](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=328) is the link to the Apple Users Forum.

Please review my earlier post about 7.10 problems on boot. From what I understand, MOL does not run on 8.04, and as I don't use it, not sure about 7.10, but think from reading threads it does there. Good luck.

---

### Post by avtolle on 2008-06-06
[https://wiki.ubuntu.com/PowerPCFAQ#head-cf835a6b16435fb0efca0a89d13844bd3b92011f](https://wiki.ubuntu.com/PowerPCFAQ#head-cf835a6b16435fb0efca0a89d13844bd3b92011f) is a link that you might also find helpful.

---

### Post by Sef on 2008-06-06
> How do I do it from the cd? I have the cd in the slot... What now?

1) The alternate cd is needed to upgrade from the cd.  

2) System > Administration > Software Sources > Check Installable from CD-ROM/DVD

---

