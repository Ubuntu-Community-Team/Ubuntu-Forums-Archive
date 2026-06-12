---
title: "Kubuntu/Ubuntu not installing on Biostar TF 7025 - M2"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by disciple on 2007-10-06
okay, just built a new system.
Biostar TF7025-M2, X2 4000+, 2 GB PC6400.

trying to install Kubuntu 7.10, but cannot even boot into the live environment;  KDM refuses to start, even under safe graphics mode....  just spits into the command line

tried an older Edgy disc i had around, and same problem ( couldnt find Feisty disc)


i am using the onboard video, which i understand gives some trouble.. .. 

help plz :-(

---

### Post by disciple on 2007-10-06
updated the bios, but still no dice with ubuntu

my sound card was picked up in XP, tho, so that allayed one of my fears ( that audio wasn't workin... was an old install of XP)


anyway.. i found an old  OpenSuse 10.2 disc, and successfully installed..
so i'll d/l  10.3 and see where it goes from there:KS

---

### Post by JR008 on 2007-10-18
I too am wondering if theres any biostar suport in ubuntu.  I have the same board and love it but it dosnt work with ubuntu :(

If anyone could help us out that would be awsome

---

### Post by karachuonyo on 2007-10-18
> **JR008 said:**
> I too am wondering if theres any biostar suport in ubuntu.  I have the same board and love it but it dosnt work with ubuntu :(

If anyone could help us out that would be awsome

I also have an old  biostar motherboard (M7 VIZ v8)on my home computer and it works flawlessly. I have Kubuntu on it for the last 2 years and the easiest install i've ever had. Maybe the newer mobos are the ones with incompatibility issues.

---

### Post by blah37 on 2007-10-18
Hi, i thought I'd chime in here too...

I just recently built a new system with a biostar tf7050-m2.  I tried installing various versions of Ubuntu (7.04, 7.10, 32-bit, 64-bit etc.) and had a couple of show-stopping problems.  I could never get the live cd to boot, it would get to "Running local boot scripts" and hang there (I waited up to 30 min. a few times and nothing ever happened).  I finally got an install to work using the 64-bit 7.10RC alternate install disc.  However, after I got it installed, my new problem was that the wired ethernet connection was not working when it is connected to my Linkysys WRT54G Router w/ DD-WRT running as a wireless bridge.  When I ran a long cable directly to my main router, it works fine.  However, that was not an acceptable solution for me, so for now I'm using openSUSE 10.3. The  openSUSE 10.3 install went perfectally normal, except that I had to attach my USB keyboard and mouse through PS/2 for the install.  Sorry for the long post that is ultimately of no help to you, but I needed to vent because this was a very frustrating experience :(  I like ubuntu, and hopefully the next version will work for me (or if anyone else can suggest fixes/workarounds for this version?).

BTW, if you do get ubuntu installed and set up right, I can confirm the onboard sound works perfectly without any extra configuration.

---

### Post by JR008 on 2007-10-18
> **karachuonyo said:**
> I also have an old  biostar motherboard (M7 VIZ v8)on my home computer and it works flawlessly. I have Kubuntu on it for the last 2 years and the easiest install i've ever had. Maybe the newer mobos are the ones with incompatibility issues.

I got fedora core 7 working on it now :) biostar 7025 AMD 4200 1GB of ram.  no luck with ubuntu :(

ALSO anyone looking at buying this motherboard (BIOSTAR 7025 or the 7050) get ram with at least 1.95 voltage.  1.8v cheapo stuff dosnt work in this motherboard.  I have some PATRIOT 2.2v at cas4 (2x512sticks)

---

### Post by bulldog885 on 2007-11-05
I was able to get the live CD (7.10) working(biostar tf7050-m2).... when it stops and asks about low graphics setup... select the screen type and vesa as card.... save it and it'll goto shell prompt then type  startx  if you don't select them then x server will halt... once you install on to the hard drive then if you want goto restricted driver then you can.....

---

### Post by nouschi on 2008-02-23
The answer to all your problems... I think.... Because i was able to get everything up and running is to boot to safe graphics and then install the graphics driver via ENVY .... I got it working n/p after hours of trial and error.. but now... it works always as long as I boot to safe graphics mode.. and can get dual monitor working too with twinview; part of the nVidia driver ENVY installs for you. I was using Kubu. My favorite barely supported UBU

---

