---
title: "Install step fails: Select and install software"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by TechieSteve on 2011-01-07
Hi!
Welcome to my 1st post!

I'm an OpenSuse user wanting to try something different.

Ubuntu Studio has caught my attention. I had a brief play with an older version a while ago and liked what I saw.

Im having problems installing though.
I've downloaded the 32bit version from the studio website link, and burnt the DVD.

However the install always fails at the same stage: Select and install software.

The error message is not specific, and no more information is given other than the step has failed.

Any ideas what could be causing this? Ive tried to burn the DVD several times, on 2 different machines, but no luck so far.

What could be going wrong?

Steve

---

### Post by TechieSteve on 2011-01-11
Still having problems with this.

I have checked the downloaded file has the right MD5 checksum, and burnt the DVD (on 2 different machines, accross 3 different OS's, using 2 different kinds of DVD) several times, verifying each time, and yet the install always fails at the same step.

Whenever I then check the Installation media (from the install menu) it fails, and tells me it has failed the MD5 checksum.

What gives? Where on Earth could this be ging wrong guys?

Any thoughts welcome.

Steve

---

### Post by cchhrriiss121212 on 2011-01-11
Possibly an installer bug. What software options did you select at that step? I will try to replicate it.

What version of Ubuntu is this?

---

### Post by TechieSteve on 2011-01-11
Ubuntu Studio 10.10

I have tried selecting all the software options (IIRC they were: 2D/3D graphics utilities, Audio creation, video creation, and audio plugins) and none of them, and I get the same problem.

I may try to install it from a USB instead, thus bypassing any DVD burning problems. Just trying to figure out how to do that.

I have the ISO, I'm now just trying to work out how to make a USB stick bootable (from within WinXP)

Thanks

Steve

---

### Post by cchhrriiss121212 on 2011-01-11
You might find it easier to install regular Ubuntu then add the studio packages you want from synaptic, it is all in the main repos.

---

### Post by leeper69 on 2011-01-13
Hi 

I have just installed ubuntu studio on my duel boot system and installed grub from that install during the setup which was done online starting with a usb drive it looked allot like the debian installer when I got to the add software section it said you could choose any number of choices but I blew it when I chose the 2d/3d... section and hit enter the install went on and I chose to install grub2 which I would regret after my first reboot.now my first choice in grub is ubuntu studio which only boots to a shell prompt. Fortunately all my other distro's  are still intact. 

 My question is what is the apt-get string to install all of the gnome package?

I just copied the ISO file to my computer then used unetbootin to install the ISO to my usb drive. Rebooted to the usb drive and away you go. You must pick install ubuntu studio from the unetbootin start up and be careful not to make the same mistake I did when you get to the add software section.

---

### Post by wdqss on 2011-01-14
Hi, you can download Ubuntu form [http://download.chinaunix.net/disc/linux/](http://download.chinaunix.net/disc/linux/),
 
 I aready download Fedora, and install is ok. but my computer is P4 desktop

---

### Post by TechieSteve on 2011-01-14
> **cchhrriiss121212 said:**
> You might find it easier to install regular Ubuntu then add the studio packages you want from synaptic, it is all in the main repos.

Yes, this is what I am going to do. Thanks.

I downloaded the latest version, burnt it to CD and popped it into a work PC for a quick look. Worked great - detected the work network and everything, and it looks real nice.

However, it won't load on my home machine as it can't get past the "checking battery status" part, but I will post seperately about that.

Thanks again.

Steve

---

### Post by ubuntu27 on 2011-01-16
I am having the same trouble with Ubuntu Natty daily CDs as well.

It gives out a red warning "Install setup failed: Select and Install software" 

I am running it using VirtualBox 4, but I see on the web that other users are experiencing the same thing, so it seems to be a Ubuntu Natty bug.

---

