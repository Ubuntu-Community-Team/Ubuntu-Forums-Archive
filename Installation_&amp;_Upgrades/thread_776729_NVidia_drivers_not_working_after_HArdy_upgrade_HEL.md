---
title: "NVidia drivers not working after HArdy upgrade HELP PLEASE"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Zaff on 2008-04-30
HI all,
I've tried a lot of things and it's really getting to me but after I upgraded the nvidia driver wouldn't work anymore. I had to use vesa and the max resolution 800x600. So I've tried several solutions posted on the forum, envyng, installing manually all that. The best I achieve is to get a working nvidia-install with 640x480 resolution. 
If I uninstall the drivers completely I get back to vesa and I can use 800x600 again.
Now I have a GeForce 7600 GS and it used to work FINE !
What's going on and how do I fix it ?

---

### Post by vexorian on 2008-04-30
During my hardy migration I noticed something messed up xorg.conf even though it was correctly using an nvidia driver the screen itself was not recognized correctly and was giving it such bad limit. So my solution was that I luckily had a correct old xorg.conf file and I updated the screen section , perhaps if you notified us what resolution you want someone can help you with an improved version of your xorg.conf file...

---

### Post by Zaff on 2008-05-02
Thanks I just went into the xorg.conf and I found that setting the resolution I wanted (1280x1024) manually instead of the 640x480 actually solved the problem. Any reason why it couldn't be done automatically ? I'm not complaining, Playing around with conf files can be fun but I just think to the averge user this can be a big pain...

---

### Post by vexorian on 2008-05-02
> **Zaff said:**
> Thanks I just went into the xorg.conf and I found that setting the resolution I wanted (1280x1024) manually instead of the 640x480 actually solved the problem. Any reason why it couldn't be done automatically ? I'm not complaining, Playing around with conf files can be fun but I just think to the averge user this can be a big pain...
No idea what's wrong, but many people have reported problems whatsoever similar to this one, I experienced it as well.

---

### Post by dedlycow on 2008-06-22
yeah I agree I am having lots of difficulty trying to get a 7600gs working as well. It worked fine until I did an upgrade last week. at the moment I have 600x800 I try to install the driver through hardware drivers.I do restart as directed and it gone when it restarts. and suprise! It does'nt get better after doing it ten time. (just faster) any help would be good thank you
david

---

### Post by Zaff on 2008-06-23
So I got it to work by downloading the NVIDIA beta driver here (check if this is right for you) : [http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html). 
Then log off and hit Ctrl + F1 to open a text terminal. Log on and type : 

```
sudo /etc/init.d/gdm stop
```

you may need to kill the Xserver as well but that should be enough though.
then run the NVIDIA-Linux-x86-173.08.pkg1.run as root from the directory you saved it in :

```
sudo ./NVIDIA-Linux-x86-173.08.pkg1.run
```

and follow the instructions (they're fairly self explanaitory). I was told to not download a kernel module but to compile it from the program and this has worked well so far. This will install the driver and modules.
Use nvidia-xconfig to generate a new xorg.conf file :

```
sudo nvidia-xconfig
```

You will need to tweak your Xorg to give it the resolution you want. Can't remember the conf lines exactly but basically where you see 800x600 replace it by your resolution. Then restart gdm and it should work.

Finally my advice : backup your xorg.conf somewhere because I've had to do this everytime there's been a kernel update (and there has been many lately...) . don't delete the NVIDIA.run file either other wise you'll just have to download it again. Next time you can just relaunche the NVIDIA installer and then copy your backed-up xorg file back into /etc/X11/.

Hope this helps.

It's a bit of a pain to do it at each kernel update but it'll only take a few minutes if you've backed up your xorg and the NVIDIa file.

---

### Post by sdennie on 2008-06-23
You can set it up so the nvidia driver automatically updates for new kernels when they are installed: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

