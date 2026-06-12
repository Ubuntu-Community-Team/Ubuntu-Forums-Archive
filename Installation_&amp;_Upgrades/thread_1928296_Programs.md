---
title: "Programs"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by WolfofAlchemy on 2012-02-19
I just recently got Ubuntu permanently as in erasing my Windows 7 because my computer doesn't really support it (graphics card wise.) I was wondering a few things since I'm going to be pretty much keeping Ubuntu because of it's fast speed and low resource usage.

1) Is there any program that you can make video with. Kind of like a program similar to Sony Vegas Pro?
2) If I ever have some sort of problem and Ubuntu won't boot, how do I fix this? 

I mean last time I tried to boot from a disc and replace Windows it wouldn't let me, but now all of a sudden I can apparently because my disc drive is a IDE and it's suppose to be SATA? I don't even know anything about this OS. 

Anyway is there anyway to fix this without using the DVD that I already formatted because it was a DVD-RW. My drive is crappy so it hardly works so I take it out and use one that only does CD (CD-R/CD-RW). Any help on this would be nice because I've had the dual boot before and Ubuntu wouldn't work and it had some sort of repair thing that worked but I'm worried this new 11.04 won't have it and I'll have a useless computer again. 

3) Is it possible to get drivers for my hardware like my graphics card, wireless adapter, and anything else I'm forgetting?
--------------------------------------------------------------------------------------------------------------------------------

Any help on these 3 things would be great. Like I said I don't know much of anything about this OS and I really do like it. :D But what if it crashes? Also I used cleaning programs for when I had Windows. Would that of been the reason why Ubuntu wouldn't boot before? (Take note that I have my own computer now and the other one I used with Ubuntu wasn't mine so I don't know if someone else messed it up.)

Thanks a bunch in advanced!

---

### Post by winh8r on 2012-02-19
If you are installing 11.04, the release notes are here:

[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes]("https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes")

Have a read through and if you are unsure or have any other questions then just ask!

Hope this is of some help to you.

---

### Post by WolfofAlchemy on 2012-02-19
> **winh8r said:**
> If you are installing 11.04, the release notes are here:

[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes)

Have a read through and if you are unsure or have any other questions then just ask!

Hope this is of some help to you.

Probably should have made it clearer. I already installed 11.04 from a disc and wiped out Windows completely. The release notes don't answer any of my questions stated above, but it did answer some of my less important questions like having hardware in my computer or using something that may not work well with Ubuntu. None of my hardware having negative effects on Ubuntu. Just maybe my mouse is a little bit weird sometimes as it always was when using Ubuntu. I've used 10.04. Honestly I think it loaded quicker when it's dual booted, but 11.04 runs really fast without Windows holding it down. Not to mention having it's own partition seems to have helped. Nice to have a quiet computer for once since Ubuntu isn't resource demanding.

---

### Post by WolfofAlchemy on 2012-02-19
My bad I ment I installed 11.10. Been having one of those really long days where my mind is lost.

---

### Post by HavarN on 2012-02-20
> **WolfofAlchemy said:**
> 1) Is there any program that you can make video with. Kind of like a program similar to Sony Vegas Pro?Check out wikipedia at [List of video editing software#Open source software]("http://en.wikipedia.org/wiki/List_of_video_editing_software#Open_source_software")

> **WolfofAlchemy said:**
> 2) If I ever have some sort of problem and Ubuntu won't boot, how do I fix this?
...
Also I used cleaning programs for when I had Windows. Would that of been the reason why Ubuntu wouldn't boot before?There could be many reasons why you could experience boot problems. Using "cleaning" programs on Windows that alter the boot loader could be one cause. In that case, you probably need to reinstall or reconfigure your boot loader. Ubuntu uses grub2 as its default boot loader.

Another problem could be using wrong or misconfigured drivers (called modules in Linux). Usually these problems are limited to the graphics card's modules need to load the gui. In that case, ubuntu would probably boot into a recovery console. It could also be the HDD controller or storage setup.

> **WolfofAlchemy said:**
> 3) Is it possible to get drivers for my hardware like my graphics card, wireless adapter, and anything else I'm forgetting?Usually these work out of the box or with a proprietary driver which is available from System Settings -> Additional Drivers. If it does not work out of the box or with such a proprietary driver, take a stand against closed source drivers, and replace your device.

---

### Post by Mark Phelps on 2012-02-20
To answer your second question, fixing boot problems -- your only recourse is going to be to come here with the problem details and see if anyone can help you fix it.  There are no guarantees that anyone can provide ahead of time regarding fixing any boot problem.

---

### Post by WolfofAlchemy on 2012-02-20
> **HavarN said:**
> Check out wikipedia at [List of video editing software#Open source software]("http://en.wikipedia.org/wiki/List_of_video_editing_software#Open_source_software")

There could be many reasons why you could experience boot problems. Using "cleaning" programs on Windows that alter the boot loader could be one cause. In that case, you probably need to reinstall or reconfigure your boot loader. Ubuntu uses grub2 as its default boot loader.

Another problem could be using wrong or misconfigured drivers (called modules in Linux). Usually these problems are limited to the graphics card's modules need to load the gui. In that case, ubuntu would probably boot into a recovery console. It could also be the HDD controller or storage setup.

Usually these work out of the box or with a proprietary driver which is available from System Settings -> Additional Drivers. If it does not work out of the box or with such a proprietary driver, take a stand against closed source drivers, and replace your device.

All my drivers work perfectly on Ubuntu and there is nothing in the "Additional Drivers" as I always checked that when I install Ubuntu. I'd image people using newer hardware would have a more likely chance of that happening. My hardware is older than 2002 which is why I love Ubuntu because it take it easy on outdated hardware. I have no money to get newer hardware. All I could afford is 2 GBs of RAM. Way more than needed for Ubuntu.

About the cleaning programs, I used a defragger that altered the boot for "faster" booting which I believe only does harm to Ubuntu and only works on Windows.

---

### Post by WolfofAlchemy on 2012-02-20
> **Mark Phelps said:**
> To answer your second question, fixing boot problems -- your only recourse is going to be to come here with the problem details and see if anyone can help you fix it.  There are no guarantees that anyone can provide ahead of time regarding fixing any boot problem.

I burned the .iso file back on to the DVD-RW that I used at first and made sure it works. I'll just use that in case I have no way to get on this forum for help.

---

### Post by grahammechanical on 2012-02-20
If you have 15 - 20GB space on the hard drive then create another partition and dual boot another version of Ubuntu.

I do this with the forth coming release of Ubuntu to test it out and to set it up the way I want it. I also test out any modifications on it so that I do not mess up my main Ubuntu install and I always have a usable Ubuntu.

Of course, if you keep Ubuntu in its standard state there should not be anything messed up that stops you booting into it.

Regards.

---

