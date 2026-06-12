---
title: "[SOLVED] No Video"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by bluewhale on 2008-02-10
Hello, my name is noob. 

I've played with Linux variants for ~ 10 years. Each time I run into a problem that would take me 2 minutes to google to a resolution in XP, however I haven't the vocabulary to do that with Linux. Someone just went chasing his doctorate after working in our office for a few years: he is a Ubuntu person. He was infectious. ( no, I haven't looked for a vaccine yet )

I just replaced the MB in my 1+ year old 'gaming' machine, intending to set it up as a Linux Media center as well as a VMWare server for things that require Windows. The CPU is an Intel 6600, the video card a 8800 GTS.  4 gigs of RAM. 

But I've run into a problem I have seen the past 2-3 years when I've tried to get interested in Linux again: no video output after the initial splash screen. This time I tried again and went into 'safe' mode from the Ubuntu CD: no change. 

As I've seen this behaviour 1-2 dozen times on different hardware I assume it's a known issue(?). 

Two possible related things: The only HD in the unit at this time is an 10k RPM 150 gig unit. It still is partitioned for Vista ( EWWWWwwww!! )  The other thing is that on THIS rig I'm getting non stop short BIOS beeps after about 90 seconds of no video output. Might be a bad MB: I'll call Intel in the morning. 

But would love to find out what I can do to get around the 'no more video when installing' issue. 

Thanks

Paul

---

### Post by varnil on 2008-02-10
You claimed to have a vista partition and so i assume you have it installed (Only logical). Anyways boot into windows and check/upgrade the bios in your graphics card (use the nvidia tools... I personally don't know how to do this as i've never had an nvidia card). Anyways, once you eliminate that as the source of the error install the nvidia xorg drivers. (just use apt get [i don't remember the specific package name just google for it or find an faq on this site])

---

### Post by Partyboi2 on 2008-02-10
try using the [alternate]("http://releases.ubuntu.com/releases/7.10/") cd which is textbase installer. Once you have ubuntu installed you will need to install the correct driver for your video card. (need working internet connection)
Boot into recovery mode and get to a terminal
at the terminal
```
apt-get install  build-essential
```then get the driver
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```then start the installer
```
sh NVIDIA-Linux-x86-169.09-pkg1.run
```then
```
dpkg-reconfigure xserver-xorg
```choose the nvidia driver and answer all the questions if unsure choose the default ones.
then
```
startx
```or to reboot into normal mode
```
reboot
```

---

### Post by bluewhale on 2008-02-11
Thanks for the detailed instructions.

I brought the unit to work today and tried a spare video card I keep around 'in case'.  It's an  XFX GEForce 7300LE.  Ubuntu boots all the way with this card.  Is it better to install with a card like this then change the video driver to the other card, or better ( reliability ) to find the appropriate driver and use when doing the initial install?

---

### Post by Partyboi2 on 2008-02-11
I have read of some people installing and changing the video card over afterwards and reconfiguring xserver with success.. I am not aware of any place in the installation that allows you to install restricted drivers. (Please correct me if I am wrong somebody) Another option is the alternate cd. After you have installed ubuntu  on the first boot with the 8800gts you will need to follow those instructions (previous post) and install the correct driver for the card.

---

### Post by bluewhale on 2008-02-12
I haven't actually installed Ubuntu yet: The HD in question still has Vista on it. ( I've disconnected the 750 gig XP drive as that has all of the files I wanted to save on it )  

I've booted to the installation desktop for Ubuntu and left the system there. 

I can easily get a cheap GEForce card like the one I temporarily have in the unit. But hate to waste a $500 ( then ) video card. :-k  

I've read a few web pages on setting up a Ubuntu or Linux media center machine. Would the better card noticeably improve media center tasks? Transcoding movies, playing WINDOWS games in a VM session. etc. 

If I really don't need the card I may try selling it. 

Thinking on it my use would be media driven: who has time for games?

---

### Post by Partyboi2 on 2008-02-12
I don't think you will have  a problem with your 8800gts card once you have the correct driver installed for it. So why not install ubuntu  with that card and see how you go with its performance, if you are not satisfied with it after some use then sell it, like you said why waste $500? 

If you are planning on dual booting or triple booting you will need to shrink the vista partition with the resizing tool that comes with vista. If you plan to wipe vista then it does not matter.

---

