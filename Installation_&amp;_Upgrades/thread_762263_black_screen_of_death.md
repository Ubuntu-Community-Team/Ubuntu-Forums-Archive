---
title: "black screen of death"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by Emerican on 2008-04-21
I burned ubuntu to a cd so i could install it as my main OS. but when i go to run it and its done loading, all i get is a black screen. before i was getting a bunch of letters and numbers but it stopped doing that. i just want this to work and see if anyone would help out. thanx and h4x

---

### Post by overdrank on 2008-04-21
> **Emerican said:**
> I burned ubuntu to a cd so i could install it as my main OS. but when i go to run it and its done loading, all i get is a black screen. before i was getting a bunch of letters and numbers but it stopped doing that. i just want this to work and see if anyone would help out. thanx and h4x

HI and welcome, could you give us some system specs like memory and graphics? Also did you check the cd for errors?

---

### Post by Emerican on 2008-04-21
thank you. 
from what i can see in my device manager i have a intel celeron and idk about memory, either 256 or 512, im not sure. and i did check the disc i made and it says that there are no errors. maybe its i donwloaded the first option but now that i see they have n intel download would that have anythiing to do with it?

---

### Post by overdrank on 2008-04-21
> **Emerican said:**
> thank you. 
from what i can see in my device manager i have a intel celeron and idk about memory, either 256 or 512, im not sure. and i did check the disc i made and it says that there are no errors. maybe its i donwloaded the first option but now that i see they have n intel download would that have anythiing to do with it?

Hi and that should be the one you downloaded for your system. You may want to checksum the iso 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
And also look at burning the cd as slow as possible. And also locate the model of the graphics card as this could be a issue.

---

### Post by Emerican on 2008-04-22
i dont really think its much as the graphics card and which one the intel?

and it took me a while cause i burned it at 2X lol

---

### Post by hannah187 on 2008-04-23
try this command in the terminal to know details of your hardware

sudo lshw

---

### Post by erginemr on 2008-04-23
Once you make sure that the Ubuntu Install CD is not faulty, you may consider editing the boot line with F6 and remove "quiet splash" from the corresponding boot parameters. This will let you view the boot messages and track down the error message that is issued during the process.

Failing that you may consider waiting just one day for the release of Hardy Heron (the new version of Ubuntu), with which you may have better luck.

---

### Post by chrisdugdale on 2008-04-23
Use Xubuntu! If you have 512Mb memory or less it will be more likely to work as it's got a lighter front end. I got a hp with only 192Mb, Puppy Linux seems to be the best answer for a quick and easy way to get it working.

---

### Post by MeURi on 2008-04-23
I had something like that, Emerican

I solved it booting into safe graphics mode (my widescreen monitor just went black and nothing more in any other way)

You'll have a 640*480 (stretched) resolution, but at least you can install the system

It did the trick, at least for me

Anyway, look for errors during boot, as erginemr said; it's way better than the trial-and-error approach ;-)

---

