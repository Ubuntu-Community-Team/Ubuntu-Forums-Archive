---
title: "Windowframes are gone after the manually installation of nvidia"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by Vossibear on 2008-09-22
Hi community

After my manual installation of nvidia driver the windowframes are gone and when I want to open the terminal, there only comes a white window with no cursor ... what I have to do? :(

---

### Post by lian1238 on 2008-09-22
You might wanna install nvidia-settings and use that to configure it.

---

### Post by Vossibear on 2008-09-22
so what do you think I have to configure?

The resolution settings doesnt solve my problem ;)

---

### Post by lian1238 on 2008-09-22
Try saving to X configuration file and restart. Back up /etc/X11/xorg.conf before you do.

---

### Post by Vossibear on 2008-09-22
it doesnt change anything :(

---

### Post by lian1238 on 2008-09-22
I'm assuming you're running compiz. What happens when you use metacity instead of compiz?
```

metacity --replace

```

---

### Post by lian1238 on 2008-09-22
Okay. This might fix your problem:
Backup your xorg.conf first though.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```Open xorg.conf for editting.
```
sudo gedit /etc/X11/xorg.conf
```Add the following line into the Section "Screen" part.
```
*Option* "*AddARGBGLXVisuals*" "true"
```Restart X.
```
Ctrl+Alt+Backspace
```Hope that fixes it.

Edit: In case you can't start X anymore or the resolution becomes very low, go to the commandline (Ctrl+Alt+1) and login. Then type:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
to restore the "working" config file.

---

