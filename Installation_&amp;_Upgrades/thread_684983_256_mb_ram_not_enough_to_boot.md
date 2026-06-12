---
title: "256 mb ram not enough to boot?"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by 99bluefoxx on 2008-02-01
ok, so i have an 1998 ibm thinkpad notebook which has 256 mb of ram init, suffecient to boot ubuntu[i booted a pc on 128 with ubuntu b4] but when i try to boot ANY ubuntu cd i own it tells me "ERR: NOT ENOUGH MEMORY TO BOOT SELECTEd KERNEL"
what is the problem here? i meet the requirementsits an p2 233 mhz with 256 mb of ramand a cd and floppy drive, pcmcia ethernet card, yet ubuntu will not boot
i am currently running puppy on it[playing geweled lols] and tried a slax cd but it was scratched, and the slackware disk i burned last night also says not enough ram, yet another pc i own has only 64 mb of ram in it and it boots any and all of my linux CDs
any suggestions here[i would go for alternate install cd but i have no burner, it broke on me[[i used my g/fs burner]] so yea...;]
anything would be nice[boot options..etc...]

---

### Post by zvacet on 2008-02-01
You can try alternate CD or even better Xubuntu alternate CD.

---

### Post by wasing on 2008-02-01
is it out of memory as in ram or memory as in hard disk space.i have a notebook with the same specs as yours  but i used the alternate Cd and i used Xubuntu because Ubuntu needs around 4GB of Harddisk space. also if you don't like Xubuntu try out fluxbuntu or Puppy/damn small linux. hope this helps i just noticed you didn't post the hard drive space.

---

### Post by kerry_s on 2008-02-01
> **99bluefoxx said:**
> ok, so i have an 1998 ibm thinkpad notebook which has 256 mb of ram init, suffecient to boot ubuntu[i booted a pc on 128 with ubuntu b4] but when i try to boot ANY ubuntu cd i own it tells me "ERR: NOT ENOUGH MEMORY TO BOOT SELECTEd KERNEL"
what is the problem here? i meet the requirementsits an p2 233 mhz with 256 mb of ramand a cd and floppy drive, pcmcia ethernet card, yet ubuntu will not boot
i am currently running puppy on it[playing geweled lols] and tried a slax cd but it was scratched, and the slackware disk i burned last night also says not enough ram, yet another pc i own has only 64 mb of ram in it and it boots any and all of my linux CDs
any suggestions here[i would go for alternate install cd but i have no burner, it broke on me[[i used my g/fs burner]] so yea...;]
anything would be nice[boot options..etc...]

ubuntu not really for old, they cut out alot of support. on some older systems with old bio's you need to specify the ram " mem=256mb " it's a bios problem.

---

### Post by mmmichael on 2008-02-01
If you have an OS running (you said you have puppy on it) try unetbootin:
[http://lubi.sourceforge.net/unetbootin.html]("http://lubi.sourceforge.net/unetbootin.html")
You can download and install a boot/root image for ubuntu or any of several distros.
When you reboot you will see a new entry in your grub menu which will launch a net installation.
I used it to install debian etch on a laptop with 256 mb ram. I installed it with no desktop gui, then installed xorg, fluxbox, and a few other apps. Works great.

---

### Post by sports fan Matt on 2008-02-01
id do xubuntu as well...I wouldnt want to push it cause 256 is honeestly imo pushing it to the max..Also what about others like fluxbuntu or DSL?

---

### Post by kerry_s on 2008-02-01
256ram is fine, i have 256ram. it's the 233mhz cpu that's going to give the most problems. for such a machine DSL is king-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

