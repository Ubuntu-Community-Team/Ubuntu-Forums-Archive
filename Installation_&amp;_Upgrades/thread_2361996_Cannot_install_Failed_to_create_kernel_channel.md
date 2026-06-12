---
title: "Cannot install: Failed to create kernel channel"
date: 2017-05-23
forum: Installation &amp; Upgrades
---

### Post by black.8 on 2017-05-23
This is what is displayed before the install gets to the desktop. 
 
[ 3.594907] nouveau 0000:01:00.0: priv: HUB0: 00d054 00000007 (1b408216)
[ 37.59239] nouveau 0000:01:00.0: DRM: failed to create kernel channel, -22

I am trying to install 16.04.2 LTS on the following hardware:
Motherboard: GA-Z270X-Ultra Gaming (rev. 1.0)
Graphics Card: Gigabyte GeForce GTX 1070 G1 Gaming 8G
CPU: Intel i5-7600k 
I have tried installing under [FONT=Ubuntu][COLOR=#111111]UEFI settings in BIOS as well as fast boot off. [/COLOR][/FONT]
[FONT=Ubuntu][COLOR=#111111]The installation process will get to the desktop and I can start the install but it will not get past the prepare to install Ubuntu.  [/COLOR][/FONT]
[FONT=Ubuntu][COLOR=#111111]Also, I normally run two monitors but when I have both of them connected to the graphics card the install process will go to the black screen. This does not happen when I only have one connected. I am not sure if this is helpful but I thought I would mention it.  [/COLOR][/FONT]

---

### Post by cooper.pilot on 2017-06-14
I created an account just to answer this question because I had the same problem, and also solved it.
It's been a while since you posted this thread so idk if you've solved it, so I'm mostly just posting this for other people with the same problem.

All I did to fix mine was unplug my gpus and it ran normally.

Specifically, I was trying to install Ubuntu 16.04.2 onto a msi Z170A M5 with 2x GTX 1070.

I hope this saves someone the frustration it caused me!

---

### Post by sloganq89 on 2017-06-15
I'm having that problem right now, I also have 2xGTX-1070's and a Gigabyte Z270X-UD3 motherboard.

How did you install unbuntu, or view your screen, with both gpu's unplugged?

---

### Post by thesquatch on 2017-07-16
I still need help please.

If I unplug/disconnect one of my video cards from my motherboard everything works fine. Install, doing stuff, etc, no problems at all.
I would like to have both my cards in SLI and plugged in to my motherboard so I can use all 8 of my screens for work.

Microsoft can burn in hell because of all the BS they are pulling with all there newer software. Ubuntu runs better all together anyway.
I have always wanted to use Linux for everything anyway just don't know how to use it, but now I am going all in if I can get SLI and RAID 0 running. (See Note below if you think I'm crazy using RAID 0.)

This is what I see when I plug in my second video card weather I use the SLI bridge or not.
[ATTACH=CONFIG]276024[/ATTACH]


Side note for all the people that think RAID 0 is tarded and a bad idea.
I run RAID 0 on my main drives where I install my OS. I get it completely setup how I want and then clone it on to spare drive that sits on the shelf.
Then I have a second set of RAID 0 drives that holds all my data and where everything I need to keep is saved,
Now I know everyone thinks I'm crazy. (Two sets of RAID 0!!! This guys an idiot!!!)
What you don't know yet is that everything on my second RAID 0 drive is backed up. When a file is added, updated, or changed in anyway it is transfered to two other storage locations immediately.
So between my cloned OS and my dual backup on my secondary drive I am safe.

---

