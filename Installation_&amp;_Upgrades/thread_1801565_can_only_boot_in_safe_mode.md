---
title: "can only boot in safe mode"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by louis.roux on 2011-07-10
After I upgraded to 11.04 I now can only boot in safe mode. When I boot up in regular mode everything on the desktop is showing but I cant open anything.  When I try to boot up in the classic mode, which is what I prefer, I just get my wallpaper on my desktop but no icons or anything.  I didn't mind the safe mode at first but I now realise I cant install any updates which isn't good.  I have 222 updates that need installed.

---

### Post by garvinrick4 on 2011-07-10
When you have booted and nothing is happening:
ctrl/alt/f2
log in
```
unity --reset
```
ctrl/alt/f7
see if it works now.
If not then
ctrl/alt/f2
log in
```
sudo apt-get update && sudo apt-get upgrade
```
that should update you.
Ctrl/alt/f7
above gets back to GUI:

---

### Post by louis.roux on 2011-07-10
Neither of those worked and I can still only boot in safe mode.

---

### Post by wojox on 2011-07-10
Hold the left shift key and choose recovery mode and root shell with networking:
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by louis.roux on 2011-07-11
Wojox, it says it cant move. Permission denied.  Ugh

---

### Post by wojox on 2011-07-11
> **louis.roux said:**
> Wojox, it says it cant move. Permission denied.  Ugh

Oh try sudo:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by louis.roux on 2011-07-15
Wojox I hope you are still there.  Sorry I am just getting back to your last reply.  But I tried the code in sudo and it says the file doesnt exist.

---

### Post by Blasphemist on 2011-07-15
Try going into recovery mode and root console like wojox said and use this code.
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot
```

---

