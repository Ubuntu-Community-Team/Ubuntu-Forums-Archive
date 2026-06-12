---
title: "[SOLVED] can not enable restricted driver, i get following error"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Hoaxe on 2007-10-21
hi, I have a Nvidia GeForce FX 5200. I get the following error when trying to enable the restricted driver.

```

E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

```

I had some bumps during the upgrade from fiesty to gutsy. 2 actually. one involved my graphics card. the result is that the restricted driver is rubbish as far as I'm concerned. I had to disable it to get proper resolutions. I am now using NV open drivers.

I also get the error when trying to download both nvidia-glx and nvidia-glx-new from the repo.

this is probably related to the bump I had during my install but it does not help me fix my problem. Although I was able to figure out that the restricted driver was the problem, it is only as far as I can get.

any help or pointing in the right direction is always appreciated.
thanks.

---

### Post by linfidel on 2007-10-21
> **Hoaxe said:**
> hi, I have a Nvidia GeForce FX 5200. I get the following error when trying to enable the restricted driver.

```

E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

```

I had some bumps during the upgrade from fiesty to gutsy. 2 actually. one involved my graphics card. the result is that the restricted driver is rubbish as far as I'm concerned. I had to disable it to get proper resolutions. I am now using NV open drivers.

I also get the error when trying to download both nvidia-glx and nvidia-glx-new from the repo.

this is probably related to the bump I had during my install but it does not help me fix my problem. Although I was able to figure out that the restricted driver was the problem, it is only as far as I can get.

any help or pointing in the right direction is always appreciated.
thanks.I also have the FX-5200, and had a similar problem.  I had used Envy to upgrade Feisty, and forgot.  I think it messed up my upgrade, and I tried every combination of tips, intuition, and repeated random choices.  It looked like the restricted driver would not work with my card.  

Finally, I decided I didn't have anything I couldn't replace, so I backed up the configs I knew I had modified (unnecessarily, it turned out), and booted up the Gutsy CD - using the alternate CD with the text install, if that matters.

I chose my former root partition to be named "/", and kept my swap drive and home directory.  I picked the same login name, and reinstalled.

After that, I booted up and my old desktop came up at full resolution.  I enabled the restricted driver, and it worked.  I enabled full effects and it works perfectly.

My profile was still used, so I had Firefox running, same startup apps, etc.

Perhaps I would have eventually found out what was wrong, but there is just too much misinformation and noise for me to waste so much time.  You'll have to decide for yourself if this might work for you.  Hope my experience helps.

---

### Post by Hoaxe on 2007-10-22
i also used envy when i was fiesty. 

huh, sucks to be us...

anyways, it's a good solution since all the data stays the same. 

i can wait a bit for a proper fix. but i hear you on the noise and misinformation, it's hard to know with the update being only a few days old now. lot's of people have problems. we'll see about this one.

thanks for the tip, if nothing shows up for a fix i'll be using this to do it.

---

### Post by solinent on 2007-10-23
This is hardly solved.  Anyone who used envy is now royally screwed :)

I'm getting the same errors.

I'm going to keep experimenting though.

---

### Post by solinent on 2007-10-23
WOW, that was quick:

solution, run these commands:

```

sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/xorg/modules/libGLcore.so

```

Only do this if you don't have nvidia-glx and nvidia-glx-new installed.  After I ran those it installed :)

---

### Post by linfidel on 2007-10-27
> **solinent said:**
> WOW, that was quick:

solution, run these commands:

```

sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/xorg/modules/libGLcore.so

```

Only do this if you don't have nvidia-glx and nvidia-glx-new installed.  After I ran those it installed :)Cool!  How did you figure that out?  Did it come to you in a dream? :)

My solutions usually pop up on my computer screen as a message from God.


... or maybe a forum response; I forget.

---

