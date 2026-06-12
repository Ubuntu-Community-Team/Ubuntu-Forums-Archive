---
title: "Blank desktop in Kubuntu"
date: 2010-02-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by todak on 2010-02-16
As per my attached screen-shot, I have an utterly blank desktop after logging in, except for the cashew in the upper right corner. This occurred after the latest updates. Everything else works, however. Launching apps is no problem using Alt+F2. When I use the plasma menu to add a widget, I can scroll across and see that the taskbar, weather report and other items are checked off as already being on the desktop, but yet they are invisible. It does not matter whether I have desktop effects enabled or not. I have to leave the effects enabled because when I minimize a window, I cannot get it back due to the taskbar being invisible, until I put my pointer in the upper left corner of the screen so it will show me all of my minimized and open windows. Then I can click on the appropriate indicator to maximize the window so that it can be used. Is this a new minimalist approach to the KDE, (I think not :D ) or did something go awry during the updates? By the way, when I log out, the login screen does not appear, just a black screen with no text or cursor. All of the key combination tricks will not get me to either a login window or a terminal. I have to issue the three-fingered salute and reboot. Any clues as to what happened?

---

### Post by infoseeker on 2010-02-17
I had a problem 2-3 days back where a 'sudo apt-get dist-upgrade' decided to uninstall kde for me.  To sort out the problem I had to reboot into recovery mode, login as your user, and issue 'sudo apt-get install kubuntu-desktop' to get it back again.

---

### Post by todak on 2010-02-17
I only do standard upgrades. I tried installing kubuntu-desktop, but was informed by apt that it was the newest version. Perhaps I will try reinstalling it with aptitude-reinstall kubuntu-desktop and see what happens. The odd thing is that my desktop exists. I can copy all kinds of things to MY desktop and see them using dolphin file manager, but the desktop that I am seeing on my screen is blank. :confused: When I bring up dolphin using Alt+F2, it shows my home folder. Maybe my desktop is a hidden folder. :???: Perhaps future updates may resolve the quandary. I am going to continue with the system installation as-is to see what happens. It is installed on a secondary disk. My main everyday system is installed on its own drive.

---

