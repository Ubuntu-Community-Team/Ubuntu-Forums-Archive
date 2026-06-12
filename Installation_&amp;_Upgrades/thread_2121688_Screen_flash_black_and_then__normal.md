---
title: "Screen flash black and then  normal"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by geomarsh on 2013-03-02
Took old pc with athlon 64X2 dual, 1.90 ghz, 2gb ram and 80gb hd and formatted with ubuntu 10 then upgarded to 12.04.  It brings up ubuntu fine but randomly the scrren goes black and then back to normal.  I tried changing system settings under "brightness and lock" to 1 hour but it didn't help.  Are there some updates that need to be installed.  Update Manager says not.   Thank you for your consideration.

---

### Post by MAFoElffen on 2013-03-02
A couple questions-

You said old PC, instead of saying laptop... so I'm assuming it's a desktop (power supply vs. battery) right?

Could you please post the results of this:
```

lspci -vnn | grep -i VGA

```
And post or attach /var/log/Xorg.0.log

---

### Post by geomarsh on 2013-03-15
00:05.0 VGA compatible controller [0300]: NVIDIA Corporation C51 [GeForce 6150 LE] [10de:0241] (rev a2) (prog-if 00 [VGA controller])

---

### Post by MAFoElffen on 2013-03-15
Got your PM. If you could answer my PM questions here... Reread your first post. 

If you tried to reset your screen brightness settings to an hour, thinking it was the screensaver timing out and blanking... and that didn't work. You were probably round-about-right. Being that is a bug with that module.

Try this. Open a terminal session <cntrl><alt><t>, and enter in this command:
```

xset s 0 0

```
If that fixes what is happening with you... To make that as a permanent work-around, open the "gedit" text editor, open the file ".profile". It will be in your "home" directory. Add a line at the end of the file and type in the same command. Save and exit. It will then do that command every time the desktop starts.

You could also just open a terminal session and say:
```

echo "xset s 0 0" >> ~/.profile

```
and it would do the same thing, but faster and no visual feedback.

---

