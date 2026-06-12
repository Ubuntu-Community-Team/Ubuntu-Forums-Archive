---
title: "Unmitigated Disaster"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2011-06-28
I have been a keen user of Ubuntu since version 7.something. In that time I have updated, upgraded, or done clean installs of each new versions usually about 2 months after the release to enable small bugs to iron out. 

There have always been minor issues usually easily rectified via this forum. However the 11.04 release is the worst I have ever come across almost forcing me back to winblows. 

So what is my gripe. -- 7 hours downloading and upgrading -- to obtain a system that does nothing -- nada. zip. it booted came to the desktop and nothing, Unity doesn't respond, no applications open, and the shutdown didn't work. 

So -- downloaded the ISO this morning did a clean install and eagerly went into my new system.

First issue -- my logitech cordless keyboard is not working, never had an issue before. so plug in a USB one, which is what I am using now. Go to the 'system settings' (took me a while to find where they had gone) but couldn't find anything in the keyboard section to allow me to configure a cordless keyboard. Failure 1

Open banshee and ask it to load the music library. It does, then click for a file to play and --- no sound! so choose another track just in case and banshee crashes, and the icon disappears from the unity bar.
Failure 2

As usual I have an Nvidea graphics card so one of the first things is to  install the proprietary driver. Never had an issue before. this time it loaded (apparently) and then I do the restart to enable it, and when I get back in there is no top bar, the Unity bar sits there and won't slide in and out, and no applications will respond. BIG failure 3

Re boot into recovery mode and opt for safe graphics mode.

System re boots - Top bar now appears, Unity remains inoperative, and when I click the shutdown icon to get to system settings --- crash and burn system shuts down.-- BIG failure 4

Re boot into recovery mode (again) run "fix broken packages" DPKG runs for a while replacing and upgrading hundreds of packages. When finished reboot -- same issue desktop stuffed! 

Currently working off the live CD. Help appreciated if possible. 

To the developers -- maybe you are pushing ahead too quickly now. this sort of overall failure will lose more users than gain. I don't usually complain but as my title says for me Natty is an unmitigated disaster. 

I can't even begin to wonder what needs repair or work

---

### Post by Alwimo on 2011-06-28
That's terrible. It's very unfortunate. :(

You could stick with 10.04 or 10.10 and hopefully those problems will be fixed in 11.10. You could try a different distribution, alternatively. [Linux Mint]("http://www.linuxmint.com/") is a close relative of Ubuntu, as is [Debian]("http://www.debian.org/") (although the latter is less user friendly). [Fedora]("http://fedoraproject.org/") provides a different experience, as does [openSUSE]("http://www.opensuse.org/en/").

One of the strengths of having so many distributions to choose from that can be switched between fairly easily is that problems with the direction of one distribution can be circumvented relatively easily.

---

### Post by tropdoug on 2011-06-28
Agreed Alwimo, I have just reinstalled 10.10 alongside Natty. I hope that some answers to the above might come, because I have until now enjoyed Ubuntu. I might give Fedora or openSUSE a go though. When you say they give a different experience, can you be more specific?

Thanks for the reply

---

### Post by Alwimo on 2011-06-28
I mean that they are not based on Debian. There are some differences because of that, such as how you can install things. Ubuntu uses .deb files, whereas both openSUSE and Fedora use .rpm files.

But more visibly, Fedora 15 uses GNOME 3 and Gnome Shell by default. Here is one video showing what Gnome Shell is like: 
[https://www.youtube.com/watch?v=bRHAio98n-g](https://www.youtube.com/watch?v=bRHAio98n-g)
A lot of people have strong opinions on whether it's good or not, so you could play around with it and see what you think.

Most people also seem to use KDE if they use openSUSE.

---

### Post by mastablasta on 2011-06-29
also OpenSUSE is more oriented towards KDE than Gnome. not sure where fedora stands. and they don't sudo i believe. but have separate root and user accounts.
 
I would say try Linux Mint. Usually they patch up a few things from Ubutnu. as a bonus they have Debian based version. so very user friendly debian (but suggest you lock it to stable).
 
if 10.04 worked for you i would stay with that. and update a few programmes maybe. until they fix the issues at least.
 
these kind of things are really annoying. i mean with all "testing" how can they manage to break things that worked nicely before?! there is too much of this kind of things.

---

### Post by tropdoug on 2011-06-29
I have to agree Mastablasta. I reckon the developers and contributors are geniuses I truly do, but perhaps that is a bit of the problem, in that the Linux platform will not get to critical mass, until the "masses" (me) can take a distro, load it up, personalise it a bit, choose the programs they want and manage the small bit of configurations required, and then get on and enjoy what I believe is the best OS base on the planet. 

Oh well, having re installed 10.10 and got it working fine, I am now installing 11.04 alongside it and will hopefully have it work this time. If not -- in the bin for another six months. 

Meanwhile I will check out both mint and fedora. Luckily I have plenty of space to put a few distros in and compare them.

:guitar:

---

### Post by tropdoug on 2011-06-29
Re installed natty - from the live cd - this time it all appeared to work, still haven't tested everything but at this stage fingers crossed. 

marking this as solved, but really developers if any read this -- perhaps take a little more time and less urge to amaze us -- the result is often negative.

---

