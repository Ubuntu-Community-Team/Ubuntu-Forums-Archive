---
title: "Screen tearing is Back"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-10-06
The reason why I was quick to jump on Karmic Alpha 1 was because a developer told me the screen tearing problem was fixed. Well, that was true (w/ compiz) until the betas started coming out. I dont know what update is causing it , but screen tearing is back and is very noticeable in Flash video.

BUG REPORT : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/448711](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/448711)

---

### Post by amauk on 2009-10-06
silly question,
but have you tried enabling Sync to VBlank in compiz?
(compizconfig-settings-manager > general > display settings)

this syncs up screen refreshes with your monitor's refresh rate, and stops tearing

---

### Post by tjeremiah on 2009-10-06
> **amauk said:**
> silly question,
but have you tried enabling Sync to VBlank in compiz?
(compizconfig-settings-manager > general > display settings)

this syncs up screen refreshes with your monitor's refresh rate, and stops tearing

no. I was told to take it off because when a notification would pop up, my screen would blink until the notification is gone. But ill enable it again to see what happens.

---

### Post by tjeremiah on 2009-10-06
nope, that doesnt work.

---

### Post by pentry on 2009-10-06
I've noticed tearing as well. Especially in flash video. Seems we're back to square one...

---

### Post by exploder on 2009-10-06
Seems to be a lot of issues with graphics lately...:(

---

### Post by tjeremiah on 2009-10-06
hopefully it improves :? But its kinda strange that in an Alpha, things were better than in a beta :? I just hope it gets resolved or I gotta boot up windows for presentations,etc again :(

---

### Post by tjeremiah on 2009-10-07
does anyone know the code to enter to create a bug report for the information related to screen tearing, to appear?

---

### Post by Technoviking on 2009-10-07
> **tjeremiah said:**
> does anyone know the code to enter to create a bug report for the information related to screen tearing, to appear?

```
ubuntu-bug -p xorg
```

Is probably the best place to start.

[https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting)

T-V

---

### Post by VMC on 2009-10-07
> **tjeremiah said:**
> The reason why I was quick to jump on Karmic Alpha 1 was because a developer told me the screen tearing problem was fixed. Well, that was true (w/ compiz) until the betas started coming out. I dont know what update is causing it , but screen tearing is back and is very noticeable in Flash video.

I notice you have in Intel video chip. What kernel & Intel driver do you have installed?
 When I installed kernel-12 and Intel-2.9.0 all was fixed for my i865 video chip.

---

### Post by tjeremiah on 2009-10-07
> **VMC said:**
> I notice you have in Intel video chip. What kernel & Intel driver do you have installed?
 When I installed kernel-12 and Intel-2.9.0 all was fixed for my i865 video chip.

the newest kernel, I believe its 12. And idk what current driver I have. I dont even know how to update the driver in Ubuntu :(

---

### Post by Sashin on 2009-10-07
What is screen tearing?

---

### Post by tjeremiah on 2009-10-07
> **Sashin said:**
> What is screen tearing?
when a video is displayed on the screen and has constant misplacement of an image, almost like its broken,torn.

---

### Post by VMC on 2009-10-07
> **tjeremiah said:**
> the newest kernel, I believe its 12. And idk what current driver I have. I dont even know how to update the driver in Ubuntu :(

This will give what kernel version & what Intel version:
```
uname -r&&aptitude show xserver-xorg-video-intel|grep Ver
```

---

### Post by Choad on 2009-10-07
> **Sashin said:**
> What is screen tearing?
when the monitor's refresh rate is not the same as the graphics card's refresh rate (ie they are not synchronised) sometimes the monitor gets updated with part of the new frame overlaying the old frame, causing moving things on the display to appear "torn". moving a window side to side rapidly is the best way to notice this effect.

---

### Post by tjeremiah on 2009-10-07
> **VMC said:**
> This will give what kernel version & what Intel version:
```
uname -r&&aptitude show xserver-xorg-video-intel|grep Ver
```

this is what I get back:
```
~$ uname -r&&aptitude show xserver-xorg-video-intel|grep Ver
2.6.31-12-generic
Version: 2:2.8.1-1ubuntu3

```

---

### Post by tjeremiah on 2009-10-07
ok, i fount the updates for the graphic card but having trouble installing it. Its a tar.bz2 file

---

### Post by VMC on 2009-10-07
> **tjeremiah said:**
> ok, i fount the updates for the graphic card but having trouble installing it. Its a tar.bz2 file

You have 2.8.1 installed. Try installing 2.9.0. It made all the difference for me. Using 2.8.1 made my system unbearably slow and weak.

deb file found [here]("http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.9.0-1_i386.deb").

---

### Post by tjeremiah on 2009-10-07
> **VMC said:**
> You have 2.8.1 installed. Try installing 2.9.0. It made all the difference for me. Using 2.8.1 made my system unbearably slow and weak.

yea, but im having trouble installing it. [http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)

---

### Post by VMC on 2009-10-07
> **tjeremiah said:**
> yea, but im having trouble installing it. [http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)

That bz2 file is the source, you want the deb file. Look at my post #18.

---

### Post by tjeremiah on 2009-10-07
> **VMC said:**
> That bz2 file is the source, you want the deb file. Look at my post #18.

:( thanks, i didnt even see the link the first time :(

EDIT : saids : Error: Wrong architecture 'i386'

---

### Post by tjeremiah on 2009-10-07
I get an error :     Error: Wrong architecture 'i386'

---

### Post by VMC on 2009-10-07
> **tjeremiah said:**
> I get an error :     Error: Wrong architecture 'i386'

Ok then. Go [**_here_**]("http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.9.0-1_amd64.deb") for amd64

---

### Post by tjeremiah on 2009-10-07
> **VMC said:**
> Ok then. Go [**_here_**]("http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.9.0-1_amd64.deb") for amd64

thanks :) . I actually figured it out. At the end of the link, i just changed it to amd64.

---

### Post by tjeremiah on 2009-10-07
alright, things installed just fine. now im gonna reset and look for a fast motion video to really test it out. Anyway, thanks.

---

### Post by tjeremiah on 2009-10-07
well it doesnt work. its actually worst with the driver update.

---

### Post by tjeremiah on 2009-10-11
BUG REPORTED : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/448711](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/448711)

---

