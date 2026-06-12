---
title: "Upgrade to 10.10 has replaced Lubuntu with Ubuntu"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by cg2916 on 2011-07-17
Last night, I upgraded my Lubuntu machine to 10.10. However, when I started it up, it has become regular Ubuntu. I have an old laptop (which is why I put Lubuntu on it), and whenever I log in, it doesn't do anything and I can't do anything other than go to a tty.

Is there any way to fix this other than reinstallation (which is my Plan B)?

---

### Post by srisharan on 2011-07-17
Go to synaptic package manager and install lubuntu desktop environment

---

### Post by snowpine on 2011-07-17
[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by cg2916 on 2011-07-17
> **snowpine said:**
> [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

I actually meant 11.10, wow I messed up.

---

### Post by srisharan on 2011-07-17
As I have previously said install the complete lubuntu desktop from synaptic.If you want you can also remove the ubuntu desktop

---

### Post by cg2916 on 2011-07-17
> **srisharan said:**
> As I have previously said install the complete lubuntu desktop from synaptic.If you want you can also remove the ubuntu desktop

Apparently Ubuntu is not installed and Lubuntu is still there. It just said it was Ubuntu. 

My main problem is that X Window server or Xorg or whatever does not start correctly. When I run startx or xinit, it says it's already running on Display 0.

**It is worth noting that I installed lightdm instead of lxdm when I upgraded.**

---

### Post by DannyDroid on 2011-07-17
As you've installed 11.10 - you are currently running Alpha software. You could install the Lubuntu 11.04 but once again, you will be running Alpha software.

I recommend you reinstall Lubuntu 11.04 as a downgrade isn't a good idea (nor possible?) but if you wish to carry on using 11.10 then you can install Lubuntu 11.10 from the recovery console using the following;

sudo apt-get install lubuntu-desktop.

I assume you did this in the terminal; sudo do-release-upgrade -d
The -d means upgrading to the latest unstable.

[Someone, please correct me if I am wrong, I'm still kinda new to Linux]

---

### Post by cg2916 on 2011-07-17
> **DannyDroid said:**
> As you've installed 11.10 - you are currently running Alpha software. You could install the Lubuntu 11.04 but once again, you will be running Alpha software.

I recommend you reinstall Lubuntu 11.04 as a downgrade isn't a good idea (nor possible?) but if you wish to carry on using 11.10 then you can install Lubuntu 11.10 from the recovery console using the following;

sudo apt-get install lubuntu-desktop.

I assume you did this in the terminal; sudo do-release-upgrade -d
The -d means upgrading to the latest unstable.

[Someone, please correct me if I am wrong, I'm still kinda new to Linux]

Lubuntu is on there, but the X Windows Manager is not. I did sudo update-manager -d

---

### Post by haresear on 2011-07-17
> **cg2916 said:**
> 
**It is worth noting that I installed lightdm instead of lxdm when I upgraded.**

I've was playing with the Xubuntu 11.10 daily builds, and noticed that when lightdm became the display manager, the GUI desktop would no longer come up (black screen). I was able to get 'startx' to work if I stopped lighdm first with 'sudo stop lightdm'.

There is a thread in the "Ubuntu +1 (Oneiric Ocelot)" group that has a solution for getting lightdm to work. It involves editing the lightdm.conf file to delete or comment out the lines starting with "default-user" and "default-session". Sorry, I can't now recall exactly where the lightdm.conf file is located.

---

### Post by mastablasta on 2011-07-18
> **cg2916 said:**
>  
**It is worth noting that I installed lightdm instead of lxdm when I upgraded.**
 
try 
 
sudo lightdm
 
mine also doesn't start (lubuntu 11.04, live session) and  i have to manually load it by using sudo lxdm.

---

### Post by cg2916 on 2011-07-18
> **mastablasta said:**
> try 
 
sudo lightdm
 
mine also doesn't start (lubuntu 11.04, live session) and  i have to manually load it by using sudo lxdm.

It says lightdm is already running, but I'll try lxdm.

---

### Post by cg2916 on 2011-07-18
I used sudo start lxdm, and it started, but nothing happened.

---

