---
title: "VNC Installation need help please"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by tripower on 2010-04-13
I really need some assistance. I have Ubuntu (Karmic) on one box and a Win 7 box. I need to get some sort of VNC client on the Ubuntu box and a VNC server on the Win 7 box. I chose tightVNC because it seemed to have both pieces but I cannot seem to install or find the tightVNC client for Ubuntu. I used the Synaptic Package Manager to install the tightVNC server and Java applet but I cannot find them anywhere. Can someone assist on getting the tightVNC client installed on Ubuntu and/or recommend a different VNC server/client or help me with connecting to this Win 7 box via RDP?

---

### Post by tripower on 2010-04-13
Anybody?

---

### Post by Bobhuber on 2010-04-13
I use Ultra VNC to access a Win7 box by using the Wine program to load the VNC client executable.
Works fine.

---

### Post by tripower on 2010-04-14
I would really appreciate it if you could give me the steps for installing UltraVNC using WINE. Thanks.

---

### Post by anglican on 2010-04-15
> **tripower said:**
> I would really appreciate it if you could give me the steps for installing UltraVNC using WINE. Thanks.

Using a VNC viewer under wine is... unnecessary, there are plenty of viewers in the repo. You can also use "Remote Desktop Viewer" from the standard network menu, though personally I don't like it. I use xvnc4viewer ("sudo apt-get install xvnc4viewer) although I vaguely recall that it didn't install a desktop file... so doesn't show up in the menus. To fix this create a file /usr/share/applications/xvnc4viewer.desktop (you'll need to use sudo for this - plus your favourite editor) containing:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=VNC client
GenericName=xvnc4viewer
Comment=View a remote VNC
Type=Application
Exec=xvnc4viewer
Icon=network-receive
Categories=Application;GTK;Network;

Which will give you a program "VNC client" in the Network menu.

H

---

### Post by Bobhuber on 2010-04-15
> **tripower said:**
> I would really appreciate it if you could give me the steps for installing UltraVNC using WINE. Thanks.
Install wine thru the synaptic package manager in Ubuntu.Download UltraVnc client and server from there site.Install the server on the windows box.Depending on your version of Ubuntu as to what you have to do to run the client.exe with wine.With Karmic 9.10 all I had to do was drag the client.exe to my desktop (that automatically creates a link to the file ) right click on the link and tell ubuntu that I wanted to use wine to run the program.Just that simple.You will of coarse have to configure the VNC software.
If you don't want to use wine just install Sun Virtual box and you can load an entire Windows operating system.

---

### Post by tripower on 2010-04-21
> **anglican said:**
> Using a VNC viewer under wine is... unnecessary, there are plenty of viewers in the repo. You can also use "Remote Desktop Viewer" from the standard network menu, though personally I don't like it. I use xvnc4viewer ("sudo apt-get install xvnc4viewer) although I vaguely recall that it didn't install a desktop file... so doesn't show up in the menus. To fix this create a file /usr/share/applications/xvnc4viewer.desktop (you'll need to use sudo for this - plus your favourite editor) containing:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=VNC client
GenericName=xvnc4viewer
Comment=View a remote VNC
Type=Application
Exec=xvnc4viewer
Icon=network-receive
Categories=Application;GTK;Network;

Which will give you a program "VNC client" in the Network menu.

H


In order for me to use Remote Desktop Viewer w/ Ubuntu I need to have an RDP server running on the Win7 box. I do not have an RDP server running since it is Win7 Home Premium. I need to install a server component on the WIn7 box and have a client component on the Ubuntu box.

---

### Post by anglican on 2010-04-22
> **tripower said:**
> In order for me to use Remote Desktop Viewer w/ Ubuntu I need to have an RDP server running on the Win7 box. I do not have an RDP server running since it is Win7 Home Premium. I need to install a server component on the WIn7 box and have a client component on the Ubuntu box.

No, remote desktop viewer **is** a VNC client, so if you have the vnc server running on your Windows box you **can** use remote desktop viewer to connect to it. From the manual introduction:

> The Vinagre application is a Remote Desktop Viewer for the GNOME desktop that uses Virtual Network Computing (VNC) system (and possibly other protocols) to remotely control another computer.

H

---

### Post by chargersfan420 on 2010-05-03
> **anglican said:**
> Using a VNC viewer under wine is... unnecessary, there are plenty of viewers in the repo. You can also use "Remote Desktop Viewer" from the standard network menu, though personally I don't like it. I use xvnc4viewer ("sudo apt-get install xvnc4viewer) although I vaguely recall that it didn't install a desktop file... so doesn't show up in the menus. To fix this create a file /usr/share/applications/xvnc4viewer.desktop (you'll need to use sudo for this - plus your favourite editor) containing:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=VNC client
GenericName=xvnc4viewer
Comment=View a remote VNC
Type=Application
Exec=xvnc4viewer
Icon=network-receive
Categories=Application;GTK;Network;

Which will give you a program "VNC client" in the Network menu.

H

Hey, this worked great for me.  Thank you very much!

I'm connecting to several XP boxes using UltraVNC, and xvnc4viewer seems to be the only one that works for me.  (Using MS Login on some of my boxes, and don't want to go around changing that).

Anyway, just curious if anyone is aware of a better GUI for xvnc4viewer.  Something that can remember a list of connections, and scale down the screen size for servers that have larger displays than the client.  Any suggestions?

---

### Post by anglican on 2010-05-04
> **chargersfan420 said:**
> Hey, this worked great for me.  Thank you very much!

I'm connecting to several XP boxes using UltraVNC, and xvnc4viewer seems to be the only one that works for me.  (Using MS Login on some of my boxes, and don't want to go around changing that).

Anyway, just curious if anyone is aware of a better GUI for xvnc4viewer.  Something that can remember a list of connections, and scale down the screen size for servers that have larger displays than the client.  Any suggestions?

On a Linux server, if you're using x11vnc you can use e.g.

x11vnc -q -scale 0.8:nb -display :0 -usepw

which will scale your server display to 80%. I would guess that the Windows servers UltraVNC or TightVNC might have something similar - I don't use Windows at all any more so can't be more specific. The point is that the scaling is done at the server end usually. In my experience, there is appreciable loss of resolution when you scale down like this.

H

---

