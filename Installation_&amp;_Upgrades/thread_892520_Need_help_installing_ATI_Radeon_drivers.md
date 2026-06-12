---
title: "Need help installing ATI Radeon drivers"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Yesideez on 2008-08-17
I've a complete Linux novice yet no computer novice at all.

As you know when it comes to installing drivers with Windows you download the desired driver and run it as an executable.

I'm trying to download the drivers I require for my system so I have as painless install as possible yet I'm already banging my head against my monitor...

Even trying to download a driver I've tried following guides to install (can't find a single driver for my Radeon X1650 Pro PCI-e card) and those I have found (for other components) seem to make sure I have certain versions of whatever installed yet doesn't say how.

Trying to follow a post here:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat87-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat87-inst.html)
> Un-installing the ATI Linux Proprietary Driver is dependent on the mode of initial installation.
How do you uninstall?

> Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
Which is where and called what?

> With super user permissions, enter the command "sh ./fglrx-uninstall.sh"
Which is set where?

I hope this shows how much of Linux I'm just NOT understanding.

Someone who used to live in the house in a room upstairs has Ubuntu installed on their laptop and they say installing drivers can be a nightmare but I can't ask them for help now as they've recently moved out.

I know Windows needs drivers for practically everything and I've no idea what Linux can talk to natively with no need for drivers.

Am I missing something or is this really as painful as I'm finding it?

Many thanks in advance.

---

### Post by Sorivenul on 2008-08-17
Not my specialty but I checked the Ubuntu Wiki page [HERE]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").
Find the specific instructions for your version of Ubuntu (looks like you're using Gutsy/7.10?), and follow them.

---

### Post by pparks1 on 2008-08-17
Quite often, most hardware just works right out of the box with Linux.  So, there isn't as much of a need to install so many drivers as most of them are just built into the system.

With video drivers...video cards often work right out of the box as well. However, to take advantage of 3D and other visual eye-candy effects, you often have to install the 3rd party drivers. 

With Ubuntu 8.04, you often get a prompt at the top of the screen indicating that restricted drivers are available for your hardware.  You click the little green card icon, follow the prompts, enable the driver, it installs the software, your system reboots and you are using the new driver.

The other option is to head out to the respective Vendors (ATI or NVIDIA) and download their driver and then install these.  This can often get a little hairy and to be honest, I've had very mixed results myself.

I've got a guide that I put together on another forum for users very new to Ubuntu to get their boxes up and running.  Take a look at this, and very much the 2nd post as it deals with video drivers, etc.
[http://itcertforum.com/forum/showthread.php?t=205](http://itcertforum.com/forum/showthread.php?t=205)


It's unfortunate that many guides don't cover exactly what has to be done...but always keep in mind that there are tons of different Linux distros out there and none of them handle these prerequisite instructions in the same way.  So, rather than tell you how to do it, they often just mention what you need.  The expectation is that you either know how to do it, or you turn to forums like these to find out what you need to do.

And as a seasoned Linux guy for about 8 years+, I'm not exactly sure that I would say "Linux is easier" than Windows.   So much hardware, software and retail stuff is geared toward Windows or Mac's and these systems are quite rigid...so it's easier to have standards here.   I think the beauty of Linux is the freedom to do 1). what you want 2). at literally no cost to you 3). without the worry of viruses, trojans, etc.

---

### Post by Yesideez on 2008-08-17
Thank-you very much!

I'll get reading that straight away :)

---

### Post by snowpine on 2008-08-17
To answer two of your other questions:

The Terminal (aka Command Line or Console) is in your Applications-->Accessories menu. 

You gain superuser (or root) permissions by prefacing the command with 'sudo' (or 'gksu' if it's a graphical application). 

For example, to install a package named 'package' using the command line: 

sudo apt-get install package

or using Synaptic:

gksu synaptic

:)

---

### Post by Yesideez on 2008-08-17
Thanks, all the information I can get on this certainly is helping me to understand how this all works.

I remember when I first went to Windows after programming the Amiga for many years was a bit of a minefield but I stuck with it and now know XP almost inside-out.

It's just going to be a "fresh start" where learning the OS is concerned!

---

### Post by estyles on 2008-08-17
IMHO, Linux will be easier to use for the completely naive user who already has Linux installed on his/her computer, and all of the hardware is already tested to work, with programs and codecs already setup and installed.  This is similar to how a new PC is delivered with Windows on it (minus the 800 "trial" versions of AOL, and whatever other crap programs are preinstalled), so it's not ridiculous to expect such a thing.  Not many companies sell Linux preinstalled, so those naive users, if they're going to use it, need someone with more experience to set it up for them.

Linux is also easier for true experts who want to make low-level changes to their PC and find themselves annoyingly shut out of stuff in Windows.  You will also find that standards compliance is a complete joke in Windows - they don't even follow their own file formats or standards they created.

Linux may or may not be easier for the intermediate user who has installed Windows before but never tried Linux.  Like in your situation, you're looking for drivers before you install, but in 90% of cases, you don't need to get separate drivers.  The restricted (non-open source) drivers just require one or two clicks to enable on Ubuntu, stuff like network connections (not wireless, though, unfortunately) just work (I've never had a clean windows install where I didn't have to install motherboard drivers to be able to use the on-board ethernet - which can be a problem if you lost your disk and are trying to get the drivers from online.)  

To be honest, there's a good chance that an intermediate user will have a few problems and some frustrations.  I put myself firmly in this group, and I have to say that the frustrations are well worth it.  And besides, anyone who has dealt with a windows installation long enough and who plays around with it like I do has had more than their fair share of frustrations with windows as well.  Ubuntu, at least, has much better community support.

---

### Post by Yesideez on 2008-08-17
Better support is one thing I've noticed already which is why I'm so hooked on getting this running.

I've decided to install this on my spare 80GB drive (question in another thread) so I can give it a good run.

---

### Post by Tx_Rx on 2008-08-17
I'm in complete agreement with most (if not all) of the above. If you've got some pretty regular hardware in the PC/laptop then you are pretty much going to have an easy time of it. 

If you don't then the support systems/forums/web do have a tonne of help, which granted can be somewhat overwhelming to new comer to Linux/Ubuntu but most of the time does get your problem sorted.

I must confess the synaptic package manager is great and it's actually a great way to save you scouring the web for apps and tools which are compatible etc.

Will say that I've ko'd a few installations on my PC & laptop but it's probably because I'm experimenting and learning all about it. Another good thing is that it's so easy to re-install!

---

