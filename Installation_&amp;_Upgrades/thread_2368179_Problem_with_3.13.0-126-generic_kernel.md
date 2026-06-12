---
title: "Problem with 3.13.0-126-generic kernel"
date: 2017-08-07
forum: Installation &amp; Upgrades
---

### Post by JKyleOKC on 2017-08-07
Just upgraded my 14.04 system this morning, including a new kernel -- 3.13.0-126-generic. Later in the day I rebooted to a 16.04 system on a separate hard drive in the same box, and when a finished my work there and rebooted back to the 14.04 system (which is still my production machine), grub went into an infinite loop, returning to its menu. After a couple of times around, I selected the older 3.13.0-125-generic kernel, which worked -- and that's what I'm using now.

Later, I decided that the grub.cfg file may have become confused, so ran update-grub and tried a reboot again. This time, the box just froze instead of returning to the grub menu, forcing me to do a hard shutdown. Fortunately, the older kernel still worked afterward, and I'm posting this from the box. Just wondering whether anyone else is having problems with this newer kernel, or did I just get a farkled update? Meanwhile I'm staying with the 125 version.

---

### Post by Autodave on 2017-08-08
No problems here on 13 machines. Are you saying that you upgrade the 14.04 to 16.04? I personally have never had any good luck doing that. (And many here will tell you that they have never had a problem.) Last time I tried, only 1 out of the 13 machines worked properly.  I only do complete installs now. I back up all the files that I need to an external HD and do a clean install.

---

### Post by JKyleOKC on 2017-08-08
The 14.04 and 16.04 installations are on separate hard drives, and both were clean installs. Like you, I do not trust updating in place. However I have both systems configured to check for updates daily (when they are running, of course), and yesterday the daily update process installed the 126 kernel into the 14.04 system. Now attempting to select that kernel in the grub menu results in a freeze, but choosing the 125 version still works properly.

Since you're using it with no problem, I have to conclude that my installed copy has become damaged. The question then becomes, "How do I fix it?"

I prefer using Synaptic for package management, rather than apt-get (I have a tendency to fat-finger the commands, and that can be disastrous). Should I simply tag the 126 kernel package for re-installation and apply it? Will that drag in all its dependencies? Or should I first purge it, then install anew?

---

### Post by vocx on 2017-08-08
> **JKyleOKC said:**
> The 14.04 and 16.04 installations are on separate hard drives, and both were clean installs. Like you, I do not trust updating in place. However I have both systems configured to check for updates daily (when they are running, of course), and yesterday the daily update process installed the 126 kernel into the 14.04 system. Now attempting to select that kernel in the grub menu results in a freeze, but choosing the 125 version still works properly.

I didn't understand your problem very well in your first post, but now I think I get it. You basically have two drives, one with 14.04, kernel, 3.13.0-126, and another with 16.04, kernel 4.4.0-x.

> 
**Since you're using it with no problem, **I have to conclude that my installed copy has become damaged. The question then becomes, "How do I fix it?"

I prefer using Synaptic for package management, rather than apt-get (I have a tendency to fat-finger the commands, and that can be disastrous). Should I simply tag the 126 kernel package for re-installation and apply it? Will that drag in all its dependencies? Or should I first purge it, then install anew?
I don't think he is using 14.04. I don't think many of us are using 14.04, with 3.13.x kernels. Why? It's an old system, with an old kernel. You should probably move that system to 16.04. You say it is your main production system, so obviously you are using it for something specific. But I would actually suggest you move to 16.04 as soon as you have the chance.

If the 3.13.0-126 kernel doesn't work, then my advice is to simply use the previous kernel, -125. That's the reason keeping one or two previous kernels as a fallback is a good idea. I don't think there is much to repair. You should just probably wait until the developers release an updated kernel, say -127, that solves the regression problem caused by -126. That's what I'd do.

Also, use the terminal; "apt, "apt-get", "aptitude", "dpkg" and family give you more control than using Synaptic or other package managers. Fat fingers? It's not a race; type slow, one character every two seconds if you need to.

---

### Post by JKyleOKC on 2017-08-11
Well, today's update to the 128 version solved the problem. I've been in the process of going to 16.04 on that system, for several months, but there's so much non-default software on it that the changeover is quite slow. It's not only my production macchine, but includes mysql, a test copy of my wordpress web site, a private ftp server, and more than a dozen VMs that support my Windows-using clients worldwide. Not to mention being the router for my SOHO LAN!

I do find that 16.04 seems much better, and am using it on the other box (from which I'm posting this update) but the changeover of the main box is moving rather slowly!

---

### Post by vocx on 2017-08-11
> **JKyleOKC said:**
> **Well, today's update to the 128 version solved the problem.** 

As you see, sometimes the problem solves itself, especially if it was caused by an update, and you expect a new update soon.

> 
I've been in the process of going to 16.04 on that system, for several months, but there's so much non-default software on it that the changeover is quite slow. It's not only my production macchine, but includes mysql, a test copy of my wordpress web site, a private ftp server, and more than a dozen VMs that support my Windows-using clients worldwide. Not to mention being the router for my SOHO LAN!

I do find that 16.04 seems much better, and am using it on the other box (from which I'm posting this update) but the changeover of the main box is moving rather slowly!
You are the reason long term support (LTS) releases exist, such as 14.04 and 16.04. Some people need stability to run their machines and keep them going for years without much change. That's good.

I just mention that the next LTS version is coming next year, 18.04, so by the time you transition to 16.04, a lot of people will have moved to 18.04. That's life.

---

### Post by JKyleOKC on 2017-08-11
Quite true, but I don't even consider moving from a LTS until the newer one is at the ".1" update level. I found long ago that it takes this long for the unavoidable bugs that accompany any major update to be found, and fixed. I do install the new LTS in a VM for evaluation, but don't make permanent changes to any of the host systems. The VM lets me get acquainted with the new changes.

---

