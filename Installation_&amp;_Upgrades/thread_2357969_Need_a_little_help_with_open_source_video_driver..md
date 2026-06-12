---
title: "Need a little help with open source video driver."
date: 2017-04-08
forum: Installation &amp; Upgrades
---

### Post by mrmond on 2017-04-08
Hi all.
What I'm trying to get working is a thing called advanced lighting and reflections or Materials, the thing in games where objects reflect the light properly around them for realistic effects & shadows.
Now the problem I'm having is that I have used the fglrx driver up until ubuntu 14.04 (and variants) which worked fine until updates rendered it useless and I could only rely on the opens source driver.
It isn't so much of a problem as the open source driver DOES provide the ability for hardware reflections in things like Secondlife on 14.04. I'm not really a gamer but I use Virtual platforms quite a lot.
If I use the fglrx driver and a fresh install and don't update there's also no issue but if I want to use the latest Ubuntu or Xubuntu which I have currently installed then I have to rely on the bult in opensource driver. No AMD support for my GPU Ati Radeon 5400 with fglrx in the latest kernel or after updating 14.04.x

Here is the problem...While the open source driver allows reflections and shadows in 14.04, it doesn't work in 16.04, I'm stuck with basic shader settings which frankly, doesn't look as nice.
I don't really understand how something that works fine in an older version *stops* working in a newer build of Ubuntu. A regression ?

I'm not looking to get fglrx working in 16.04, I gave up on that, and I'd quite happily stick with 14.04 for now if the guide to get voice working at [http://wiki.secondlife.com/wiki/Voice/Linux_Sound_Settings](http://wiki.secondlife.com/wiki/Voice/Linux_Sound_Settings) still worked, but  some packages seem to have changed and even on a fresh install of Xubuntu it fails with package errors.

So, any ideas ? Is there a config setting for the Opensource driver that will get the advanced lighting to work in 16.04 ?

---

### Post by ubfan1 on 2017-04-08
I can't help with the video, but sound in second life can work in 16.04 (and I guess 14.04) by using wine and the secondlife viewer.  Of course the 64 bit Kokua viewer uses a hack that Linden Labs disapproves of, so it may go away, but since I'm running a 64 bit system, the sound just works without all the extra 32 bit packages.  Sample below, replace xxx with your username.
wine /home/xxx/.wine/drive_c/"Program Files (x86)"/SecondLifeViewer/SLVoice -ll 0 -lf /home/xxx/.secondlife/logs/ -st 5

---

