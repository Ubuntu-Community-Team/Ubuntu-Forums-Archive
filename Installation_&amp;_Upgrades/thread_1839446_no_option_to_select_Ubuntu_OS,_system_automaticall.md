---
title: "no option to select Ubuntu OS, system automatically switching to Window7"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by pcvaishnav on 2011-09-05
hello all,
greetings!

Ubuntu New for me, I have successfully installed Ubuntu 11.04 Along with Windows7. After installation i have restarted my computer.

I have installed Ubuntu inside Windows through a USB flash Drive.

But there is no option to select Ubuntu OS, system automatically switching to Window7.

Please help me out, what i have to do run Ubuntu OS Along with Windows7.

Regards,
pc vaishnav

---

### Post by Sef on 2011-09-05
Use a Live CD/USB and to the terminal copy and paste this command ```
sudo fdisk -l
```.

copy and paste the results here.

---

### Post by Dumbutt on 2011-09-05
I'm a newbe too, but know the problem you're referring to, so try this:  Do a reboot, restart...and have your finger on the &quot;Down Arrow&quot; on your keyboard, as soon as you see the purple screen with a type written list in the upper left hand corner pop up,  ~[it only stays there for a couple seconds or so, before moving on to the start up.]  As soon as you see the typed written list, Quickly hit your down arrow to freeze it there, read the list to select the OS that you want to boot up, [with your up / down arrows & hit Enter.]     In the Windows system, you can also type &quot;Misconfig&quot; into your &quot;Search&quot; and look at your boot-ins, see how many 'seconds' you have set for your delay on the boot screen, you can give yourself 10 seconds, or 15 seconds or ? so as to give yourself enough time to read your options on the reboot screen, to select the OS that you want too.   Hope this helps!

---

### Post by Mark Phelps on 2011-09-05
The entry you need to make in Windows is "MSCONFIG" -- Not Misconfig.

---

