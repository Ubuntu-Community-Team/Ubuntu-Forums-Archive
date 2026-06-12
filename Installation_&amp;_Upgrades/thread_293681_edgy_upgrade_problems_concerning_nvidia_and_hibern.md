---
title: "edgy upgrade problems concerning nvidia and hibernation"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by Tim.thelion on 2006-11-05
A few days after the release of edgy, I ran $ gksu "update-manager -c" and waited for about 2 days for it to download.  At the end there where several packages that had failed, but the upgrade program told me to restart anyway.  Upon restarting my computer, a Pentium 4 3.0 gz 2gig of ram machine with an nvidia fx5200 graphics card, I received an error telling me that X had failed to start because it could not initialise nvidia.ko(or something like that) after 5 minutes of googleing and re-installing nvidia-glx and nvidia-kernel-common I gave up and decided to try an application named envy.  Latter that day, I decided I wanted to hibernate my computer, so I went to the little door at the top of the screen and pressed hibernate. the screen faded out, flashed some text, too quickly to read, then went to a log in screen. I logged in, and everything was still there, but the wireless network card(ndisswrapper) did not work.  I saved my work and restarted my computer and the wireless card worked again, but hibernating did the same thing. Yesterday, there was an automatic update, I do not recall what it was, I just told it to update whatever it was that it wanted to update. One restart latter, today, I got that same message about nvidia.ko not being able to initialise,  I again ran envy to get back to where I am now. On the off hope that whatever update it was that I had run had fixed the hibernation problem I tried hibernating again, now, the screen flashes and comes back to gnome, instead of coming back to the login screen, the wireless card still stops working when I try to hibernate.  

Before the upgrade to edgy, hibernate worked just fine.  Also, I had never had any troubles with nvidia before, I have been running this computer with ubuntu since breezy, though I had to reinstall upon upgrading to dapper. 

I have a kind of odd configuration, I have my home directory on one harddisk (sda1) and the rest on another (hda1).  my home directory has been around since I was running breezy.  

I do not want to have to reinstall the hda1 part of my system, mostly due to the absolutely enormous amount of software that I would have to reinstall too(alot of it not gotten through apt but cvs or tarball)

---

### Post by Tim.thelion on 2006-11-07
ok, I solved my problem by following the instructions here [http://ubuntuforums.org/showthread.php?t=287096](http://ubuntuforums.org/showthread.php?t=287096)

---

### Post by Tim.thelion on 2006-11-07
[http://ponderer.org/ubuntu_edgy?reply](http://ponderer.org/ubuntu_edgy?reply) I also had to add the resume line...

---

