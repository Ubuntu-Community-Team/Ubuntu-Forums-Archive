---
title: "Help! Live CD hangs"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by anujv73 on 2007-07-18
hi frds i am trying to install ubuntu from last 7 days but i am not able install it. i have 256ram,celron PC; i know it little bit slow proccesor.but it run quite good in window.i think thats the main region why people not like linux.
when ever i run my live CD in that when i click to install   it take too much time start and after that it hang.
 i didn't understad what to do 
i think linux is not my cup of tea!!!!!!!!!!!!!!

---

### Post by Henry Rayker on 2007-07-18
The problem is that you are trying to run from a CD. Optical drives are incredibly slow. This is normally okay, because the entire disk contents get loaded into RAM...however, you have very little RAM as well. If you want to install, you should try the alternate install as the live cd needs more RAM to do well.

Honestly, linux uses far less system resources than a comparable windows system, so I don't think that's where peoples' gripes come in. The problem is that people come over expecting to be able to apply their windows only knowledge to a new operating system.

---

### Post by aysiu on 2007-07-18
**Thread title change**
Such sensationalist titles as *ubuntu is not good enough!!* may get you a lot of attention, but the kind of attention you get will distract from the help you would be getting with a more sensible title, so I've retitled the thread to be one asking for help.

If you would rather rant about how much Ubuntu sucks instead of asking for help, then I can retitle the thread back and then move it to *Ubuntu Testimonials and Experiences* instead of keeping it here in the *Installation & Upgrades* support forum.

**About your problem**
The live CD runs completely out of your computer's RAM (it does not use the hard drive at all, unlike Windows or the installed version of Ubuntu). If you have only 256 MB of RAM, the live CD will work quite slowly.

---

### Post by anujv73 on 2007-07-18
at list tell me any else way which r they?

---

### Post by aysiu on 2007-07-18
any else way which r they? I don't know what you're asking.

---

### Post by anujv73 on 2007-07-18
can any else way to install ubuntu to my PC?beside run live CD?

---

### Post by anujv73 on 2007-07-18
i know i am little bit harsh but that's true.window installation i learn without any one help.and over here.....

---

### Post by merlinus on 2007-07-18
> 
i know i am little bit harsh but that's true.window installation i learn without any one help.and over here.....


This ain't gatesville -- no spyware, adware, viruses, intrusion, and trojans, and definitely no windows bloatware!

You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by aysiu on 2007-07-18
> **anujv73 said:**
> can any else way to install ubuntu to my PC?beside run live CD?
Use the Alternate CD instead of the Desktop CD.

The Alternate goes straight to installation without also running a live session, which will suck up all your RAM.

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) will help you.

---

### Post by lefen on 2007-07-18
Hay, I'm in the same boat with my 7.04 live CD. My work box (1GB RAM) boots the live CD fine, but my home box (512 RAM) takes 20+ minutes to load and then crashes with weird screen colours and characters when it's time to load Gnome.

Now, my home box loads the 6.06 live CD with no problems, so I'm just a bit worried that 7.04 doesn't support my hardware? This doesn't actually seem possible, since I'm running 6.06 right now, but I'm a bit worried using the alt CD incase I completely ruin things.

Does anyone have advice? Basically my options are to use the 7.04 alt CD, or update 6.06 through 6.10 and then to 7.04 using the command line updater, but then I've read some horror stories on the forums about the latter method to make me think twice about it :/

Thanks for any help (^_^)

---

### Post by PryGuy on 2007-07-19
Yep, get a DVD image and run Alternative install from there. Ubuntu CD hangs on 256Mb RAM. Another option that helped me in such case, I've partitioned drive with a third party utility and made ext3 and swap partitions. I think Ubuntu recognizes and mounts swap partition and this helps. Good luck to you, Ubuntu is really a nice thing!

---

