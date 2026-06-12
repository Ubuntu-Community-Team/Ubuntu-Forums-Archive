---
title: "Installation problem"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by lelovely7315 on 2012-12-28
Hi everyone,


     well here I am again. I know I just put it on that the problem is solved, well it was with what was wrong. Now I have a different problem, I am trying to install Ubuntu 12.04 LTS.. I am doing it from the live CD that I purchased from this website. I can run the OS from the CD (Like I am doing now), it doesn't work as good as if it was on the HDD. Anyway I can't get it to install from the CD to my HDD. I get up to choosing the kind of install, and when I choose the direct install it takes off like it will install, but it never stops. It should be installed in 2hrs. at the most, but it never gets installed. So what is the problem? I know that all the components on the inside are good because it is running now off the CD. So what step must I do to get it to install from the CD?
                  Thanks Larry ( Mr. Purrfect58 ) :(

---

### Post by deadflowr on 2012-12-28
How far along on the install does it get?

Do get to the various installation screens(select language, where to install, username and password screens, etc, etc)?

Can you run the 'try Ubuntu' option and then try installing from there?(It should be an icon on the desktop).

Lastly, which version are trying to run? 32-bit, 64-bit?
And what kind of system are you trying to install on?

Sorry for asking so many questions.

---

### Post by The Cog on 2012-12-28
One thing you could try is as the installer CD boots there is an option to go for extra options (perhaps F5, I can't remember for sure). Set the option for **nomodeset** and then try the install again. This is the only way I can get it to install on my PC.

---

### Post by Yougo on 2012-12-28
1) when you boot from cd, you can choose an option that says to check the cd for errors. 

while the live cd appears to work ok, there are other sections of the cd that are dedicated for installation. with this option, you can check the entire cd, just to be sure.
if the cd is damaged, could you download the iso from ubuntu.com and burn the iso to cd?

2) are you trying to make a wubi install, install over or alongside an existing install, or install on a completely wiped/clean disk?

3) did you note at what point the installation gets stuck?

during installation, just above the progress bar you should be seeing notification of what is being done at the moment. first it prepares the harddrives and the partitions, then it copies installation files to the disk, then it starts to unpack and install all the programs, configure the hardware drivers, finally it will create userprofiles.
can you tell where it gets stuck?

4) when the installation halted, can you reboot the computer into any command prompt?

if there is a usable system, maybe you can fix things from there, or at least figure out what's wrong.

---

### Post by ajgreeny on 2012-12-28
Another possibility that I had problems with was the ubiquity-slideshow that should run while the system is installing.  On some hardware it looks as if the whole installer crashes when the slideshow starts and leaves the spinning cursor on screen, but nothing actually happening, and no installation proceeding.

I overcame this by booting to the live system from CD, running ```
sudo apt-get remove ubiquity-slideshow-ubuntu
``` then installing immediately from that running system.  It is possible that the bug for this was overcome with 12.04.1, which my be the version you have, but it could be worth trying the slideshow removal if nothing else suggested works.

---

### Post by grahammechanical on 2012-12-28
> (perhaps F5, I can't remember for sure)

for accuracy it is F6.

At the first purple screen press Enter. Then select the language. English is the default so you may press Enter a second time. Then press F6 and scroll down the list until you highlight nomodeset and then press Enter and finally press Esc to get back to the Try or Install screen.

Regards.

---

### Post by Bucky Ball on 2012-12-28
*Thread moved to **Installation & Upgrades***

---

### Post by lelovely7315 on 2012-12-29
Hi Everyone,
    Thanks for the info to solve my latest problem. Here is the way it goes when I try to install from the Live CD. I get the welcome screen, then preparing to install, install type, my location, keyboard layout, who are you or me. I get a coping files graph at the bottom of this window. window closed and left me with the CD's desktop and a small ball for the cursor with rotating dots inside. After 7hrs. it is still trying to install. I am trying to install a 32bit system, the CPU is AMD 2400 XP, 2gb ram, 200gb HDD, Video = Gforce FX 5500. I am trying to do a clean install on the HDD. It goes through the motions of installing and I can look at the HDD to see what it has partitioned. It partitions 4.5gb Swap, 2.0gb sda1 ext. 4, then 189.7gb is sda HDD. It looks like it has installed , but when I try to reboot it without the Live CD in it won't boot up. So there is the info of what it is doing, so what is wrong?
              Thanks Larry  ( Mr. Purrfect58 )

---

### Post by TOMBSTONEV2 on 2012-12-29
Is the Nvidia GeForce FX5500 onboard or is it plugged into a pci/pcie slot? When I had my Dell Dimension 1100 ubuntu had sooooo many issues with this card. It too hung on the install, I had to unplug this pci card and start fresh in order to get it to install. Albeit this was ubuntu 10.04 at the time.

To get it to boot up the card had to be removed. I ended up putting a switch in so the card could be "removed" without having to take apart my pc, at this time I had a dual boot with windows xp and a dual monitor configuration. Windows had both monitors, ubuntu had only one.

---

### Post by ajgreeny on 2012-12-30
> **lelovely7315 said:**
> Hi Everyone,
    Thanks for the info to solve my latest problem. Here is the way it goes when I try to install from the Live CD. I get the welcome screen, then preparing to install, install type, my location, keyboard layout, who are you or me. I get a coping files graph at the bottom of this window. window closed and left me with the CD's desktop and a small ball for the cursor with rotating dots inside. After 7hrs. it is still trying to install. I am trying to install a 32bit system, the CPU is AMD 2400 XP, 2gb ram, 200gb HDD, Video = Gforce FX 5500. I am trying to do a clean install on the HDD. It goes through the motions of installing and I can look at the HDD to see what it has partitioned. It partitions 4.5gb Swap, 2.0gb sda1 ext. 4, then 189.7gb is sda HDD. It looks like it has installed , but when I try to reboot it without the Live CD in it won't boot up. So there is the info of what it is doing, so what is wrong?
              Thanks Larry  ( Mr. Purrfect58 )
This sounds exactly the **ubiquity-slideshow-ubuntu** problem I mentioned at post #5.
Boot to the live CD, remove the slideshow package as I suggested and without shutting down the live CD, try again to install from that live session.

---

### Post by lelovely7315 on 2013-01-03
Hi everyone, Okay I have decided to build a new clean computer. I have transferred all the insides from one case to another. This computer is running Zorin, which is based on Ubuntu and Debain, mostly Ubuntu. So the OS is operating in this case with Zorin OS instead of Ubuntu 12.04 LTS. I am going to build a bigger and faster machine to put Ubuntu on. So this Installation problem can be classified as Solved. But as soon as I get that other computer built I will be back with more problems. So thanks to everyone for the help and info, I will talk to you later.

                      Thanks Larry  ( Mr. Purrfect58 ) :)

---

### Post by Bucky Ball on 2013-01-03
Please mark the thread as Solved from Thread Tools at top right and post a new thread with a descriptive title for any further problems.

Good luck.

---

### Post by lelovely7315 on 2013-01-08
Hi Everyone,
    Yes it is me again, well this time I don't have the instillation problem. I have built another computer, this one is up to date or close anyway. I set the CMOS first and then I put the Ubuntu 12.04 (LTS) CD in the drive and started the install. It went all the way through and it is working just fine. So now I must learn how to use it. So now the install problem is SOLVED and I can go onto some other problem now. Thanks to all that helped me. 

     Thanks Larry  ( Mr. Purrfect58 ) :D

---

### Post by Bucky Ball on 2013-01-08
Remember to post a new thread with a descriptive title for any further issues rather than adding to this one. Thanks.

---

