---
title: "Can't boot from Hoary CD"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by helgman on 2005-06-08
Hello!

This problem seem somewhat strange to me ... and I don't know what to do.

I'm about to start installing Hoary on a (5 years old) computer that's going to be given to an older relative. I've already talk him into trying Linux and since I'm using Ubuntu that's what I'm going to give him (I hope).

Now ... here is the problem. I have the Hoary (shipped) CD but the CD-ROM drive is unable to find it (or boot from it, call it what you want). Okej, you might say, maybe you haven't set up the BIOS to boot from CD? Sorry ... I have. And the strange thing (for me anyway) is that I can boot up from the Knoppix live-CD ... no questions asked, but when ever I try the Hoary CD (live or install) ... nothing. I'm downloading Hoary right now and I will try to burn it ... but ... why should it work when I burn it rather then when I use the shipped copy? I even tried diffrent (Hoary) CD's ... no luck.

Thankfull for any sugestions.

---

### Post by asarwate on 2005-06-08
I had a similar problem with a burned Ubuntu CD, but as it turned out the problem was with the drive (which was also a bit old and failing) -- if the burned CD doesn't work as well it might be a hardware problem, although I'm not sure why the Knoppix CD would work.

---

### Post by helgman on 2005-06-08
Yes ... I'm starting to belive it is a drive-problem (I got it from a friend saying he didn't remeber if there was a problem or not) ... strange is ... Knoppix still works EVERY time I put it in the drive.

Took another shoot at the Hoary CD right after using Knoppix and got it as far as "mount CD" in the pre-installation process. But ... strange sounds coming from the ROM ... might have to change it for installation (has another one I could try with ... also old and tierd but ... worked in the past).

Thanks for the replay, and as you say ... why does the Knoppix work but not Ubuntu?!

---

### Post by helgman on 2005-06-08
Okej ... so this is what happened:

Tried the Hoary CD one last time ... it started the installation but died at 4-5%. Got no further. Then I (GNOME)baked a new CD (2xspeed) of the .iso I downloaded and put that into the drive ... reboot ... and now the system is up and happely running. Still don't know what caused the problem. But ... hey ... it works!

---

### Post by asarwate on 2005-06-11
I also had to reburn the CD at 1x speed to get it to install properly, even though all of the checksums and so on worked.  Maybe there is something funny with the CD-ROM driver that comes with the installer?

---

