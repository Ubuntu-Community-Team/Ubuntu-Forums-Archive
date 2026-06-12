---
title: "Install freezes on load screen 10.10"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by kkozuch1 on 2010-10-18
Hi, new to installing linux, but i have recently downloaded the 32 bit version or 10.10. I have followed the directions on the ubuntu website to create both a bootable usb, and disk. I have tried both ways to install ubuntu on a separate HD from the windows 7 install. Both ways have failed at the same spot. It will boot into either the cd or USB, but once it gets to the ubuntu screen with the 5 dots  that change from white to orange, it freezes after a few minutes of loading on that screen. I Have tried to download ubuntu multiple times to make sure it just wasn't a bad download but i get the same result. Any help would be appreciated.

---

### Post by Kainakos on 2010-10-21
I have the same problem though my screen doent freeze it just keeps loading forever :(
I tried 3 different usb sticks and both 64bit and 32bit version from the site. :confused:

---

### Post by fungisamongus on 2010-10-23
Having the same issue here looking for answers. 
I am new with ubuntu, I'm installing ubuntu 10.10 64bit. After the install process I don't get anything except a frozen and scrambled screen that freeze up and then I am forced to reboot. 
I have ran the live CD and ubuntu with out installing. Everything works. Also check disc for errors and everything worked before the install.
I am not sure what to do or how to fix it. 
Any help would be great. Thank you

---

### Post by Ubrotun on 2010-10-25
Bumping thread. Having the EXACT same issue.

---

### Post by fungisamongus on 2010-10-25
> **Ubrotun said:**
> Bumping thread. Having the EXACT same issue.
  What kind of computer are you loading on to?

---

### Post by ronbrooks on 2010-10-25
I am having the same trouble with my lap top HP 9000.  I can load and install the live cd in my two desk computers. I know that the cd must be okay as it would not load at all if it was bad.  I have the up to date drivers for my video card. I have been looking around the net but now solution yet. The live cd 10.04 will load okay.  Any help?

---

### Post by bruteforce05 on 2010-10-25
I am having the same problem.  I have a nine year old windows XP machine.  I put G Parted on a seperate CD and was able to use it, but didn't know what I was doing in the command line stuff, basically guessing.  I ended up at the graphical interface where I think I did it right.  But I get hung up trying to boot up with the Ubuntu boot disc where the dots are blinking over and over with the word Ubuntu, never does anything.  I hope someone can get an answer for this, maybe a glitch in this new release?  I'm real close to becoming brand new to Linux if I could get it installed.

---

### Post by mooseye on 2010-10-26
Same here but my diac loaded on wifes laptop with no problem. It just hangs on this xp box.

> **bruteforce05 said:**
> I am having the same problem.  I have a nine year old windows XP machine.  I put G Parted on a seperate CD and was able to use it, but didn't know what I was doing in the command line stuff, basically guessing.  I ended up at the graphical interface where I think I did it right.  But I get hung up trying to boot up with the Ubuntu boot disc where the dots are blinking over and over with the word Ubuntu, never does anything.  I hope someone can get an answer for this, maybe a glitch in this new release?  I'm real close to becoming brand new to Linux if I could get it installed.

---

### Post by suneil9 on 2010-10-26
I also have this problem! If there are any diagnostic tools to help with figuring out the problem, that would be a good start.  Thanks!

---

### Post by Lokiii on 2010-11-01
Same issue here...

---

### Post by peskykid82 on 2010-11-01
I am also new to ubuntu.. I have a question for all of you because I have had a similar problem. As soon as the CD spins up press the F6 key. This brought me to the menu screen.. I can install from there. But as for myself after the install of 10.xx the machine hangs there also, basically it will not boot the Os.. Hopefully this will help. Good luck!

---

### Post by Michael Norris on 2010-11-04
Same problem here.
Running eeepc 1001HA and have tried installing both Desktop version and Netbook Remix and have tried multiple USB sticks.

---

### Post by jjaakkol on 2010-11-04
> **Michael Norris said:**
> Same problem here.
Running eeepc 1001HA and have tried installing both Desktop version and Netbook Remix and have tried multiple USB sticks.

There seems to be already punch of people who has same problem. I have it too.

I have had Ubuntu 10.04 in my laptop previously...but with Wubi install. It was broke after some updates so removed it and now I have tried to install Ubuntu from Live CD or USB.

Story is here:
[http://ubuntuforums.org/showthread.php?t=1604104](http://ubuntuforums.org/showthread.php?t=1604104)

---

### Post by jjaakkol on 2010-11-06
> **jjaakkol said:**
> There seems to be already punch of people who has same problem. I have it too.

I have had Ubuntu 10.04 in my laptop previously...but with Wubi install. It was broke after some updates so removed it and now I have tried to install Ubuntu from Live CD or USB.

Story is here:
[http://ubuntuforums.org/showthread.php?t=1604104](http://ubuntuforums.org/showthread.php?t=1604104)


Finally I got my Ubuntu working. :D

UBUNTU installed  with "Alternative downloads" from CD
[http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download](http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download)

After that desktop was still not working. Initially I did not have any desktop installed, only prompt.
From prompt I installed desktop with "sudo apt-get install ubuntu-desktop" but desktop was still not working. 
But from Grub2 I could choose Recovery mode for Ubuntu

So solution was:

1. picked up NVIDIA graphic card driver matching to laptop hardware from NVIDIA site to USB stick
2. Started ubuntu with recovery mode

In recovery mode you need to give command to be able to install driver:
3. telinit 3 (it will ask your username and psw what you gave in installation)
4. mkdir /media/usb
5. mount -t /dev/sdb1 /media/usb (you can check your usb stick "dev name" with sudo fdisk -l)
6. cd /media/usb/linux (I had driver in linux directory)
7. sudo ./NVIDIA-Linux-x86-260.19.12.run
Installation should start. I just followed instructions.
8. sudo reboot- f
9. Start Ubuntu in normal mode.

Desktop is OK now! So my problem was in the end that graphic driver in Ubuntu installation "package" was not compatible with my hardware.

---

