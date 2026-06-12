---
title: "Unable to open display"
date: 2019-06-28
forum: Installation &amp; Upgrades
---

### Post by ndnd on 2019-06-28
Hello, 
I had earlier been able to login remotely (using vnc) to ubuntu server 18.04 running xfce4. I am now however running into the following problem 

Whenever I log in I only get a blank window with an X sign. I tried reseting the VNC connection and have also checked SSH x11 forwarding. All works fine. 

I tried to see if executing the command to start the xfce would help but it gave the following error 

> 
 startxfce4
/usr/bin/startxfce4: X server already running on display localhost:10.0
xrdb: Resource temporarily unavailable
xrdb: Can't open display 'localhost:10.0'
xfce4-session: Cannot open display: .
Type 'xfce4-session --help' for usage.



I also tried to do 

> 
 echo $DISPLAY
localhost:10.0


This seems right. Then I tried 

> 
export DISPLAY='IP:0.0'


I also moved the .cache folder and .xsession_error file in case it helps (someone had suggested doing so online)

In case you need more info can you please tell me the exact command to get that info as well. 

I feel there is something corrupted

---

### Post by TheFu on 2019-06-28
The gray screen with an X is the X root window. Right click anywhere to see a menu.  Looks like you just need to run the window manager that you want.  Start a terminal from the menu and run whatever you like, assuming it doesn't need direct access to a GPU.  **openbox** is pretty safe. I don't know what xfce uses for a window manager.

I don't use vnc. I think there are better options for my needs, so I'm unfamiliar with the startup files it uses.

---

