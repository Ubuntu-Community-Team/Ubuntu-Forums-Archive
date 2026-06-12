---
title: "Recent Update broke Nvidia Proprietary drivers"
date: 2015-01-25
forum: Installation &amp; Upgrades
---

### Post by greg69 on 2015-01-25
Kit:
Gigabyte GA-78-LMT-S2P
AMD FX 6100 6 core processor
EVGA GTX 760
G.Skill Ripjaws 8GB RAM
An update on the 19-22 of January

I'm an Avid linux gamer. I do a lot of stuff. I played 7 days to die. No issues. I turned off my computer for the night. (I've been playing with this driver for months)
I woke up in the morning and oddly enough, "OpenGL is not using direct rendering." This stopped me from opening any kind of game. I read up that a driver reinstall would fix it so I reinstalled.
Restart and I got to the login screen. Left screen was disabled. Not something to worry about, I did change display drivers.

What happened was, Keyboard and mouse input was deadened. Password screen was perfectly fine and the box ticked with the cursor and everything.

After multiple reinstalls and checks, I discovered this. If I didn't use Software Updater, I could run the binary drivers perfectly fine. With a small hit to performance in some games and a massive performance hit in Counter Strike: Global offensive.

I tried Xubuntu. No change.

I also read up that disabling ACPI in the GRUB menu solves the keyboard and mouse issue. So I did it and guess what? I could input stuff into the Password box. I logged in and... Nothing. I was stuck in limbo between the Password screen and the Desktop.

If I updated everything and Kept with Nouveau I can run all my games. However this isn't a good working because the Nouveau drivers are weaker than the Proprietary ones.

I tried updating with Nvidia-331 from apt-get. The same issue persists.

I'm stuck for ideas. Is anybody else having this issue? Can anybody link me the faulty update? Is there a workaround?

Thanks.

---

### Post by MAFoElffen on 2015-01-25
Which driver are you trying to use? nVidia packaged through the Additional drivers (jockey) or the nVidia binary from nVidia? Whar version #? From main or edgers?

It would help if you installed, booted, tried to switch over to a TTY via <cntrl><alt><F2> to 
```

sudo rn /etc/X11/xorg.conf /etc/etc/X11/xorg.conf
sudo reboot

```
Then post your /var/log/Xorg.0.log file

---

### Post by greg69 on 2015-01-25
NVIDIA-Linux-x86_64-346.35 is the one I'm trying to use.
I tried Nvidia-331 from apt-get but that didn't work either.
Also, Ctrl+Alt+F1 didn't work. I got to the password screen and it took no input.

---

