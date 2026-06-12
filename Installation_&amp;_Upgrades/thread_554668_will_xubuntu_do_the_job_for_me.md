---
title: "will xubuntu do the job for me?"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by gdp77 on 2007-09-19
Hi to all.

I am a primary education teacher and besides my laptop I managed to get an old desktop pc for my classroom. It is a PII 266 with 128MB RAM and it runs Win95 crap. 

I need to setup a lite linux distro with word processor, excel, web browser, a paint program etc. Basically I would like all the programs ubuntu comes with, so it can actually be usefull and my pupils can use it.

I was thinking of installing xubuntu 7.04.

I tried the xubuntu live cd today, but it took about 20 min to boot and the panels never appeared on the screen. The desktop was there and the icons, but no panels.

1) Is this because of the low ram or if i try to install it, the panels won't work as well?
2) The 20 min boot time will improve once I install it,  or the pc specs are too low?
3) I don't want to install small distros like damn small linux, etc, since this computer has no internet access and it won't be easy to install any programs, so I want a out-of-the-box full package solution
4) Do I have any other choice besides xubuntu?

Any help it would be greatly appreciated.

P.S. Sorry for my bad english.

---

### Post by Pumalite on 2007-09-19
Increase your RAM. Or use a small distro.

---

### Post by Neobuntu on 2007-09-19
Increasing RAM as a given and understanding it may be capped or cost more than the computer I suggest the following:

Since no internet will be available (not good for upgrading) and if you don't want to build up a Icewm Debian Etch system (which is what you do with Internet) I suggest Absolute Linux.

The only caveat being that you would need to partition the hard drive yourself ("/" and swap) with the Absolute Linux installer. A Gparted live CD would be ideal for this. Absolute would install everything else.

So you need a Gparted live CD and a Absolute install CD. If you haven't downloaded and "burned" your own CD, just ask a computer friend. (Do not just burn the iso file to a CD, burn it as an image, to the CD and VERIFY it.)

Absolute comes fully loaded with small programs and it's fast. Visually appealing and it has educational games installed.

Note that Absolute would require one to make up a user (student) account (easy and a menu choice) and type "startx" but that can be automated. For separate student accounts, this would be ideal. For one overall student(s) user account this would also work (KISS). This way, they'd less likely crash it.

I know you mentioned Puppy but a Puppy 2.15CE (specifically) live CD would be a finished (practically zero time) solution, run live. You could do this too (both).

The problem with having the programs (off-line) and more you may want to add, is you'll need to go on-line occasionally to get/add them. Jockeying CD's is no fun and harder than finding Internet.

So if there's anyway possible to get Internet (wireless?) part-time, then that's what you'll want. In that case, I strongly suggest Debian and the effort to install Etch (easy) and add what you want from fast, stable, DYNAMICALLY CHANGING and huge repositories.

With Debian, install Etch with "expertgui" (from 40r1 CD-1) and uncheck ALL packages, even standard in the tasksel package selector. Then simply > aptitude install xorg icewm icewm-themes icemc rox-filer rxvt leafpad feh iceweasel msttcorefonts gtk-theme-switch gtk2-themes-spherecrystal xarchive arj p7zip rpm unzip zip pciutils gnumeric abiword  also perhaps > aptitude install sun-java5-jre sun-java5-plugin sun-java5-fonts sun-java5-bin alsa-base alsa-utils alsa-oss aumix-gtk  and whatever else you like (like synaptic). Note you'll then want to select the Silver XP theme and edit icewm to your custom preference (It's just copying from /etc/X11/icewm to ~/.icewm and editing text files). Try icemc then too.  You could use "rox" (note that "Ctrl-Alt-Spacebar" lets you type and run "rox" before you have set it up on your toolbar titled "Home" or "My Computer". Don't miss the folder "bookmarks" ROX has as well. Type "switch2" (both as root and as user) to select Spherecrystal (for looks). 

For the Kids(age?), some you may like are: Anagramarama concentration tuxpaint tuxmath and many more. in any case, with Debian, the world is yours (given some Internet). Note: you can download and burn a Debian CD sets (not the source ones) but they will be stuck at that time. That's not good. Plus there may be packages you want that are not on those CD's but on the Internet.

Otherwise you're doomed to old scratchable Windows educational game CD's (which one could still do; dual boot). 

In any case, have fun. Absolute is the answer to your question but Debian is better.

XFCE is a fine somewhat leaner DM (than KDE). Yet, not than much. not lean like icewm (the #1 champ; bar none IMHO).

Remember, all software systems stink, as far as total user friendliness goes. These suggestions stink the least, for old computers.

---

### Post by maybeway36 on 2007-09-19
Another option: see if you can get some more RAM (maybe from someone with an old PC they don't use anymore) and try the Edubuntu live CD.
Or if your "lite distro" you set up uses the Ubuntu base, you can install programs from the repos too.
(Actually, Edubuntu+Fluxbox might be a nice idea.)

---

### Post by CREEPING DEATH on 2007-09-19
Xubuntu or Debian XFCE is good for that machine, I might use Debian though because it'll be older, more stable, and lighter.  If you look around (google) there are a few line-by-line how-tos on installing XFCE on older machines like that.  I've used Debian-XFCE on much lesser machines than that laptop.

CD

---

### Post by RedSquirrel on 2007-09-20
> **gdp77 said:**
> I tried the xubuntu live cd today, but it took about 20 min to boot and the panels never appeared on the screen. The desktop was there and the icons, but no panels.

1) Is this because of the low ram or if i try to install it, the panels won't work as well?
2) The 20 min boot time will improve once I install it,  or the pc specs are too low?
3) I don't want to install small distros like damn small linux, etc, since this computer has no internet access and it won't be easy to install any programs, so I want a out-of-the-box full package solution
4) Do I have any other choice besides xubuntu?

P.S. Sorry for my bad english.

I think once you install it the performance of Xubuntu will improve. However, according to the [system requirements]("http://xubuntu.org/get#requirements"), you won't be able to install using the LiveCD; you need 192 MB RAM for that. So, you'll need the alternate Xubuntu CD if you want to try installing it (that one only requires 64 MB RAM). I would give it a try since it's free and see how it goes. 

If it's too slow but you still want to use something Ubuntu-based, you could do a minimal installation and the add the packages you need on top of that. The latter part won't be too easy if the computer won't have internet access, but it may be possible to download the packages (as deb files) using your laptop and transfer them to the old computer using a CD, for example (if the old computer has a CD drive).

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)


PS - Your English seemed just fine to me. :)

---

