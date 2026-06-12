---
title: "video display messed up"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by steve984 on 2008-01-05
I was ubuntu for about  week and it was running good, I installed a tv capture card and tried to put mythtv on my system. but it messed up my network connection so it wouldn't log on. so I reinstalled ubuntu but now I am getting purple ghosting all over my screen.  I have an ati graphics card but it was working before I put mythtv on my system. I have tried to change the reslution and it di not make a differance. does anybody have an iadea on how to fix this any help would be appeciated

---

### Post by Partyboi2 on 2008-01-05
Have you tried reconfiguring xorg?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by steve984 on 2008-01-05
I'll try that, It has something to do ith the color bit rate cause it screws the card up in windows to and I have to swich from 32 bit color to 16 bit and it clears up I tried to find a way of doing it in ubuntu but I am not sure where that setting would be.  Now it won't even work with the live cd and I wasn;t haveing a problem before. will that command change the color bit rate.  they need make that live cd not so taxing on the video it starts at such a reslution I have to change it right aWAY

---

### Post by Partyboi2 on 2008-01-05
To change the color from 32 to 16 you can just change it in the xorg file.
```
gksudo gedit /etc/X11/xorg.conf
```Scroll down till you get to
```
Section "Screen"
```change
```
Defaultdepth    32
```to
```
Defaultdepth    16
```save
then
Ctrl+Alt+backspace

---

### Post by steve984 on 2008-01-05
I tried using the gksudo /etc/X11/xorg.conf in terminal and nothing comes up

---

### Post by Partyboi2 on 2008-01-05
try nano
```
sudo nano /etc/X11/xorg.conf
```
To save the file you will need to press Ctrl+o then enter
then to exit Ctrl+x

---

### Post by Craigus on 2008-01-05
> I tried using the gksudo /etc/X11/xorg.conf in terminal and nothing comes up

That's because you aren't running an editor in that command. You want:

> gksudo [COLOR="Red"]gedit[/COLOR] /etc/X11/xorg.conf

---

### Post by Partyboi2 on 2008-01-05
Sorry I forgot to type gedit. Thanks Craigus

---

