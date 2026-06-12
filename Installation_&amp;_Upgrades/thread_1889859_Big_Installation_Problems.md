---
title: "Big Installation Problems"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by blazerboy777 on 2011-12-02
So In the last 6 hours...

1) downloaded ubuntu 11.10 32 bit
2) tried installing it as a dual boot next to windows 7 64 bit
3) Botched my entire windows instalation in process
4) Decided to "Screw it all" and just chose wipe entire disk and install
5) Upon completion got a black screen with a white blinking cursor.

This is ridiculous and my installs are taking forever "Retrieving Files" and "downloading language packs" Iv done this 3 times tonight...

I must be doing something wrong....anyone wanna lend a hand? I go out on a limb try it out, awesome ubuntus awesome, but installing it is really this difficult?

---

### Post by Blindleistung on 2011-12-02
when you get the blank screen, can you tell if the system is alive (without graphics)?

If you have another machine available, try to ping it or log in on SSH over your network.

If SSH works, you could get at the system errorlogs to look into (or post some here).

---

### Post by blazerboy777 on 2011-12-02
I had to reinstall (another 30 minutesish) Then had to update that took another hour cuz of slow download speeds. (200 kBps) Anyways....now i have another problem. Driving me nuts. I dont know how to install this dumb gpu graphics drive, linux 32 bit....gtx 470 driver. It took me 2 hours to figure out the commands for root access, killing off xserver, deleting nouvenou (i think i did) and I dont even think it worked. This is all just a huge headache, why is it taking me hours upon hours to install just a simple driver....im not even making the driver....and i cant even find a guide that works, im pulling bits and pieces from different guides to try to make it work...commands arent being found in terminal, just if someone can link me to a guide to installing a graphics driver for gtx 470 ubuntu 11.10. Would be so grateful, and also, if its installed it would say it on the system information right? Cuz right now it just says unkown graphics and standard...and my box has sli gtx 470s....kinda pissing me off.

---

### Post by collisionystm on 2011-12-02
try this

[INDENT]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current




from here [http://www.hecticgeek.com/2011/10/how-to-install-latest-proprietary-nvidia-drivers-in-ubuntu-11-10-oneiric-ocelot/](http://www.hecticgeek.com/2011/10/how-to-install-latest-proprietary-nvidia-drivers-in-ubuntu-11-10-oneiric-ocelot/)

[/INDENT]

---

### Post by kwildman on 2011-12-02
drop to the command line where it is hanging...

Ctrl + Alt + F1

rename your current xorg.conf file so that a new one is created on the next boot. 

$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.OLD
$ sudo reboot

---

### Post by blazerboy777 on 2011-12-02
Not working....Ugh man.

the systems fine i guess, but i cant install the lousy graphics card ...haha. I think i screwed something up, does this mean another reinstall i dont know. running on no sleep getting aggravated because my entire home networks down need it back up and operational by the weekend...and it doesnt look like its going to happen. I wanted to expand the things I could do with my system and network, and all its doing is giving me a headache nothing you guys are saying is working on my system, I dont know why. Did I install the wrong version maybe? Do i go download 11.04, or do i download the 64 bit or am i doing everything right just someone messed up something somewhere? I dont know.

---

### Post by collisionystm on 2011-12-02
You need to run the nvidia-xconfig

open a terminal

sudo bash

nvidia-xconfig


log out and back in when it finishes 



[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/chapter-03.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/chapter-03.html)

---

### Post by blazerboy777 on 2011-12-02
I did that sudo update thing

It seemed like it worked for the first time and then i got an error


The following NEW packages will be installed:
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 34.4 MB of archives.
After this operation, 102 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) oneiric/main nvidia-current i386 290.10-0ubuntu1~oneiric~xup1
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) oneiric/main nvidia-settings i386 290.10-0ubuntu1~oneiric~xup1
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current_290.10-0ubuntu1~oneiric~xup1_i386.deb](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current_290.10-0ubuntu1~oneiric~xup1_i386.deb)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_290.10-0ubuntu1~oneiric~xup1_i386.deb](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_290.10-0ubuntu1~oneiric~xup1_i386.deb)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by collisionystm on 2011-12-02
can you get on the internet?

try what it says

sudo apt-get update --fix-missing

---

### Post by blazerboy777 on 2011-12-02
What you just said to do made a backup, but nothing changed.

---

### Post by blazerboy777 on 2011-12-02
Ok it went through, I think I might have a problem with my network dropping off after i installed ubuntu causing it not to download. I noticed that before, like my network card keeps dropping my internet for split seconds here and there or something like it.

What am i supposed to do after its done downloading? Like I just did the apt-get install current and it worked and what do i do after?

---

### Post by blazerboy777 on 2011-12-02
Nothing changed still got the lousy no driver standard stuff . Ah this is so complicated man lol

Edit: Went into run level 1 to disable X, booted up the sudo sh ..... to install downloaded graphics driver.

It says there appears to already be a driver installed on your system (versions 290.10) . As part of installing this driver (Version: 290.10) the existing driver will be uninstalled. Are you sure you want to continue

I hit no, but why is this not showing up in system info? If i have the driver "installed"

---

### Post by collisionystm on 2011-12-02
You need to run that nvidia-xconfig

---

### Post by blazerboy777 on 2011-12-02
I did, my nvidia settings pop up show both my video cards so im assuming that its working, but is it integreated into linux i dont know , cuz when i boot up system info it says graphics unknown.

Also another thing, my speed is greatly reduced, im having trouble even finishing a speed test.

ping is good 24ms, but my download is 3.8 and my up is like .3

it should be roughly 12 and 1.5

Could it be that my motherboards ethernet driver isnt installed or something? Cuz the connection drops off too at times like I said, and then comes back, but like I said its about 4 times slower than it should be.

---

### Post by blazerboy777 on 2011-12-03
Ok so I found out the problem through the help of someone on these forums, the problem was that the Realtek R8169 driver was installed but there are problems with it so I had to uninstall it and install the Realtek R8168 driver, so good to go on that front. 

Back to the nvidia gtx 470 problems...I decided to try to just use the propriety drivers (I had to reinstall ubuntu again) but its still not showing up on system info.

---

