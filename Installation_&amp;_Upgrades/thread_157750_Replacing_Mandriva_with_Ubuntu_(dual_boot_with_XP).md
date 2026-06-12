---
title: "Replacing Mandriva with Ubuntu (dual boot with XP)"
date: 2006-04-09
forum: Installation &amp; Upgrades
---

### Post by FroGGerUK on 2006-04-09
I hope you guys can help...

For ages now I've had Mandriva LE2005 on this system dual-booting with Windows XP but I've never really got on with Mandriva and hardly used it.

I *really* like the 'live' version of Ubuntu so I'd like to replace Mandriva with it - but how?

Is there anything I need to do in Windows like removing the logical drives in 'Computer Management' (there are three - one 5.85GB, one 1.07GB and one 5.12GB) or will it be easy to get Ubuntu to reformat these when installing? Are they big enough for Ubuntu?

What about the GRUB? Should I let Ubuntu overwrite the GRUB that Mandriva installed? Reading these forums it looks like many have problems with the GRUB and I really don't want to lose the ability to boot to Windows just yet :-) 

Finally, the only Ubuntu disc I have is V5.04. Is it easy to get Ubuntu up to the latest version from V5.04 or should I install the latest version from the off?

Many thanks for your help.

---

### Post by evilgold on 2006-04-09
Load up the install cd and see. It gives you options on what partitions to use and format. Just choose your old mandriva partitions to use for the new ubuntu install. Grub will be overwritten and as long as the /boot (or the entire root) of your old install is formatted it should work fine.

I'd reccomend installing the latest version first, but im sure there are tutorials on this form about how to do a dist upgrade.

---

