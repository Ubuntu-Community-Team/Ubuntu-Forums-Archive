---
title: "Noob questions : Won't boot off ISO"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by grinch on 2007-04-24
I've burned the ISO to a disc,  and i know the DVD player is capable of booting of a disc...  but it won't pick up the ISO.


There are no error messages of any kind, it reads the disc (light flashes) then gives up after a while and boots into windows.

I know i may be being bit vague, but can anyone offer any advice?

Thanks

---

### Post by blitzer on 2007-04-24
Hi grinch,

Yes, it is a bit vague :)    Is your BIOS set-up to boot from CD-Rom first ?  You can check this on start-up by hitting the delete key or F1 depending on your system ([COLOR="Red"]Check your manual[/COLOR]) in one of the catagories is boot-up option - change it to CD-rom first.  :)

---

### Post by az on 2007-04-24
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by grinch on 2007-04-24
DVD drive is definitely set to be bootable, and will boot off other CDs.

Burnt the iso with InfraRecorder  and checked it with winMD5sum just to be sure.

It still won't boot off the disc.  :confused: 


Thanks

---

### Post by psusi on 2007-04-24
How did you check the md5sum?  Under windows?  I assume that you followed the howto already linked and that if you look at the cd you don't see a .iso file on it?

---

### Post by grinch on 2007-04-24
> **psusi said:**
> How did you check the md5sum?  Under windows? 


Yes.

> **psusi said:**
> 
 I assume that you followed the howto already linked and that if you look at the cd you don't see a .iso file on it?


Followed the how to, and there's definitely  an ISO burned to the disc.

Thanks

---

### Post by phidia on 2007-04-24
I believe what psusi is saying is that you don't want to see a .iso file on the cd. The iso needs to be burned as an image- a bootable image.

---

### Post by grinch on 2007-04-24
> **phidia said:**
> I believe what psusi is saying is that you don't want to see a .iso file on the cd. The iso needs to be burned as an image- a bootable image.

Ive  definitely burned as an image in a previous attempt.
My ignorance has me  at quite a disadvantage.

---

### Post by psusi on 2007-04-25
Yes, what I meant was if you stick the disc in and open it in explorer, do you see a .iso file, or a bunch of other files?  If the former, then you didn't burn it as an iso.  

As for the md5sum, how did you do this under windows?  IIRC, even if you get a win32 port of md5sum, trying to run "md5sum d:" fails.

---

