---
title: "nVidia GeForce 5200 FX installation"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by UbFX on 2011-04-27
I have come across a couple of posts about this topic but none really seem to answer my question clearly. Before I start I'd like to point out that I am a complete novice to Ubuntu, so please can you not get too technical on *Ubuntu specific *terminoligies and features?

My computers getting on quite a few years now, it bearly gets used anymore but when it does it struggles a lot with xp. I was hoping to give it a bit more speed by installing a less taxing OS onto it and Ubuntu was my first point of call. I've seen from the website how easy it is to install or even just try out by booting it from a CD.

Here's where I encountered my problem, the CD won't boot and my motherboard doesn't support USB booting so I'm stuck! I've seen how there is a problem with my graphics card however I'm helpless in doing anything; such as booting in safe mode, if I can't even get to the installation screen?! A kernal loads up and just stops at different points every time and I don't seem to be getting anywhere!

Does anyone know the workaround to my problem, and how I can go about trying out Ubuntu from a CD boot with the current graphics card?

Thanks. ;)

(I tried with a 10.10 install, I'm guessing 11.04 won't be much different?)

---

### Post by mörgæs on 2011-04-27
HI, welcome to the fora. 

I have one of these graphics cards, and it works well.

First of all let's hear all hardware specifications, especially how much memory is in the machine.

---

### Post by UbFX on 2011-04-27
It has as far as I can remember, Pentium 4 - 512mb Ram - (hard drive space doesn't matter on CD boot up does it, cause it has very little room at the moment), and the graphics card. Can anyone help? I was super looking forward to testing out Ubuntu aswell :(

---

### Post by inobe on 2011-04-27
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

have a look at safe graphics mode, also check out the other options.

---

### Post by xd20 on 2011-04-27
If you have an issue with a nvidia card working on ubuntu, good luck getting it fixed.  I've been trying since October 2010, and no one here has helped resolve the issue successfully.

---

### Post by mörgæs on 2011-04-28
Have you tried booting the alternate version?
[www.releases.ubuntu.com](www.releases.ubuntu.com)

If 10.10 does not work, you could give 10.04.2 a try.

---

### Post by xd20 on 2011-04-28
If he's having the same issue as me, the alternate version will work all the way up until you need to partition the drives.. then it will fail to partition and you'll be stuck again.

---

### Post by mörgæs on 2011-04-28
xd20, your comments are of very limited value. Your graphics card is way different. Please use your energy for something better.

---

### Post by Eric Christenson on 2011-04-28
Morgaes:

There's an awful lot of folks having trouble with nvidia and upgrades.  As you are a mod, can we make this a forum category, and maybe get all the basic docs together so we have the tools to get the right drivers working?

---

### Post by IPEX-731BA5DD06 on 2011-04-28
UbFX, ):Plets start at the basics, people here tend to be a bit too high brow, ie they don't talk the basics. Very helpful people, just a tad over the top in advice.

Your System, a Pentium 4 with 512 of Ram is fine to Run UBUNTU 10.04.2 I run it on a pentium 4 with 4 Gig of Ram, Video card is an Gforce 5600 fx my friend only has 375 Meg of Ram Pentium 4 and it runs with an Internal video card/sound card.

1st. Have you downloaded the ISO image, and burned it to a BLANK CD. Verified the burn etc, its all on the Ubuntu. com page of how to set up and create an ISO image.

2nd. Once you have this done, set your computer BIOS, (hit F2 (Most), F8(some) or F10(few) upon initial boot up till it come up on screen. You'll have an option to Boot from CD 1st. Not the HDD, not the USB or any other item, It'll list an option to boot from your CD, This has to be the Number one or default option for booting.

3rd. Once both these tasks have been achieved, you insert your BOOT CD of Ubuntu into your CD DRIVE. Restart the computer and it should boot from the CD. 

Giving you a selection of Try UBUNTU 11.04 or Install Ubuntu 11.04.

Then you go through the various options, pages, selections, trials etc.

Note: I'm Currently running Ubuntu 10.04.2 LTS Edition, supported for 3 Yr's or is it 5?? Hmm Works fine, 173 Graphics drivers installed correctly for the Nvidea Video card range. 

With a Dual install, 11.04 also works, separate partition.

BUT!!!!!!:confused:

When I upgrade the Video Driver to 173, for my 11.04 installation, that's when the problems start with Flashing screen, default or plain back ground, no Menu's or Icon's at top of Screen, WHICH WORKED on plain driver.

Please note, as we've (both of us) have old video cards, we can't run the new Unity desktop, so we BOTH have to use the old default desktop.

UbFX, let us ALL know how it went, good luck and welcome to UBUNTU and the FORUMS
:popcorn:

---

### Post by mörgæs on 2011-04-29
> **Eric Christenson said:**
> Morgaes:

There's an awful lot of folks having trouble with nvidia and upgrades.  As you are a mod, can we make this a forum category, and maybe get all the basic docs together so we have the tools to get the right drivers working?

I am not a mod, so I can not change anything here. 

There are a lot of people having trouble with upgrades in general, not only related to Nvidia. I have been using Ubuntu since 5.10 on many different machines, and I have never managed to upgrade without errors. 

In contrast, a backup and a fresh install only takes a moment, and it actually works.

More here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

For this particular problem, let's begin with the basics: A fresh install (with all updates applied afterwards) using only the default open-source drivers. How does this work?

---

### Post by mörgæs on 2011-04-29
> **IPEX-731BA5DD06 said:**
> 
I'm Currently running Ubuntu 10.04.2 LTS Edition, supported for 3 Yr's or is it 5?

It is both 3 and 5 :-)

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by mathdater on 2011-04-29
I JUST UPGRADED TO 11.04. I HAVE EMACHINE WITH 1GIG RAM; WORKED REALLY SLOW ON WINDOWS 7 SO I DECIDED TO TRAY UBUNTU AFTER HAVING IT ON OLDER PC AND WORKED FINE. I HAVE NVIDIA GEOFORCE 5200 AND NOW I AM SUCK AT SCREEN SAYING ; \\ " Stopping Userspace bootsplash."; any help will be greatly appreaciated !!!!

---

### Post by mörgæs on 2011-05-07
Did you people get the systems working? Else there might be some advice here:
[http://ubuntuforums.org/showthread.php?t=1743386](http://ubuntuforums.org/showthread.php?t=1743386)

---

### Post by polka123 on 2011-05-07
Hi, I am also having nvidia problems, I have a geforce7300le and get nice new bar displayed on screen with 11.04 but nothing works except for the cursor! Does anyone know of a graphics card that does work with 11.04?
 
Thanks
Rod

---

