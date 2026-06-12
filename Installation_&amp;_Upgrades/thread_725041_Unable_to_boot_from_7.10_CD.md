---
title: "Unable to boot from 7.10 CD"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by easytech205 on 2008-03-15
I downloaded 7.10 ISO and then burned it as an ISO but when I try to boot to it it will not boot fully.  It gets to the initial boot screen which has all the options and then whichever option you choose (including Check CD) it just stops!

Any ideas?

---

### Post by forestpixie on 2008-03-15
check the md5sum and did you burn it slowly

ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

---

### Post by easytech205 on 2008-03-15
Forgot to check the md5sum for the ISO but yes I did burn it slowly...

> **forestpixie said:**
> check the md5sum and did you burn it slowly

ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

---

### Post by forestpixie on 2008-03-15
well have you checked it now - also when you start the cd - there is a check cd for defects option, which I always do just to be sure

[https://help.ubuntu.com/community/BurningIsoHowto#head-6788e413b69a8947c263c08d435f3e7fa8a3237d](https://help.ubuntu.com/community/BurningIsoHowto#head-6788e413b69a8947c263c08d435f3e7fa8a3237d)

---

### Post by Peter09 on 2008-03-15
Might be worth publishing your system specs so that we can have an idea of what Hardware you have.

---

### Post by easytech205 on 2008-03-15
Not able to check until I get home from work later today.  When i tried the "Check CD" option it also locked up and did nothing!

I shall use that burning guide this evenign and try reburning it if the checksum is correct.

> **forestpixie said:**
> well have you checked it now - also when you start the cd - there is a check cd for defects option, which I always do just to be sure

[https://help.ubuntu.com/community/BurningIsoHowto#head-6788e413b69a8947c263c08d435f3e7fa8a3237d](https://help.ubuntu.com/community/BurningIsoHowto#head-6788e413b69a8947c263c08d435f3e7fa8a3237d)

---

### Post by MONODA on 2008-03-15
have you tried the alternate install cd. It is an installation cd in text mode. You can download it from the ubuntu site.

---

### Post by bhocay on 2008-03-15
i've succed installing ubuntu by flash Drive as boot able disk and put the iso's on the hard drive

first of all.. it was fail, i forgot what hapened.. 
but  i've change the Vmlinuz and initrd installation files coz the file could be corrupt
Download from here [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/)

and viola.. :)  it works
hope this will help
let me know if it works :)

---

