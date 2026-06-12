---
title: "Terrified nooby stuck in install"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by abrianb on 2007-07-16
O.K. maybe not terrified but stuck all the same. I started using ubuntu 6.06 a few weeks ago on a laptop and I like it real well. I saw an issue of Linux Pro on the newstand yesterday with its Ubuntu 7.04 DVD inside promo I thought cool, give it a try. It loaded up on my laptop no problem. So I thought go for it, set up the desktop as dual boot. I popped in the DVD hit restart and then selected install. The Ubuntu logo lights up all is well, then we move to some text followed by a warning that X-org failed to load and the question would you like to see the output. I select ok and then the screen filled with errors such as 
  [138.988981] SQUASHFS error : sb_bread failed reading block 0x7a7c4
  [138.989018] SQUASHFS error : unable to read page, block 1e9ebfdd, size 52f6
  [138.939387] SQUASHFS error : sb_bread failed reading block 0x7a7c4
 This continues to fill the screen over and over the six digits after [138. change but the rest is the same. 
any suggestions ?
  Thanks!

---

### Post by yabbadabbadont on 2007-07-16
Looks like a bad DVD, dirty DVD drive and/or disc, or the disc is damaged in some other fashion.  (e.g. warped, since it was included in a magazine)

---

### Post by Pumalite on 2007-07-16
What are the specs of your laptop please? How did you partition? Is  only 6.06 there now? Does it have a 'Rescue Partition' somewhere?

---

### Post by abrianb on 2007-07-16
My laptop is an IBM T-20, the DVD worked fine and it is now running 7.04 feisty. The problem is my desk top a Compaq presario 4409cl. Intel celeron 1.4ghz , 512mb memory,integrated Direct AGP 3D graphics with 8mb Dynamically allocated as video memory. Mobo ia a Compaq 07a8h.
 Hope this helps. I did not get to the point of partioning.

---

### Post by Pumalite on 2007-07-16
What do you have in your hard drive? XP? Vista? Another distro? I ask you this because you don't seem to have hardware problems. Partitioning is different in XP compared to Vista. I would recommend Gparted, except if you have Vista; then you have to do the partitioning from WITHIN Vista, You have enough memory to run Ubuntu. If you are afraid of graphical interface problems; then go with the Alternate CD.

---

### Post by abrianb on 2007-07-16
Its running Windows xp . No other distros.

---

### Post by abrianb on 2007-07-16
The DVD appears to be flat, it has a feature to test it self. it tests good. The DVD player loaded microsoft office no problem, so I think its good. any suggestions?

---

### Post by Pumalite on 2007-07-16
How did you get the DVD? If it's an iso. Did you do Md5sum? When you install there is a feature that allows you to check the CD or DVD for corruption before install. Did you burn at 4x or less? Did you download the iso? Torrent is better than HTTP or FTP.

---

### Post by yabbadabbadont on 2007-07-16
> **Pumalite said:**
> How did you get the DVD? If it's an iso. Did you do Md5sum? When you install there is a feature that allows you to check the CD or DVD for corruption before install. Did you burn at 4x or less? Did you download the iso? Torrent is better than HTTP or FTP.

He said in his first post that it came with a magazine he bought...  Someone hasn't been paying attention.  :D

---

### Post by abrianb on 2007-07-16
Yes it came from a magazine, Linux Pro, July 2007. It has a test feature and it tested good. It worked fine on my laptop. It failed on my desktop.

---

### Post by yabbadabbadont on 2007-07-16
Since the disk worked on the laptop, I would guess that there is a problem with the drive in the desktop machine.

Edit: Clean the drive (if you have a cleaning disc) or, if possible, swap it out with another.

---

### Post by abrianb on 2007-07-16
I'll give it a try tomorrow morning. For now I'm going to watch the History  Detectives and drink a a wee bit of amber  liquid formerly  known to haunt the highlands.

---

### Post by itzpapalotl on 2007-07-16
Not to probe with endless clarification questions, but the desktop has XP now? and the install is happening from a DVD which if it is like the Dapper DVD i got from the Ubuntu book contains a number of install options, a Live CD option, as well as some fo the repositories.

If you have the option to "Install in Text Mode" try that. Otherwise download the alternate install ISO. I have found that especially on systems in the 1.something Ghz / 512 ram range that installing from the live CD is a hair puller from start to finish. 

Text mode installs are every bit as easy, and in my experience a bit more reliable, If the live cd will run off your box, then you can pretty well count on the installer to get your video drivers right during the install process. 
Also defrag your XP. Then defrag it again just to be sure, and as always, if you care about the info on the drive now, back it up before playing with the partition tables. 

Luck

---

