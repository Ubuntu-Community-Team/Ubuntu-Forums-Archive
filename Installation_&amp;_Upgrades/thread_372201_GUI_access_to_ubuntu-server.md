---
title: "GUI access to ubuntu-server"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by jdpipe on 2007-02-27
Hi all

I am trying to gain GUI access to a recently-installed ubuntu-server machine so that I can do some GUI based administration. I'm doing all this remotely via SSH.

First thing was that I ran "apt-get install ubuntu-desktop". This installed a zillion packages but didn't give any errors.

But afterwards, even after a reboot, I get no response when I type 'xeyes'. The console just sits there:

user@host:~$ xeyes

user@host:~$ (after ctrl-C)

I am connecting via 'ssh -X [email]user@host.doma[/email]in'.

I tried running dpkg-reconfigure xserver-xorg but that didn't help.

I also tried 

sudo /etc/init.d/gdm start

but it didn't help either.

Is there some residual configuration from the ubuntu-server installation that is stopping the ubuntu-desktop from starting up as expected? Do I actually need to sit in front of this computer in order to get it working correctly in the GUI mode?

Would appreciate any suggestions. Also -- what are the security implications of installing X, GNOME etc on a server?

Cheers
JP

---

