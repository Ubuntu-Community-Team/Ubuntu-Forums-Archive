---
title: "how to install vnc"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by dark lord on 2010-07-13
Hello,

I am new to this forum i just joined to ask .. how to install vnc on a headless/monitor-less Ubuntu 10.04 ?i googled A LOT i couldn't find a well explained guide .. i am not sure if this is the right place to post the thread. if it is not please move the thread.

thanks,

---

### Post by Naitsirhc Hsem on 2010-07-13
I would look at vino, default vnc server for ubuntu.  which version of ubuntu are you using?

---

### Post by Naitsirhc Hsem on 2010-07-13
System > preferences > remote desktop
same ports as regular vnc

you might want to enable automatic login, vnc only works once logged in

---

### Post by dark lord on 2010-07-13
> **Naitsirhc Hsem said:**
> System > preferences > remote desktop
same ports as regular vnc

you might want to enable automatic login, vnc only works once logged in
Hello,
my VPS is using "ubuntu-10.04-minimal_10.04_i386" i am using Windows XP , i want to control the VPS with VNC i heared that it is the "best" for remote desktop.

---

### Post by dark lord on 2010-07-13
Bump~ sorry i really need help with this >.<"

---

### Post by Naitsirhc Hsem on 2010-07-13
[http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)

guide

---

### Post by dark lord on 2010-07-14
Hello,
thanks for the guide but it is for Ubuntu to Ubuntu .. i am looking forward a Windows to ubuntu ..

---

### Post by dark lord on 2010-07-14
Hello guys,
i think i asked it in the wrong way .. i rebuild the VPS it doesn't have gnome or anything for graphic interface . so i am looking forward a guide that allow me to install a graphic interface and setup vnc remotely all i have is an SSH access.

---

### Post by Naitsirhc Hsem on 2010-07-14
ok, for a gui, ```
 sudo apt-get install gnome-desktop 
```

you need to enable automatic login, search for that here

vnc works on both windows and linux

---

### Post by YesWeCan on 2010-07-14
Or...you can use 'tightvncserver'. This doesn't require you to be locally logged in to the VPS like 'vino' does. Instead, you export an independent desktop (or more than one if you wish). You still need to install gnome-desktop as previously advised but you won't need an auto-login. I prefer this because I don't want to be logged on where my server is when I am not there.

You can find a vnc viewer for Windows here: [http://www.tightvnc.com/](http://www.tightvnc.com/)

Be aware that vnc is not secure. So it is unwise to use it over a public internet because it would be very easy for a hacker to log in to your VPS. An encrypted tunnel is required for this such as an SSH port-forward or a VPN.

---

### Post by dark lord on 2010-07-14
Hello,
thanks guys for the help .. i used tight vnc .. in this guide .. it is REALLY great and well explained...[http://markus.revti.com/2009/08/installing-vnc-remote-desktop-on-ubuntu-linux-vps/](http://markus.revti.com/2009/08/installing-vnc-remote-desktop-on-ubuntu-linux-vps/)

---

### Post by amr mohsen on 2010-10-26
thanks but not enough

---

### Post by wannahavelinux on 2010-10-26
I use X11vnc. 

1. Install x11vnc
   sudo apt-get install x11vnc
2. Set up vnc password
   x11vnc -storepasswd
   (by default it will save password in /home/username/.vnc/passwd
3. Edit /etc/gdm/Init/Default
   sudo vi /etc/gdm/Init/Default
   Add the follwoing line before last line (exit)
   /usr/bin/x11vnc -rfbauth /home/username/.vnc/passwd -o /var/log/x11vnc.log -forever -bg
4. Edit /etc/gdm/custom.conf (new file) and add following line
   KillInitClients=false

5. Turn of remote desktop sharing
   Preferences->Remote Desktop
   You won't need it as x11vnc will give you complete solution.

Reboot and enjoy...

---

