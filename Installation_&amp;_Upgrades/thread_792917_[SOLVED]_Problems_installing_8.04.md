---
title: "[SOLVED] Problems installing 8.04"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by navy pilot 26734 on 2008-05-13
I'm a relative noob to the linux world, and a recently I have been considering switching to Ubuntu based on a recommendation of a friend and a recent experience with Vista.  I downloaded previous versions of Ubuntu and ran them in vmware with few problems, so when I recently purchased a 1TB HD I figured it was time to try using a dual boot machine.  I downloaded both the (64-bit)live CD and (64-bit)alternate versions of Ubuntu and have had a heck of a time getting them installed.  When I tried installing off the live CD version, my computer kept shutting down with no warning.  After several failed attempts to do it this way I finally tried using the alternate CD and after a few attempts was successful in getting it installed, but once I get into Ubuntu, the computer again shuts off without any warning or error messages.  I would really like to get away from windows so any help you can give me to help me solve this problem would be greatly appreciated.  BTW, my system config is below.

AMD Athlon 64 X2 Dual Core 5200
2.61GHZ   4GB RAM
NVIDIA 8800 GTS
Creative SB X-Fi 

currently running XP Pro (stable)

---

### Post by dstew on 2008-05-13
Did the Live CD desktop run OK? That is, did it only start giving you problems when you tried to install?

---

### Post by navy pilot 26734 on 2008-05-13
I had the live CD up and going for at least 10 minutes with no problems, except that it didn't find all of my hardware. The problems started once I tried to install.  Sometimes the install would get further along than other times.

---

### Post by Landscapeman on 2008-05-13
Im having sort of the same problem. Unable to install

---

### Post by dstew on 2008-05-13
Did you check the CD integrity (menu choice)?

---

### Post by navy pilot 26734 on 2008-05-13
Yep did that after the install failed the first time.  It checked good.

---

### Post by Mr A Mouse on 2008-05-13
Do you have a list of hardware that it didn't find in Live CD mode?

---

### Post by dstew on 2008-05-13
Possibly the Live CD system had some problems interacting with your hardware. Since you were able to install with the Alternate Install CD, it seems like hardware is an issue for Ubuntu.

In Ubuntu, check in the System --> Administration for the Hardware Drivers window. See if any drivers are available there to install. If not, then the next step would be to look at your log files to see if there are some problems. The main log file can be seen with the **dmesg** command. Look for errors in it. Especially valuable are logs made during a crash or lock-up. There are lots of different logs you can check. They are stored in the /var/logs directory.

---

### Post by navy pilot 26734 on 2008-05-13
I can't even get the system to stay on long enough for me to get to the log files, any other suggestions?

---

### Post by Mr A Mouse on 2008-05-13
> **navy pilot 26734 said:**
> I can't even get the system to stay on long enough for me to get to the log files, any other suggestions?

Even in Live CD mode? 

If it won't stay on in Live CD mode, I'd recommend stepping down to the 32-bit version. If that doesn't work ... heck, then I dunno.

---

### Post by Violat3d on 2008-05-14
I too am trying to install 8.04 onto a clean, freshly wiped HD. not looking good...

last night i had the live CD up and running and i had high hopes for Ubuntu (my first Linux OS) i tried 3 seperate CD's, all burned at different speeds (16x,8x,4x) and from the same/different download hosts. all CD's work fine in live mode but when i go to install it gets 50-70% and says there's either missing/corupt/bad data.

i tested my HD, passed with flying colors, tried a sepereate brand new HD... still same issue.

any suggestions?

---

### Post by Mr A Mouse on 2008-05-14
If I remember correctly, there's an option to check the install disk from the install menu. Did you give that a try?

---

### Post by navy pilot 26734 on 2008-05-14
I think I might have solved my problem.  I was reading another post and it was suggested that the originator try updating his BIOS and since I have an ASUS MB also I thought I'd give it a try.  So far so good (the system stayed on for 20 min).  I will let it stay on overnight and see what happens.  I'll report back tomorrow.

---

### Post by navy pilot 26734 on 2008-05-14
Well my system has been up and running for 11+ hours with no problems, so I think I've solved my issue.  I guess Ubuntu was giving the CPU an instruction it didn't understand so it shut down.  Thanks to everyone for your suggestions.

---

