---
title: "How to install Gallium3D on Ubuntu 11.10"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by emptycoder on 2011-10-21
Hi, I'm still noob, so please bear with me.
I recenetly had some problems with ATI Radeon HD 5470, so I did some researches and I found out about Mesa Gallium3D Driver.
They were so many posts and different insturctions so simply I'm lost!
Would you please guide me how to install Gallium3D step by step please?
And could someone explain me what is xorg-edgers for, in brief?
Thanks a lot!
(P.S. I had to post this thread again, 'cuz I posted on General Help and I got no respond at all)

---

### Post by emptycoder on 2011-10-21
Help?:(

---

### Post by novaraz on 2011-10-25
I don't know too much about Gallium3D in depth, but I can say it works wonderfully for my Radeon Mobile X1400, even better than ATi's drivers (used to) work. xorg-edgers is kind of an experimental repository for bleeding edge packages dealing with xorg, including the Gallium drivers. Since its cutting edge, you can screw up your system if you don't known what you're doing.

Disclaimers aside, to install Gallium drivers (assuming you have a compatible chipset), open a terminal and type
```
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update
sudo apt-get upgrade
```

Reboot and hopefully enjoy some 3D acceleration. I recommend Minecraft :)

---

### Post by deimosaffair on 2012-03-14
Hello, 

my first post, yay!!!

so, i'm noob at this. long story short, i hate fglrx. not switching my card to nvidia. so, before i start running ubuntu on vm, i want to give a go at the radeon open source driver.

i have the same question, after removing catalyst, how to install the whole OSS thing? 

quote:
Disclaimers aside, to install Gallium drivers (assuming you have a compatible chipset), open a terminal and type
```
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update
sudo apt-get upgrade
```


i don't understand this, the "upgrade" option on man page says: 
upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new versions
           available are retrieved and upgraded; under no circumstances are
           currently installed packages removed, or packages not already
           installed retrieved and installed.



this means that if don't have the radeon OSS already installed, they will not install. also, making an unnecessary upgrade to all packages seems overkill and asking for another month reconfiguring a currently stable machine(apart from the driver, that is :))

so, what do we need/want to install? xorg radeon package? mesa/gallium?  something else? all the above? in what order? and are these packages old versions? if so, what would be the best option, get sources and compile? questions, questions...

anybody out there who "just installed" all this like they're eating a cookie, could give some instructions as if i had brain damage?  :D

---

### Post by novaraz on 2012-03-14
If I run a <code>lsmod</code>, it seems the Gallium drivers are running from the 'radeon' xorg driver package, so I believe the package you need to install/update is 'xserver-xorg-video-radeon'.

```
sudo apt-get upgrade
```

will indeed install all the latest packages, but it's exactly the same packages that the GUI Update Manager installs. If you are tweaking your system to the degree that standard updates are causing instability, you probably know how to install just the drivers you want. Otherwise, the upgrade option is both safe and desirable.

Side note: This is an old thread, I've updated to 11.10 since my last post. <code>glxinfo|grep Gallium</code> reports that the render is Gallium 0.4, and on my x1400, there are significant text corruptions. I haven't had time to look into solutions.

---

