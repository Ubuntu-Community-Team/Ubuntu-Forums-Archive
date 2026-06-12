---
title: "Dell Inspiration 15 5000series fstab Dropbox, Screen resolution and audio odities"
date: 2017-10-22
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2017-10-22
Mt wife decided to break her laptop and bought a new one.  This Dell Inspiration 15.  I installed xUbuntu for her, but there seem to be some quirky problems I can't get a tidy fix for.  She is even considering going back to Windows in frustration.

The first problem is fstab does not load the remote drives on boot.  I/she has to run "Mount -a" to load them. The same lines in her fstab I have entered in other PCs and it works on boot, but they are Ethernet connected and not Wi-Fi.  Remote drives I refer to as Directories on another PC running on our LAN  The code works once this is done, but it has to be manually completed after boot.  
I created a scrip to do this but that does not work, plus she has to add her password which again is not ideal.  

Solutions, please. Dropbox:  Seen this error in various blogs, but I have tried to install a fix in the form of a script to run at boot, but again it does not work.  I have also craeted one on her desktop, but again it does not always work.  The only way to guarantee it works is to type the cmd in a terminal.  The issue is the one where Dropbox does not launch properly.  The icon does not appear in the panel and so sync and changes do not work.  

The command to make it work is "dropbox stop && dbus-launch dropbox start".  Any help so she does not have to do this herself and it guarantees working during boot.
Resolution:  She teaches and uses a projector a lot.  On her previous machine and in the Windows, when she connects the projector it just appears at the correct resolution but in this she has to change the resolution and it is different on both machines.  Difficult to explain, but it makes working with the xUbuntu clumsy for her and I would either like it to recognise the projector correctly or have a simple script (Launcher) that switches between the two profiles....Audio:  She uses a JAM Bluetooth speaker and she says it does not work very well.  The sound is poor.  She says it works fine in Windows.  
I have yet to get to the bottom of this and shall report back on what the issues are when I get clarity, but for now can anyone help with the three above.Please feel free to ask questions and any specific configs that I have installed.  Not added here as the advance option is not showing and it would make the page messy.

---

### Post by flocculant on 2017-10-22
> The first problem is fstab does not load the remote drives on boot. I/she has to run "Mount -a" to load them. The same lines in her fstab I have entered in other PCs and it works on boot, but they are Ethernet connected and not Wi-Fi. Remote drives I refer to as Directories on another PC running on our LAN The code works once this is done, but it has to be manually completed after boot.
I created a scrip to do this but that does not work, plus she has to add her password which again is not ideal. 

Pretty sure that wifi is not up when fstab mounts it's lines. What script did you create? What doesn't work? How are you starting it? 

> Dropbox: Seen this error in various blogs, but I have tried to install a fix in the form of a script to run at boot What script did you create? How's that starting?

---

### Post by Jonners59 on 2017-10-22
> **flocculant said:**
> The first problem is fstab does not load the remote drives on boot.  I/she has to run "Mount -a" to load them. The same lines in her fstab I  have entered in other PCs and it works on boot, but they are Ethernet  connected and not Wi-Fi. Remote drives I refer to as Directories on  another PC running on our LAN The code works once this is done, but it  has to be manually completed after boot.
I created a scrip to do this but that does not work, plus she has to add her password which again is not ideal.

Pretty sure that wifi is not up when fstab mounts it's lines. What script did you create? What doesn't work? How are you starting it? 

```
#!/bin/bash

mount -a
```

If  I type ```
mount -a
```   in to a terminal it works and  in a script launched in Session and  Startup, then it never works, but that may be because it needs a delay, plus it needs sudo, I think to make it work.


> **flocculant said:**
> Dropbox: Seen this error in various blogs, but I have tried to install a fix in the form of a script to run at boot:
 How's that starting?

```
#!/bin/bash

dropbox stop && dbus-launch dropbox start
```

If I type ```
dropbox stop && dbus-launch dropbox start
```  in to a terminal it works and  in a script launched in Session and Startup, then it sometimes works.  I know this was a known problem, which is where I found the cmd.

Does this help?

Another, I forgot, is also a known problem and have found fixes for, but does not work for me, is the screen times out every 15 seconds.  I created this script to also load at start, like the others....
```
#!/bin/bash
export DISPLAY=:0.0

if [ $# -eq 0 ]; then
  echo usage: $(basename $0) "on|off|status"
  exit 1
fi

if [ $1 = "off" ]; then
  echo -en "Turning monitor off..."
  xset dpms force off
  echo -en "done.\nCheck:"
  xset -q|grep "Monitor is"
elif [ $1 = "on" ]; then
  echo -en "Turning monitor on..."
  xset dpms force on
  echo -en "done.\nCheck:"
  xset -q|grep "Monitor is"
elif [ $1 = "status" ]; then
  xset -q|sed -ne 's/^[ ]*Monitor is //p'
else
  echo usage: $(basename $0) "on|off|status"
fi
```

---

### Post by flocculant on 2017-10-22
re dropbox - might need to do more there than just that script. 

2nd answer [here]("https://askubuntu.com/questions/732816/xubuntu-dropbox-icon-fail") points to :

    Run the proposed command once to make the Dropbox icon appear in your notification area: dropbox stop && dbus-launch dropbox start
    Open Dropbox preferences (click on the Dropbox icon in the notification area).
    Disable "Start Dropbox on system startup" and apply your changes.
    Go to XFCE settings > Session and Startup > Application Autostart.
    Search for an existing Dropbox item and confirm it is disabled.
    Add a new item with this configuration (do not edit the existing Dropbox item because it is recreated in each reboot):
        Name: Dropbox
        Command: dbus-launch dropbox start -i
    Be sure that the new application is enabled in the list.

re mount and sudo - yea that needs sudo, not sure what to do there - had a quick look elsewhere, but not getting far atm

re monitors - not a clue - never needed to fiddle about with that stuff.

(Note: might possible have been better to create 3 seperate threads for your issues)

---

### Post by Jonners59 on 2017-10-22
> **flocculant said:**
> re dropbox - might need to do more there than just that script. 

2nd answer [here]("https://askubuntu.com/questions/732816/xubuntu-dropbox-icon-fail") points to :

    Run the proposed command once to make the Dropbox icon appear in your notification area: dropbox stop && dbus-launch dropbox start
    Open Dropbox preferences (click on the Dropbox icon in the notification area).
    Disable "Start Dropbox on system startup" and apply your changes.
    Go to XFCE settings > Session and Startup > Application Autostart.
    Search for an existing Dropbox item and confirm it is disabled.

DOne up to here already - it always re adds the Dropbox launch at start itself.


> **flocculant said:**
> 
    Add a new item with this configuration (do not edit the existing Dropbox item because it is recreated in each reboot):
        Name: Dropbox
        Command: dbus-launch dropbox start -i
    Be sure that the new application is enabled in the list.


I'll give that a go.....  Cheers.


> **flocculant said:**
> 
re mount and sudo - yea that needs sudo, not sure what to do there - had a quick look elsewhere, but not getting far atm

re monitors - not a clue - never needed to fiddle about with that stuff.

(Note: might possible have been better to create 3 seperate threads for your issues)

Thanks anyway.  See what others have to say

---

### Post by Jonners59 on 2017-10-22
Shoot won't boot up fully.  Gets to logo and timer, then screen goes black with a line of text SDA7 clean, blah, blah, blah and then no more just stays there.  Can't see why this is happening.

---

