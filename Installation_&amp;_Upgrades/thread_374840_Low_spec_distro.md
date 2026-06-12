---
title: "Low spec distro"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Smokeymcpawt on 2007-03-03
I need a low Spec distro, 

500MHZ processor, 64 mb ram. 10gb harddrive.


Xubuntu doesn't get past configuring anthy, and DSL just sucks.

---

### Post by hardyn on 2007-03-03
any chance you might want to ebay up some ram?  500mhz isn't too bad, but 64mb of ram is gettin way down there.

---

### Post by ssavelan on 2007-03-03
I am surprised that xubuntu won't run that machine nicely.  And, I kinda like DSL.

But anyway, my friend puts linux on all kinds of older computers and he swears by the minimal install of Debian.

He does usually work his way up to the better part of xubuntu including xfce.

---

### Post by aysiu on 2007-03-03
From the Alternate CD, select the *Install a Server* option, which will give you a barebones installation.

Then, from the command prompt, type ```
sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox synaptic
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` That'll give you a nice, light Ubuntu environment.

---

### Post by kerry_s on 2007-03-03
I agree go custom. if you got good internet try the mini.iso net installer->
Edgy -> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)
Feisty-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by cstrippie on 2007-03-03
Damn Small Linux or Puppy Linux.  I like Puppy, but YMMV.

---

### Post by tagginannie on 2007-03-03
> **Smokeymcpawt said:**
> I need a low Spec distro, 

500MHZ processor, 64 mb ram. 10gb harddrive.


Xubuntu doesn't get past configuring anthy, and DSL just sucks.

I have Kubuntu  running  on Pentium II 500 mhz but you need more memory or else Ubuntu will do a lot writing to swap also called thrashing. All though, I just read on the kde forums that someone got kde 3.3 running on a p 166 with 64 mb ram and 2 mb graphics, with a previous version of kubuntu.

---

### Post by Smokeymcpawt on 2007-03-03
Hmm, I burned mini.iso to a disk, and the system doesn't boot from it. That has happened with quite a few distros i'v tried.


If I can figure out how to install GRUB, then i believe that I can boot into the xubuntu install I sorta have on it, because the only step it doesn't do is installing GRUB.


Edit: Ut oh, it won't boot from ANY CD now...What did I break?!

Is it possible for me to remove the harddrive from that PC, hook it up to my normal PC, then install xubuntu on it from this PC, then put the harddrive back into the old PC.

---

### Post by ssavelan on 2007-03-04
> **kerry_s said:**
> I agree go custom. if you got good internet try the mini.iso net installer->
Edgy -> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)
Feisty-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

Thanks for the info.  I have been thinking about stepping back and building my own custom desktop;  I thought that I would have to get Debian; but, I like Ubuntu so much.

I am wondering.. is there a way (somewhat conveniently) that I can not have any default ALSA and compile the latest source.  It seems that the ubuntu ALSA defaults sometime wreck havoc on my tinkering.

*I think it would be nice to have an option to get the most up-to-date source for certain packages through apt instead of defaulting to older packages* - make any sense?

Sorry to diverge from topic.

---

### Post by tagginannie on 2007-03-06
> **ssavelan said:**
> Thanks for the info.  I have been thinking about stepping back and building my own custom desktop;  I thought that I would have to get Debian; but, I like Ubuntu so much.

I am wondering.. is there a way (somewhat conveniently) that I can not have any default ALSA and compile the latest source.  It seems that the ubuntu ALSA defaults sometime wreck havoc on my tinkering.

*I think it would be nice to have an option to get the most up-to-date source for certain packages through apt instead of defaulting to older packages* - make any sense?


Sorry to diverge from topic.

Makes perfect sense, I had to install Alsa from source to get the onboard sound working in this old PC 
[U]
[http://www.alsa-project.org/](http://www.alsa-project.org/)


[/U]

---

### Post by ssavelan on 2007-03-07
> **tagginannie said:**
> Makes perfect sense, I had to install Alsa from source to get the onboard sound working in this old PC 
[U]
[http://www.alsa-project.org/](http://www.alsa-project.org/)


[/U]

It seems that my "make install" sometimes trips over the ubuntu defaults; and, with my layla24 and hda-intel the "Preferences>>Sound" is dangerous to play with.

---

