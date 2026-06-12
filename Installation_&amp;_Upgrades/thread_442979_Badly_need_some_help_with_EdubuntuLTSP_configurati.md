---
title: "Badly need some help with Edubuntu/LTSP configuration"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by Chris_Hansen on 2007-05-14
Hi everyone,

I work at a large college, where we are planning on setting up at Edubuntu thin client network.

We have installed edubuntu on it's own Xeon Server, but are having some problems changing the default ltsp configuration to match our network settings.

Out of the box, Edubuntu assumes that the clients connect to the 192.x.x.x range. However, we need the clients to run on a specific VLAN instead, more specifically in the 172.x.x.x. range.

Can someone please help me out with detailed instructions on exactly where I need to make changes, i.e. what files, configurations etc. ??

It is starting to get a bit annoying that I can't get it to run, specially considering that I have a large number of thin clients arriving any day - and need to show some results :( 

Thanks in advance.

---

### Post by hboshoff on 2007-05-17
Welcome to Edubuntu, Chris!

Two things need to be done:
[LIST]
[*]Change the IP address of your network interface.
[*]Regenerate the SSH keys.
[/LIST]

The IP address can be set in various ways. Eg on the top panel menu, click System -> Administration -> Network to open the Network Settings applet. Select the relevant ethernet interface currently pointing to 192.x.x.x. It is probably eth0 or eth1 with the heading "Wired Connection." Click on Properties, and edit the IP address and other entries in the Settings window. Click OK, and make sure the interface's box is checked. Click on Close.

You may want to  make sure that the changes took effect by using ifconfig, ifdown eth0 & ifup eth0 in a terminal, or with the applet System -> Administration -> Network Tools (which can be used to do the IP configuration as well).

The applets are only another way to edit the entries in the file /etc/network/interfaces. You can do it directly by launching gedit with superuser privileges. Press Alt-F2 on the keyboard and type "gksu gedit /etc/network/interfaces" in the top box. You will definitely need to ifdown/ifup your interface after saving this file.

For the second item you will have to open a terminal, and type
```
sudo ltsp-update-sshkeys
```

This is briefly documented in the Edubuntu Handbook, which is installed with Feisty. Click on System -> Help and Support, which will open Yelp with Ubuntu Help Center. On the left panel, second from the bottom, is Edubuntu Handbook. Open the chapter "Edubuntu Server and Thin Client Computing" paragraph "Keeping your Edubuntu server in shape" subparagraph 3.5.3 "Changing the IP of your LTSP server."

I highly recommend reading the whole Handbook. It is available on the web as well, at [http://doc.ubuntu.com/edubuntu/handbook/C/]("http://doc.ubuntu.com/edubuntu/handbook/C/").

Boot a client to test. It may be necessary to first reboot the server, but I am told that is a bad Windows habit.

If nobody is using the server yet, and all else fails, you may consider reinstalling. The server IP address is one of the few parameters asked at installation time, and you may enter any valid address, including 172.x.x.x.

I wish you success.

---

### Post by Chris_Hansen on 2007-05-18
Hi hboshoff,

Thank you so much for your very detailed reply.

I will follow your instructions, and post back here then.

Thanks again!

- Chris

---

