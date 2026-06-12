---
title: "Problems w/ Upgrading - X Server"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by th3gh05t on 2006-06-01
Hi, 

After the long process of downloading and installing of the packages through apt-get in the Terminal. I finally rebooted my computer in anticipation of the new release.

To my demise, it didn't load the X server correctly and I am not sure how to restore it. 

If I let Ubuntu load up normally, I get all of these Inbound and Outbound connections displayed across the screen for my eth0. So I tried to load up the recovery kernal, and then "startx" from there. 

Again, it had problems starting Gnome. 

Here is the error message that I am getting:

> Fatal Server Error:
failed to initialize core devices

Please consult the Xorg Foundation project

Pleas also check the log file at "/var/log/Xorg.0.log" for additional information.

XIO: fatal IO error 104 (Connection reset by peer) on X Server ":0.0"
after 0 requests (o known processed) with 0 events remaining.

Has anyone else experienced problems upgrading? Are there any files or logs that you need to see in order to answer my question? How would I get those files off the computer?

Thanks for your time!

th3gh05t

---

### Post by th3gh05t on 2006-06-01
I did a little digging and found out the GDM isn't configured correctly either. 

When I tried the cmd, "sudo dpkg-reconfigure gdm", I got the following error message:

> 
invoke-rc.d:initscriptgdm, action "reload" failed.
install-menu: Warning: Unknown identifier 'removemenu' on line 47 in file /etc/menu-methods/xdp-desktop-entry-spec-apps. Ignoring.
install-menu: Warning: Unknown identifier 'removemenu' on line 51 in file /etc/menu-methods/xdp-desktop-entry-spec-apps. Ignoring.


Additionally, when I try and run "sudo /etc/init.d/gdm restart", it tries to load up the GDM but then it says that it isn't configured properly, and offers to show the log file.

Please help me out!!

---

### Post by cvmostert on 2006-06-01
It looks like i have the same problem, after upgrade, the gdm does not work, or is not configured right.. i will try what you did and see if i get lucky.. 

if something wierds happens and i get it right ... i will post here..

---

