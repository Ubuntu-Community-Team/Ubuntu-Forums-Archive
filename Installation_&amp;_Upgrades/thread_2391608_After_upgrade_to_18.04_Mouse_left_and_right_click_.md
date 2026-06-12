---
title: "After upgrade to 18.04 Mouse left and right click do not work"
date: 2018-05-11
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2018-05-11
I have upgraded to 10.04 LTS and now the mouse moves about the screen, but when I try and right or left click on anything, nothing happens.  Keyboard seems OK, and have managed to find a way to reboot, but that's just about all.  I have failed as yet to even find a way to open a terminal.

Can anyone help, PLEASE :-(  I have to file my time sheets to get paid.

---

### Post by csghone on 2018-05-25
Facing this problem - couldn't find a fix.
Workaround: 
1. Goto virtual console using Alt-Ctrl+F1
2. Go to Alt-Ctrl+F8 (Skipping this step crashes my X sessions)
3. Go to Alt-Ctrl+F7 to go back to your X session.
Mouse click should start working,

---

### Post by Jonners59 on 2018-06-08
> **csghone said:**
> Facing this problem - couldn't find a fix.
Workaround: 
1. Goto virtual console using Alt-Ctrl+F1
2. Go to Alt-Ctrl+F8 (Skipping this step crashes my X sessions)
3. Go to Alt-Ctrl+F7 to go back to your X session.
Mouse click should start working,

Thanks for this.  Apologies for me not replying, I had no notification and only came in to give an update that I had a temporary work-around.  Not too dissimilar to yours

[HTML]Alt+Ctrl+F6
Sign in
Alt+Ctrl+F7[/HTML]
and it seems to work......

---

### Post by Jonners59 on 2018-12-11
Having had no further support or advise on this I decided to rebuild the machine.  Before doing so I had noticed multiple kernels, many were old.  I tried removing them, even searching for purging and force removal of, and none would work, so my conclusion is that this error, and others that come with it are caused by broken old kernel installs that have not properly uninstalled.  I think it is a bug.

---

### Post by ajana on 2019-07-17
[SIZE=+1][FONT=Helvetica]Accidentally posted similar problem in a SOLVED thread, have reposted problem in new thread:
[https://ubuntuforums.org/showthread.php?t=2423122&p=13873750#post13873750](https://ubuntuforums.org/showthread.php?t=2423122&p=13873750#post13873750)     
[/FONT][/SIZE]

---

