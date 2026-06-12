---
title: "Installing Xubuntu on a PIII with a Intel I815 video card"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by barraclou on 2007-11-01
Hi, It is probably nothing new for you, but since I try to escape from the Redmond-based empire, I have only a very limited experience on Linux. 

So, here's my story. Presently, I try to install any of Xubuntu 7.10 or Ubuntu 7.10 from the iso image file found on this site or Fedora 7 from its livecd on a Pentium III 733mhz machine with 192mb ram. It will be a dual boot with Win2000sp4.  

Before running the cd and installing (X)ubuntu, I had trouble with GParted and I found that the fact I have a Intel I815 video card was not working properly with the latest version of GParted, even if I selected to use the Intel I810 drivers specs. So, I had to download a older version (GParted 0.3.3) to be able to partition and format my hard drive. 

So, I am running the cds. It takes a while (that's ok), I see the progress bar and everything reacts properly, but where it ends its loading, I heard the welcome sound, and my screen goes black with no flashing underscrore in the corner. I thought that it might be because I don't have enough memory to install/run Ubuntu, but Xubuntu does the same time. Also, I thought to my "unwilling" video card, but I can see the installation menu and progress bar. So, it seems to be something about the resolution or similar to.   

When I run the Fedora cd, it will load the desktop and the icons, but no bars at all. So, I can see the directories and browse them. If I click on the "install to hard drive" icon, I will see my pointer changing to the waiting status (the spinning wheel), then nothing else.

Is somebody can helps me to make it successful?

Jeff

---

### Post by Pumalite on 2007-11-01
256 MB of RAM with integrated graphics or less> Xubuntu Alternate CD. Or you might have to stick to a smaller distro. Give us your memory and graphics and we'll be able to help you better,

---

### Post by barraclou on 2007-11-25
Here`s an update. I upgraded the ram to 384mb and I was able to fully install Fedora 8 on this machine. It seems (X)Ubuntu is harder to install on that machine, but at least, I succesfully installed a Linux distribution on that computer.

---

### Post by Pumalite on 2007-11-25
Good for you! Good luck.

---

### Post by the_monster on 2007-12-11
My IBM NetVista (6579-lau) is the exact same specs and I found when you max the mem out (512 megs)
you have no problems using any of the Ubuntu version except for this:

it insists on using the highest rez, which combined with my Dell D1028L monitor, caused what looked like vertical interference lines, but then switching to 1024x786 solved the problem. The login screen still insists on using the higher resolution, but switches to the proper rez once I login.

---

