---
title: "How to change window manager to default?"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by rezaee on 2017-10-20
I wanted to create a kiosk Ubuntu, then I followed this instruction: [https://web.archive.org/web/20131210161955/http://phunehehe.is-great.org/2010/run-linux-with-a-bare-window-manager/](https://web.archive.org/web/20131210161955/http://phunehehe.is-great.org/2010/run-linux-with-a-bare-window-manager/)
[INDENT]Add a custom session by creating a file at /usr/share/xsessions/metacity-session.desktop. This file tells the  login manager about your session.   content:
[/INDENT]```
[Desktop Entry]
Encoding=UTF-8
Name=Metacity
Comment=Metacity without GNOME
Exec=/usr/local/bin/metacity-session
Type=Application

```[INDENT]Create the file to be executed by the session added in (1)  /usr/local/bin/metacity-session.content:
[/INDENT]```
#!/bin/bash
if test -z "$DBUS_SESSION_BUS_ADDRESS"; then
eval `dbus-launch --sh-syntax --exit-with-session`
fi
metacity --replace ccp & wmpid=$!
sleep 1
if [ -f ~/.metacity-session ]; then
source ~/.metacity-session &
else
xterm &
fi
# Wait for WM
wait $wmpid

```[INDENT]Create the user-specific config file ~/.metacity-session. This file will be  executed by the file added in (2). The content should be the program  you want to run, followed by an ampersand, for example
[/INDENT]```
 firefox &

```But when I did logout then wanted to login with metacity-session it didn't work(a black screen for a second and then back to login page again). Then I decided to restart my computer and then, I couldn't login even with my Ubuntu default desktop! Because when I try to login, after entering password and logging in, I have no menu and nothing! only default background pic shows and mouse pointer, nothing else!
Then I tried to install Putty on my other laptop with Win10, then connecting via SSH to Ubuntu laptop and remove all 3 files I did create before(3 files that the above instruction says). But nothing happened and I can not use my Ubuntu, because after logging in there is nothing! only background pic without any menu.

---

### Post by TheFu on 2017-10-22
Window managers usually don't provide a menu system. If you want one, then you need to configure it, manually.  That is a major reason that people use DEs - for the menu.

Different window managers have different initialization methods / startup methods.  I don't use metacity, so I cannot help there, but openbox uses a ~/.config/openbox/autostart file which is run after login by an end user.  Mine sets up my personal touchpad settings, starts xscreensaver with my preferred option, then starts my background changer script.  I could also have it start a browser in kiosk mode, assuming that is possible using a command line option.  I found firefox to be lacking in that ability.  In a kiosk setting, I'd strongly recommend using firejail with a private storage area too.

So, to solve the issue, I'd find how to force firefox into a kiosk mode from the command line and how metacity startup processing works. 
 R-kiosk extension looks interesting. I've never installed or attempted to use it, but it removes the menus after forcing fullscreen mode.  Hope these hints are useful.

---

