---
title: "Install Nvidia driver 260.19.12"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2010-10-23
I've searched and seen many how to's and guides to installation of the new nvidia driver.  I have tried to install the two suggested drivers in ubuntu 10.10 driver update utility.  However, neither of them worked.  On reboot I get the tty console without the gui.  So, I had to enter the recovery mode and then un-active the driver.

I saw some instructions on manually installing the current driver from nvidia's web site.

Stop GDM
install
reboot etc...

I see these instructions....

cd desktop
sudo /etc/init.d /gdm stop
sudo sh ./Nividia-Linux-x86-260.19.12.run

choose x.org automatic configuration  at last step of installl

sudo reboot


I have tried this, but when I kill or stop the gdm I just see my wonderful picture I use as my back ground.  I don't see the tty console or terminal.....

Should I get rid of the background image and use the stock purple one?

Any advice on this?

I see some mention of the code.....  sudo telinit 5

blacklisting several items....

disabling nouveau

I'm quite confused as I see soooo many ways of doing this, which method is correct and which steps do I need to follow.

---

