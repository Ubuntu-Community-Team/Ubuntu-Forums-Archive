---
title: "network manager doesn't recover from hibernate"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by brydong on 2007-11-06
This is driving me nuts...I have a new thinkpad x61 with a clean install of gutsy. The gnome-network-manager is useless when I turn it on from hibernate. Rebooting causes network manager to properly bring up the wireless connection as expected. This sucks and is frustrating as I have to reboot to get a network connection again.

Any help is appreciated...

brydon

---

### Post by kd7swh on 2007-11-07
all I can say is I feel your pain. NetworkManager is horribly broken in Gusty. The PPTP plug-in only works with eth0, there is a giant memory leak that kills slow computers, and it crashes after powersaving modes (sleep, hibernate, screensavers) start.

I just patched mine (new update in synaptic today) hopefully they fix it.

---

### Post by brydong on 2007-11-07
Aye, that's not good news but helpful. Any ideas on working around this? I tried wicd but it didn't seem to work at all for me. I'm able to get wifi-radar to find networks sometimes as a work around.

---

### Post by Whiffle on 2007-11-07
I added dbus and hal to the  line 

STOP_SERVICES=""

in

/etc/default/acpi-support

on my T43.  It seems to have helped a bit, except that it makes the machine suspend funny.  Whats weird is right when I installed everything was working great, only in the last week or so have things been acting funny.

---

### Post by brydong on 2007-11-07
Meaning that that line is now....

STOP_SERVICES="hal,dbus"

Can you expand on "acting funny"? I'm wondering if it's funny that's tolerable in return for a working network manager.

---

### Post by Whiffle on 2007-11-07
Sometimes kpowersave crashes (or kde-guidance-powermanager), and when I hit the suspend button it may not react, or it will take a while to suspend.  Most of the time it works.  

and actually tis 

STOP_SERVICES="dbus"

I just tried it without stopping hal and it seemed okay.  I think when I did that I just threw hal in for good measure.

---

### Post by stefangachter on 2007-11-08
I have the same problem, NetworkManager does not recover from hibernate, or even simpler, if I plug out the network cable and plug in it later, NetworkManager does not recover either. I have no solution so far... and I am surprised that something that worked nicely in 7.04 doesn't work properly anymore in 7.10.

---

### Post by zaklad on 2007-11-11
Hi, 

I also have a brand new X61... What a babe...

I have managed to find a truly ugly way to get it working:
Open a Terminal and do:
```
$ sudo /etc/init.d/networking restart 
$ pkill nm-applet
$ screen -S nm
$ nm-applet &
and press CTRL+a and then CTRL+d 
```


If you do another hibernation now and again the network manager doesn't work, You don't need to open a new 'screen' session. just open the Terminal and do:
```
$ sudo /etc/init.d/networking restart 
$ screen -r nm
$ fg

this will bring nm-applet to the front.
Press CRTL+c to stop (cancel) nm-applet and then

$ nm-applet &

and again CTRL+a and then CTRL+D just like before 
```

The problem is that this causes  multiple instances of nm-applet after the next reboot.
Killing the excess ones doesn't help. They re-appear the next time you start the computer...
So I went to System -> Preferences -> Sessions and under the 'Current Session' tab I removed all the excess apearences of nm-applet. There was one line 'nm-applet --sm-disable' and some other longer lines that started the same but with some random letters at the end of each line (something like  'nm-applet --sm-disable quekfj' if I remember correctly) I removed all the long line and kept only the 'nm-applet --sm-disable'.
This caused the excess appearances to be closed and they did not appear again after restart...

Hope this helps... If anyone can make something more elegant out of this please let me know...


Note: Updated version later on this thread...

---

### Post by zaklad on 2007-11-11
Actually, ever since I did all I mentioned above everything just works without any action needed. I don't know if it hasd anything to do with what I did...

Note that --sm-diable was mentioned in several other threads I found about this multiple instances issue...  I don't know what it does but it seems to be important... so if it appears on your current session tab without this flag remove it and ad a new entry as mentioned: 'nm-applets --sm-disable'.

Edit:
I was wrong. It did happen again and I do need to do this procedure every time...

---

### Post by brydong on 2007-11-12
Ok, so you recommend just repeating those 4 steps??

thanks,
brydon

---

### Post by zaklad on 2007-11-12
Five. 
Unless you want to keep the Terminal open, you should press CTRL+a and then CTRL+d before you close the Terminal or else your newly started nm-applet will be shut down.
If you don't care having the Terminal open you can skip the 'screen' command...

The rest is only if you have an issue with multiple instances of nm-applet.

note that I have added a section about 'screen' and more than one hibernation instances...

---

### Post by zaklad on 2007-11-14
Update:

This is trivial... Don't know why I haven't though of it earlier...

Instead of the whole 'screen' thing just press alt+F2 and run nm-applets from there...

So, to sum thing up:
on the Terminal:
```
$ sudo /etc/init.d/networking restart
```
then go to System > Preferences > Sessions
on the Current Session tab remove all the nm-applet instances you see (It's easier to find if you sort by name...) and close the window.
Now just press ALT+F2 and run nm-applet...

Another option someone suggested is just running Wifi-rader (available at your preferred package manager). I haven't tried it myself but the guy claims it woks flawlessly even when nm-applet doesn't...

---

