---
title: "noob driver problem"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by EasyWind on 2007-07-17
I need some help with a problem I probably caused myself...

I finally got Edgy installed and working perfectly and then updated all the packages, etcbe ...

I verified that I had the latest update manager and then updated to feisty...

Then I was snooping around and found the desktop effects thing and that's when things went south...

The desktop effects didn't work like I thought so I tried to switch back to the previous driver settings and now when Ubuntu boots up, I get a white box centered on the screen which turns all white after a few seconds.

How can I fix this? Would the easiest thing to do be to reinstall everything starting with the Edgy CD - i have spent several hours trying to get this all working right.

I have installed Ubuntu on a Dell I8100 that is using an Nvidia Geforce2 video card . I am also running Windows XP Pro as well and it still boots and runs properly..

---

### Post by dfreer on 2007-07-17
What video driver are you currently using (it's listed in /etc/X11/xorg.conf, if you don't know where it is in that file, you can simply post the file here, we might need it anyways).

---

### Post by EasyWind on 2007-07-17
thanx for replying, dfreer:


You're right, I don't know which driver I am using but wouldn't I need to be able to get into Ubuntu to access a command line to find that out?

Just asking - I am a true linux noob and this is my first venture into linux (I finally got fed up with the whole Microsucks thing although I am still using Windows XP until I can reach some kind of comfort level with linux)

thanx for any help....

---

### Post by confused57 on 2007-07-17
> **EasyWind said:**
> thanx for replying, dfreer:


You're right, I don't know which driver I am using but wouldn't I need to be able to get into Ubuntu to access a command line to find that out?

Just asking - I am a true linux noob and this is my first venture into linux (I finally got fed up with the whole Microsucks thing although I am still using Windows XP until I can reach some kind of comfort level with linux)

thanx for any help....
After Ubuntu boots up to a white screen, try pressing "Ctrl+Alt+F1", login, enter:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```
you can probably just select the defaults for each screen, but select "vesa" or "nv" for your video driver...once you've finished configuring xorg, enter:
```
startx
```

This should at least get you back to a GUI.

---

