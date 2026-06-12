---
title: "Ubuntu CD won't boot!"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by willywonky on 2007-05-27
I downloaded Ubuntu 7.04 and burnt the image onto cd with nero.  It boots fine on my good computer, but when I put it into an old computer (an old pentium III) which I actually want to install it on it doens' t boot but goes straight to windows, even though I've selected the cd drive as first boot device in the cmos.  Tried booting from another linux cd but that didn't work either.  The CDROM doesn't even light up while booting, but once in windows it appears to work fine.  Ideas anyone?

---

### Post by rillip on 2007-05-27
Have a Windows install disk around? I'll bet it doesn't boot from that either.  If you've shown the disk to be good in another compute,r it sounds like your bios, despite being set to boot from CD first, isn't.  Might want to look and see if you can update it from your motherboard manufacturer's website.

---

### Post by southernman on 2007-05-27
> The CDROM doesn't even light up while booting, but once in windows it appears to work fine

You mean the cd works in windows? If so, then... 
Sounds like maybe the cdrom has crapped out on ya.

Have you tried to put the old cdrom in your newer box?
That would give us more to go on, if you tried this.

[edited] The more I read your OP, the more confusing it seems... your original post that is.

---

### Post by andreasmascher on 2007-05-27
I've got the same problem as well. The CD boots perfectly well on other computers, but not on my laptop. I checked the bios options of course, did try other boot cds (wich worked, winxp for example) and even formatted my harddrive and installed win xp on it (to get started for dual machine). But it just ignores feisty (the little bitch :p) 

I am running it by the way on a fujitsu siemens, I dont know, 2 years old regular machine, 2GHz, Standard ATI Graphic with 3D Acceleration and 1GB RAM and a Intel Processor. Dont have particular information but just to give you an Idea of the laptop. 

Any idea what I can try next? Thats like crazy! Might it be a 64bit Computer? (and how can I find out?)
By the way, did the installation many times before, running ubuntu on my computer for month now... sadly my friend can't!!!!

Thankfull for ANY kind of advice! :p please! :o

---

### Post by rillip on 2007-05-27
It's possible to just bipass the CD and do a net install.

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

I've never used this method, but in theorey it should work... best of luck if you decide to try it!

---

### Post by OzRob on 2007-05-27
Check the contents of the CD. There should be a whole bunch of files. I suspect that Nero has just burn't the ISO file to the CD which won't be recognised, and therefore is ignored during starting. Go to [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and follow those instructions, including downloading and using the burning software recommended.

---

### Post by andreasmascher on 2007-05-28
Hey people, thx for your replies, that was quick!

I checked the burned cd and found all of the files on it. I guess that nero did the job because otherwise it would have been just the iso file. Anyway, I've tried the net install once and it was fun acutally. I would even recommend it because it shows how powerful the installation is. But I'd like to show someone how easy it is to install ubuntu, like just pop the cd into your drive and get yourself a coffee sort of installation. 

\\:D/

But yeah, the online installation is definitely a very good advice and alternative way though. But maybe the CD was just corrupted somehow.

---

