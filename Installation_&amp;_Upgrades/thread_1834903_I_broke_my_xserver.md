---
title: "I broke my xserver"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by waylow on 2011-08-28
I have just come back to Ubuntu in the past few days (11.04) after a few years on mac

I had some trouble getting my dual monitors to work but I did get them up and running.  Now after a few days, I've been working happily, then I started to mess around with my display settings (compiz settings) and changed something

then after a reboot my system was getting stuck on "checking battery status" on reboot

I launched a terminal (Ctrl Alt F1), logged in and could only boot into classic mode

after messing around some more -I have made things go from bad to worse

I couldn't launch into anything except the terminal so 
I tried to purge the nvidia drivers so I could reinstall

but the system can't connect to the internet in it's current state
so I couldn't reinstall all the stuff I need

so now my system goes to a purple scambled screen at launch
I can't log in to a terminal or anything


is there a way to rescue the system w/o a reinstall
I can log in with the live CD and view all my files

would it be possible to put back the missing packages and fix the xorg.conf file?

otherwise I can only think of transferring my home directory to another drive, doing a fresh install and then transferring all my files back

any advice

the command I did in the terminal was

```

sudo apt-get remove --purge nvidia*

```

---

### Post by bruno9779 on 2011-08-28
You can download the proprietary Nvidia drivers from their website and copy them on a usb.

Then start up your system am press SHIFT during boot to get the boot selection screen.

Choose "rescue mode"

After logging in, copy the Nvidia installer to your home folder.
```
cp /media/$nameofusb/Nvidia* /home/$username
```

make sure that gdm is switched off:

```
sudo service gdm stop
```

and start the installer

```
./Nvidia*
```

---

### Post by dino99 on 2011-08-28
try with purging compiz* then reinstall

---

### Post by waylow on 2011-08-28
Thank you

I couldn't install the driver from the usb but I did manage to get the classic version working again through the "failsafeX" mode


I know am having the same issue as I did a few days ago getting unity and the Nvidia driver activated
(it's activated but not currently in use)


I can't remember how I solved that but I know it's possible because I had it working before


at least I have a working system again

---

### Post by waylow on 2011-08-28
all working now

I deleted all my nvidia, compiz and unity packages from synaptic

then I restarted into classic mode and installed the nvidia drivers (additional drivers)
rebooted into classic mode again
set the nvidia drivers with the nvidia-settings tool
installed unity packages from synaptic
rebooted into ubuntu (with unity)


:)

---

