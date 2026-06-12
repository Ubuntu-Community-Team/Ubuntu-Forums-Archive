---
title: "Wubi install - no monitor support"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by RobotGymnast on 2010-08-26
I tried installing Ubuntu via the latest Wubi on my HP machine; AMD64 processor, NVIDIA GeForce 6150 LE graphics card. After restarting and selecting Ubuntu, my monitor (Viewsonic) told me it had no input, and proceeded to stand itself by. The computer sat there, turned on with no monitor, for about half an hour, and when I came back, windows was up. I tried restarting into Ubuntu again, got to the Grub menu, and selected Ubuntu before the same thing occurred. This time I didn't wait, but hard restarted it after a minute oh waiting. When I tried starting Ubuntu in Safe Graphics mode, I got through the initial bash bootup instructions before this occurred. Any suggestions?

---

### Post by bcbc on 2010-08-26
> **RobotGymnast said:**
> I tried installing Ubuntu via the latest Wubi on my HP machine; AMD64 processor, NVIDIA GeForce 6150 LE graphics card. After restarting and selecting Ubuntu, my monitor (Viewsonic) told me it had no input, and proceeded to stand itself by. The computer sat there, turned on with no monitor, for about half an hour, and when I came back, windows was up. I tried restarting into Ubuntu again, got to the Grub menu, and selected Ubuntu before the same thing occurred. This time I didn't wait, but hard restarted it after a minute oh waiting. When I tried starting Ubuntu in Safe Graphics mode, I got through the initial bash bootup instructions before this occurred. Any suggestions?

#1, don't hard restart Ubuntu, especially not wubi. It'll corrupt the root.disk. 

#2. With NVIDIA cards you'll need to install the proprietary driver. Luckily for you, the first time you left the computer is was actually completing the 'unattended' installation, so that is out of the way. Now you just have to override the boot options and get it to display.
Select the first grub entry, hit 'e', go to where it says 'quiet splash' and add nomodeset. i.e. 'quiet splash nomodeset' without quotes. Hit CTRL+X to boot.
Once booted go to System, Adminstration, Hardware drivers and it should offer an nvidia driver.

---

### Post by RobotGymnast on 2010-08-26
> **bcbc said:**
> #1, don't hard restart Ubuntu, especially not wubi. It'll corrupt the root.disk. 

I had no way of knowing if it would restart itself again; I assumed the first time was completing the installation, but on subsequent attempts I assumed that was no longer the case and that it wouldn't restart on its own.

> **bcbc said:**
> 
#2. With NVIDIA cards you'll need to install the proprietary driver.
...
you just have to override the boot options and get it to display.
Select the first grub entry, hit 'e', go to where it says 'quiet splash' and add nomodeset. i.e. 'quiet splash nomodeset' without quotes. Hit CTRL+X to boot.
Once booted go to System, Adminstration, Hardware drivers and it should offer an nvidia driver.

Thanks, I'll try that when I reboot.

Update: Works great, thanks. Updating and installing driver now.
There are 3 NVIDIA drivers available, but one is marked as current and recommended, while the others are older versions. However, the system keeps popping up that little icon that tells me drivers are available, despite the fact that I've installed the recent one. Can I change this?

---

### Post by bcbc on 2010-08-26
> **RobotGymnast said:**
> I had no way of knowing if it would restart itself again; I assumed the first time was completing the installation, but on subsequent attempts I assumed that was no longer the case and that it wouldn't restart on its own.



Thanks, I'll try that when I reboot.

Update: Works great, thanks. Updating and installing driver now.
There are 3 NVIDIA drivers available, but one is marked as current and recommended, while the others are older versions. However, the system keeps popping up that little icon that tells me drivers are available, despite the fact that I've installed the recent one. Can I change this?
Not really sure on this one since I don't have an nvidia card and never needed to use proprietary drivers. Maybe ask on IRC #ubuntu or maybe someone will see this and respond here.

EDIT: maybe this link can help [http://ubuntuforums.org/showthread.php?t=840123](http://ubuntuforums.org/showthread.php?t=840123)

---

### Post by RobotGymnast on 2010-08-26
Perfect, thanks

---

