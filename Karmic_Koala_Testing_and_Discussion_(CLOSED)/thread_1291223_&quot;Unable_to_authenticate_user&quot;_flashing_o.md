---
title: "&quot;Unable to authenticate user&quot; flashing on startup 9.10a"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by madde001 on 2009-10-14
Hi,

I'm somewhat new to Ubuntu, so bear with me. I just upgraded from 8 to 9.10b. I've got the server version installed, but I still have gdm installed since I like to login to the graphical desktop for many of my applications.

Since installing, I can boot fine, and I can login via terminal, SSH and also via webmin. But when I try to login locally to the gdm desktop, the "spotlight" splash comes up, then the screen goes black for several seconds, then the spotlight background comes up again and I get the black panel against the spotlight background with the ubuntu logo and my computer's name, where-- I guess -- I should be offered to enter my username/password.

EXCEPT instead of that, the panel starts blinking on and off and on, and every 5-6 blinks it displays the message "Unable to authenticate user". And I can't get control of the local screen from my keyboard.

I can still login via webmin, and -- for what it's worth -- my most-cpu intensive process has the command line:

	/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-E5hJTf/database -nolisten tcp vt7

and it shows these other gdm-related processes running:

  1363	root	12:04	gdm-binary
      1567	root	12:04	/usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
         1616	root	12:04	/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-E5hJTf/database -noli ...
         2638	gdm	12:05	/usr/bin/gnome-session --autostart=/usr/share/gdm/autostart/LoginWindow/
            2709	gdm	12:05	metacity
            2739	gdm	12:05	gnome-power-manager
            30597	gdm	12:20	/usr/lib/gdm/gdm-simple-greeter
  2636	gdm	12:04	/usr/bin/dbus-launch --exit-with-session
   2637	gdm	12:05	/bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
   2641	root	12:05	/usr/lib/devicekit-power/devkit-power-daemon
   2662	gdm	12:05	/usr/lib/libgconf2-4/gconfd-2
   2687	gdm	12:05	/usr/lib/gnome-settings-daemon/gnome-settings-daemon --gconf-prefix=/apps/gdm/si ...
   2700	gdm	12:05	/usr/lib/gvfs/gvfsd
   2702	gdm	12:05	/usr/lib/notification-daemon/notification-daemon

Can somebody help me figure out how to get a well-behaved login panel for the graphical desktop?

John

---

