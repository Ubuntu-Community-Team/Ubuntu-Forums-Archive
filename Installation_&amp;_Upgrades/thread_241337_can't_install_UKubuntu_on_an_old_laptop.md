---
title: "can't install U/Kubuntu on an old laptop"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by tubunu on 2006-08-22
I've tried this with a friend's laptop. Tried both Ubuntu and Kubuntu desktop CD's and then tried with Ubuntu Alternate CD. The alternate installation doesn't proceed, after (it seems) the copying of the files is done everything just hangs...

The laptop is pretty old with 128RAM, that's why I decided to try the Alternate Ubuntu CD. It's funny but as the last resort I tried Mandriva 2006 and it DID INSTALL perfectly, works a little slow, but it does work. 

Could anyone please suggest what might be the problem? Should I try Xubuntu alternate CD? Though I'm not so sure the problem is about the distro, but the installer.

---

### Post by cstronach on 2006-08-22
I had some major freezing up problems recently on a Ubuntu install to an old laptop - nearly gave up until I tried adding acpi=force to the kernal line in the Grub startup menu.

A reference:
[http://www.linuxquestions.org/questions/showthread.php?threadid=330447](http://www.linuxquestions.org/questions/showthread.php?threadid=330447)

Everything worked fine after that... but I forgot that I had managed to get through the install first (with some temporary freezing). Anyway, I hope that helps you somehow.

---

### Post by tubunu on 2006-08-23
Thanks, I'm gonna try it. Will post here if I encounter any further problems. Cheers.

---

