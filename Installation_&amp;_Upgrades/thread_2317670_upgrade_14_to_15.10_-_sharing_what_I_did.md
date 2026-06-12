---
title: "upgrade 14 to 15.10 - sharing what I did"
date: 2016-03-18
forum: Installation &amp; Upgrades
---

### Post by crackers_altitude on 2016-03-18
this is solved for me. I thought I'd inaccurately share what I did to get an Ubuntu 14 system up to 15.10. I saw some help from the top Google results, but - meh - didn't want to plow through all these wild commands willy-nilly.

I had Google Chrome and some other things that blocked an upgrade, so I had to eventually uninstall them - all using the synaptic gui.

when that seemed all set, I proceeded to do the big upgrade, again using GUI's - IOW all auto-magical, nothing to prove my skills, right?

the end result was a system with a plain-text login screen and command line environment - which has its charms, like the nice color scheme of ls, but - what you really want is that GUI/desktop thing, so you can use the mouse. At this point, Google results were coming up with some reasonable-sounding things like running startx, futzing with nvidia or nouveau drivers - which you might know is a large pile of fun - and then some results where the user had a "black screen". ugh - has Ubuntu finally lost it? so I looked around the running OS, saw that networking services were off or wouldn't start, I noticed some openConnection things - really starting to get lost - so the fix was when I finally got up the guts to start running apt-get, possibly purging things (here's the inaccurate part), and then apt-get itself told me to run `dpkg --configure -a` (I think!). this ran for a long time, did some obvious things, and voila - back to "normal".

it works now so I'm happy. why I lucked out with apt-get helping me I owe to intelligent software writers. I hope that helps anyone else out there who, for various reasons, might have been reluctant to do the big upgrade. why it had to be that way? I don't know. maybe because my disk is nearly full, maybe not - maybe because I read absolutely zero release notes or anything prudent like that, maybe not.

sorry if that's in the wrong user section but I had an opportunity to put this out there for the help I got so far, so - there. have a happy day.

---

### Post by slickymaster on 2016-03-18
*Moved to the ***Installation & Upgrades*** sub-forum*&#8203;

---

### Post by grahammechanical on 2016-03-18
I have seen several posts about users upgrading from 14.04 LTS to 15.10 and I cannot understand why they are doing that when 16.04 LTS will be released at the end of April and there is a direct upgrade path to 16.04. Ubuntu 15.10 users will have to upgrade to 16,04 before the end of summer anyway as 15.10 reaches end of life in July. So, why do this now? It beats me. 

Upgrading to 15.10 without going through 14.10 or 15.04 is a new thing. And some are finding that the results are not so good. The options for a broken upgrade are

1) over-write the broken OS with a fresh install
2) get to a command line and run apt-get update; apt-get upgrade; apt-get dist-upgrade and see if that improves things a bit. Likewise with apt-get install -f and dpkg --configure -a

But how to get to a command line with a broken OS?

Grub menu Advance options for Ubuntu>Recovery mode. At the recovery menu select network to establish an internet connection and then select Root shell prompt. When finished running commands, type exit to get back to the recovery menu and then select Resume and see where that gets you.

Regards.

---

### Post by RobGoss on 2016-03-18
> **grahammechanical said:**
> I have seen several posts about users upgrading from 14.04 LTS to 15.10 and I cannot understand why they are doing that when 16.04 LTS will be released at the end of April and there is a direct upgrade path to 16.04. Ubuntu 15.10 users will have to upgrade to 16,04 before the end of summer anyway as 15.10 reaches end of life in July. So, why do this now? It beats me. 

Upgrading to 15.10 without going through 14.10 or 15.04 is a new thing. And some are finding that the results are not so good. The options for a broken upgrade are

1) over-write the broken OS with a fresh install
2) get to a command line and run apt-get update; apt-get upgrade; apt-get dist-upgrade and see if that improves things a bit. Likewise with apt-get install -f and dpkg --configure -a

But how to get to a command line with a broken OS?

Grub menu Advance options for Ubuntu>Recovery mode. At the recovery menu select network to establish an internet connection and then select Root shell prompt. When finished running commands, type exit to get back to the recovery menu and then select Resume and see where that gets you.

Regards.


I have to agree with you on this I also wanted to upgrade from 14.04 but was advised it's best to just wait  a few weeks until 16.04 is released. I system is running at it's best and I'm not gonna mess that up if I can help it.

---

### Post by crackers_altitude on 2016-03-18
It's mostly personal why I went to 15.10 - for instance Google Chrome - the browser says it won't update because of the OS. The browser doesn't work sometimes. What I discovered after upgrading (or didn't read the detailed release notes about) is they stopped supporting 32 bit Google Chrome. That was supposed to be a joke.... tough room.

It's healthy to upgrade though, looking forward to 16.

---

