---
title: "Xubuntu with only 126mb ram"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Sega dude on 2011-05-12
I am attempting to install Xubuntu via Wubi on an old HP e-Vectra PC. It only has 126mb of ram. Wubi installed successfully but when I get to the part where you finish the installation after you restart I get a black screen after the wubi 11.04 screen. I really don't want to upgrade the ram in this computer If I don't have to due to the difficulty of doing so.  Is there any way I can get it to work?

---

### Post by kerry_s on 2011-05-12
lol, 126mb of ram, it's probably still trying to load, how long did you wait? :D

that really is not enough ram for a modern linux.

---

### Post by ACMarina on 2011-05-12
When you get to your "Wubi 11.04" screen, have you tried to see if you can start with limited graphics or something?  I've installed on dozens of computers with more limited hardware than what you've got, and I sincerely doubt ram is your issue.  Graphics wouldn't be too much (I wouldn't think) but you may have to iron out some glitches.

When the screen goes blank, do you notice any hard drive activity or anything?

Edit to add - Kerry, I'm assuming that the OP knew that he was dealing with limited hardware and thus went with Xubuntu for that purpose.  Just to see what would happen I installed Xubuntu 10.10 on a Pentium 233 with 32 MB of Ram, and it started fine.  It was a little draggy and I had to set some swap limitations out of the norm since it's not a lot for modern web browsing and such, but it would boot..

---

### Post by Sega dude on 2011-05-12
> **ACMarina said:**
> 
Kerry, I'm assuming that the OP knew that he was dealing with limited hardware and thus went with Xubuntu for that purpose. 

That is exactly it. I tried safe graphics mode and it said lots of things about being out of memory. Then after all the verbose the same thing happens. That has led me to believe that the memory is the issue. There is hard disk activity for a while after the screen turns black but it eventually dies down. When I tried safe graphics mode I notice that it failed to load fallback graphics devices or something like that.

---

### Post by snowpine on 2011-05-12
Have you tried a regular (non-wubi) install?

If that still doesn't work, maybe try Lubuntu or a "minimal" 'buntu install?
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Also worth considering are "lightweight" distros designed specifically for older hardware such as: Puppy, SliTaz, Tiny Core, AntiX, etc.

---

### Post by gmargo on 2011-05-12
Have you tried hitting ALT-F1 (or ALT-CTRL-F1) to attempt to get to a console login prompt?

If the computer is otherwise running but just the graphical part is not working, you may see a black screen and no login prompt.  (I usually see this after installing a command-line-only system.)

---

### Post by abohsin on 2011-05-12
126MB RAM, and you really expect the interface to load and graphics to work? LOL, try the command line as expressed by the audience, if it works fine, then probably you are out of memory before you start!

---

### Post by bcbc on 2011-05-12
The installer requires 256MB ram. You need the alternate installer (which does not support wubi installs). And even then you probably will have issues running  it.

From: [http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)
> Minimum system requirements
You need 256 MB RAM to run the Live CD or 256 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.

To install Xubuntu, you need 2.0 GB of free space on your hard disk.

Once installed, Xubuntu can run with starting from 256 (or even just 192) MB RAM, but it is strongly recommended to have at least 512 MB RAM.

---

### Post by Sega dude on 2011-05-12
> **bcbc said:**
> The installer requires 256MB ram. You need the alternate installer (which does not support wubi installs). And even then you probably will have issues running  it.

From: [http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

I tried both the minimal install and alternative cd mentioned above. The minimal cd worked up until it started the partitioner. After that nothing happened.  The screen was blank. With the alternative cd I can't even get the installer to start. He is what the screen looks like when I boot the alternative cd.  

[[IMG]http://img714.imageshack.us/img714/6452/photodpc.th.jpg[/IMG]](http://imageshack.us/photo/my-images/714/photodpc.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

Pressing enter just throws the same error.

---

### Post by kerry_s on 2011-05-12
that looks like the result of a bad installer to me. that's the only time I seen that type of error.

---

### Post by wandalalakers on 2011-05-12
Try

---

### Post by Sega dude on 2011-05-12
I managed to get the alternative cd to boot by typing help at the boot prompt. I am still having trouble with the partitioner. I get this error after the partitioner starts. [[IMG]http://img15.imageshack.us/img15/4991/imagepkb.th.jpg[/IMG]](http://img15.imageshack.us/i/imagepkb.jpg/)

Pressing enter takes me to the same blank screen the minimal did.

---

### Post by NormanFLinux on 2011-05-12
You need Puppy Linux on this old beast. It just won't boot up since there won't be enough RAM to run Xubuntu and all the applications.

---

### Post by zealibib slaughter on 2011-05-12
+1 on puppy.  There is also DSL but with puppy you can activate the ubuntu repos.

---

### Post by Sega dude on 2011-05-12
> **NormanFLinux said:**
> You need Puppy Linux on this old beast. It just won't boot up since there won't be enough RAM to run Xubuntu and all the applications.

Thanks for the reccomandation. I really wanted to install xubuntu but I was watching youtube videos of Puppy linux and it looks awesome. I will be installing it tommmrow.

---

### Post by NormanFLinux on 2011-05-12
There's AntiX and Lubuntu. And Bodhi Linux and PCLOS e17, Openbox and wiimi are also worth looking at.

---

