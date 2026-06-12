---
title: "DSDT problems with new install"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2006-11-09
Hi there,

ive been trying to install Linux on my new laptop for a couple of weeks now. I started by trying to install various forms of Ubuntu with various boot options but all with no luck. So far i have tried the following

Edgy   -   i386 and 64bit, alternate, desktop and even server
Dapper   -   as above
Fedora Core 6   -   i386 only
Mandriva 2007   -   i386

none of them worked and they all freeze/hang at the same point, just after it loads the kernel image for the first time after selecting "new install"

the best info i could get was during the server installation of Edgy which spat out the following as the last message before it hangs

```
checking if image is initramfs...it isn't (no cpio magic); looks like an initrd
ACPI: Looking for DSDT in initrd...not found!
not found!
```

now i have no idea what this means. i've done some googling but there is not much useful info.

this is my laptop by the way [Evesham Quest A240](http://www.evesham.com/products/info.asp?e=B4FD51BB-DE44-42CD-8305-811E407E4078). i cant find a more detailed hardware spec but i can find out anything easily enough from Device Manager in XP if anyone needs to know.

does anyone recognise this and can explain what it means? is it possible to workaround or am i just gonna have to face facts and accept that i may have to return to XP?

Thanks, any advice/help is appreciated

---

### Post by renzokuken on 2006-11-10
Ok, i found Mandriva 2006 on an oldish CD that came with a magazine, I tried that and seemed to boot ok, until i got to the partitioning stage at which it said it could not partition/format because my NTFS file system is corrupted.

I cant see how this is related to above but thought it might help shed some light for someone to come and save my day

---

