---
title: "Autostart TeamViewer and reduce to tray icon with Kdocker"
date: 2017-08-30
forum: Installation &amp; Upgrades
---

### Post by Xubuntist on 2017-08-30
If you see [this thread]("https://ubuntuforums.org/showthread.php?t=2213726") I created back in 2014, I solved the "TeamViewer autostart docked" problem using Kdocker. However, recently this stopped working as it should. TeamViewer would start but would stay onscreen instead of being docked. I can't say since when but every *ubuntu install I have done for a while, TeamViewer has continued to autostart but has NOT been docked like it was before, and some users find it disconcerting to have this app always show in the centre of their screen on startup. I finally found the solution which was, as often is the case, dead simple.

I'll recap from the beginning so new users won't have to switch between posts:


[LIST=1]
[*]Install TeamViewer (I have a deb file for TeamViewer8 on my USB key) 
[*]In your file manager, go to **/usr/share/applications** and **Rt-click > Copy** on Teamviewer 
[*]In your file manager, go to **~/.config/autostart** (create the folder if it doesn't exist) and inside this, **Rt-click > Paste**, putting the TeamViewer icon in the **autostart** folder 
[*]Now open:
(Xubuntu) Settings manager > System > Session & Startup > Application Autostart
(Lubuntu) Preferences > Default Apps > Autostart
and, if it isn't already, tick the TeamViewer entry 
[*]Install Kdocker
```
sudo apt-get install kdocker
``` 
[*]Now open
(Xubuntu) Settings manager > System > Session & Startup > Application Autostart
(Lubuntu) Preferences > Default Apps > Autostart 
[*]Add the following **custom **StartUp command:
```
kdocker -n TeamViewer -i /opt/teamviewer8/tv_bin/desktop/teamviewer.png -d 40 /usr/bin/teamviewer &
``` 
[*]Close and restart the PC to verify it's working: 
[/LIST]

[IMG]http://farm5.staticflickr.com/4434/36108172953_416fc79589_b.jpg[/IMG]


That's all there is to it. The "error" was that in my previous installs I always had 
```
kdocker -n Teamviewer -i /opt/teamview...
```
and not 
```
kdocker -n TeamViewer -i /opt/teamview...
```
I spotted, using **wmctrl -l**, that the window is called **TeamViewer** and not **Teamviewer** as previously. Maybe it changed because of an updated TeamViewer install file I use (TeamViewer 8), who knows, but anyway, the **V** of TeamViewer changed to uppercase and whereas this is usually immaterial in Windows, in Linux case is king.

[SIZE=1]_Kdocker key_
-n = Name of window[/SIZE][SIZE=1] (this was where I saw the error once I ran wmctrl)
[/SIZE][SIZE=1] -i = the icon file to use
-d = an nn second limit after which Kdocker will give up of it can't find a matching window[/SIZE]

---

