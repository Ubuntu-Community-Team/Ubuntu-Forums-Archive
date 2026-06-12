---
title: "running dkpg --configure -a fails"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by Robertjm on 2008-01-27
Hi all,

Yesterday I ran Synaptic to get the latest and greatest updates for Hardy Heron. There were 300+ that needed to be installed!!!

It downloaded them and tried running, but choaked and I got the msg about running:

dpkg --configure -a

However, when I try and run that it bails on me.

First it tells me:

[COLOR="Blue"]Setting up initramfs-tools (0.85eubuntu22)..
update-initramsf: deferring update (trigger activated)

Processing triggers for initrams-tools...
update-initramfs: Generating /boot/initrd.img-2.6.24-5-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-5-generic
dpkg: subprocess post-installation script returned error exit status 1
[/COLOR]

After pawing around the internet I came across several suggestions that perhaps my /boot partition has filled up. When I go to /boot and check the files I seem to have five different kernels installed, along with their back files. I don't remember the exact size of my /boot partition, but I'm thinking its filled.

I tried uninstalling the oldest kernel that was installed, however, that chokes on me telling me I have to run the dpkg --configure -a command again!! 

Feels like I'm sort of chasing my tail right now.

Can someone give me a suggestion on how to clean up my /boot so I can finish running the dpkg command??

Or am I going in the wrong direction?

Robert

---

### Post by oldos2er on 2008-01-27
Why are you running Hardy? I imagine it's far from stable. Anyway, run "sudo dpkg --configure -a"

---

### Post by maybeway36 on 2008-01-27
Go in a terminal and run "df -h".

---

### Post by Robertjm on 2008-01-27
When I run the df command it comfirms what I thought, that /boot is 100% in use, with nothing available. 

As to the question of WHY I'm running Hardy? I had some big problems in early December trying to get my Sony Walkman player playing nice with Amarok. I tried using Gutsy to no avail, When I upgraded to Hardy that solved it.

Sure, its not stable, but its only had two major breaks for me since I started using it. Albeit those were major pains. First one caused Gnome to become unusable, so I started using KDE 3.5. That was working fine until yesterday's update. However, it seems like the problem with yesterday's update was not specific to KDE as much as it was to some restricted modules update, judging from other people's posts.

As for running dpkg under sudo, that's not going to be able to done till I can clear up some space on /boot.

Robert

---

### Post by tkots199 on 2008-03-12
when i run dkpg --configure -a it pops up with

dpkg --configure -a
dpkg: requested operation requires superuser privilege

what can i do about this I just can't figure it out it dosen't let me download any programs or anything its starting to annoy me to the point of return to windows :S that's not good but some one better help me out fast

---

### Post by Robertjm on 2008-03-12
slap a "sudo" in front of it and you should be good to go.  :)

BTW: I ran into that problem when my /boot partition filled up so if you still have problems reboot into the latest kernel's recovery mode and then delete some old kernels that you're sure you're not using any more.

Robert
-----------------------------------

> **tkots199 said:**
> when i run dkpg --configure -a it pops up with

dpkg --configure -a
dpkg: requested operation requires superuser privilege

what can i do about this I just can't figure it out it dosen't let me download any programs or anything its starting to annoy me to the point of return to windows :S that's not good but some one better help me out fast

---

### Post by tkots199 on 2008-03-12
when i put sudo it said 

sudo dkpg --configure -a
sudo: dkpg: command not found

so now what

and i have to ubunutu's installed and I need to get rid of one how?

---

### Post by plucky on 2008-03-12
That would be ```
sudo dpkg --configure -a
``` not **dkpg** unless it is just a typo.


Good luck

---

### Post by Joeb454 on 2008-03-12
Try copying the code **plucky** posted, it should work :)

---

### Post by Robertjm on 2008-03-12
As the others pointed out, dpkg, not dkpg. Sorry I didn't catch that in the first response.

Robert

---

### Post by tkots199 on 2008-03-12
thank you guys im pretty sure its working now your a life saver
:guitar::guitar::guitar::guitar:

---

### Post by linuxisfree on 2008-03-12
> **Robertjm said:**
> When I run the df command it comfirms what I thought, that /boot is 100% in use, with nothing available. 
 
As to the question of WHY I'm running Hardy? I had some big problems in early December trying to get my Sony Walkman player playing nice with Amarok. I tried using Gutsy to no avail, When I upgraded to Hardy that solved it.
 
Sure, its not stable, but its only had two major breaks for me since I started using it. Albeit those were major pains. First one caused Gnome to become unusable, so I started using KDE 3.5. That was working fine until yesterday's update. However, it seems like the problem with yesterday's update was not specific to KDE as much as it was to some restricted modules update, judging from other people's posts.
 
As for running dpkg under sudo, that's not going to be able to done till I can clear up some space on /boot.
 
Robert
 
Try running the ff. (they might free up some much needed space.)
```
sudo apt-get autoclean
```
or
```
sudo apt-get autoremove
```

---

