---
title: "Intersting installation attempt"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by count23 on 2008-01-03
Hello everyone,

I've got an oldish server here, it's about 5 years old and i wanna put Ubuntu on it. 

Interestingly enough, it doesnt have a video, keyboard or mouse port - And i dont have BIOS access because it doesn't turn up when you start the system up. It seems to be running some stripped down version of linux i've never seen before. 

However, i do have access to GRUB, root access to the operating system already installed. The system also has USB ports (external CD rom and whatnot) and network ports. 

What I want to do is put ubuntu server on this system and have it racked up in my lab somewhere.

My question is, can ubuntu server be installed via a serial console and how would i get GRUB to recognize a USB CD ROM devices (or boot from tftp) if it can't give me a bios?

---

### Post by Borbus on 2008-01-03
Well there's a guide here for installing Debian from a remote location by debootstrapping your system: [http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)

It should work for Ubuntu too, I'd use Debian on a server instead of Ubuntu anyway.

---

### Post by count23 on 2008-01-03
Thanks for that Borbus, however, it appears that the linux flavour i'm on does not have RPM or DEB abilities, only tar and untar. So I don't suppose there's an alternative to these or a way to convert archive types to tar?

---

