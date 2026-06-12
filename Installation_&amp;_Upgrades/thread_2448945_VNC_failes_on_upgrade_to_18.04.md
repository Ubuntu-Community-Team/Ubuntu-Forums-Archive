---
title: "VNC failes on upgrade to 18.04"
date: 2020-08-17
forum: Installation &amp; Upgrades
---

### Post by merlinsilk2 on 2020-08-17
Hi, today I finally had the guts to upgrade from 16.04 to 18.04 and mostly this seems to have worked. I could still log in via putty from my windows machine, but where I ran into trouble was VNC access. On the windows side I am using a realvnc viewer and on the ubuntu side I am using x11vnc (pretty sure) server. It appears that I can not start x11vnc because there is no X server running - but I am not sure what to look for in the list of running processes to determine what I have running - if any - in terms of a graphical interface. This is a remote server with a dongle in the hdmi port to simulate a connected display, so I can't really see if I just have a command line or a graphical login (which had been the case in 16.04). As far as I understand, there were big changes in the graphics part of ubuntu in this update.
Any help to point me in the right direction on getting that VNC access re-established would be very much appreciated.
Thanks - Merlin

---

### Post by merlinsilk2 on 2020-08-18
I was actually mistaken with my assumption that most of the upgrade had gone right. I pulled the server out of its rack and connected monitor and kb/mouse and nothing really worked on the graphical side. I spend a bit time to fix it, but as the goal had been to to to 20.04 after the intermediate step if 18.04, I abandoned 18.04 and started fresh with a new download of 20.04 - that was my second attempt to update an ubuntu - I promise I will never do this, better to save all the customization and start with a clean install.
Anyway - I have done most of it working again, except one shortfall that I might need a bit help with:
I have to automatically log into a user to get the X desktop. 
Systemd starts the vnc server with 
ExecStart=/usr/bin/x11vnc -display :0 -auth /run/user/1000/gdm/Xauthority -rfbauth /root/.vnc/passwd -shared -forever -o /var/log/x11vnc.log
and I can connect from my windows vnc client. But when I log out, I will lose the connection to the vncviewer and never get it back (except reboot - which will log in the user).
If I don't log in automatically, there does not seem an X session to which x11vnc can connect - the xopen fails.
Could somebody give me some insight in what is actually running on my terminal when nobody is logged in and the login screen is displayed - how would I authorize x11vnc to connect to that and then to the X session that start after logging in?
Under 16.04 that had been working, and I did not need to be automatically logging into a user account.
Thanks - Merlin

---

