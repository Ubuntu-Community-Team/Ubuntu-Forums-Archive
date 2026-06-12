---
title: "Installing VMware Tools the VMware way?"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by grahamt on 2005-05-06
I have been reading lots about Howto Install VMware Tools onto Ubuntu but none of the answers seem to fit the problem.  Perhaps someone out there knows the answer?

I have successfully installed Ubuntu under VMware 4.5.2-8858.  VMware wants me to install VMware Tools to better support video and mouse operation (although it doesn't actually work so badly without!!!!).

However, the instructions demand that the guest O/S is running in command line mode when doing  the install.  It states that merely starting a command line terminal window will not be sufficient.

I read the excellent wiki about installing the VMware Tools and that clearly does indicate a manual installation procedure that enables it to be installed via a terminal window as root but it falls at the first hurdle for me, if I have read it correctly as it seems to assume that I have access to the VMware Installation CD, which I don't.

So, it seems that what I need to do is follow the VMware instructions to return to a command line interface after Ubuntu has completed booting and after installing VMware Tools, restart the gui interface.

Can anyone help me with the procedure/commands I need to issue in order to get back to a command line interface and then to (presumably) restart Xwindows and Gnome afterwards?

---

### Post by grahamt on 2005-05-06
Finally I found the answer to my own question, well, mostly.  The command (issued from the Root Terminal in Applications > System Tools) is - killall gdm.  This drops you back to Command Line Linux at a Login Prompt (you lose your login that you did initially).  Here you can login as Root and start tackling the VMware Tools installation.

I haven't tried restarting Xwindows and Gnome.  I just do a shutdown -h now and then reboot.

I understand that with Rel 5 of VMware you don't have to go through this rigmarole.  You can install VMware Tools in a graphical environment

---

