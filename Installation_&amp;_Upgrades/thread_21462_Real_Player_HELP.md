---
title: "Real Player HELP"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by 93viking on 2005-03-22
I installed Real Player on my Desktop PC at home with no issues. This morning I installed Ubuntu on my Laptop at work and everything works great including my wireless card  :) except for Real Player. I followed the instructions below...

 Go to [http://www.real.com/linux/](http://www.real.com/linux/)
Click the "Download RealPlayer" button.
Open up a terminal window, cd to where you downloaded it to, and type in the following.
chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
When it prompts for Directory, type /usr/local/RealPlayer.
When it asks if it should "configure system-wide symbolic links", say y,
and then <enter> when it asks for prefix (i.e. leave it as /usr).

I see it in my Applications menu but when I click on Real Player nothing happens. I've rebooted just in case but still no help. Any ideas?

Thank you

---

### Post by Buffalo Soldier on 2005-03-22
Managed to try and get realplayer running once while I was using Warty. Haven't tried on Hoary. I'll try to test it as soon as possible and get back to you soon.

---

### Post by bored2k on 2005-03-22
[QUOTE=93viking]I installed Real Player on my Desktop PC at home with no issues. This morning I installed Ubuntu on my Laptop at work and everything works great including my wireless card  :) except for Real Player. I followed the instructions below...

 Go to [http://www.real.com/linux/](http://www.real.com/linux/)
Click the "Download RealPlayer" button.
Open up a terminal window, cd to where you downloaded it to, and type in the following.
chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
When it prompts for Directory, type /usr/local/RealPlayer.
When it asks if it should "configure system-wide symbolic links", say y,
and then <enter> when it asks for prefix (i.e. leave it as /usr).

I see it in my Applications menu but when I click on Real Player nothing happens. I've rebooted just in case but still no help. Any ideas?

Thank you[/QUOTE]
 I suggest you install Helix instead of Real . I have experienced issues with Real but not with Helix [theyre the same though] . Helix is @ the same download link as RP .

---

### Post by 93viking on 2005-03-22
I tried Helix, but I was not able to play a file with the .ram extention. This is an online radio station that I was trying to get. Any ideas on how to get this to work?

I have no clue what I did to get it to work on my Home PC?  This is just crazy.  8-[

---

### Post by bored2k on 2005-03-22
[QUOTE=93viking]I tried Helix, but I was not able to play a file with the .ram extention. This is an online radio station that I was trying to get. Any ideas on how to get this to work?

I have no clue what I did to get it to work on my Home PC?  This is just crazy.  8-[[/QUOTE]
 Weird. After I install mozplugger/totem and helix/realplayer Im able to stream anything .

[ I got helix/rp working with rfi.fr rm stream btw ]

---

### Post by 93viking on 2005-03-22
>  Weird. After I install mozplugger/totem and helix/realplayer Im able to stream anything .

[ I got helix/rp working with rfi.fr rm stream btw ]

I'm really new to Linux. Can you tell me what you mean by "mozplugger/totem" and what you said in the [ ]?

---

### Post by 93viking on 2005-03-22
One other question.  What all should be checked off in my repository under Synaptic right now I have the two Universal's and the top one for the CD.

---

### Post by madzzoni on 2005-03-22
[QUOTE=93viking]One other question.  What all should be checked off in my repository under Synaptic right now I have the two Universal's and the top one for the CD.[/QUOTE]

I got the same problem with RealPlayer as you! It makes crazy, soon!

i got all Ubuntu-archieves active (main, universe, multiverse)

---

### Post by bored2k on 2005-03-22
[QUOTE=93viking]I'm really new to Linux. Can you tell me what you mean by "mozplugger/totem" and what you said in the [ ]?[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger](http://ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger)

I said that after installing Helix I could listen to the streams in [www.rfi.fr](www.rfi.fr) .

---

### Post by macewan on 2005-03-22
odd.

I just downloaded and installed

[[IMG]http://i.realone.com/assets/rn/cms/2004/other/Download_RealPlayer_Button.6770676.gif[/IMG]](http://www.real.com/realcom/R?href=http%3A%2F%2Fforms.real.com%2Freal%2Fplayer%2Fdownload.html%3Ff%3Dunix%2FRealPlayer10GOLD.bin%26product%3Dplayerplus%26system%3Dlinux%26pcode%3Drn%26src%3Dlinux%26opage%3Dlinux&pageid=linuxPage&pageregion=offer_button) 

chmod a+x Real*.bin

sudo ./Real*.bin


/usr/local/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: **F**
Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: **Y**

- Just finished uninstalling and then reinstalling everything real related.

I typed a capital **F** & hit [enter] instead of just relying on it to default

```
Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F
```

and I typed a capital **Y** & hit [enter] instead of just relying on it to default

```
Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: Y
```

It worked from the menu under:

Applications > Sound & Video > RealPlayer 10


This started up the [RealPlayer Wizard](http://www.macewan.org/screenshots/RealPlayerWizard.jpg).

The browser plugin [immediately worked](http://www.macewan.org/screenshots/RealPlayerPlugin.jpg).

Not sure what to tell you.  :-k

---

### Post by 93viking on 2005-03-22
Thanks for all your help!  I just re-installed Ubuntu and got all the updates. I then tried to install like you said in your last post but still will not open. I see it in my Applications menu but it just wont launch.

I guess I will give the mozplugger and Helix a try.

Is there a way to un-install Real Player 10 from the OS?

---

### Post by bored2k on 2005-03-22
[QUOTE=93viking]Thanks for all your help!  I just re-installed Ubuntu and got all the updates. I then tried to install like you said in your last post but still will not open. I see it in my Applications menu but it just wont launch.

I guess I will give the mozplugger and Helix a try.

Is there a way to un-install Real Player 10 from the OS?[/QUOTE]
 read the README .

---

### Post by macewan on 2005-03-22
[QUOTE=93viking]Thanks for all your help!  I just re-installed Ubuntu and got all the updates. I then tried to install like you said in your last post but still will not open. I see it in my Applications menu but it just wont launch.

I guess I will give the mozplugger and Helix a try.

Is there a way to un-install Real Player 10 from the OS?[/QUOTE]



Does it run if you type from commandline:

realplay

---

### Post by 93viking on 2005-03-22
Nope...

I thought of that also.  The really crazy part of it is I installed it on my Desktop PC P4 3.2G Prescott no problem with the same Ubuntu Hoary 5.04 install.

I install the same OS on my Centrino 1.5G laptop and Real Player installs but won't launch.

I tried the Warty 4.10 on my laptop but I was not able to get the wireless to work. I have the Wireless LAN 2100. Linspire 5.0 is the only Linux distro that works out of the box for my laptop.

---

### Post by madzzoni on 2005-03-23
[QUOTE=macewan]
It worked from the menu under:

Applications > Sound & Video > RealPlayer 10


This started up the [RealPlayer Wizard](http://www.macewan.org/screenshots/RealPlayerWizard.jpg).

The browser plugin [immediately worked](http://www.macewan.org/screenshots/RealPlayerPlugin.jpg).

Not sure what to tell you.  :-k[/QUOTE]

This dosn't work on my LapTop either!!!! I cant figure out, what is wrong. But thanks anyway. The strange thing is i got no problem with RealPlayer on my Desktop (Warty)...hmmm

---

### Post by hysun on 2005-04-17
I am having exactly the same problem on my desktop pc.

I was previously using debian sarge, installed realplayer 10, worked perfectly. i was also using beep-media-player on debian, very happy with it. again it won't play my music on ubuntu. sad...

and ...  ](*,) , yes, realplayer 10 works well on another desktop pc i have with ubuntu installed. the two PCs have quite different hardware configuration.

---

### Post by Eliyahu on 2005-04-18
This was very helpful. Thanks!

Eliyahu

Shilo, Israel

---

### Post by kiwibird on 2005-06-18
I've got the same problem with Ubuntu Hoary, it just won't do anything when I try to start it. 

```
kiwibird@kiwishiba:~$ realplay

[1]+  Stopped                 realplay
kiwibird@kiwishiba:~$ ps -A|grep real
 4089 pts/5    00:00:00 realplay
 4094 pts/5    00:00:00 realplay.bin
 4096 pts/5    00:00:00 realplay.bin
 4097 pts/5    00:00:00 realplay.bin
kiwibird@kiwishiba:~$ realplay

[2]+  Stopped                 realplay
kiwibird@kiwishiba:~$ ps -A|grep real
 4089 pts/5    00:00:00 realplay
 4094 pts/5    00:00:00 realplay.bin
 4096 pts/5    00:00:00 realplay.bin
 4097 pts/5    00:00:00 realplay.bin
 4119 pts/5    00:00:00 realplay
 4124 pts/5    00:00:00 realplay.bin
 4126 pts/5    00:00:00 realplay.bin
 4127 pts/5    00:00:00 realplay.bin
kiwibird@kiwishiba:~$ echo and so on...

``` 

Nothing happens... I've got Ubuntu Hoary 5.04, installed the Helix player first (from synaptic, helix 1.0.1-1, will try 1.0.4 now. I haven't tried the mozplugger & totem-xine thingy, is that supposed to work on RealPlayer .smil-files? And is it possible to have both totem-xine and totem-gstreamer? Because I seem to remember it messing up things before, at least...

---

### Post by kiwibird on 2005-06-18
[http://www.ubuntuforums.org/showthread.php?t=24331&page=2&pp=10&highlight=realplayer](http://www.ubuntuforums.org/showthread.php?t=24331&page=2&pp=10&highlight=realplayer)  seems to have some help, I'm adding new *default_options=-nobeeps -as 3* to /etc/esound/esd.conf to make it look like this:
```
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
# added by KBU (don't beep on startup,
#   release device after 3 secs)
default_options=-nobeeps -as 3

```

**UPDATE**: This works!!!  \\:D/ It even lets me keep playing music in RhythmBox. I had problems before with different programs using different sound drivers, but it's all working now (I guess all it needed was that "release device after 3 secs" thing). So, for any newbies (newer than me, that is) who have trouble with RealPlayer 10 not starting up, and didn't quite understand what I did, here's what to do:

open a terminal window (Applications -> System tools -> Terminal) and enter this command: 

*sudo gedit /etc/esound/esd.conf*

enter your password when prompted, and go down to the bottom of the file where it says *default_options=* and make it say

*default_options=-nobeeps -as 3* 

(alternatively, remove everything and paste in the contents of the file in the CODE-block up there). 

Sorry if this post is totally redundant, but the thread was pretty high on google...

---

### Post by celticmonkey on 2005-08-06
I did this and the RealPlayer worked.

System > Preferences > Sound > General > uncheck enable sound server

---

### Post by kenl on 2005-08-11
nicely done, thanks for that.. but it seems a bit sticky every 3 sec...

---

