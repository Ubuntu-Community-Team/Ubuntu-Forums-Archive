---
title: "Trouble installing on Biostar TForce965PT"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by Watter on 2006-12-05
I just put together a new system and I'm having some serious issues getting Edgy installed. Here are the relevant specs:

Biostar TForce965PT Motherboard
- Realtek RTL8110SC NIC
- Intel P965 Express North Bridge
- Intel ICH8 South Bridge
Intel Core 2 Duo E6300
2Gb Geil DDR2 800 memory
GeForce 800GTS Video Card

The CD's I'm using for the installation are known to work as I've used them to install Edgy on several other machines.

The live CD doesn't work at all. After choosing to boot it from the initial boot selection screen, all I get is a blank screen; no hard drive access; nothing.

The alternate CD works a little better. The installation works pretty well except that it can't detect the integrated Realtek network card. Other than that it runs through to completion and ejects the CD. Upon rebooting however, all I get after selecting Ubuntu from the grub menu is "Starting..." and never anything else. Frankly I'm at a loss. I don't even know what steps to take to try and debug the issue. Any advice?

---

### Post by Watter on 2006-12-07
For what it's worth, opensuse 10.2 RC1 installed without issues. I still dont' quite "get" opensuse after having used Kubuntu for so long, but right now I don't have many other options. 

Hopefully, I'll run across a solution to my Kubuntu installation problems and be able to come back to familiar territory.

---

### Post by Watter on 2006-12-08
Just another update for anyone who might be in the same boat. 

Feisty Fawn Alpha 1 works. The common denominator between Feisty Fawn and OpenSuse 10.2 that led to these working seems to be the 2.6.19 kernel. 

Don't try and install the normal nv or nvidia driver if you're using an 8800 series card. It's not supported. You'll have to manually install the beta driver from [http://www.nzone.com](http://www.nzone.com) to get any kind of support for that card. The current nv and nvidia drivers wont' even load X on an 8800 card. You can follow the guide here to install the beta drivers. It worked great for me:

[http://ubuntuforums.org/showthread.php?t=296933&highlight=nvidia+howto](http://ubuntuforums.org/showthread.php?t=296933&highlight=nvidia+howto)

On another note, installing using these drivers was the easiest I had ever gotten my Dell 2405fpw to be detected and used. I never even touched xorg.conf and the correct resolution of 1920x1200 was detected and used once this driver were installed and configured with "sudo nvidia-xconfig".

The downside is that I'm having to use an alpha level OS. In only 20 minutes of use I've already run across a number of annoying things that are, of course, to be expected from this early of a release. Yuck.

---

### Post by Watter on 2006-12-11
In a continuation of my own little monologue here...

Feisty Fawn was just too slow for acceptable use. In this case, slow refers to normal desktop rendering speed. For instance when alt-tabbing between two windows the time it took to render or put focus on the new window was close to a second. That doesn't seem like much but you'd be amazed at just how much a productivity killer it is. That's just one example, of course. Dragging a window around was a lesson in patience. Unfortunately I did have the nvidia graphics driver correctly installed and running (my 3d scores weren't too bad, really), so I dont' know what is causing the poor desktop performance. 

Honestly, while slightly better, Edgy is no speed demon either. I seem to recall in the past how Kubuntu was one of the snappiest distros I had ever tried. I must have something configured incorrectly because I can't seem to get that level of "snap" back.

Anyone know how to get better 2d desktop rendering performance?

For what it's worth, I know it's not the kernel or the graphics driver because OpenSuse 10.2 on the same machine with the same kernel and driver is snapperific. Unfortunately, OpenSuse is no Kubuntu, but I have to get actual work done on this machine so I'm not left with many options.

---

### Post by Watter on 2006-12-11
Apparently it's a KDE problem. I installed Ubuntu and it was snappy as could be. I then did "sudo apt-get install kubuntu-desktop". I also chose kdm as the manager. After rebooting I logged into both KDE and gnome. KDE was low and chunky and Gnome was quick and snappy. This isn't an indictment of KDE in general. As I said in a previous post, KDE on OpenSuse worked fine. I wish I could figure this out as I really do prefer KDE. At least i can use an Ubuntu variant now instead of OpenSuse, even if it is Gnome.

---

### Post by daahli on 2006-12-25
Hey,

I have a very similar setup. The only problem I ran into during the installation was that the ethernet was not detected. I was pretty worried, but when I booted up the first time I immediately had a connection!

However, I've noticed since then that the connection I'm getting is pretty bad, and I don't think it's due to the actual Internet connection, but that it probably has something to do with the driver that Ubuntu is using. 

Have you had a similar Internet experience?

---

### Post by Watter on 2006-12-27
> **daahli said:**
> However, I've noticed since then that the connection I'm getting is pretty bad, and I don't think it's due to the actual Internet connection, but that it probably has something to do with the driver that Ubuntu is using. 

Have you had a similar Internet experience?

No, I'm currently running OpenSuse 10.2 on this machine with no problems. Everything was detected and ran right off the bat. I'm sure that once Feisty is released it will work smoothly as well. In the meantime, I'll just work in OpenSuse. It's not so bad. It's not as snappy as Kubuntu but it has some nice touches that Kubuntu lacks, and in this case the "just works" moniker applies to it instead. ;)

I'm looking forward to Feisty so that I can move back into the Kubuntu camp.

---

