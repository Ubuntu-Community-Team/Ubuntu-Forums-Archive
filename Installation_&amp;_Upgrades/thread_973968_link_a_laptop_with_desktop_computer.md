---
title: "link a laptop with desktop computer"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by mucmicu on 2008-11-07
Hi there

I'm a windows user and I'm really new in GNU world but i wish to learn, and the best method to learn is to read and try. I have home,  two computers( a laptop and a desktop). My wish is to have Ubuntu on the desktop machine and Vista on the laptop but to work only from the laptop. I have a router which give us the IP's, so the machines are in a network.

1) Is possible to work only from the laptop and command the desktop computer? As far I've read is about using a samba server. Can you give me a good resource about how to do that?

2) How healthy is for a beginner and my desktop to configure Ubuntu first on my laptop using VMWare and latter to put that image on the desktop?

many thanks

---

### Post by meindian523 on 2008-11-07
> **mucmicu said:**
> Hi there

I'm a windows user and I'm really new in GNU world but i wish to learn, and the best method to learn is to read and try. I have home,  two computers( a laptop and a desktop). My wish is to have Ubuntu on the desktop machine and Vista on the laptop but to work only from the laptop. I have a router which give us the IP's, so the machines are in a network.

1) Is possible to work only from the laptop and command the desktop computer? As far I've read is about using a samba server. Can you give me a good resource about how to do that?
First of all,welcome.About your questions,
Samba is the answer,but you will have to wait for people who have used it to point you to good resources about how to use it.
> **mucmicu said:**
> 
2) How healthy is for a beginner and my desktop to configure Ubuntu first on my laptop using VMWare and latter to put that image on the desktop?

many thanks

As a learning experience,probably very good.Do you intend to make a customized install of Ubuntu which you would later transfer to your desktop?

---

### Post by greatgoogamooga on 2008-11-07
Many questions, many answers.

you can do all of the above.  My suggestion would be to install Ubuntu on the desktop, then use VMWare on the laptop.  You can then boot into Ubuntu on VMWare, but connect to the desktop by selecting XDMCP to remotely log into the Desktop.  You must first configure the desktop to allow remote logins.

The disadvantage to XDMCP is the speed of the network.  If you have a slow connection between your computers, you will see a lag.  Then there's the speed that you will lose because VMWare is still slower that actually booting into Ubuntu directly.

Samba will allow you to share files with windows computers on a windows network, but not control another computer.

Do you have room on the HD to install Ubuntu as well as windows, so you can dual boot?  How about a USB stick?  You can boot Ubuntu with a USB drive, then use XDMCP...or create a persistant USB drive and save any info onto it.

Goog

---

### Post by meindian523 on 2008-11-07
And Ubuntu 8.10(Intrepid Ibex) has an option in the menu itself to install to a USB drive.:)

---

### Post by tarps87 on 2008-11-07
You can also use a VNC program on your laptop which will allow you to control the desktop without the need for Ubuntu on your laptop. It will work like windows remote desktop so you will need to have a user logged onto the desktop pc, although unlike the windows one you can still use the desktop at the same time. From Ubuntu you can enable it under system -> preferences -> remote desktop, from windows you will need to find a VNC program.

---

### Post by mucmicu on 2008-11-07
wow, many thanks for you fast and detailed answers. This seams to be a great community and I'm happy to be near you.

Now I'm installing Ubuntu on my desktop machine and I'll try to configure samba, in order to control it from windows. 

I really don't need to have the graphical interface. If I'll be able to login into the desktop from the laptop using a command line interface this will be great for me.

---

### Post by greatgoogamooga on 2008-11-07
If all you need to do is share files, then Samba will do the trick nicely.  I highly recommend that you install SWAT (a web interface) to make configuring Samba easier.

Again, Samba will not allow you to _control_ the desktop, only share files.

If you do not need a graphical interface, and are familiar with bash/shell commands, you can either telnet or SSH in a terminal.

---

