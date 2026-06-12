---
title: "After a difficult installation..."
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by stefano3 on 2013-10-04
Hi guys, this is my first thread, so be patient if I did something wrong posting my problems here :D

In a few words this is the issue:

I wanted to install Ubuntu on my PC, but I had a problem, which ,I found out, is quite common.
Everyone with a little bit of experience in the Ubuntu fixing world will understand what i'm talking about.
Since I still don't know what kind of problem it is, I can only tell you that I had the monitor black after clicking on "Install Ubuntu", and in order to fix it had to modify the linux boot line adding "acpi=off apm=on". In this way the installation succeeded.
Now when the OS boots it blocks, and again my monitor is freezed in black. 
Should I start Ubuntu writing every time "acpi=off apm=on"? Annoying...

I'm confident in your assistance ;)

---

### Post by oldos2er on 2013-10-04
You can make the change permanent by editing your /etc/default/grub file. Open a terminal with Ctrl-Alt-t:

```
sudo cp /etc/default/grub /etc/default/grub.original

gksudo gedit /etc/default/grub
``` First command makes a backup copy of the file, second opens it in a text editor with admin privileges. Change the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off apm=on"

Save the file, exit, and run ```
sudo update-grub
``` You should see the changes you want at next boot.

---

### Post by stefano3 on 2013-10-05
Thank you, this is quite helpful, but actually I was looking for a way to completely solve the problem.
By typing the string "acpi=off apm=on" I can definitely and finally have Ubuntu on my PC, but I can't shut down the system, see the battery level, etc. :?

---

### Post by grahammechanical on 2013-10-05
It may seem to you that the issue is the same but is it? It could be an issue with the Video driver. There are a couple of things to try and you can do both at the Grub menu. With Ubuntu selected press E to enter Grub Edit mode and insert "acpi=off apm=on" in the line that says "quiet splash" and just before those words. Then boot by pressing F10 (I think) the instructions are at the bottom of the screen.

If the problem remains the same, then at the Grub menu select Recovery Mode. Assuming that you are using 13.04 you will find Recovery Mode in the Advanced Options sub-menu. At the Recovery menu select Resume and see if that gets you to a working desktop. If it does go to System Settings>Software and Updates>Additional Drivers tab and experiment with another video driver. This is for 13.04. It is different for 12.04.

Regards.

---

### Post by stefano3 on 2013-10-17
> By typing the string "acpi=off apm=on" I can definitely and finally have  Ubuntu on my PC, but I can't shut down the system, see the battery  level, etc. :???:
I was looking for something else.
Now i'm going to change video driver, let's pray...

---

### Post by mastablasta on 2013-10-17
also post system specs (especially GPU, CPU, mothebaord, if laptop maybe model also. etc.): [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by stefano3 on 2013-11-14
Problem magically and suddenly disappeared.. :neutral:
BTW thank you everyone
):P

---

