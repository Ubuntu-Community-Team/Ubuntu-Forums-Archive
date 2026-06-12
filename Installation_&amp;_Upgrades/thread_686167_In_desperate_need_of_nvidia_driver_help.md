---
title: "In desperate need of nvidia driver help"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by gamergonelinux on 2008-02-02
Helo all, after some deep though, I decided I wanted to steer away from windows for moral reasons (mostly because I was disgusted that microsoft, yahoo, and cisco would sell technology to china to help them spy on their residents). I though "okay, so I'd like to be able to do everything in ubuntu that I do in windows". That involves a lot of gaming, a ton of multimedia, and other home uses. I got to work and installed Wine and had steam going. Well I use 2x7900gt cards in SLI, and I didn't realize that sli was supported under linux. Well needless to say I tried to update my drivers. I tried running the "sh" install command on the .run file in the console (the alt+ctrl+f1), and I've tried using the synaptic package manager, as well as the apt-get. I've reconfigured the Xserver xorg.conf many times, and I've tried to run nvidia-settings (each time it tells me to run the configuration for xorg or something like that).

I've reinstalled 3 times now... It's getting ridiculous. I tried using the default forceware that you're told is proprietary, and asked to enable. that works, but it's older so i wanted to update to the 169.09 forceware. Well now I uninstalled nvidia-glx-new, and then reinstalled using the hardware manager (I forget the actual name, and can't access it right now). Each and every time I'd try to install or fix or regenerate the xorg.conf file it'd start up, and say that it needs to run in low video mode. Well after this last time using the synaptic package manager to auto install it didn't. I got all excited and typed in my password and username, but it doesn't get past the login. the screen flashes black with a few brownish boxes and then goes back to the login. What could I possibly do now?
Thanks

I just reran the sudo dpkg-reconfigure xserver-xorg command in recovery mode. I can now get back in, but it's at the like 800*600.
Also, when it says it's going into low video mode I tell it to go at 12*10 but it goes to 8*6 anyway. At the same time, it always reads my first gfx card (they're both MSI NX7900GT cards) as something different.

Oh and after further research, maybe it's the resolution mode /refresh rate of my desktop messing up my logins? I'll try the fix for this now.

---

### Post by gamergonelinux on 2008-02-04
just a bit of a bump. I fixed my driver graphical problems (well mostly, there's still some tearing when using the cube compz effect), but now I get a wine "audio test failed" and there's no sound. I've updated to the latest, and I've tried using the esound driver. Also, I have the realtek onboard audio on my Abit NF4 based motherboard.

---

### Post by Odrodzona-Sarmacja on 2008-02-04
Audio test doesn't work currently in wine, so just choose alsa as your sound driver. If you have any problems with getting sound at all you can choose oss driver, but from my experience it gives nasty crashes.

---

### Post by gamergonelinux on 2008-02-05
> **Odrodzona-Sarmacja said:**
> Audio test doesn't work currently in wine, so just choose alsa as your sound driver. If you have any problems with getting sound at all you can choose oss driver, but from my experience it gives nasty crashes.

well sometimes when I restart it works, but not always. Also, out of the ~5 times I've played CS:S the sound worked once, and it was laggy (which is acceptable, but I'd prefer to fix that too). Also, my drivers aren't exactly fixed either. When I switch between desktops, the old desktop appears over it, or a frame from when it was turning between them. I have the newest compiz and have the cube enabled. I can get rid of the old frame by cursing over it or moving a window there, but it's rather irritating... Any ideas as to what's wrong?

---

### Post by alexandreracine on 2008-02-05
Did you tryed Envy?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It's a simple application that will install the lateast nvidia or ati drivers and configure X.

---

### Post by gamergonelinux on 2008-02-05
no I haven't, I'll give that a try after I finish installing the set of apps I just added.

---

### Post by fizur2002 on 2008-02-05
i was having the same problem installing the nvidia drivers, not sure how to tell if Envy did it correctly as im totally new to using linux.

---

### Post by gamergonelinux on 2008-02-05
well I got them installed correctly I just have graphical problems with compiz now... I think I'll make a thread in the desktop addon forum. I started a thread with what I believe is the right forum. I've added screenshots in that one.
[http://ubuntuforums.org/showthread.php?t=688850](http://ubuntuforums.org/showthread.php?t=688850)

---

### Post by gamergonelinux on 2008-02-05
> **fizur2002 said:**
> i was having the same problem installing the nvidia drivers, not sure how to tell if Envy did it correctly as im totally new to using linux.

type nvidia-settings in the terminal
and see what pops up.

---

