---
title: "Gnome-wm doesn't start at boot time automatically after upgrading to Lucid lynx"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by vjani on 2010-05-14
Hi all,


 
 I have recently started using Ubuntu and this is my first question to the forum. First of all, thanks for such a wonderful OS :), I am really enjoying it. I just did a distribution upgrade on my laptop from 9.1 to 10.04, and it went fine for the most part except this issue. After it boots up, I don't see any window titles/scrollbars/borders and on clicking the icon for "Show desktop" on the bottom left, I see the following error message:
 
 "Your window manager does not support the show desktop button, or you are not running a window manager."


After googling a bit, I realized that gnome-wm is not starting automatically and so I have to manually start each time to see the windows working properly. Can somebody tell me if there is a way to make sure that gnome-wm starts automatically? I know I can put it in my .bashrc but I want to do it the correct way if possible. If not, I will have to go with that workaround.


Thanks,
Vivek

---

### Post by FaizanKazi on 2010-05-15
Hi!
check out this post! [http://superuser.com/questions/89942/ubuntu-9-10-gnome-session-not-starting-automatically]("http://superuser.com/questions/89942/ubuntu-9-10-gnome-session-not-starting-automatically")

Method 1:

Go into your Gnome session and in the terminal, open ~/.xinitrc (or create it if it isn't there already) using your editor of choice:

$gedit ~/.xinitrcadd this to it:

#!/usr/bin/env bash
exec gnome-sessionmake the file executable:

$chmod +x ~/.xinitrcLet's link it to ~/.xsession so it's read by GDM on startup:

ln -s ~/.xinitrc ~/.xsession 

Reboot.


Method 2:

Just Type: 'sudo apt-get install gnome-session ubuntu-desktop' into the terminal and reboot

---

### Post by vjani on 2010-05-15
Hi FaizanKazi,

Thanks for you reply. I tried both methods but still the issue comes :(.

Actually gnome-session does run at boot time, but it is the gnome-wm (i.e. window manager), that doesn't run, due to which i don't get window title bars/buttons and can't switch between windows or switch to desktop. The above methods seem to be the solution for gnome-session not starting at boot time.

Let me know if you have other solutions.

Thanks,
Vivek

---

### Post by FaizanKazi on 2010-05-16
try:

compiz --replace &

metacity --replace

gtk-window-decorator --replace

---

### Post by vjani on 2010-05-18
I ended up doing fresh install of lucid lynx. Even after that, the issue persisted, so I tried removing .gconf, .gconfd, .gnome2,.gnome2, .compiz from my profile. That didn't work either :(. Later I realized there was 1 more folder .config which contains gnome related settings in gnome-session/compiz/gtk-2.0 etc. Removing the files there did the trick finally :)

Thanks for your help anyway.

---

