---
title: "Themes don't work for second user"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nicedanmonkey on 2009-04-02
I'm using 9.04 beta and so far it's been great. The main user on the computer works great. I tried making a second user for my wife but the themes don't work. When I try to open the Appearance program it says that "gnome-settings-daemon" won't start. Here's what it says what it says when I try to run it from the terminal.

> ** (gnome-settings-daemon:10193): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:10193): WARNING **: Could not acquire name


Also, every time I try to log out it says the power manager is not responding. 

Again, everything works good with the user I set up upon installation, it's just the user I set up for my wife that is causing the problems. I've tried deleting the user and the corresponding home directory and re-establishing the user but that didn't fix the problem.

This was a clean install of 9.04. I'm also using ext4.

---

### Post by psyke83 on 2009-04-02
> **nicedanmonkey said:**
> I'm using 9.04 beta and so far it's been great. The main user on the computer works great. I tried making a second user for my wife but the themes don't work. When I try to open the Appearance program it says that "gnome-settings-daemon" won't start. Here's what it says what it says when I try to run it from the terminal.



Also, every time I try to log out it says the power manager is not responding. 

Again, everything works good with the user I set up upon installation, it's just the user I set up for my wife that is causing the problems. I've tried deleting the user and the corresponding home directory and re-establishing the user but that didn't fix the problem.

This was a clean install of 9.04. I'm also using ext4.

Try to create a new user via System -> Administration -> Users and Groups, but ensure that you set the user type to "Administrator". Log in using those new credentials and see if you receive the same errors messages.

Perhaps it's also related to [this]("http://ubuntuforums.org/showthread.php?t=1113542") thread?

---

### Post by nicedanmonkey on 2009-04-03
I've tried setting up a new user as both desktop and administrator, either way I have the same problem. I haven't looked at the permissions for the multimedia folders yet. Do you think that would cause gnome-settings-daemon to not load correctly?

---

### Post by chrisccoulson on 2009-04-03
Those errors when you try to run from the terminal are probably because gnome-settings-daemon is already running. Hve you checked that, just in case they are a red herring?

---

### Post by nicedanmonkey on 2009-04-03
> **chrisccoulson said:**
> Those errors when you try to run from the terminal are probably because gnome-settings-daemon is already running. Hve you checked that, just in case they are a red herring?

It looks like gnome-settings-daemon is trying to run but it doesn't look right. There are three entries for gnome-settings-daemon. I'll attach a screenshot.

[IMG]http://ubuntuforums.org/picture.php?albumid=1013&pictureid=3617[/IMG]

---

### Post by nicedanmonkey on 2009-04-08
Has anyone else been having any issues with other users? I've been applying updates as they come but so far nothing has fixed it.

---

### Post by xerosis on 2009-04-08
I logged in with vnc (which spawns a new desktop session for each vnc session) and I had a messed up theme like you are, I put it down to vnc but I suspect I'm seeing the same as you.

---

### Post by Polygon on 2009-04-08
report it on launchpad.

---

### Post by nicedanmonkey on 2009-04-08
> **Polygon said:**
> report it on launchpad.

Submitted bug

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/358117](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/358117)

---

### Post by nicedanmonkey on 2009-04-22
Reinstalling Jaunty seemes to have fixed the problem.

---

