---
title: "Boots into prompt - no GUI"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alligoodw on 2009-08-21
I just did a fresh clean install of Karmic Koala Alpha 4.  OS was installed on a HP Pavilion dv6000 laptop.  OS is shared with Windows Vista - Grub 2 looks great. 

When I load up using the Karmic Koala (development) menu item, I boot up to a prompt, I never get to the GUI; the Karmic Koala recovery doesn't do any better.  Question - how do I correct this problem?  How do I get into the GUI?

---

### Post by inportb on 2009-08-21
Did you do any partial upgrades earlier? It might be a good idea to install ubuntu-desktop (or whichever you use) just to make sure you have everything...

---

### Post by alligoodw on 2009-08-21
This is what happened.  

I had Ubuntu (Desktop) 9.04 installed on my system; I upgraded to Karmic Koala Alpha 4.  This morning, I did a partial update and couldn't get back into my system - I had the prompt again, no GUI.  I thought to myself, maybe I should just download Alpha 4 and install it over what I had on my hard drive.  I downloaded the ISO and burned it.  During the installation, I allowed Karmic to handle the partioning automatically, partitioning a windows (Vista) and a ubuntu OS.  I rebooted the system.

I noticed GRUB 2 immediately - its very nice!  Selected Karmic Koala development version menu item sent me to the prompt - no GUI.  This is where I am.

---

### Post by cariboo on 2009-08-21
It may sound simple, but have you tried typing startx at the prompt to see what happens?

---

### Post by Krause on 2009-08-21
The recent update installed Nvidia 185 drivers, and removed the old Nvidia 180 packages, either the removal of the old took some of the new packages out, or it forgot some needed 185 packages I'm not sure.

Simple fix, from console type "sudo apt-get update" and when that finishes type "sudo apt-get install nvidia-185-kernel-source"

The rest of the needed files will be found as dependencies and auto installed after you authorize it by hitting "y"

"sudo reboot" when its finished and your good to go again.

---

### Post by rtalcott on 2009-08-21
Had the same problem....followed the directions....the response was that the 185 kernel source was there....I rebooted....now I have HUGE fonts on the screen and am trying to login but it's a bit of a mess...this may mean a reinstall...

EDIT: Did a hard reboot and now I have normal fonts + can login...still no gui and I confess to being clueless as to how to get there.
rt

---

### Post by Krause on 2009-08-21
> **rtalcott said:**
> Had the same problem....followed the directions....the response was that the 185 kernel source was there....I rebooted....now I have HUGE fonts on the screen and am trying to login but it's a bit of a mess...this may mean a reinstall...

EDIT: Did a hard reboot and now I have normal fonts + can login...still no gui and I confess to being clueless as to how to get there.
rt

have apt remove the package and then reboot and have it reinstall. It could be there but due to how it was installed/the 180 package being removed it might not have the dependencies it needs.

also before you do that, do a apt-get upgrade, it had additional packages (a new kernel) after the initial install/reboot that screwed up the video driver.

---

### Post by rtalcott on 2009-08-21
Krause:  Thank You!  I will give it a try shortly!
rt

---

### Post by rtalcott on 2009-08-21
Krause:  Thank You!  That worked!!!!!!!!!!!!!!!!!

rt

---

### Post by cornflake000 on 2009-08-21
this just happened to me but having gone through this in the jaunty alphas, this is all I have to do...

change xorg.conf to the failsafe ie. vesa

restart.. you'll get the 640x screen

in administration/hardware drivers, upgrade the nvidia driver to 185 (again)

restart...

all is normal again...

---

### Post by caryb on 2009-08-22
I have followed the instructions & removed -> rebooted -> reinstalled & still have the Black screen of Death. I cant even ctl + alt F1 to a terminal I have to power off & go to recovery to change back to nv driver.


Any thoughts? BTW I'm using Kubuntu but that shouldn't make any difference.


Cary

---

### Post by chrismine on 2009-08-22
I had the same problem and managed to fix it like this:
Go to safe mode and choose e to edit the startup entry and delete splash and vga=795 and use Ctrl + X to boot into safe mode otherwise it boots with splash on and you just get a blinking cursor.
I then did a sudo apt-get update and sudo apt-get upgrade which pulled in the kernel stuff but it still did not work. I then noticed when I do startx that it says no screens found and no driver loaded so I did sudo apt-get install nvidia-185-kernel source but something was still amiss. I then did sudo apt-get install nvidia-185-glx and it downloaded and compiled the driver and after startx I booted into Ubuntu normally.

Originally there was a partial upgrade and everything looked allright so I went ahead. Looked all the packages were not ready yet, but then why did it not block the upgrade I wonder. The Nvidia driver changes has been working very well for me lately and this is the first problem with Nvidia in a long time...

Hope it helps somebody.

Most of the info I got from reading the latest threads on the forums - thanks for your everybody that posted!

---

### Post by StevenKinloch on 2009-08-22
Had the same problem after partial upgrade (22 Aug), booted to command prompt, no GUI.

> **Krause said:**
> Simple fix, from console type "sudo apt-get update" and when that finishes type "sudo apt-get install nvidia-185-kernel-source

The above command fixed the problem and all looks normal. Thanks Krause.

Constantly impressed that an Alpha version runs so well. I've had installs of XP that fall over more than this!

---

### Post by BobCFC on 2009-08-22
> **Krause said:**
> have apt remove the package and then reboot and have it reinstall.

Thanks! Removing nvidia-185-kernel-source and then reinstalling it triggered the missing nvidia-glx-185 and now it works! (Didn't need to reboot)

Fortunately I could browse to the forums form the command line using the w3m browser lol

---

### Post by bren21 on 2009-08-22
> **chrismine said:**
> I had the same problem and managed to fix it like this:
Go to safe mode and choose e to edit the startup entry and delete splash and vga=795 and use Ctrl + X 

Dude, your a lifesaver. Thanks.

---

### Post by evets on 2009-08-23
> **Krause said:**
> The recent update installed Nvidia 185 drivers, and removed the old Nvidia 180 packages, either the removal of the old took some of the new packages out, or it forgot some needed 185 packages I'm not sure.

Simple fix, from console type "sudo apt-get update" and when that finishes type "sudo apt-get install nvidia-185-kernel-source"

The rest of the needed files will be found as dependencies and auto installed after you authorize it by hitting "y"

"sudo reboot" when its finished and your good to go again.


Sweet! Thanks for the help, you saved my bacon. :P

---

### Post by Wistful on 2009-08-23
With the kernel 2.6.31-6-generic, Nvidia drivers 185.18.36/173.14.16 fully installed I can't manage to start either GDM/KDM/XFCE correctly. 

X is starting but for some reason when I try to go GUI it remains black. I read the logs but I can't figure it out what the problem is so I was thinking I should patch my kernel to a new PatchLevel and that solved the problem.

---

