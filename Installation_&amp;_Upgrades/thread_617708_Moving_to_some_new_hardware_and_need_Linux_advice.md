---
title: "Moving to some new hardware and need Linux advice"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by Hopworks on 2007-11-19
Within the next 2 to 3 weeks, I'll be moving my hardware around. I'm building a Core 2 Duo machine, so my P4 3GHz hardware gets moved down the line. My C2D machine will be (reluctantly) my winblows machine (I blame Blizzard's World of Warcraft), my current winblows machine (the P4 3GHz) becomes my Linux box. My old linux box goes to my daughter, hers goes to my wife, etc. etc. etc.

This should help the performance of my Linux machine and its role in my house quite a bit, since it is jumping up from an Athlon XP 2600+ to the P4 3GHz Prescott.

What I'd like to know is, is it at all possible for me to keep all the newbie work I did learning linux and use that on my new machine? This didn't matter a few months ago, but I spent an amazing amount of time configuring my Apache server, well, my LAMP all together, my MythTV, my desktop, Samba for file sharing with my notebook, Hellanzb, my file systems,  etc. etc.

I didn't keep very good notes, and if I have to do it all again, I can with much difficulty, but since Ubuntu has been such a great answer to my limitations with winblows, I thought maybe there was something I can do to at least preserve some of the 'essence' of my current configuration.

After all, it runs so good, and serves me well. Just want to give it some new hardware to do better.

Thanks for your time!

Hop

---

### Post by reckless2k2 on 2007-11-19
ok i'm very confused by your post. i think you are asking how to preserve everything you did on a computer you are offloading to someone else on a new machine. if i understand that correctly, you can tar your whole filesystem, install the same distro on the new system, then untar it on the new system. then you will have everything. 

someone chime in but i think that's what you're talking about and what you need to do.

---

### Post by mellowd on 2007-11-19
That's pretty much right. Do a full system backup using tar. Reinstall again and ensure your partitions match. then untar your backup, restart and everything will be back

---

### Post by Hopworks on 2007-11-19
> **reckless2k2 said:**
> ok i'm very confused by your post. i think you are asking how to preserve everything you did on a computer you are offloading to someone else on a new machine. if i understand that correctly, you can tar your whole filesystem, install the same distro on the new system, then untar it on the new system. then you will have everything. 

someone chime in but i think that's what you're talking about and what you need to do.

Sorry I didn't clarify, and no, not offloading the Linux stuff on someone else. I'm moving my Linux machine to my daughter, wiping it and installing Windows for her. I want to move my work to my current Windows machine, because it is being replaced by the core 2 duo.

So if it is that easy, I'm so relieved! What I was worried about was device drivers, and just about everything that matters concerning some radically different hardware.

And is it really just that easy? My god. Why did I stick with windows for so long???

Hop

---

### Post by Pumalite on 2007-11-19
I'll be interested in knowing if the old installation works with new hardware.

---

### Post by Hopworks on 2007-11-19
> **Pumalite said:**
> I'll be interested in knowing if the old installation works with new hardware.

I'm thinking it won't, but I'm hoping that the important configuration stuff concerning my LAMP and MythTV will work. I mean, after all, those systems are not device specific.

Hop

---

### Post by mellowd on 2007-11-19
> **Hopworks said:**
> I'm thinking it won't, but I'm hoping that the important configuration stuff concerning my LAMP and MythTV will work. I mean, after all, those systems are not device specific.

Hop

Your configs will transfer as remember all configs in linux are just plain text files :)

---

### Post by reckless2k2 on 2007-11-20
To Pumalite's post,
I know you're ninja and all with linux but i have successfully moved from hardware to hardware with hard drive installs with little issue because the the nature being such that many drivers are built into the kernel.  Hence the reason that linux is so much better in that respect than windows. I've moved hard drives from P3 to P4 or from 32MB vram to 256MB vram with no issue. I've drastically changed hardware with little or no issue. Even using the tar method. 

all that said, it may blow up. hahaha. have fun. haha.

---

### Post by Pumalite on 2007-11-20
No ninja here. I've had success sometimes, but most time it doesn't work, even though the kernel is supposed to load the modules according to the hardware  it faces. I congratulate you on your good luck.

---

### Post by Hopworks on 2007-11-21
I'll post my results when I do it. Since I have a few weeks until the move to the Pentium 4 Prescott, I could use that time to zero in on key configurations on my current LAMP setup, and practice with a second drive installing and moving those key files. I kind of plowed on through all of it and I'm sure I have forgotten some key challenges I had to overcome to get to where I am now.

But seeing what worked and didn't is good information, so I'll try to take very detailed notes, and post here if everyone doesn't mind. It's all part of me 'becoming' in the Linux world, a place I am really in love with now.

Also, since I'm doing all these changes, reinstalling OS's for the kids, my wife, I was seriously thinking of installing Ubuntu on my wife's new build. She frowns at it, but I assured her that it will offer her everything Winblows can, and is much more efficient and stable. We'll see there, but I had another sinister thought...

Since my Daughter (16) likes to try to get us into trouble with file sharing, viruses via unsafe surfing, I was thinking of playing a nasty trick on her, and dual-booting Linux on her new build as well. I'll see if I can get it to boot Linux just the first time, and be ready with my camera to capture the shock on her face. :D

She's an iPod fan though, iTunes, and with her, it's all about the "i" and not just related to the apple hardware. The moment she wants to do something I have to dig through google to research and get working with Ubuntu, her Linux experiences will be done, over and out. hahahaha

Afterthought: Just trying to secure a Windows XP install to protect the OS from a surfer-witch like our daughter is a certification all in its own. No matter what I do, limit her account, anti-virus, hardware firewall filters, etc. She finds a way to hose the OS. Even GROUNDING her is no answer.

Happy Thanksgiving everyone!

Hop

---

### Post by Hopworks on 2007-12-05
Alright, I have my Core 2 Duo up and running, which means my Linux box will be getting a much-needed boost via hardware this weekend. Currently Athlon 2600+, will be a P4 Prescott 3GHz, and from 2gb, to 4gb RAM.

Now I'm wondering, would it be better to backup all my settings, then reinstall Ubuntu Feisty Server and move all that config stuff over to get my machine to where it is now with the Athlon hardware? Then upgrade to Gutsy? Or should I just reinstall Gutsy, and then move all those config files over.

The current Feisty install has some issues I'd like to get rid of, like my HellaNZB is older, and I can't seem to remove it, and I'm having trouble using SSL with my usenet server. I haven't tried stunnel yet on Linux, but did on windows and it works with NZB-OMatic-Plus. I'd rather do it fresh with the latest version. I also have a weird thing with my mouse, where I can scroll through a web page with the wheel ONLY when the mouse pointer is over the scrollbar.

I'm just worried that my config files will be incompatible with gutsy, and thought that if I got a solid Feisty server working, just clicking the upgrade button will take my current configuration into account and do the hard work for me.

Sorry for the late bump, and long-winded plea for help. I just want to do the right thing, and not have to go over a mountain of research to get back to where I am now just to get some extra power from my hardware.

I hope that all made sense. =)

Hop

---

### Post by Pumalite on 2007-12-05
If you must have Gutsy, save data and /home and do a clean install.

---

### Post by Hopworks on 2007-12-05
> **Pumalite said:**
> If you must have Gutsy, save data and /home and do a clean install.
I love your signature by the way!

I'm thinking that all the work I did getting my LAMP correct is worth the expenditure of buying a big drive and copying all that over, so I can get access to it if needed. The Seagate ST3300622AS-RK 300GB 7200 RPM SATA 3.0Gb/s Hard Drive on newegg.com is $70, so I can access whatever I need from my current install and put those config files back if that will work.

I really don't need Gutsy maybe, but more like a clean install of Feisty. Not sure. I have some hoops to jump through, because the new video card I'll be using is an AGP 512mb Radeon, 1650 pro. The card I was using was an nVidia.

It's just that I spent so much time getting to know Webmin, MySQL, PHP, Apache, Samba, TightVNC, HellaNZB, MythTV. I would hate to lose all those achievements on a new install and have to do all that over again. I've been searching here and on google, and haven't found anything definitive on what to back up that is truely all-encompassing related to what you have set up on my Feisty install of Ubuntu.

Many of the tutorials and guides I read about what I'm doing point to different paths than what I have installed, so I guess that is what I have worrying me.

One instance of that is the delay logging in via Putty from a windows machine, after the username, and then waiting 6-10 seconds for the asking of a password. I pained through months of that until I finally got a solution. Now, I have no idea what I did to fix it. A new install, I'll have to do all that crap again, and that sucks. lol

Hop

---

### Post by Pumalite on 2007-12-05
Hello Hop:
Glad you liked it.
I think your are right. I believe that if one has a system that works and one likes, there is no need to upgrade.

---

