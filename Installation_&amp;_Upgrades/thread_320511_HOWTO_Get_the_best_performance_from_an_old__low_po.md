---
title: "HOWTO: Get the best performance from an old / low powered computer"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by sideshowb0b on 2006-12-17
I've searched for some time to find _simple_ instructions for installing a linux system that works well on an old computer. I've not found anything particularly useful, so I'm starting a thread here. Please post any helpful tips you've discovered for freeing up memory / hard drive space / processor time. If I get enough responses I'll make this into a HOWTO. 

Here's my meager offerings:

**Which Distro?**
IMHO Xubuntu seems to be the best all-round contender for the job - sure there are smaller distros, but xubuntu installs very easily for the novice and gets you going with Xfce  straight from the install

**Which GUI**
Xfce is a good choice for low system requirements but with good usability - preconfiguration - and varying degrees of eye candy depending on resources.

**Viewing System Resource Usage**

*Processor time:*
The "top" command is a shell version of a system resource monitor. Simply type "top" in a terminal and it will list the processes using the most processor time. It updates the list every 4s or so. Press "q" to quit.

*Memory Usage:*
Again the "top" command can be used. To list processes by memory usage type "top" then press "SHIFT+o" then "n" then "ENTER"

*Hard Drive Usage:*
For swap usage you can use "top" again.
To view the amount of drive space taken up by the installed packages use the following command.

dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n

might want to redir to a file and "less" it (add " > ~/packagelist" to the end of the line then type "less ~/packagelist")

(thanks to [http://www.pixelbeat.org/docs/packaging.html](http://www.pixelbeat.org/docs/packaging.html))

**Removing the Optional Extras**
The default install of Xubuntu is a very complete system. However if your happy to go without some of the services/features. You can save valuable resources.

*Xfce Destop*
Xfce lets you use nice bitmap back drops for you desktop and allows you to place icons there too. If you use "top" you'll notice that the Xfce services are displayed separately and you'll probably see Xfce Desktop fairly near the top for memory usage. If your happy to forgo the backdrop and icons then you can disable this feature under Applications > Settings > Desktop Settings.

*Xfce Application menu*
The default install will show pretty icons in the Applications menu. If draws very slowly then try disabling them under (some where in settings - will find later)

*Xfce Multiple Desktops*
If you don't use them then disabling them might save memory. Just set workspaces to 1.

*Xfce Terminal*
Although it looks nice, the Xfce terminal uses alot of memory. Try xterm instead. You'll need to enable the scroll bar and font with:

xterm -sb -rightbar -fn "-*-fixed-medium-r-*-*-14-*-*-*-*-*-*-*"

*Xfce theme*
Apparently the more basic themes use less resource

*Xfce font*
Xfce manipulates the display font (anti aliases etc) to make it look better. If you disable this things might work faster - however it looks pretty bad because true type fonts dont display well at low res. I've tried to find a raster/screen font to use - but not luck so far - any ideas?

*xscreensaver*
Disable this and try the novel approach of turning your monitor off when not in use! Havent tried this one yet.

*Other Possible Extras*
Does anyone know if the following can be disable without adverse affects.

perl - perl is a programming language - why is it running?
xfce-mcs-manage - what is this?
xfce4-panel - is it possible to access applications and current tasks with out this - eg using mouse menus?
xfce4-session - if i don't want to save sessions then can I disable this
Thunar - does this need to be running in the background when Im not using the file manager?
hald - if im happy to manually mount CDs do i need hal?
gdm - is there a way to set tty1 to automatically startxfce4 when logging in, will the system shutdown from xfce without gdm?

*Open Office*
This takes up alot of disk space. If you just want to work prosses then try abiword.
The best way to remove is type

sudo aptitude remove ??? (whats the package name - i've already done this so can tell)


Hope this helps! Please add suggestions / corrections.



If anyone is interested my system is a Toshiba Satellite 310CDT (Laptop).

The spec as best as i can remember it is :
Pentium 200Hz
96 Mb Memory
2Gb HDD
800x600x16M Display

Sadly it runs best with win95. I know this is not a fair comparison but I'm sure i can strip down xubuntu to make it run faster. The default install was very slow. Mostly a memory issue.

I've installed FC1 in the past and now have Xubuntu 6.10 installed. Couldn't use live CD because of lack of memory - however the installation CD worked fine - except i had to update the Xorg setting manually for the LCD display.

---

### Post by Brian Smith on 2006-12-17
Great thread idea.
On my Pentium 1 233, running Xubuntu Edgy, I've found Opera to run much faster than Firefox, making browsing on that machine something I would actually do.

You may have to enable additional repositories in Synaptic, but that is not much trouble, and certainly is worthwhile.  

I think that the biggest limitation on machines this old is not the easily upgraded hard drive, but rather the low amount of memory typically installed in them.  Big gains can be had by adding memory, such that you can make a machine this old actually useful for contemporary internet use, excluding video play.

---

### Post by Wall86 on 2006-12-17
older cpu's are much much easier and safer to overclock, and even a 10% gain in cpu performance would be a drastic improvements (just get a few cheap case fans) 

following the overclocking idea, you might be able to OC your RAM, and other perifirals (PCI, GPU, etc...) 

and since it is an older RIG you do not have to be too too too worried about hardware failure

I learned how to Overclock on a p2 333Mhz, with 256 MB RAM and a rage 128 ;) 

it can be a great (but costly at first) hobby.

---

### Post by Brian Smith on 2006-12-17
> **Wall86 said:**
> older cpu's are much much easier and safer to overclock, and even a 10% gain in cpu performance would be a drastic improvements (just get a few cheap case fans) 

following the overclocking idea, you might be able to OC your RAM, and other perifirals (PCI, GPU, etc...) 

and since it is an older RIG you do not have to be too too too worried about hardware failure

I learned how to Overclock on a p2 333Mhz, with 256 MB RAM and a rage 128 ;) 

it can be a great (but costly at first) hobby.

Though that P90 would probably safely run at 110MHz or even 120MHz, at a risked cost of less than $20 for a replacement of up to 200 MHz, and that would yield a huge performance increase for using, for example, Win95, I think that even Xubuntu is more demanding of RAM being over, say, 128MB than it is demanding of absolute processor speed.  
My 233MHz Pentium 1 with Xubuntu Edgy will routinely run MUCH slower if I have, say, 50 percent of my 128MB "filled" versus 25 percent of it "filled."  I use the devices in the XFCE to monitor resource usage, and a small difference in the amount of RAM already allocated to running processes makes a surprising difference in how long the CPU usage tops out at 100% to complete the same new function.  Perhaps changing the "swappiness" would help significantly, but I'm certain that doubling my installed RAM to 256MB would make a very noticeable difference.

---

### Post by compwiz18 on 2006-12-17
You have no idea how much that extra 128mb helps.  I've got five P2s with 320MBs of RAM running Xubuntu, they originally had 64 and were crazy slow.  I'm using them as servers- they take at least seven-eight seconds to load up one php/mysql page on apache2.  And that is with each one running a different server, ie, one is the router, one is the file server, one is the mysql server, one is apache2 w/ php.  I'm always amazed how slow they can be...

---

### Post by Brian Smith on 2006-12-17
> **sideshowb0b said:**
> 
If anyone is interested my system is a Toshiba Satellite 310CDT.

The spec as best as i can remember it is :
Pentium 90Hz
90 Mb Memory
2Gb HDD
800x600x16M Display

Sadly it runs best with win95. I know this is not a fair comparison but I'm sure i can strip down xubuntu to make it run faster. The default install was very slow. Mostly a memory issue.

I've installed FC1 in the past and now have Xubuntu 6.10 installed. Couldn't use live CD because of lack of memory - however the installation CD worked fine - except i had to update the Xorg setting manually for the LCD display.

When I did a web search for the specs on that Toshiba machine, I found that it was supposed to come with a 200MHx MMX processor, not a 90MHz processor....perhaps you should, for the low cost, replace the processor.  A 144pin SODIMM of up to 128MB is useable, and I think that would be a big upgrade as well.  I think if I had this machine, I would either run Win95 OSR2 on it, or if I needed an up to date browser on it, Ubuntu with an even lighter GUI on it.  Maybe the cost of both a processor upgrade and memory upgrade is greater than replacing the whole unit with an upgrade.  How much did your XFCE tweaks help out?  Have you tried Fluxbox?

---

### Post by kerry_s on 2006-12-18
> 
If anyone is interested my system is a Toshiba Satellite 310CDT.

The spec as best as i can remember it is :
Pentium 90Hz
90 Mb Memory
2Gb HDD
800x600x16M Display

Dude with those specs i would go totally custom install. Grab the alternate
 [http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso)
or
 [http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-alternate-i386.iso](http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-alternate-i386.iso)

Do command-line/server install

login

sudo su

nano /etc/apt/sources.list
comment(#) out the cdrom & uncomment all the repos(they start with deb)
ctrl + x & y & enter to save

apt-get update

apt-get install x-window-system-core gdm xfce4

reboot

for fluxbox->
apt-get install x-window-system-core gdm fluxbox emelfm leafpad synaptic

---

### Post by sideshowb0b on 2006-12-18
Brian:
Ah the shame! - It seems you know my machine better than me - I've done the relevant edits above. On upgrading - I thought laptop cpus were hardwired into the motherboard  - I'll have to open mine up and have a look. I've already used the memory slot - i think the upgrade to 128Mb is either not around any more or is very expensive.
Good point about browsers! Have you ever tried Dillo tho - apparently it works quite well on slow machines. 

I like your idea about swappiness - any tips on how to tweek this?

Im surprised you suggest using win95 on the ubuntu forum - can't you get kicked off the forum for that sort of thing (lol). But seriously, surely its possible to configure Xubuntu to run as fast as win95. Its along time since I had win95 on the machine - so maybe it ran slower than i remember - however i did have a usb tv tunner plugged in running full screen video at one point. In Xubuntu the example ogg videos run at about 1 fsp and the image doesn't display correctly. This could be a hardware setup problem tho?

I've managed to speed up Xfce considerably. The default install used practically all my memory. Turning off the desktop management made some free, but run a few programs and it soon grinds to a halt(ish). Turning of the menu icons made them much faster and obviously xterm is much faster than xfce-terminal. I does seem that Xfce is becoming more bloated as time goes on. Perhaps i should look at fluxbox?

Walls:
Good ideas - do you know of any websites that show you how to do this. I've done it the hardware way before (changing jumpers) but that was on a desktop machine. Can you do anything via the os? I don't think the bios settings on my laptop allow any clock changes.

Kerry:
Sounds interesting. I'll have to do some digging on the alternate install CD and flux box. I'm assuming I can get to a similar point from where I am now by uninstalling unnecessary packages. Perhaps not the best way to go about it in retrospect.

---

### Post by compwiz18 on 2006-12-18
A clean command line install can run in 22MBs, so that is all that is really required.  However, I can imagine that one you get XFCE up, you start eating RAM:twisted:

---

### Post by kerry_s on 2006-12-19
> Kerry:
Sounds interesting. I'll have to do some digging on the alternate install CD and flux box. I'm assuming I can get to a similar point from where I am now by uninstalling unnecessary packages. Perhaps not the best way to go about it in retrospect.

Yes, the difference is you have more control from the start. You actually build your own system, you select exactly what you want installed. I haven't used a full desktop in ages.lol, i always prefer to make mine from the ground up. You can save alot of space & get a really fast system. I even have a install of fluxbox & thunar, it's like xfce4 on steroids.lol. The thing is, once you learn the basic steps you can build your system to your exact needs with only the applications you want. Right now i'm playing with a feisty build up just using it to mess around & test application(currently playing with seamonkey browser :D  ) 

Here's a pic, look at the size of my install(594mb with cache) with out the extra apps i usally run around 450->500mb, my memory usage at start up before i start opening apps is 3%

---

### Post by K.Mandla on 2007-01-10
For my money, starting with a clean server install and adding Openbox is the fastest and most functional system you can get. It takes a little setting up, but is worth it in the end. And I've made systems that took up about 550Mb and reached the desktop on 19Mb.

FVWM-Crystal is just as good, and has the added benefit of some highly configurable eye candy. Straight FVWM is equally quick, but unlike the Crystal version, is so ugly that I don't even want to take the time to fix it.

After that, Fluxbox or IceWM. Those are both as fast, but have peculiarities I don't care for. 

Just my $0.02.

---

### Post by halw on 2007-01-10
Following is a link to Installation on low memory systems. I found it to be a valueable resource when setting up my old Toshiba 2545xcdt laptop (AMD K6 333 MHz w/192 MB ram) with dapper.

Link: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

