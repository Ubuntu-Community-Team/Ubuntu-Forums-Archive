---
title: "Laptop freezes and screen goes blank towards end of upgrade"
date: 2019-09-08
forum: Installation &amp; Upgrades
---

### Post by daij163 on 2019-09-08
Hello, I was running Ubuntu 14.04 alongside Win 10 (dual boot) on my Asus S400CA laptop. I decided to upgrade to 16.04 and I could proceed until maybe 80% point of installation of upgrades.

The laptop suddenly appeared to freeze, with the screen going off and the "drive" and the "wifi" lights started flashing. I tried hitting the "Esc", "Enter" and numerous key combinations, including Ctrl+Alt+F1/ F2/ F3..., but the screen stayed off. I could only force shut down using the Power switch.

Of course, upon reboot, I could only get to a Grub prompt. It says "Minimal BASH-like line editing is supported" above the "grub>". The heading indicates the version to be "GRUB version 2.02~beta2-36ubuntu3.22".

I tried hitting the shift key just before the grub> appeared but it didn't do anything. I attempted this procedure twice to no avail.

May I know what I can do next to see if the installation actually completed sufficiently for me to salvage the system?

Thank you!

---

### Post by mörgæs on 2019-09-08
I suggest that you in a live boot copy all relevant files from the drive. After that a clean install of 18.04.3.

---

### Post by daij163 on 2019-09-08
Thank you. Yes, a clean install is probably the best.

I ran the Backups within 14.04 of the Home folder just before I attempted the upgrade. Is that enough or are there specific files that I should copy from the drive?

---

### Post by mörgæs on 2019-09-09
A standard user saves all files in /home but a web developer is likely to have stuff also in /var/www.

Remember to pick the individual files from the backup and not the entire collection of files.

---

### Post by daij163 on 2019-09-09
Thank you much. Will do. Will post back to let you know how it goes. Have a great week!

---

### Post by daij163 on 2019-09-09
Happy to report all seems well with the option to install over the failed 16.04. The option to overwrite the 16.04 and all files, settings was provided as part of the installation process. That made it simple since I didn't have to mess around with the partitioning of the drive again.

Much appreciated your assistance and patience!  :grin:

---

### Post by mörgæs on 2019-09-10
Good that you got it working and thanks for marking the thread 'solved'.

Now your turn to save people who have been trapped in a failed upgrade :-)

---

### Post by daij163 on 2019-09-11
> Good that you got it working and thanks for marking the thread 'solved'.

Yes, a very happy user. Marking it "solved" is the small bit that I should do.

> Now your turn to save people who have been trapped in a failed upgrade 

From someone who has just been "saved" to saving someone else is still a very big gap that I will need years to bridge.;)

Having said that, perhaps I can summarize my experience as follows for the benefit of similar poor souls in future :

1. Hardware - Asus laptop model S400CA, previously running Win 10 and Ubuntu 14.04 as a dual boot.
2. Tried to do an upgrade to 16.04 using Software Updater. Unfortunately when the upgrade process neared the 90% mark, the laptop froze, screen went blank (no cursor, CAPS key didn't work) and indicators for Drive and Wifi started flashing.
3. Tried different key combinations to revive laptop but nothing worked. No other action or key worked either. Had to force a shut down using the Power switch.
4. At reboot, I could only get "grub>", a grub prompt. Typing "exit" at the prompt allowed me to boot into Windows.
5. Using an Ubuntu 18.04 Live USB, I was able to copy all my files in the Home folder of my 14.04 installation onto a backup drive.
6. After that, from within the Live USB, I started a fresh install of the 18.04. I was offered the option of overriding the failed 16.04 installation, for which I took with much relief. I didn't have to do any partitioning work or specify mount points again in this particular scenario.
7. The installation went smoothly and all my hardware components worked perfectly out of the box. The only item that "behaved" differently was the trackpad, where the right click button was mimicking the function of the left click button. I followed the instruction at [https://itsfoss.com/fix-right-click-touchpad-ubuntu/](https://itsfoss.com/fix-right-click-touchpad-ubuntu/) (and many other similar sites shared the same trick) and I managed to get the right click working as before again.
8. Fairy tale ending :D

---

### Post by bulgin on 2019-09-11
I am having a similar problem also an Asus. . . 

[https://ubuntuforums.org/showthread.php?t=2426623](https://ubuntuforums.org/showthread.php?t=2426623)

In my case I need to solve the problem without resorting to backup (which I have already done) and re-install as I have some difficult to replicate web sites and data files on the install that won't start.

---

