---
title: "base session script error"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by drumanart on 2008-05-21
Hello folks.
Everytime I open the GNOME Desktop I get the failer message:
[B]
Cannot find or run the base session script.
Running the GNOME failsafe session instead[/B].

After this message a pop-up window shows up with:
[B]
This is the Failsafe GNOME session. You will be 
logged into the "Default" session of GNOME without
the sturtup scripts being run. This should be used
to fix problems in your installation.[/B]

Also if I try to start **fluxbox** I land allways in the GNOME failsafe mode.
Thks

---

### Post by Partyboi2 on 2008-05-21
Have you tried reinstalling gnome-session?

---

### Post by drumanart on 2008-05-22
No, and as a UBUNTU novice I don't know how to reinstall the GENOME session.
Thks for help

---

### Post by Partyboi2 on 2008-05-22
When you get to the login screen instead of entering your username and password  press Ctrl+Alt+F2 to get to a terminal, then login. After you have logged in reinstall the package.
```
sudo apt-get install --reinstall gnome-session
```

---

### Post by drumanart on 2008-05-22
If I press Ctrl+Alt+F2 (at the loggin screen) the monitor becomes black like the universe and nothing happens anymore.
Is ist because I have the UBUNTU-STUDIO installed?.

---

### Post by Partyboi2 on 2008-05-24
Can you get to a working teminal when you boot into recovery mode? When you boot your system wait till you see grub loading on the screen then press "Esc" to enter grub menu then choose recovery mode. Recovery mode should take you to a teminal where you can try to reinstall gnome-session

---

### Post by drumanart on 2008-05-25
Ok, I reinstalled GNOME but but unfortunately without success.

---

### Post by spibou on 2009-04-25
Ok this is an old thread but in case anyone else has the same problem the following is worth a try:
```
sudo chmod 755 /etc/gdm/Xsession
```
Try to login again and see if it works.

---

