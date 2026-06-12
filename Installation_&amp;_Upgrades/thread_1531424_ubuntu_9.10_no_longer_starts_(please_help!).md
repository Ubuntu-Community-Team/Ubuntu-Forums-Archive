---
title: "ubuntu 9.10 no longer starts (please help!)"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by daweefolk on 2010-07-15
I installed minimal ubuntu 9.10.
over about 6 months or so i perfected system. fluxbox, all codecs i needed, games, etc...

last night it just.. stopped working. 
during the boot process here's what happens, roughly.
1- shows grub menu
2- Setting preliminary keymap
3- loading AppArmor profiles
4- setting console font and keymap
5- screen goes a dark grey (about as close to black as possible while still being grey) 
6- nothing. Well, eventually the screen will go black until i hit a key so it's booted to a certain extent. i think.
**Normally apache, mysql and mpd would load at some point before getting to my login shell. After "setting console font and keymap" it's like a continuous 'clear'**

I never get a shell. absolutely no input is recognized unless it "goes to sleep" and accepts a keystroke to wake it up.

this happened a few days after i did an apt-get to update my system. i booted from a mythbuntu livecd to check my grub's menu.cfg but there are no previous kernels to try booting from.

There has to be a way to fix this from a livecd or something... i've never screwed linux that badly. 
however, if ABSOLUTELY necessary i can sudo mount my hdd from a livecd and back everything in my documents to an external and reinstall. I'd rather not though.

EDIT: crap already posted this on ubuntuforums. this post can get deleted, it's already in here somewhere

---

### Post by stlsaint on 2010-07-15
Since you say that you cant get to your terminal than all fixes will have to be done via livecd. Boot to the cd and take a look at your xorg.conf in /etc/X11. Make sure that your driver is listed as correct driver that your running on system. You may even try backing up the old xorg.conf and deleting it to see if another can be regenerated with command:
```
xorg --configure
```

---

