---
title: "Can't install Ubuntu 10.10, 11.04, 11.10, Mint 11"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by Quinflax on 2011-10-29
Hello,

I am pretty new to Linux and am trying to install Ubuntu on my desktop that has Win7 on it.

I have tried installing Ubuntu versions (32-bit) 10.10, 11.04, 11.10 and Mint 11 using CD, USB pendrive and Wubi all with the same result.

1. I get the Ubuntu loading screen: [http://i303.photobucket.com/albums/nn129/Quinflax/IMAG0079.jpg](http://i303.photobucket.com/albums/nn129/Quinflax/IMAG0079.jpg)
2. After a couple of minutes it then goes to this screen [http://i303.photobucket.com/albums/nn129/Quinflax/IMAG0081.jpg](http://i303.photobucket.com/albums/nn129/Quinflax/IMAG0081.jpg) and stops whatever it was doing.

I have searched but can't seem to find anything like this problem. Most graphics problems (which is what i'm guessing this is) seem to occur after installation or after updating the drivers.

Versions 9.10 and 10.04 install fine (just have an issue with wireless not working!)

System:
Intel i5 2.8 GHz
4 Gb RAM
NVIDIA Gforce GT240
Creative SB Audigy

Please could somebody advise,
Thanks.

---

### Post by bcbc on 2011-10-29
Have you tried using the 'nomodeset' boot option: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sweathog on 2011-10-29
I'm having similar troubles, and have used all you mentioned cd,pendrive etc. Was up until 3:30 trying to install any version on a windows xp machine. I did so many installs and reformats these last two weeks that microsoft has cancelled the key to the windows os. The one that worked best was 10.4 on several machines. IMO there is something very wrong with the wubi.exe.


My advice is forget it, I give up. If you've been using this os for a few years you have a chance,but not as a newbie. An old saying is, "to many cooks spoil the broth!" with regards to the wubi and the tens of versions of ubuntu offered.

---

### Post by Quinflax on 2011-10-30
Thanks bcbc, I followed the instructions in the post you linked to and using the nomodeset option did the job. I now have ubuntu 11.10 up and running. (No problems with wireless in this version too. Bonus!)

---

### Post by bcbc on 2011-10-30
> **Quinflax said:**
> Thanks bcbc, I followed the instructions in the post you linked to and using the nomodeset option did the job. I now have ubuntu 11.10 up and running. (No problems with wireless in this version too. Bonus!)

Great! Try running "Additional drivers" and see if there is one available for your card. Then you won't have to keep running with nomodeset.

---

### Post by Quinflax on 2011-10-30
After the successful install I did a reboot and ubuntu rebooted successfully (i forgot about the additional drivers in my excitement!). 

I did not alter the kernel boot options to use nomodeset either, but it still rebooted successfully. That seems a bit odd, but that may be my ignorance.

Interestingly, the Additional Drivers app can't/won't activate the NVIDIA accelerated graphics driver (version current) [Recommended]. It only lets me activate the NVIDIA acclerated etc (post-release updates) (version current-updates).

I could post the log but I think this post may be straying off-topic...

Anyway, I'll get researching those 2 drivers and what it all means (you know, life, ubuntu and EVERYTHING!).

Thanks again!

---

