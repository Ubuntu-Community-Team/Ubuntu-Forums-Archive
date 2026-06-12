---
title: "Preparing for an Upgrade/Fresh Install"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by noremac on 2008-04-23
I am about ready to go ahead and upgrade to 8.04 from 7.10, however I have some questions. I would like to keep most of the configurations I already have and know this can be done by keeping my /home folder on a separate partition, but I did not know about this when I installed 7.10 many months ago. I also know I could move it now, but is it worth the hassle? I mean, I know it would be handy to start up the computer and it be ready to go, but would a fresh install be pretty nice too?

I guess I am most concerned with the stuff that I don't think will transfer over with my /home folder. I have a TV Tuner card that I had to work on to make work. I don't remember the steps to getting it to work really. I suspect I could find it all again though. But along with that, I remember my dual monitor setup being a real pain and nuisance to get going. A 17" and 20" widescreen. Should I simply save my xorg.conf file and paste it into my new one if I do a fresh install?

I am sort of lost and not sure which way to go, upgrade or reinstall. Recently, my current install has been iffy. Gnome won't load, frequently is freezing up when I come back from a screen saver. So it sounds like a reinstall would be best. Would any of these freezing issues follow me if I were to use the same /home folder in my new install?

Just would like someone to agree with me and say I can trust myself to make it close to perfect again once I do reinstall...

Thanks for any help and insight.

-Cameron

---

### Post by ad_267 on 2008-04-23
The improved hardware support in Hardy should make it easier to set those things up so I think you won't have any major difficulty. Depending on how big your home folder is you could back it up on multiple cds or dvds.
Also I think that with hardy the way x is configured is slightly different. It is supposed to be a lot simpler and more automated so I'm not sure if backing up the xorg.conf file will work, but it could be worth a shot.

---

### Post by noremac on 2008-04-23
I have a 64 bit processor. So I should be able to use the 64bit version. However I am currently running the 32 bit version of 7.10 as I downloaded the wrong one and didn't know about it till I had installed and simply didn't worry about it. I want to make sure that if I use the 64bit version I at least won't lose any compatibility. 

I am told most programs will then have to run under emulation and may make them slower. Along with some Driver Support might be not as good. Is that true and how much will it effect the system, if there is really even an answer to that.

---

### Post by Pumalite on 2008-04-23
Do a clean install with the 64 bit iso.

---

### Post by noremac on 2008-04-23
> **Pumalite said:**
> Do a clean install with the 64 bit iso.

Should I even worry about the /home folder? Or just start over there as well? 

I will likely just make a new one, but this time on a separate partition.

-C

---

### Post by Pumalite on 2008-04-23
Do a straight clean install. Later, you can do this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by noremac on 2008-04-23
Another question:

How *should* Grub work with this reinstall? Right now it is a dual boot machine with Windows XP. When I install 8.04 over 7.10, will Grub boot menu figure it out and replace 7.10 with 8.04?

---

### Post by ptcbus on 2008-04-24
I upgraded from 7.10 to 8.04 and had no problems. See the steps I followed here: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by qpieus on 2008-04-24
> **noremac said:**
> Another question:

How *should* Grub work with this reinstall? Right now it is a dual boot machine with Windows XP. When I install 8.04 over 7.10, will Grub boot menu figure it out and replace 7.10 with 8.04?
Yes, if you install over 7.10 (meaning you install 8.04 to the same partition 7.10 is on) grub will (should) figure that out and also still see the windows installation. I did this recently with a fresh install of 7.10 over an existing 7.10 and the grub menu was correct afterwards - it had the new 7.10 and the pre-existing xp install. This should work with either a fresh install or an upgrade. Even if grub messes up and the menu is not exactly right, it's really easy to fix that.

---

### Post by noremac on 2008-04-24
> **Pumalite said:**
> Do a straight clean install. Later, you can do this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Might I ask why I should wait till after I install it to do the transfer? Will it be a little simpler or something compared to when installing the OS? Not trying to be a nuisance though.

Thanks qpieus for your help on that. Makes me feel better about the installation process.

---

### Post by noremac on 2008-04-27
Also, before I do the reinstall (waiting for a day off work so I can pay attention strictly to the installation) is there a way to accumulate a list of all the programs I have installed? Making it easier to get it all back once I do the reinstallation...

Thanks for the help,

-Cameron

---

### Post by noremac on 2008-04-29
Well I did the reinstallation last night and everything went really well. I was really happy with it. 

Problem I am having right now is that Firefox is having some bad memory usages. I upgraded to a FF3 beta before I left the world of 7.10 and the usage wasnt too bad. My conky always reported it at, or very near 10% (I have 1GB RAM). Now though, its reporting at 15% or more with only 2 tabs open. Thats rather pathetic. Also Gmail inbox is very sluggish in scrolling. Is this a known issue?

-C

---

