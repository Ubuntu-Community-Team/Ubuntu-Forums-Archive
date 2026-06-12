---
title: "autostart teamviewer and reduce to tray icon with alltray"
date: 2014-03-28
forum: Installation &amp; Upgrades
---

### Post by Xubuntist on 2014-03-28
Hello,

Xubuntu 13.10

I can install Teamviewer and it works beautifully
I can install Alltray and it works beautifully, and I can manually reduce Teamviewer to the tray as required
I can set Teamviewer to run at boot-up in StartUp Programs and that works beautifully. However, it leaves the Teamviewer window open on the screen.

But what I cannot fathom for the life of me (and I am dizzy from reading dozens of posts and trying lots of "solutions") is how to get :

[LIST=1]
[*]Teamviewer to start with Xubuntu 
[*]Alltray to start With Xubuntu 
[*]get Teamviewer into the system tray automatically at boot-up 
[/LIST]

[This post in particular interested me]("http://ubuntuforums.org/showthread.php?t=1669060&p=10367545#post10367545"). But I cannot figure out how to automate it. The poster says he did:
```
bash -c "sleep 20; alltray teamviewer"
```
but even when I enter that into a terminal window (with or without "sleep") it only opens Teamviewer, it doesn't minimise it to the tray.

I have put the following command in the Alltray StartUp program 
```
alltray /opt/teamviewer/teamviewer/7/bin/teamviewer
```
Once again, all this does is open Teamviewer maximised on boot-up, it does not minimise it to the tray.

I also tried to make it work with 
```
/usr/bin/alltray /opt/teamviewer/teamviewer/7/bin/teamviewer &&
```
Once again, all this does is open Teamviewer maximised on boot-up, it does not minimise it to the tray.

I'm still going through all sorts of options I have found online, but I wonder if somebody could give me a hand with this?

Many thanks with your continued patience and generosity.

François

---

### Post by Xubuntist on 2014-03-28
I just tried this,
```
alltray -s -l /opt/teamviewer/teamviewer/7/bin/teamviewer %u
```
Once again, all this does is open Teamviewer maximised on boot-up, it does not minimise it to the tray.

---

### Post by Xubuntist on 2014-03-28
OK, I've finally fixed it, not by fighting with Alltray, but by dispensing with it and switching to KDocker instead. Here's the command and, by jiminy, it works :p

First install KDocker
```
sudo apt-get install kdocker
```

In Xubuntu : **Settings manager > System > Session & Startup** > **Application Autostart > Add**

Name :  Teamviewer
Command :
```
kdocker -n Teamviewer -i /opt/teamviewer/teamviewer/7/desktop/teamviewer.png -d 40 /usr/bin/teamviewer &
```
OK & Close

PS. This works with Teamviewer 7 and Xubuntu 13.10. 
PPS. I just tested this on my Xubutu 12.04 laptop which has Teamviewer 5 installed and this did **not** work. I'll therefore be uninstalling version 5 and install version 7. I may have to upgrade the laptop to 13.10 for this to work on that laptop, I don't know yet.

I hope this helps somebody else as completely frustrated as I was!

---

### Post by Xubuntist on 2014-03-28
[IMG]http://beretgascon.fr/data/images/capture.png[/IMG]

---

