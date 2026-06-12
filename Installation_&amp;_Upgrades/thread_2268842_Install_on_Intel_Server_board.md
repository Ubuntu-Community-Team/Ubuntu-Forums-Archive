---
title: "Install on Intel Server board"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by Mike_Ohlhausen on 2015-03-11
Hello, I am having an issue with installing Ubuntu 14.10 onto an Intel SE7520BD2 mother board. All goes well until it says remove the install disk and reboot. I got a message from the monitor saying the resolution was out of range please reset to 1920x1080. Then all went black, and I couldn't see the command line, or anything. I know there used to be a way to modify the video driver behavior on Linux installs... not sure if there still is. 
Here is a list of the hardware I have currently connected. I am at barebones pretty much to test. I don't have any old PCI vid cards, or a PCIe card or I would go that route. 
Intel SE7520BD2SATA2 motherboard
2- Intel Xeon 2.8 processors
1 stick of 1 Gb ECC PC3200 - 400 ram (waiting for the 16 Gb set of ECC to get here)
2 Kingfast 30Gb SSD sata drives
1 Sony PATA DVD drive to install from

Thanks in Adv...

---

### Post by Mike_Ohlhausen on 2015-03-12
Hm, well I finally stuck in a CentOS 6 install disk I had, and poof, it sees the gpu, and all is good, then it ignores the password I am trying to type in, and I can't log into root or my user account. Wow, I see Linux has gotten little further than it was 15 years ago. After burning several DVD's, different flavors, different versions, this hardware, that hardware, search the internet high and low, finally it installs, and you have no access. This is just about as frustrating as I remember. Finicky, glitchy, and not quite prime time. Ok, back to reinstall again.... I was hoping there might be a magic clue here, guess it just has to be certain hardware you must buy. Used to be you had to use old stuff, and Linux was happy. Now maybe it just has to be new stuff? Wonder if Windows installs... or maybe server install is broke, and I can only do desktop... hmm Maybe 14.04, is ok, I'll burn my last disk and see. I guess there is nothing to do but persist and get it myself, since there seems to be no one that has a clue. I always seem to be talking to myself in these Linux forums. Yea, me too, then I think, maybe too much info, maybe not enough info... maybe I smell bad... I don't know. I will try for another week, and end up with some distro I don't really want, a desktop version of that, and hack and slay it to make it look like a server just to get by with something that will somewhat work. Linux is sure loosing it's shine to me. I still have a pile of cd's I burned back then when I was building a simple file server... and I think a personal cloud is somehow possible for this... lofty goal my myopic friend. Maybe, I can burn a freenas disk. Or maybe just ask in each forum and see who answers? then choose the distro according to who accepts new people more readily. I know, at one point I had to hire a guru to come to my house last time since I was so 'dumb' and it only took him 2 days of phone calls, and tech support and coding to get a fancy new 3ware raid card to work in RH7.2... I need a smoke, sigh

---

### Post by Mike_Ohlhausen on 2015-03-12
Ok, so at this point I have installed Ubuntu 14.04 LTS. The monitor complains at boot, no visible console, black screen. So, since I installed SSH server at install, I go to my Windows machine - (Yay Windows! sorry, but it works...) and go to Putty and log into the server. It works, and maybe I can fix the video from here someday... Odds are real good I will be re-installing several times before I actually get it serving any files...

---

### Post by Mike_Ohlhausen on 2015-03-12
Odd, but I installed the VNC server, which needed the core Gnome packages, and opened the server in TightVNC Viewer from the windows machine. Afterwards, when I went back to the Ubuntu box to shut it down, it was up on the login screen for Gnome, which worked just fine. So, the only issue with the video is pre-X, at the command line. So, the server has to have a desktop installed to work on it. Seems counterintuitive... found some hopeful ideas while searching the interweb I am going to try, we shall see if I break Grub....

---

### Post by tgalati4 on 2015-03-12
Turn the kernel [modesetting]("http://askubuntu.com/questions/207175/what-does-nomodeset-do") off.  Yes, the linux installation experience has been remarkably consistent over the past 15 years.

Welcome back.

---

