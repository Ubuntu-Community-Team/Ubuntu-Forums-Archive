---
title: "dpkg: status database area is locked by another &gt;
dpkg installer problem"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by pibot on 2005-04-10
Hi,
I'm having troubles installing .deb packages, i allready installed a package

opera_7.54-20050131.5-shared-qt_en_sarge_i386.deb
and everything worked fine, Now dpkg makes problems when i try to install other .deb packages.

dpkg: status database area is locked by another process

I hope its the right translation because i have the german version of ubuntu 5.04 hoary.

How can i find out which process this is and unlock it, I allready tried lsof and lsof | less but it does not help me.

---

### Post by alastair on 2005-04-10
What about :

ps ax | grep dpkg

---

### Post by pibot on 2005-04-10
Thank you but, i still don't know how to solve this problem, I searched the web for two days to find a solution. The man pages for dpkg didn't help. Does anyone know about this Problem?

---

### Post by az on 2005-04-10
The only programs that can lock the database are dpkg frontends like apt-get, synaptic, aptitude or dselect.

---

### Post by pibot on 2005-04-10
THANK YOU ;-))
I killed thy Synaptic Process and everything worked well,
I don't know why this process is locking the status database and hope I don't to do it everytime I'm using dpkg.


--oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=39
 7772 ?        S      0:01 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=40
 7774 ?        S      0:04 /usr/lib/gnome-applets/stickynotes_applet --oaf-activate-iid=OAFIID:GNOME_StickyNotesApplet_Factory --oaf-ior-fd=41
 8640 ?        S      0:00 gksudo /usr/sbin/synaptic
 8641 ?        S      0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- /usr/sbin/synaptic
 8642 ?        S      0:02 /usr/sbin/synaptic
 8930 ?        S      0:00 /usr/lib/gconf2/gconfd-2 13
10849 ?        S      0:00 pickup -l -t fifo -u -c
11459 ?        S      0:00 gksudo /usr/bin/x-terminal-emulator
11460 ?        S      0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- /usr/bin/x-terminal-emulator
11461 ?        Sl     0:03 gnome-terminal
11464 ?        S      0:00 gnome-pty-helper
11465 pts/0    Ss     0:00 bash
11829 pts/0    R+     0:00 ps ax
[/SIZE]

---

