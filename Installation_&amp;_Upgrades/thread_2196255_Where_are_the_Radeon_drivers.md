---
title: "Where are the Radeon drivers?"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by l6griffin on 2013-12-28
I upgraded from 12.?? to 13.10 and the AMD drivers no longer work. I can still get to a text terminal. I did my research and found info to purge and install drivers. I purged the AMD drivers. Then I gave the command to install the open source drivers;
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

I get the message, libgl1-mesa-glx, and libgl1-mesa-dri, not found.

Larry

---

### Post by Bashing-om on 2013-12-28
l6griffin; Hi !

The command is valid, did you run update prior ?

```

sudo apt-get update
sudo apt-get upgrade

``` to get the databases in sync .

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by l6griffin on 2013-12-28
The command is from [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=fullsearch&context=180&value=radeon+display+drivers&titlesearch=Titles](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=fullsearch&context=180&value=radeon+display+drivers&titlesearch=Titles)

I ran the commands you provided and that allowed completion. Unfortunately I'm back to where I started. I get the login screen, enter my password, and get blank screen. I'll have to go back to the link and see if I can find the problem.

Thanks, Larry

---

### Post by Bashing-om on 2013-12-28
l6griffin; Humm,

Can you boot to the GUI using ther "nomodeset" boot parameter option ? ..
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
Maybe get a hint on what we are dealing with and a direction to go.

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by l6griffin on 2013-12-28
It's an HP 2000z-300 laptop with a AMD Radeon 6310 "Wrestler". I've been banging on the keyboard most of the day, I've had enough. I'll run your code in the morn. I'm not familiar with "nomodeset", I'll look for that in the morn too.

Larry

Ignorance can be fixed, stupid is forever.

---

### Post by Bashing-om on 2013-12-28
l6griffin; Roger;

We can help with the former !

[INDENT][INDENT]later
[/INDENT][/INDENT]

---

### Post by l6griffin on 2014-01-01
Spoke too soon. :rolleyes: Found the icon to select desktop, Gnome seems to work, Unity is blank. Think I'm missing the dock(?). Back to reading the manual.

Larry

---

### Post by Bashing-om on 2014-01-01
l6griffin; Hey, Reading is good !

What do you get when you right click on the unity desk top ? System Settings ? Maybe from there see what happens.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by l6griffin on 2014-01-02
When I right click, I get a window one of the options is create new folder. That's what lead me to think it was working(?). I was able to create a new folder on the desktop. I logged in using the Gnome desktop which is what I had under 12.10. The dash with the icons are on the left.  I'm looking at the log files, and I'm not finding the /var/log/Daemon.log or Debug.log. They have either changed name, or in a different location. I was hoping to find some reference to the error msg.s I've seen. I upgraded from 12.10 to 13.04, then 13.10. Since I upgraded, I now tempted to download the image and start over.  I had some USB problems, my track ball  went away.

Larry

---

### Post by Bashing-om on 2014-01-02
l6griffin; Hey ,

I understand that you have 2 desktop environments available; gnome works in one, but "unity" is blank when choosing to use "unity ".
If so, we need to focus our attention on (re-)configuring "unity". In the Unity environment all is functional except the desktop, right ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by l6griffin on 2014-01-02
Correct 2 desktops. I would like to get Unity working. As mentioned USB is acting strange, and there is a problem with screen brightness. Every time I login, I Brightness & Lock and move the brightness from min to max. The brightness issue is why I put Ubuntu on the back burner for a year.

I want to get a reliable Ubuntu desktop and connect a Phablet with Touch to it. A Phablet hqas too much to offer to pass up, GPS, camera, TV remote,,,, I don't have the Phablet yet but considering a Nexus 7.

Larry

---

### Post by Bashing-om on 2014-01-02
l6griffin; Hey,

All I expect have solutions, protocol on this forum is one problem to each thread. Let's focus on unity.
To reset unity in version 13.10 :
[http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/)

Do those commands, advise if any errors, and we take off from there.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by l6griffin on 2014-01-02
Ran the commands, the first no problem, the second setsid unity, multiple errors. It now appears hung, I'm waiting in the hopes it will clear. The errors, Decoration not found, glib-critical **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed. 

I've got an open terminal window anyway to close it?

Larry

---

### Post by Bashing-om on 2014-01-02
l6griffin; uhmmm,

Configuration issue (??) .
Try:
```

sudo dkpg-reconfigure unity

```

[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by l6griffin on 2014-01-02
Despite all the errors it appears to work. I was able to get the terminal window closed. It appeared hung, but when I activated the up/down slider on the window the cursor started blinking on the command line. I didn't run DPKG. I'm going to do a search for the brightness problem.

Larry

---

### Post by Bashing-om on 2014-01-02
l6griffin; Good deal !

If now your desktop(s) is (are) functioning properly, please mark this thread as solved. [1st post -> thread tools] 
In order to address the other problems, One may open as many threads as desired -> one problem to the thread. Forum protocol for reasons.

[INDENT][INDENT]ubuntu, where there is a will there is a way[/INDENT][/INDENT]

---

