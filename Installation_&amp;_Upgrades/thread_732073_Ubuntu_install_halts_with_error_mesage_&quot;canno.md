---
title: "Ubuntu install halts with error mesage &quot;cannot display this video mode&quot;"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by ubuntogenius on 2008-03-22
Hi, I'm trying to install Ubuntu (Feisty Fawn) onto a machine (which has a Dell 19" TFT monitor).
After the initial boot/install menu, no matter which install option I choose, the screen goes black and I get an error message saying
"Cannot display this video mode
Optima Resolution 1280x1024 60hz"
I tried it with another tft (an old LG 15") and got the an Out of Range message from the OSD.
Obviously the Ubuntu disc is trying to set some sort of bizarre resolution\refresh rate which these monitors cannot handle.
What can I do to get the installation underway and set the resolution and refresh rate used for the install?
I have found a couple of solutions via google that suggest editing files but they all assume that you have access to those files in the first place and would know what to do with them once there.
Please note that I am pretty much a complete Linux virgin and installing this for learning purposes, so if you're going to tell me to edit a file, you'll also need need to tell me EXACTLY what commands to enter to find the file and EXACTLY what commands to enter to open it for editing - hence the high points value of the question. Treat me like a simpleton, because that's what i am in this case.
Thanks for reading...

---

### Post by confused57 on 2008-03-22
At the first screen with boot selections, press the F6 key, then you should be able to use the right arrow to navigate to the end of the boot options, remove the quiet & splash options.  If you get an out of range after booting into the desktop, press "Ctrl+Alt+F1", enter:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
```
select your desired resolution(s),then
```
sudo /etc/init.d/gdm start
```

---

