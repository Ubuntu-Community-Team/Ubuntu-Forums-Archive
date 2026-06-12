---
title: "Moving ubuntu to a new pc"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by micdhack on 2008-10-21
I want to move my current ubuntu configuration. When i say configuration i mean everything on my /home/ including files which start with . and configuration from /etc/ samba etc. In general i want everything as it is on my new pc.
My question is because we are talking about different builds, processor, graphics card,etc. What problems might occur and what would be the best way to do it...or at least most of my configuration?

Old laptop has ubuntu windows xp dual boot while the new will have ubuntu +vista. I am thinking of firstly following a guide that says how to do the dual booting and all and after this to start file transfer. Im guessing a should be also curefully about not moving the old grub config to the new one.
So as you understand i need some dos and donts about which files i should transfer and which i shouldnt.
I also found that this can be achieved by remastersys. Has anyone tried this program?

---

### Post by micdhack on 2008-10-25
solution was at first transfering my big folders to the new-laptop vista partition(after its being resized). Then using remastersys i created a live cd which i booted and installed. 
Everything worked fine. My configuration on /etc and on my home directory remained. And as far as the drivers goes, as soon as i restarted the system i had a new message that wanted me to install nvidia drivers..also with an apt-get update and upgrade everything was well.

---

