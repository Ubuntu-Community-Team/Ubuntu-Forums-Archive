---
title: "Updating with apt-get CD-ROM troubles?"
date: 2006-05-20
forum: Installation &amp; Upgrades
---

### Post by phreaky- on 2006-05-20
I wanted to install a package called 'bc'. So I did apt-get install bc. Then he will ask for the cd-rom. But it sais I don't have the right cd-rom.

I downloaded ubuntu for testing purposes and after trying I was sold. I ordered the 5.10 retail cd's and trown my burned cd away. So for the updates I tried to use the retail cd and that doesn't work now.

I edited /etc/apt/sources.list and put a # in front of:

deb cdrom:[Ubuntu-Server 5.10 _Breezy Badger_ - Release i386 (20051013)]/ breezy main restricted

So now it will download the release from The Internet but I have a slow connection and for me it's usefull if I could use the cd without reinstalling? Is there a workaround.

---

### Post by aysiu on 2006-05-20
Do you want to use the CD-ROM or the internet?

If you want to use the CD-ROM, comment out the internet sources and uncomment the CD-ROM one.

If you want the internet, go with what you have.

If you think you may have the wrong CD-ROM, put your CD in the drive, go to Synaptic Package Manager, and click Edit > Add CD-ROM. It'll add whatever you've got as a CD source. Then comment out your bad CD-ROM source.

---

### Post by phreaky- on 2006-05-21
Yes I want to use the cd-rom. But don't have the correct (burned) cd-rom anymore. I have a retail cd now. I don't have the graphical user interface installed. So Synaptic won't work for me?

---

### Post by aysiu on 2006-05-21
[QUOTE=phreaky-]Yes I want to use the cd-rom. But don't have the correct (burned) cd-rom anymore. I have a retail cd now. I don't have the graphical user interface installed. So Synaptic won't work for me?[/QUOTE] If you're working off a server install (not graphical user interface), then you'll have to use the ```
apt-cdrom add
``` command. I'm not sure whether it's that or ```
sudo apt-cdrom add
```

---

### Post by phreaky- on 2006-05-31
Thank you that option worked for me :)

---

