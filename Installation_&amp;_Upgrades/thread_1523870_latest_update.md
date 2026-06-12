---
title: "latest update"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by rockrhino27 on 2010-07-04
Anybody have a problem with the latest ubuntu 10.04 update?  

I updated my system yesterday.  It required a restart.  I restarted the computer, got to GDM.  Logged into the system, my wall paper comes up then it stops.  The gnome-panels don't come up, my desktop icons never come.  I let it sit for a while, thinking it was running something in the background but nothing.  I then went to a terminal and ran ps auxw, and nothing was pegging the CPU.  I get a mouse cursor, but cannot do anything.  When I manually restart gdm I also get the same thing.  

Any ideas?  

I have never come across anything like this before...  Any help would be appreciated.  

Thanks, 

Rock

---

### Post by dino99 on 2010-07-04
boot without "splash" (edit the boot line)

then into a console:

metacity --replace &
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

---

### Post by TheBilgeRat on 2010-07-04
Same problem with Xubuntu 10.04 update.  Boots fine from previous kernel but th latest hangs on "display not supported".  Complaints on Plymouth in the logs.  I will just wait for an official fix to this issue.  It feels like Dapper all over again :P

---

### Post by rockrhino27 on 2010-07-06
I tried reconfiguring GDM and Plymouth.  

dpkg-reconfigure gdm
dpkg-reconfigure plymouth

No love.  I think i am going to edit the grub.cfg file to boot from the old kernel.  

Any suggestions on how to do that?  

Thanks for all the help thus far.  I love Ubuntu!!!

Rock

---

### Post by rockrhino27 on 2010-07-06
That didn't work.  I un-hid the hidden grub menu and tried two linux kernels back.  I guess the problem is not with the new kernel, but with some software package relating to the gnome desktop.  When I have more time i'll have to re-install 10.04 and remember not to update....   :(

Rock

---

### Post by Dilutu on 2010-07-06
Same for me here: I dont get my panel until about one minute after the desktop is up and running.

---

### Post by danielcraigie on 2010-07-07
No problem with my graphics card but since the restart the machine won't suspend or hibernate.  I found this out when I picked up the netbook (inside its carry case) and almost burned my hand!  Closing the lid does not put the computer to sleep, nor when I click suspend/hibernate from the main menu.

Another side effect of the software update is that I can no longer use the touch screen interface.  After several attempts to re-calibrate it I noticed that no matter where you put the stylus on the screen, it is interoperated as a click in the top left corner of the screen.  Perhaps I need to re-install the drivers again?

[Asus EeePc T101mt - Ubuntu 10.04 netbook edition]

---

