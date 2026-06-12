---
title: "Upgraded graphics card, greeted with plain text"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by mo79 on 2007-03-09
I recently had to upgrade my deceased video card, and as it died untimely I had no chance to remove the ATi drivers as I'm now on an nVidia card. All's fine in Windows, but when I try to boot Ubuntu I just get a message about how X can't start and then just a command prompt. How do I get 'round this?

---

### Post by milton1 on 2007-03-09
sudo pico /etc/X11/xorg.conf

editing xorg.conf and setting 'driver=nv' should get you a functional gui. you can then install and configure nvidia-glx to get better performance. Many guides all over this forum to help with that.

edit: you will need to restart X.

---

### Post by taurus on 2007-03-09
Boot into recovery mode from GRUB menu and at the prompt, edit /etc/X11/xorg.conf.

```
nano -Bw /etc/X11/xorg.conf
```
Replace "ati" or whatever Driver in there with either "nv" or "vesa".  Save it with <Ctrl>o and <Ctrl>x.

Then, reboot with

```
shutdown -r now
```
Once X is working again, install nVidia driver for your new graphic card.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by bulldog on 2007-03-09
```
sudo aptitude install nvidia-glx
```

```
sudo dpkg-reconfigure xserver-xorg
```

With this two commands you should be able to get in to your graphical environment again.
You can un- install your ATI drivers of course.

---

### Post by Algren_San on 2007-03-13
ok what would happen if the last graphic card was built in but the new one is pci and ubuntu just freaking load the onboard i allready disable the primary video device  and its set it up to my new card the thing is why it just hangs and i cant even made it to the command pront to introduce the commands i have to re enable the last built in graphics and do the changes there but still not freaking working.... what should i do? thx

---

