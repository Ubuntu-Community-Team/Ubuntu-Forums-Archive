---
title: "Installation hangs in beginning"
date: 2004-11-07
forum: Installation &amp; Upgrades
---

### Post by Scor3p on 2004-11-07
PC: Pentium 2 - 400Mhz, that's actually all I know of it. But I installed Debian Sarge on it before i was trying this.

And this is The Warty Warhog... I checked de md5 sum, it passed, I burned it with low speed twice. But when I want to install, it get's stuck after this:

Loading /install/vmlinuz . . . . . . . . . . . . . . . . . . . . . . . .
Loading /install/initrd.gz . . . . . . . .

I really don't know why it hangs. I left the PC on all night, but after 9 hours it was still at that point..

Any help is appreciated..

[update]
A few more hours later I get an error:

Loading /install/initrd.gz . . . . . . . . isolinux : Diskerror 80, AX = 4200, drive 9F

Boot failed : press a key to retry

---

### Post by mercurus on 2004-11-08
Nothing definitive but this looks like a possible cause:

[http://lists.suse.com/archive/suse-linux-e/2004-May/0533.html](http://lists.suse.com/archive/suse-linux-e/2004-May/0533.html)

What has me baffled is why the Debian Sarge pre-release CD booted ok, and yet Ubuntu's (almost identical) installer failed. Is the isolinux image that different ?

Cheers
mercurus

---

