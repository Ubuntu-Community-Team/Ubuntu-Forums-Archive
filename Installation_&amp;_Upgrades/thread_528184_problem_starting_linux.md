---
title: "problem starting linux"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Irti on 2007-08-17
hey......i am a beginner using linux.....i installed it a couple of months back....then i went for hols for around a month...when i came back and started up my system.....the nvidea drivers for linux werent workin and the whole gnome interface is gone...i mean there is no graphical interface....it just gives a message of nvidea not workin and shows up with the command prompt....the funny thing is that vista is still running smoothly and so are the nvidea drivers for vista...............i have a dual boot system with ubuntu fiesty and vista.....1 gb ram ...a dual core 2 64 bit amd processor....and a 512mb nvidea graphics card....please help

---

### Post by Pumalite on 2007-08-17
Re-install your driver.

---

### Post by dabl on 2007-08-17
Well, maybe

```
sudo apt-get install nvidia-glx-new
```

?

---

### Post by Irti on 2007-08-17
ya the problem is that i will be getting net at my place next month...isnt there some way i can get the old nvidea drivers to work.....the nvidea cd i have works only with xp.....

---

### Post by Pumalite on 2007-08-17
Do you have proprietary driver safely tucked away in your /home folder?

---

### Post by Irti on 2007-08-17
ok......how do i check if i do....i think i should have a propriety driver......how do i run it again???

---

### Post by merlinus on 2007-08-17
If you cannot find the linux drivers for your card, perhaps vesa will get you up-and-running for now.

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

-merlin

---

### Post by Irti on 2007-08-17
thanx gonna try it out as soon as i get home.....

---

