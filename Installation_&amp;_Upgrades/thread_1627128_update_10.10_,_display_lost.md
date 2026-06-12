---
title: "update 10.10 , display lost"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2010-11-21
So far I made updates on this system , but now first time update kind of failed.

before 10.04
updated to 10.10, now no display
During the update installation, I noticed that there were somehow some nvidia files installed, but this computer has intel 82830 as graphic adaptor.

Now I can not boot to graphic at all, also from recovery to safe graphic is not possible.

Trying to boot to previous kernel ends up in black screen only, can however still boot to recovery console.

I have also xface installed on this, so this could help, but have no idea how to start it from the console.
During boot, I often see some messages like display not found or no display etc.

Any way to repair all?

---

### Post by dino99 on 2010-11-21
remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

then reboot and check driver activation (system admin additional driver)

note: you might have xserver-xorg-video-intel installed (synaptic)

---

### Post by ottosykora on 2010-11-21
ok, removed the xorg.conf, tried to reinstall the xserver-xorg-video-intel, got replay the lastes version is installed.
Still no luck with start of either gnome or xface.
The boot of the older kernel left from the 10.04 ends up in CLI, the attempt to boot into the current ubuntu ends up in nothing, means black screen.
Is there a way to try the xface from the command prompt somehow?

---

### Post by Stephen_at on 2010-11-29
Its a known issue with Linux and the intel 82830 chipset. its to do with the kernel mode feature which basically means any computer using this chip set probably wont work with later versions of linux. You can try the solution(s) mentioned here :

[http://www.insidesocal.com/click/2010/02/intel-82830-cgc-830m-graphics.html](http://www.insidesocal.com/click/2010/02/intel-82830-cgc-830m-graphics.html)

---

