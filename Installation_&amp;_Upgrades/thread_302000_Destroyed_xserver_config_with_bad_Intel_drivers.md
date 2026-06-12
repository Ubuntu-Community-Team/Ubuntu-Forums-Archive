---
title: "Destroyed xserver config with bad Intel drivers"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by Exakun on 2006-11-17
I followed a guide posted in the ubuntu forums (which after thorough searching I still cannot find again) regarding how to install the latest graphics drivers for the 900 series intel graphics cards. I followed the guide exactly, but it hosed my xserver. I can use the command prompt but when I switch to a running xserver, my laptop monitor turns off!

I desperately need to know how to fix this, as I need to be able to use my computer as soon as possible without losing all of the settings it took me months to figure out. Right now I am using the Ubuntu 6.06 LiveCD in safe graphics mode to connect to the internet. If you know which post I am referring to and can provide me with a link to it, that would help me at least get rid of the bad drivers (I hope :(). Even better, if anyone has experience with or knows how to fix this issue and could offer me support or point me in the right direction, that would be most appreciated.

I have looked throughout the forums and there don't seem to be any threads on this topic. I have found it damn near impossible to find any information on Intel graphics cards (beyond installing 915resolution, which I remember the thread's OP said I would no longer need), even harder to find working and or somewhat recent information, and harder still to find anything even referencing intel graphics drivers, let alone how to install them.

Terribly sorry to bother everyone with this, and I hope this is in the right forum. If it helps, I am using a Toshiba Satellite M105-S3031 notebook with an integrated 945GM express chipset. Thank you in advance for your help :)

---

### Post by an.echte.trilingue on 2006-11-18
I don't know how to configure your card per se, but this is how you can get thngs back to the way they were before:

You can do two things:

First, see if your old configuration for xorg is still there as a backup.  Backup versions usually have the date when they were last changed written on the end of the file name, such as this below:
```

mat@desktop:~$ cd /etc/X11/
mat@desktop:/etc/X11$ ls
app-defaults             xinit                   Xsession
default-display-manager  Xloadimage              Xsession.d
fonts                    xorg.conf               Xsession.options
rgb.txt                  xorg.conf.200609121908  XvMCConfig
sawfish                  Xresources              Xwrapper.config
X                        xserver
mat@desktop:/etc/X11$
```

Here, the file xorg.conf.200609121908 is the backup configuration.  To start using it again, simply:
```
sudo cp xorg.conf.200609121908 xorg.conf
```
Then restart your xserver with CTRL+ALT+BACKSPACE, or if you are in the recovery mode (which you probably are) type "sudo startx" or "sudo init 5"

If you find you do not have a backup xorg.conf, then run this command in the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

That will start the graphics configuration tool, and select a good conservative driver such as vesa.

---

