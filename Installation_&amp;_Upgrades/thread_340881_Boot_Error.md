---
title: "Boot Error"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by ChaseLeonard on 2007-01-17
First off i'm new too ubuntu and am having some problems with the cd. i followed the instructions on the site about burning iso's. but
when i boot with the live cd i select run/install and it immediatly goes too boot error and i've done it with multiple cds they are imation, 1x-4x compatible, 80min/700mb.

 i have 960 mb of ram
and i have a gateway laptop
with a mobile AMD sempron
so it should work am i doing something wrong?


Thanks

---

### Post by confused57 on 2007-01-17
Here's an excellent guide for downloading & burning an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Make sure to select burn "as an image" in your cd burning software(don't burn as a data cd or as a bootable cd), set your bios to boot to the cd drive before your hard drive(s).

Write down what error messages you're seeing, that'll help diagnose the problem.

---

### Post by ChaseLeonard on 2007-01-17
that's just it the error was that it said boot error and then it rebooted and yeah i followed the instructions on this site about downloading that software and then go to actions and then burn to image](*,)

---

### Post by ChaseLeonard on 2007-01-17
i also see this in green lettering at the type when i get the error= isolinux: disc read error 80,

---

### Post by confused57 on 2007-01-18
> **ChaseLeonard said:**
> i also see this in green lettering at the type when i get the error= isolinux: disc read error 80,

I did a forum & google search for this error, but it appears there's not a definitive solution...there was everything from bad iso burn, using different cd media, problems with cd drive, to flashing bios.

If you followed the link, you probably did a md5sum to ensure the integrity of the iso download...if you downloaded the 64-bit, maybe try the 32-bit...maybe try another brand of cd media(new preferably, not rewritten cd-rw)...or download something like Puppy Linux(think it's only about a 50 Mb download),burn & try it...if you don't mind a larger download, possibly Knoppix.
I don't think using the alternate vs desktop cd would make a difference, they probably use the same bootloader.
Good luck with it, wish I could help you more.

---

### Post by ChaseLeonard on 2007-01-18
> **confused57 said:**
> I did a forum & google search for this error, but it appears there's not a definitive solution...there was everything from bad iso burn, using different cd media, problems with cd drive, to flashing bios.

If you followed the link, you probably did a md5sum to ensure the integrity of the iso download...if you downloaded the 64-bit, maybe try the 32-bit...maybe try another brand of cd media(new preferably, not rewritten cd-rw)...or download something like Puppy Linux(think it's only about a 50 Mb download),burn & try it...if you don't mind a larger download, possibly Knoppix.
I don't think using the alternate vs desktop cd would make a difference, they probably use the same bootloader.
Good luck with it, wish I could help you more.


im gonna try the other linux's and try it with a diffrent cd media. and let my friend harrison mess with it, he dual boots windows and ubuntu

---

