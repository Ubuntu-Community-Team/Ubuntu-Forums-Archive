---
title: "Unity does not work / Gnome 2 fine"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by crashed111 on 2011-04-28
Hi All

Like many of you I have installed 11.04 on my desktop today. My previous upgrade experiences have been fine however I have hit a problem with Unity. 


[LIST]
[*]I am using an Nvidea card
[*]Propitiatory drivers are installed
[*]I have run the hardware test to check everything is good for 3d and all is fine
[/LIST]
I am having the following problems - 


[LIST]
[*]Since upgrading to 11.04 my login screen, background etc have stayed the same (probably not a problem but background information)
[*]When I log into Unity the background image comes up but no more
[*]Right clicking etc does not work I have to revert to command line via keyboard shortcut and reboot the system
[*]Booting into Ubuntu classic is fine
[*]I can log onto KDE but when I try to click on any of the menus nothing happens. I can navigate the mouse round the screen fine.
[*]Booting into Ubuntu (Safe Mode) just puts me into the classic Gnome 2 interface
[/LIST]

I am not sure what the problem here is I am running dual monitors however do not think that should be a problem. 

Any help  will be appreciated 

Cheers!

---

### Post by crashed111 on 2011-04-28
Installing the 2d Unity interface works fine which is strange. I have checked and I have the latest Nvidea driver

---

### Post by DrMilo on 2011-04-29
Similarly, when I try unity, my mouse moves but does nothing when I click. The numbers that are supposed to be on the icons to launch them, aren't. Also, new, untitled folders keep appearing on my desktop. 

I also get a strange, inverted white screen, after I press a Grub option, but before the login screen.

I use a propitiatory NVidia card driver but that has been supported just fine through at least 3 versions of Ubuntu, so why that would be a problem now I have no idea. The only part of the install where I did not use defaults was not updating etc/sysctl.conf, and the only thing that is doing is tweaking my broadband connection.

Looks to me like Unity has a problem with at least some NVidias. Mine is detected as a GeForce 7300 SE/7200 GS. Frankly, I can't remember if that's what it is. However, the problem is only in Unity and before Grub, so I doubt that the driver detection can be doing it. IOW, Gnome works fine.

---

### Post by superfrogman94 on 2011-04-29
> **DrMilo said:**
> Similarly, when I try unity, my mouse moves but does nothing when I click. The numbers that are supposed to be on the icons to launch them, aren't. Also, new, untitled folders keep appearing on my desktop. 

I also get a strange, inverted white screen, after I press a Grub option, but before the login screen.

I use a propitiatory NVidia card driver but that has been supported just fine through at least 3 versions of Ubuntu, so why that would be a problem now I have no idea. The only part of the install where I did not use defaults was not updating etc/sysctl.conf, and the only thing that is doing is tweaking my broadband connection.

Looks to me like Unity has a problem with at least some NVidias. Mine is detected as a GeForce 7300 SE/7200 GS. Frankly, I can't remember if that's what it is. However, the problem is only in Unity and before Grub, so I doubt that the driver detection can be doing it. IOW, Gnome works fine.

I have the same exact problem! i am pretty sure i have a 7300 LE. only diffrence is with the driver enabled gnome wont work either :( i ended up reinstalling and now i am using the gnome desktop but no nvidia driver :( i really wanted to use unity... i have 2 monitors and unity 2d is annoying since i cant delete the panels i have 2 of the same on both screens, BTW with the nvidia driver the 2nd monitor turns off... what the heck is wrong with the nvidia driver! i wonder if their is a way to use the older driver i used in 10.10... ugh

---

### Post by dino99 on 2011-04-29
nothing wrong with nvidia driver

select "classic" while logging in gdm

or remove unity & ubuntu-desktop from synaptic

---

### Post by superfrogman94 on 2011-04-29
> 
nothing wrong with nvidia driver

select "classic" while logging in gdm

or remove unity & ubuntu-desktop from synaptic
if i install the driver i cant use even the gnome desktop, it is frozen when it logs in interface appears but do es not respond) the ctrl-alt-f1 session is all white and ugly so it wouldn't be fun to remove unity or the driver with it... unity should have worked, this is the first time i ever had a problem with the nvidia driver as it worked perfectly fine in 10.10. man this last time i install on day-1, ill wait a week or two from now on...

---

### Post by crashed111 on 2011-04-29
Well it looks like there are several people with similar problems and in similar threads. 

For now I am using the 2d variant and growing to like it (although I have not used it for work yet so am yet to try its multitasking capabilities properly)

I am not sure if it is to do with the fact I have kdm installed and I am using that over gdm.

---

