---
title: "ubuntu or fluxbuntu or xbuntu"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by Alan Coleman on 2008-10-11
I have a couple of pentium 2 laptops. Is there a big difference between installing ubuntu and then changing the window manager to something lighter weight, and downloading and installing xubuntu or fluxbuntu.

thanks 
a

---

### Post by Pumalite on 2008-10-11
Memory?

---

### Post by Alan Coleman on 2008-10-11
memory... ah yes!

At the mo the bios batteries are flat so they dont...work
However I can see that one has a 64meg chip and the other seems to have more but im wary of pulling things out of laptops unless I have too and there are no obvious numbers. 

I see your point, little memory...problem.
i google and i see...

Bare Minimum requirements (ubuntu)

It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation. 

# 300 MHz x86 processor
# 64 MB of system memory (RAM)
# At least 4 GB of disk space (for full installation and swap space)
# VGA graphics card capable of 640x480 resolution
# CD-ROM drive or network card 

Ive been reading abit about thes Alternate install CD's today.
I dont have a burner so -- they dont sound very useful to me.

---

### Post by Pumalite on 2008-10-11
Try a minimal Installation:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Alan Coleman on 2008-10-12
Thats quite a page that one. Am I right in saying ubuntu, kubuntu, fluxbuntu, xubuntu, edubuntu systems are the same just with different window managers and applications? Or the kernel is the same in all disto's?

thanks
a

---

### Post by madmetal on 2008-10-12
i suggest trying either Xubuntu or Damn Small Linux...
they are both useable and light for your system..

---

### Post by simtaalo on 2008-10-12
id recommend crunchbang [http://crunchbang.org/projects/linux/](http://crunchbang.org/projects/linux/) it uses a minimal ubuntu install with the openbox window manager. openbox is alot more lightweight than xfce (the windows manager that xubuntu uses).

if thats too much for your system then use DSL [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by snowpine on 2008-10-12
Hi Alan, my recommendation to you depends on three questions: 
What applications do you absolutely need to run on these old laptops? 
What is your comfort level with the command line?
Do you have a strong preference for Ubuntu as the base system?

For a laptop with low ram, for example 64-128mb, your first challenge is simply finding an installer that will work, because most live cd installers require more ram. You need to use an alternate install cd or the mini.iso to install a minimal command-line only Ubuntu, then build it up from there with a lightweight windows manager such as IceWM, Openbox, Fluxbox, Xfce, etc. Pumalite's link is really good, and here's another guide: [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

However, if the computer only has 64mb, you may run into this bug: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

If you don't like the command line and have a bit more ram (128-256mb), you can try installing a lightweight Ubuntu derivative such as Crunchbang or Fluxbuntu. These would both run better than Xubuntu or Ubuntu on your computers, though perhaps not as fast as a minimal install.

Then, there are non-Ubuntu distros with much smaller footprints. SliTaz, Puppy, and DSL are popular options in this niche.

---

### Post by Alan Coleman on 2008-10-13
Good questions...

What applications do you absolutely need to run on these old laptops?

I want to use them to surf the net, a bit of light multimedia. Wifi is essential from the outset as that is my only internet connection. I tinker and I like the ethos of older systems. They are eco friendly and do approximately 90% of (the essential stuff) that you can do with 2ghz processor and 2ghz of ram. Or do they, I want to know.

What is your comfort level with the command line?

I like to use command line. When it works. tried to install a printer via command line-unsuccessfully. But generally speaking I can follow a command line howto.
But I like it as a tool. I loved Pumalite's howto suggestion but it dosnt include how to get wifi going from square one,
	
Re: ubuntu or fluxbuntu or xbuntu
Try a minimal Installation:
[https://help.ubuntu.com/community/In...wMemorySystems](https://help.ubuntu.com/community/In...wMemorySystems)

Do you have a strong preference for Ubuntu as the base system?

Ubuntu is my chosen system at the moment. Ive tried some others DSL, knoppix. Ubuntu makes wifi easy. Im starting to get used to ubuntu and know the system, I know a lot of the apps etc.


As for what I will do with these systems. First thing is to get the bios to work by getting some batteries for the them, then either try to upgrade the ram which Ive discoverd is 64mb in both.

An Idea Im playing with is if I was to get hold of a 128mb chip of ram that would bring the laptop up to 192mb of ram which is the minimal necessary for using a live cd.
Idealy I need to come up with 4x128mb chips two for each machine and, memory problem solved.

anyway, thanks for taking the trouble to read this.

finally...

Im prompted to ask the question are all ubuntu distros the same underneath differing only in window manager and chosen applications?
also...Dose wifi require a lot of system resources to run processing power ram etc?

thanks Alan C

---

### Post by Pumalite on 2008-10-13
You need 384 MB of RAM to boot a live CD. You could make a /swap partition of 500 MB ahead of time and boot a Live CD with that memory.

---

### Post by snowpine on 2008-10-13
Hi Alan, rather than regurgitate information I've read here on the forums, let me share a little bit of my personal experience. I have what I would consider to be an "old laptop". It is a Dell Latitude Cpx, 500mhz Pentium 3, 256mb of ram (lately upgraded to 384mb), and a 6gb hard drive. It's probably 8 years old and originally came with Windows 98.

I started out with Ubuntu 7.10 (installed using the Alternate CD) as a complete Linux novice. It was easy to use but a bit on the slow side. Wireless was my #1 biggest hassle in the beginning, as my Linksys WUSB54Gv4.0 does not "play nice" with the Linux kernel. Finally got it working though with the help of these forums. 

I've since used several Ubuntu variants on this laptop (Xubuntu, Fluxbuntu, Crunchbang). All of them made me happy and allowed me to get my work done. Boot time was about 2-3 minutes. Applications like Firefox or Openoffice took 5-20 seconds to launch. Flash video was choppy viewed online but acceptable if I downloaded the video first. 

Lately, I've been using a non-Linux distro called SliTaz. My boot time is just under a minute, and most applications take no more than 5 seconds to launch. 

My conclusion is that all Ubuntu distros are basically the same "core" with different applications and a different windows manager. The first version of Ubuntu came out in 2004, and the "core" system is optimized for typical hardware of that era. If your hardware is more than 5 or so years old, you are going to have to make some compromises. In your case, I'd suggest fairly drastic compromises, including 1) more ram--64mb just doesn't cut it in 2008 ;); 2) start with a minimal command line system and install only what you need; 3) choose lightweight applications, because the "standards" like Firefox and Openoffice will probably be too heavy. Only you can decide whether to make the "ultimate compromise" and leave the wonderful-but-resource-intensive Ubuntu family for something like SliTaz, Puppy, or DSL. :)

(edit) in case I did not make it clear, my "old computer" is not quite as old as yours, so I have no direct, first hand experience installing Linux on a Pentium 2 with 64mb of ram (or 192mb for that matter), so please take my advice with a grain of salt!

---

