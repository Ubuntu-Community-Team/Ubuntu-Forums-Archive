---
title: "Sound : webcam at main sound device instead soundcard"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by cosmocat on 2005-04-23
Hello,

I have installed ubuntu Hoary (good ;) ) and I still have sound with totem.
After a lot of time of reinstall alsa package, modify config files (with not too mutch knowledge), I find that I have not sound with all the application exept totem (rhytmbox, amarok,juk,cdplayer,...) because my webcam (on usb) is detected like my first soundcard instead of my sound blast live.

cat /proc/asound/cards
```
0 [Camera         ]: USB-Audio - Camera
                     Camera at usb-0000:00:1d.2-2, full speed
1 [Live           ]: EMU10K1 - Sound Blaster Live!
                     Sound Blaster Live! (rev.8) at 0xdf40, irq 22
```

Someone on the french forum tell me to add this line :
options snd-usb-audio index=-2
at the of the config file /etc/modutils/alsa-base but it changed nothing.

it seems it is a bug on ubuntu : [https://bugzilla.ubuntu.com/show_bug.cgi?id=1467](https://bugzilla.ubuntu.com/show_bug.cgi?id=1467)

and I can have sound if I don't use my webcam but it's not what I want.

I also try to edit the file /usr/share/alsa/alsa.conf to change all the file like this one :
defaults.ctl.card 0
by 
defaults.ctl.card 1
expecting to use the sound card detected by the numer '1'.
But nothing change too.

Have you got a solution for me??? You can imagine how I will be happy!

thanks in advance.
cosmocat

---

### Post by cosmocat on 2005-04-23
Sorry,
it was an error. I have posted my problem in the Warty part of the forum but it's a  problem on my ubuntu Hoary. So, I have reposted this message in the good forum hoping that I will have most answers.

If an administrator of the forum can delete this thread....

cosmocat

---

### Post by Rushan spy on 2005-04-28
I have the same problem. HELP please

---

### Post by kombipom on 2005-05-05
I found the following on another website so can't take any credit (or blame) for it.  I've just added a blow by blow description of what to do for Rushan as I know he's a total newbie.

1. Read all the instructions first then,
2. Open terminal
3. type su and enter password
4. type gedit /etc/rc.local
5. insert the following lines at end of file (it's probably empty at the moment)
# fix for audioproblem webcam, by aRTee:
rmmod snd-usb-audio
service sound stop
service alsa stop
rmmod audio
modprobe snd-emu10k1
modprobe snd-usb-audio
modprobe audio
service sound start
6. save file
7. close terminal
8. reboot with webcam plugged in and see if it works.

If it doesn't work it might be that your soundcard is not using the emu10k1 driver and you need to change this line to match your driver.  Try man modprobe to find out how to list all your modules and see if you can find your soundcard module.

Hope this helps

Kombipom (son-of-Rushan)

---

