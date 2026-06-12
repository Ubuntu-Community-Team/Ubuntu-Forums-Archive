---
title: "new to linux"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by jarrod76665 on 2008-05-23
I am very new to linux and dont know anything about the linux language. i am trying to download how to install the nvidia driver for my video card I have downloaded it from the internet but i click on the icon and nothing happens i have looked up some things on the internet but they tell me to type in # su NVIDIA-Linux-x86_64-169.12.pkg#.run but it says bad command name or something like that What do I do? please be specific I really do not know very much i am typing all this stuff into terminal window is that the right place? 
Thanks for all the help

---

### Post by iaculallad on 2008-05-23
> **jarrod76665 said:**
> I am very new to linux and dont know anything about the linux language. i am trying to download how to install the nvidia driver for my video card I have downloaded it from the internet but i click on the icon and nothing happens i have looked up some things on the internet but they tell me to type in # su NVIDIA-Linux-x86_64-169.12.pkg#.run but it says bad command name or something like that What do I do? please be specific I really do not know very much i am typing all this stuff into terminal window is that the right place? 
Thanks for all the help

You could let the "Restricted Drivers Manager" do the dirty job for you. Navigate System->Administration->Restricted Drivers Manager

---

### Post by epidemiks on 2008-05-23
What if it doesn't show up as a restricted driver?
I have an nvidia geforce 6700 GS & it isn't there.
envy is not helping either

---

### Post by iaculallad on 2008-05-23
> **epidemiks said:**
> What if it doesn't show up as a restricted driver?
I have an nvidia geforce 6700 GS & it isn't there.
envy is not helping either

Had you have any problem with Envy? What errors did it prompt you?

---

### Post by epidemiks on 2008-05-23
none, thats the problem.. does what its meant to, just doesn't give me 1680x1050 with usable nvidia settings. reboots with 800x600 'low graphics mode'

---

### Post by iaculallad on 2008-05-23
> **epidemiks said:**
> What if it doesn't show up as a restricted driver?
I have an nvidia geforce 6700 GS & it isn't there.
envy is not helping either

Seems like you do not have any problem with your restricted driver.

> **epidemiks said:**
> none, thats the problem.. does what its meant to, just doesn't give me 1680x1050 with usable nvidia settings. reboots with 800x600 'low graphics mode'

But rather, a problem on screen resolution since Envy did not show you any error at all.

Can you post the content of your /etc/X11/xorg.conf then so we could take a look at it.

**cat /etc/X11/xorg.conf**

---

### Post by epidemiks on 2008-05-23
don't want to hijack jarrod's thread..
existing one: [http://ubuntuforums.org/showthread.php?t=799643](http://ubuntuforums.org/showthread.php?t=799643)

---

### Post by jarrod76665 on 2008-05-23
Well i went to system and i dont have a restricted drivers option i have hardware drivers page and it has a generic driver for all NVIDIA cards but i needed to install one so i can use Cedega and play games is there still a way i can use hardware drivers or do i need to do something different

---

### Post by jarrod76665 on 2008-05-23
oh ya i forgot i am using ubuntu 8.04 hardy when i run system test in cedega it says when i first open the tests "You appear to be missing one or more dependencies for the system tests. This could be because your 64-bit system is missing the 32-bit emulation libraries. Without them, the tests and other auxiliary programs will not run. not a dynamic executable" then the open gl direct rendering fails the 3d acceleration fails and the ALSO audio fails but i still get sound any help would be so appreated
Jarrod

---

### Post by jarrod76665 on 2008-05-23
i am using a NVIDIA 8600 GT

---

### Post by iaculallad on 2008-05-24
> **jarrod76665 said:**
> i am using a NVIDIA 8600 GT

Jump to this [thread]("http://ubuntuforums.org/showthread.php?t=501495"), you got the same video adapter. Hope this could help.

---

