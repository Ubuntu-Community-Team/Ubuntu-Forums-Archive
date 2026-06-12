---
title: "ERROR: Unable to find a medium containing a live file system."
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by cocobrotha1 on 2009-12-24
Wassup ubuntu tribe, i'm having like this uber problem installing ubuntu 9.10.  i have 2 custom built computers, 1 with XP, the other is a modded version of XP. Now, i taken all of my files and goodies out of modded tower and wanted to install 9.10. But, when i install it, it starts at the installation screen, then no matter what choice i make it takes like over a minute to load, then i get a white ubuntu logo gleaming off and on, then black screen. Then i get an error message once i press any of the keys. So, can someone please explain to me what am i suppose to do next.  

Custom build specs:

AMD athlon XP (2GHZ)
PC 2700 (1GHZ)
Asus-A7V8X
GeForce FX5500 256mb
Win XP Pro (Black Edition) Modded.

---

### Post by tommcd on 2009-12-24
The first thing you need to do is to rule out a bad CD. 
How did you burn the CD? If you are burning it from XP, try using Iso Recorder or Infra Recorder, and be sure to burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then when you boot the CD, first choose the option "check CD for defects". This will take a minute or two to run. If it passes the check, then the CD is good.
If the CD is good, and you still get the error message, then post the error message you get here.
Also try running memtest from the Ubuntu CD for a while, like a couple hours at least, to check if the RAM is good. Your 1GB RAM should be enough for the live CD.

---

### Post by cocobrotha1 on 2009-12-24
Well i used Nero 8 in windows. The slowest speed i could take it down to was 12x.  As for me posting the message, its in the thread title. I'll have 2 write down exactly what it says on the error screen.  when i type help it gives me a list of commands in order for me to i guess, fix the problem. I don't understand/or know any of the commands for me to work my way to fixing it. That's gonna take me a heck of a lot of time.  I had 8.04 version a while back, but never was able to get flash to work properly on that one. anyway, this problem i'm having big time. Tommcd, thanks for taking the time to help a brotha out.

---

### Post by the_darkside_986 on 2009-12-24
I'm having the same problem here trying to boot up 9.10 on a Compaq Presario (one of the most Linux-hating devices I've ever had the misfortune of purchasing); I checked the md5 sum and burned at the correct speed. Other, old distros with stale software don't give this error.

At the busybox prompt I can't find any CD device at all under /dev. The sda ones show up though.

---

### Post by tommcd on 2009-12-25
> **cocobrotha1 said:**
> Well i used Nero 8 in windows. The slowest speed i could take it down to was 12x.  As for me posting the message, its in the thread title. ...
So did you run the option to check the CD for defects? That should always be the first thing you do when installing Ubuntu, especially when running into problems like this.

---

### Post by tommcd on 2009-12-25
> **the_darkside_986 said:**
> I'm having the same problem here trying to boot up 9.10 on a Compaq Presario (one of the most Linux-hating devices I've ever had the misfortune of purchasing); I checked the md5 sum and burned at the correct speed. Other, old distros with stale software don't give this error.
At the busybox prompt I can't find any CD device at all under /dev. The sda ones show up though.
Try googling the exact model number of the Compaq +Ubuntu, or +linux and see what turns up.

---

