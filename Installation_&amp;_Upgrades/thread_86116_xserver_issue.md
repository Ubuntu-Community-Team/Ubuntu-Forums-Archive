---
title: "xserver issue"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by feralcelt on 2005-11-04
Well here is the story. I recently installed Ubuntu on my neighbors computer. It worked fine for a few days and then xserver stopped working and she is now unable to use a graphical desktop environment.

I looked up similar issues here and I tried to reconfigure the package but it said no such package found

i tried to go to the usr/bin/xstart and it is gone. 

I know next to nothing about linux command line and if there is anyone out there that could give me a step by step guide on how to download/install/run xserver I would be thankful for them for the rest of my life.

---

### Post by Kyral on 2005-11-04
Okay....looks like somehow X got nuked....

Try this

```
sudo apt-get install xserver-xorg
```

---

### Post by feralcelt on 2005-11-04
Okay, lets say that does not work, what would be another thing I could do? For instance what if I have not configured the synaptic package manager or what if internet connectivity is an issue will i still be able to apt-get?

---

### Post by drashkeev on 2005-11-04
Yes, you'd need an internet connection or an ubuntu CD to reinstall X. You might want to run apt-get --reinstall install xserver-xorg.

---

### Post by feralcelt on 2005-11-04
I have the ubuntu cd do I need to do anything special to have it install from the cd?

---

### Post by drashkeev on 2005-11-04
Try just running apt-get install whatever, with the cdrom in the drive

if it barfs, run 

apt-cdrom add
apt-get update
apt-get install whatever

That should work

---

### Post by feralcelt on 2005-11-04
thanks for all your help. I'll try it when i get home.

---

