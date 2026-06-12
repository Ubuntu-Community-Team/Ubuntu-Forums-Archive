---
title: "LAMP Install Complete - Would Like a Simple GUI with Remote Access"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by skorpi0wn on 2006-08-02
I apologize if this has been asked previously, but I haven't been able to find enough information using search tools or by browsing the forums.

I have successfully setup a LAMP box using the Server install CD.  Everything is configured properly and running great.

Now, I would like to add the ability to access this box remotely using a GUI.  All I would like to do with the GUI is use Firefox and a couple of java apps which means I probably don't need KDE, Gnome, or XFCE.

How can I get a minimal install of XWindows with a very simple window manager?  Also, what should I use to access the box remotely?  I've used vncserver in the past, but I don't like how slow it runs.  I tried using FreeNX in the past, but I could never get it to work.

Thanks for any help in advance that you can provide.:D 

Machine:
AMD Thunderbird 800MHZ
768 MB memory
2 - 30GB IBM Deskstar drives in Raid 1 configuration
No local display

---

### Post by az on 2006-08-02
Enable universe and install

sudo apt-get install x-window-system-core gdm icewm menu mozilla-firefox xterm 

Maybe synaptic and a filemanger, too?

You can also install ssh and use that to get into your box.


ssh -X skippy@192.168.1.100
will allow you to log into your box and run remote x applications on your screen.

---

### Post by alex30002 on 2006-08-02
you may use Terminal Servel Client.
It can be found hre Applications > Internet > Terminal Server Client.

It looks like this 

[img]http://img349.imageshack.us/img349/2058/screenshotterminalserverclientbz0.png[/img]

It`s nice and very easy to configure .

Goodluck

---

### Post by alex30002 on 2006-08-02
Delete Me

---

