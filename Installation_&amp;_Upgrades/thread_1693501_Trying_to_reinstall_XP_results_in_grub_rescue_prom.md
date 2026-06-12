---
title: "Trying to reinstall XP results in grub rescue prompt"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by sixcorners on 2011-02-22
When I attempt to reinstall Windows XP Home Edition using the CD that came with the computer, it doesn't correctly boot into windows when it is done. Instead I get to a prompt that says "grub rescue>"
The installation CD that came with the computer uses this installer: [http://www.flickr.com/photos/23660395@N08/2951879640](http://www.flickr.com/photos/23660395@N08/2951879640)

I'm guessing that it's not installing the windows boot loader, ntldr but that's just a guess. Next time I am at the computer I am planning on using some kind of utility that would fix that.

---

### Post by zvacet on 2011-02-23
If you are dual booting Windows and Ubuntu then you can reinstall grub following [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by sixcorners on 2011-02-23
I am trying to boot to windows exclusively. Would reinstalling grub set it up so that it could chain-load ntldr on the MBR of the Windows partition? I'm not even sure if ntldr is there though.
Why did the computer come with this different Windows installation software? Has anyone had any experience with this or software like it?

---

