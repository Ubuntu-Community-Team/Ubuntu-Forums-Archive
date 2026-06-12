---
title: "Problem with ubuntu installation - xserver fails!"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by ccaazz on 2007-03-23
Hey, i have a problem with my pc when i try to install ubuntu, the loader shows the boot screen ok, but once the installation gets past the ubuntu logo with the loading bar, i have a blue and grey screen saying something about xserver faiing.

I am using a dell dimension 1150, with 1 gig of ram, and a 256meg, x600 ati graphics card.

I have gathered that this problem is quite common for ati cards, and have even come accross a solution.

> 1) type: sudo nano /etc/X11/xorg.conf (Remember, Linux is case sensitive)

2) Find the line driver "ati" change it to "vesa" and then press Ctrl+x, then "Enter" to overwrite.

Now You will be able to start the "X", to do it type: startx then "Enter"

3) Now The ubuntu was loaded and you will see a install shortcut in your desktop screen. Well, now just follow the install instruction and setup the system. After you complete the process you will be in a black terminal screen again. Don't worry it just happened because GDM wasn't full loaded and after restart it will not happen again. To restart type sudo shutdown -r "now"


this does not seem to work for me.  When i reach the xserver fails screen, i select "ok" twice, to see the report and then exit.  I am then get a completely blank screen except for a flashing underscore (_) bar.  I can type in the commands here, but nothing at all happens.  

Can someone please explain to me what i am doing wrong here (really really simply please! lol)

- also there someother fix where you press f6 when the bootloader comes up, and delete the phrase --splash (something along those lines).  I tried this, and eventually i seem to be in the console.  However, when i type in the command:  "sudo nano /etc/X11/xorg.conf" - it says somehting about not being able to find the file etc, or the file not existing (mi can't remember what exactly!) 

please help me fix this problem! - if not i will be forced to use another distro lol (will i encounter the same problem on a different distro such as fedora etc?)

THANKS!:guitar:

---

### Post by wpshooter on 2007-03-23
Are you getting this when you are trying to boot off of the CD or have you already installed to your hard drive ?

Thanks.

---

### Post by daynah on 2007-03-23
The way I fixed it was by pressing Ctrl+Alt+F1 to get into the terminal but I never deleted a splash... I then just edited xorg.conf like in the instructions.

---

### Post by ccaazz on 2007-03-23
i get this when i boot off of the cd (i can't even install ubuntu yet!)

---

