---
title: "Ubuntu 11.04 installation woes"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2011-06-29
I am here terribly upset!:(

I installed ubuntu 11.04 (after being well satisfied with its installation via wubi) in 2 laptops (a compaq presario and a vaio VGN-CS) using bootable USB flashdrive (via unetbootin) in a separate partition (C for windows 7, D for storing my files, ubuntu in another partition). They worked perfectly for a few hours. Then suddenly i ran into problems. I tried to correct them with no avail! Here are the list of my woes:

In Vaio:
Initially i ran into some display errors related to Nvidia graphics drivers. But somehow i managed to update them and my system was working fine thereafter. Then i booted into windows and shutdown. When i rebooted thereafter, i see the grub menu. But, when i select to boot ubuntu, i get a blank screen and a flashing '_' cursor (thankfully i am able to load windows7). 
I saw a lot of threads with the same problems, but i could not find any which offered a less complex, followable, step-by-step instruction. I tried to follow some of them, but failed. I even reinstalled my ubuntu (well! not completely though! I selected upgrade 11.04 to 11.04 as i did not want to lose my files), but the same problem persisted.

In Compaq,
If this is not enough, with the Compaq i am facing even more problems.
It was also working fine, when suddenly when i started firefox i got this message, 
"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard drive is not full or close to full, it is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."
I saw threads with this problem also, but i was unable to solve it.
So i decided to just ignore it and started using chrome instead. Now, new problems sprung up. The screen would freeze temporarily, the launchbar on the left alone would go blank, the shutdown button on the top would move further right going out of view. When i press the shutdown button on the laptop, the normal shutdown screen (which usually has options for suspend/shutdown/restart etc.) had rectangular boxes in it instead of letters. 
I reinstalled (upgraded 11.04 to 11.04) ubuntu here also. No change! And to top it all, now my windows 7 in that computer is giving a blue screen error!:mad: (While typing this i did a complete reinstall, and now the firfox error is not there. I hope the freezing/hanging and the bluescreen error also get corrected/not recur).

What should i do? Ubuntu was running perfectly with the wubi installation. I thought that by installing ubuntu in a separate partition i would make ubuntu faster and more stable (as it would be detached/independent from windows, so that, even if windows encounters some problem i could use ubuntu). But this seems not the case! 

Ubuntu is an excellent piece of software no doubt. But it seems that, for busy people who have lot of things on their plate (with no time to fix complicated errors through terminal commands) it is not the right option. For example, i've been using windows for more than 10 years and i have gone to the command prompt only very few times. Everything could be done through GUIs.

A few of my suggestions (They may not look appealing, but novices like me will find them very useful):
1) The initial installation should be easier. Say, in windows i just select the partition i want to install it in and that's all!. Here i had to create separate root and swap partitions myself. (Although a friend here told me that this could be done by the default installer, i found it not as easy to use as the windows installer).
2) Less reliance on terminal. For almost every problem i have to go to the terminal. Common people do not know these commands. And, they don't have the time or patience always to learn them. GUIs suit them.
3) Easy installation and uninstallation. Although the ubuntu software center is quite good, installing separately downloaded sofware is difficult (except for .deb files). Why is there no installer (like the .exe for windows). Installing softwares through terminal commands is quite tedious. Despite trying hard, I still could not figure out a way to install my .tar.gz files! (And if i [who am so enthusiastic on computers], find it so difficult, my friends who know next to nothing about computers will be very reluctant to give up windows which is so easy for them). Also uninstallation through the synaptic package manager is not very easy. There are a lot of packages for a single software, so i get confused on which to uninstall.
4) Make it easy to find information. The inbuilt help file is not of much help. The ubuntu help site's instructions are a bit too complex for the ordinary user. For each and every problem i have to rely on this forum (But the people here are really friendly and extremely helpful! I have solved quite a bunch of my problems with thier help so far). A robust step by step by step guide is essential, especially for troubleshooting.

I am not complaining, but ubuntu should become more user friendly if it wants to find more users. Hope that happens soon! Good luck! 

I just wanted to tell the community the problems i faced (before i give up altogether!) so that someone may find it helpful! 

I will keep in touch with ubuntu always. I still love it, despite its flaws....

---

### Post by mörgæs on 2011-06-29
Sorry to hear that you ended in trouble. Yesterday all seemed fine.

For your problems with screen cards, best is to search this thread:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

For your suggestions about Ubuntu, you can vote here:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by ktp.kti on 2011-06-29
**Solved the Vaio issue with this,**

In the grub menu (i.e the 1st menu after boot which lists linux generic, recovery mode, memtest, windows 7 loader) type 'e' on your keyboard keeping the 1st option (i.e linux generic selected). This will open the edit screen.

In the edit screen, replace “quiet splash” with “nomodeset” .  

Hit CTRL + X to continue  booting. 

Once logged in install the latest Graphics drivers. [I]System -> Administration -> Additional Drivers

[/I]**Solved my Compaq issue by doing a full reinstall**

Yipee! :D Happy now! Ubuntu! here i come again!

Thanks [mörgæs]("http://ubuntuforums.org/member.php?u=939075") for your continued presence! It is like having a friend around here! :-)

---

