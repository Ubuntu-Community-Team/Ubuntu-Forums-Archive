---
title: "X Server Fatal Error: No screens found"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by nauthez on 2006-10-27
Alright, I downloaded ubuntu 6.10 and I ran the disk. When it comes to the part of loading the x server, it gives me the error "Fatal Error: No screens found" so I can't countinue or install it. I have an nVidia FX 5500 video card and I want to know if theres some way of fixing this or bypassing it. Im also a newbie at ubuntu, so I don't really understand much about it, and I wanted to know if someone could help me. Thanks

---

### Post by cuplex on 2006-10-27
same problem here! i waited for edgy to make a clean install! well after getting those error on a64 disc and i386 disc i booted to dapper and updated via aptitude! well fine update only problem was i had no clean install and my xserver didnt start until changing driver to vesa!

anyone can help? is there a way to tell the livecd that it should vesa?!

well the dapper dvd worked fine! livecd bootet in safe graficmode and from there fine install!

regards

---

### Post by gabrieliscool on 2006-10-27
I also have this problem, but luckily, I have a built in Intel Video Card so I'm using that.

Here's A link to a thread I posted, hope it works.

[http://ubuntuforums.org/showthread.php?t=282638](http://ubuntuforums.org/showthread.php?t=282638)

---

### Post by nauthez on 2006-10-27
the thing is that on mine, I get the error while running the live cd. I don't know how to install it by command prompt and the only other way I know is live cd and click on the install icon on the desktop.

---

### Post by frodon on 2006-10-27
Before doing anything else, please everyone who have this problem run this command and reboot, it will solve the issue for some of you :
```
sudo aptitude reinstall linux-restricted-modules-2.6.17-10-generic
```

---

### Post by nauthez on 2006-10-27
Alright, since I don't know how to do anything, how do I put in the code on the live CD?

---

### Post by frodon on 2006-10-27
Sorry, this is for an install not with the live CD.

---

### Post by Timothy Butwinick on 2006-10-27
You need a working Internet connection to use that command, right? I have the same problem with X on my laptop (apparently, it cannot find the "vesa" driver). Moreover, ndiswrapper fails to start wlan0, and eth0 does not work either. 

I think my problem is due to my stupidity when upgrading from Dapper Drake:
I was told to run 
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```
I only ran apt-get dist-upgrade *once* before rebooting, so upstart was not installed. However, I managed to make my wireless card working after the reboot, by first removing it, then reinsering it again. This has only worked for me that one time. I managed to run another apt-get dist-upgrade, but it did not solve the problem. 

Can I activate wlan0 or eth0 from the command line?

---

### Post by nauthez on 2006-10-27
How can I install it using the CD? Everytime I boot on it, it goes into live cd instead of installing. Is there a way of installing it without having to resort to the "install" icon on the desktop?

---

### Post by dreamsayer on 2006-10-27
> **nauthez said:**
> Alright, I downloaded ubuntu 6.10 and I ran the disk. When it comes to the part of loading the x server, it gives me the error "Fatal Error: No screens found" so I can't countinue or install it. I have an nVidia FX 5500 video card and I want to know if theres some way of fixing this or bypassing it. Im also a newbie at ubuntu, so I don't really understand much about it, and I wanted to know if someone could help me. Thanks

When the CD first boots, try selecting the safe graphics mode option. See if that helps.

---

### Post by nauthez on 2006-10-27
tried it and it gives me the same error

I also wanted to know if any older versions work, and if so, can it be upgraded to 6.10 after I isolate the problem?

---

### Post by nauthez on 2006-10-27
alright, I managed to install ubuntu by removing my video card and using the motherboard one. I did the steps you told me in the terminal, and whan I put the card in again, it gives me the same error.

---

### Post by tedwick on 2006-10-27
having the same problem. same thing happens in safe mode and regular install. does the boot splash deal, then hangs for a while. then it goes into the blue x screen, saying "fatal server error: no screens found"

i'm wondering the same thing. can you upgrade straight from 6.06 to 6.10?

---

### Post by nauthez on 2006-11-01
so, any help? I heard that all nvidia cards are supported, yet mine won't work... card is an FX 5500

---

