---
title: "[SOLVED] X-server won't start anymore after installing updates"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by Katzwinkel on 2008-11-22
Hello,
I have had Ubuntu "Feisty Fawn" installed on my PC for several years now, and it worked without problems. Some time ago I dowloaded some Updates from the official Ubuntu Site (don't know which ones anymore, but they were "highly recomennded" by the Package manager.)
Now the X-server won't start anymore. The report contains the following message:

FATAL: Error running install comand for NVIDIA
(EE)NVIDIA(0): Failed do load NVIDIA Kernel Module!
Fatal server error:
No screens found

So now all i can do is work in the shell, but i don't have any Graphical Interface anymore (which sucks). I have and always had a NVIDIA graphic-card.
I don't know enough about Unix/Linux etc to know how to reconfigure the x-server to make it work again, but there must be a way to fix it, no?
Can somebody give me tipps for this?

---

### Post by braacken on 2008-11-22
> **Katzwinkel said:**
> Hello,
I have had Ubuntu "Feisty Fawn" installed on my PC for several years now, and it worked without problems. Some time ago I dowloaded some Updates from the official Ubuntu Site (don't know which ones anymore, but they were "highly recomennded" by the Package manager.)
Now the X-server won't start anymore. The report contains the following message:

FATAL: Error running install comand for NVIDIA
(EE)NVIDIA(0): Failed do load NVIDIA Kernel Module!
Fatal server error:
No screens found

So now all i can do is work in the shell, but i don't have any Graphical Interface anymore (which sucks). I have and always had a NVIDIA graphic-card.
I don't know enough about Unix/Linux etc to know how to reconfigure the x-server to make it work again, but there must be a way to fix it, no?
Can somebody give me tipps for this?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Katzwinkel on 2008-11-22
thanks, I've tried that, but I don't know what exactly to change. I've set the graphics-card to NVIDIA (but according to the xorg.conf-file it was already set to that). That didn't work. the x-server still won't start.
maybe this will mean something to you, this was in the detailed x-server ouput:

(II)Nvidia(0): Enabled
(EE)NVIDIA(0): Failed to load the NVIDIA kernel Module!
(EE)NVIDIA(0):***aborting***
(II)unloadmodule:"NVIDIA"
(II)unload module:"ramdac"
(II) unload module:"fb"
(EE) Dcreen(s) found, but none have a usable configuration.n
Fatal server error
no screens found

My graphics card is NVIDIA GeForce 6610XL

---

### Post by braacken on 2008-11-22
> **Katzwinkel said:**
> thanks, I've tried that, but I don't know what exactly to change. I've set the graphics-card to NVIDIA (but according to the xorg.conf-file it was already set to that). That didn't work. the x-server still won't start.
maybe this will mean something to you, this was in the detailed x-server ouput:

(II)Nvidia(0): Enabled
(EE)NVIDIA(0): Failed to load the NVIDIA kernel Module!
(EE)NVIDIA(0):***aborting***
(II)unloadmodule:"NVIDIA"
(II)unload module:"ramdac"
(II) unload module:"fb"
(EE) Dcreen(s) found, but none have a usable configuration.n
Fatal server error
no screens found

My graphics card is NVIDIA GeForce 6610XL

Can you drop to terminal by Ctrl-Alt-F1 through F5 and login?

Do you have a backup of xorg.conf?
```
ls -a /etc/X11
```It will be labeled xorg.conf.(something)

---

### Post by Katzwinkel on 2008-11-22
Yes, i can use the terminal. there is no x-server backup-file from when the x-server still worked. 
After looking into other threads about x-server problems it seems to me that  there are some general problems with NVIDIA-drivers and Ubuntu (although i don't know much about that kind of thing). But it used to work before! Could it be that with these "recommended downloads" i got a newer version of the x-server that can't handle NVIDIA-drivers? If yes, can i downgrade to the older version that worked? I was quite happy with my old, working Ubuntu, and don't need any potential new features. I just don't want to reinstall the whole system.

---

### Post by braacken on 2008-11-22
That's what we were trying to do. Are you sure there are no other xorg.conf files in /etc/X11 directory? I know I have about 7 of them and they don't always require the user to manually back them up. We would simply overwrite your current bad xorg.conf with one of the backups.

```
ls -a /etc/X11
```when you drop down to terminal

If there is one right down the filename and then login as root.

```
cd /etc/X11
``````
touch xorg.conf.20080824
```If you have a backup made it will differ after xorg.conf; those have date backup was made in the filename

```
mv xorg.conf.20080824 xorg.conf
```Answer Y to the overwrite

Then reboot or ```
shutdown -r now
```

---

### Post by Katzwinkel on 2008-11-22
Thanks for replying so fast. Okay there are several conf-files, but they all date from today (from just now in fact) when i tried to reconfigure the xserver. no older conf-files.
 
But now i've tried this and the x-server works again: As far as i can understand what is beeing said in other forums and threads there really seems to be a problem with NVIDIA and ewer Ubuntu versions. And it seems to be a workaround to set the graphic-card to "Vesa" or "nv". I chose "nv", rebooted and...it works!

That's ok for me, but that can't be optimal can it? I mean, my graphic-card IS NVIDIA and it always worked with Ubuntu, so somehow i can't understand why it doesn't anymore.

But thanks for your help anyway, and downgrading to the old xserver that worked with my NVIDIA-Card would have been my preferred option, but since there are no old xorg.conf-backup-files thats probably not possible anymore, or?

---

### Post by braacken on 2008-11-22
Nope. But try to remember to back up a working copy in case it happens again.

---

### Post by Katzwinkel on 2008-11-22
Sure. Now that i know this should be done i'll definitely do it. I think i'll even backup the whole system before i do any future updates or upgrades. But right now i'm happy because my ubuntu is working again:)

---

### Post by jadhav333 on 2008-11-23
> **Katzwinkel said:**
> 
But now i've tried this and the x-server works again: As far as i can understand what is beeing said in other forums and threads there really seems to be a problem with NVIDIA and ewer Ubuntu versions. And it seems to be a workaround to set the graphic-card to "Vesa" or "nv". I chose "nv", rebooted and...it works!



How do u set / selct nv or vesa as the graphic card

---

