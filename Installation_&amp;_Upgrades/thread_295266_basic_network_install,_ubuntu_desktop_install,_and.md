---
title: "basic network install, ubuntu desktop install, and now?"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by max334 on 2006-11-07
Hi,

I have no working CD Rom drive in my laptop and only an non-bootable USB CD drive available. After some researching I chose to install Ubuntu via the netinstall option. This installed the base system first and then asked me what to install next and I chose 'Ubuntu desktop'. All of this is finished now and I rebooted. Now I arrive in the shell and I am able to login with username/pwd. 

My question: How do I proceed from here? I want to start in runlevel 5 with the normal gnome desktop. 

I tried 'startx' and this is not recognized. Then I tried 'sudo init 5' and nothing happens. 

I am not a linux specialist, but have some basic understanding.

Thanks.

---

### Post by catlett on 2006-11-07
That is a bit strange because the ubuntu-desktop package installs gdm and gdm is what gives you the graphical login. You shouldn't be getting a text login. Just to be safe, use aptitude and update first.
```
sudo aptitude update
```
```
sudo aptitude install ubuntu-desktop
```
That should be all you need to get a graphical login into a gnome desktop.
If that doesn't work, try to see if their are any errors. There may be a video card issue but it would have given you an error saying 'x could not start' and then drop you to the shell.
Try updating and reinstalling ubuntu. Then post anything strange. Even the exact error when you try startx.

---

### Post by max334 on 2006-11-07
Thanks for this. I thought the installation of the 'Ubuntu desktop' option did this already, but after running your commands it starts to download packages worth 495MB - so the desktop was not installed after all!

I will come back after the installation is complete. However, this may take a while :-).

Thanks.

---

### Post by catlett on 2006-11-07
> **max334 said:**
> Thanks for this. I thought the installation of the 'Ubuntu desktop' option did this already, but after running your commands it starts to download packages worth 495MB - so the desktop was not installed after all!

I will come back after the installation is complete. However, this may take a while :-).

Thanks.

Good luck. I think that was the issue. Maybe the dash wasn't in there, maybe not but it looks like you will be fine now. Post if there is an issue.

---

