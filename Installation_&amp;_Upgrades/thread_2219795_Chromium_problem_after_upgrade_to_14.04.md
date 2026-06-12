---
title: "Chromium problem after upgrade to 14.04"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by mike176 on 2014-04-25
Hello
I've been using Chromium and when I upgraded to 14.04, Flash Player stopped working. I clicked on the install Flash Player button which appeared on the Chromium page. I was directed to the Adobe site. There are too many choices of versions so I tried them all. However, it doesn't install so I've had to revert to Firefox which I don't like. Is there a Command Line I can put into Terminal which activates Flash Player?
Thanks
Mike

---

### Post by slickymaster on 2014-04-25
Linux Adobe Flash will stop working on Chromium because Chromium will soon stop using the Netscape Plugin API. To get Flash working in Chromium it's the pepperflashplugin what you have to install. To achieve it, just run the following in a terminal window:```
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```

---

### Post by pfeiffep on 2014-04-25
Here's a pretty good [read and instructions]("http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html").

---

### Post by mike176 on 2014-04-25
great. thanks for the link mate.

---

### Post by cwlinux2 on 2014-06-17
I've tried all the install threads I can find regarding Chromium and Chrome and pepperflashplugin.  Every time I install the pepperflash plugin I get message "System program problem detected" when I try and fire up Chromium or Chrome.  Anybody else having this problem ?

---

### Post by bapoumba on 2014-06-18
> **cwlinux2 said:**
> I've tried all the install threads I can find regarding Chromium and Chrome and pepperflashplugin.  Every time I install the pepperflash plugin I get message "System program problem detected" when I try and fire up Chromium or Chrome.  Anybody else having this problem ?

How did you install it ? Which instructions did you follow ?

---

### Post by cwlinux2 on 2014-06-19
Chromium is fine until I install pepperflash using :-

sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install

When I fire up Chromium I get a "System Error" message.

I've also tied installing pepperflash with the PPA instructions :-
[COLOR=#0000ff]To add the PPA and install Adobe Pepper Flash from Google Chrome in Ubuntu (to be used in Chromium), use the following commands:
sudo add-apt-repository ppa:skunk/pepper-flash
sudo apt-get update
sudo apt-get install pepflashplugin-installer
 
Once installed, there's one more step to get Chromium to use the Google Chrome Pepper Flash Player: you need to open /etc/chromium-browser/default as root with a text editor (e.g.: gedit - which I'll use in the command below):
sudo apt-get install gksu #it`s not installed by default in Ubuntu 13.04
gksu gksu gedit /etc/chromium-browser/default
("gksu" is used twice to avoid a bug with Gedit opening a blank file next to our file)
 
and in that file, paste the following line at the bottom of the file (after the CHROMIUM_FLAGS="" line):
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
(yes, there's a dot in the beginning of the line, then a space!)
[/COLOR][COLOR=#000000]When I fire up Chromium and browse a page containing flash video it comes up saying  Adobe Flash Player required

[/COLOR][COLOR=#ff0000]**Now here's a strange thing.**

The problem seems to be with embedded Youtube videos.[/COLOR][COLOR=#000000]
If I go to Youtube and play a video it works OK but if I go to a page that has that same video embedded then I get the message Adobe Flash Player required.

Anyone got any suggestions about this ? 
[/COLOR][COLOR=#0000ff]
[/COLOR]

---

### Post by s9032g@comcast.net on 2014-06-19
[http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/](http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/)

---

### Post by cwlinux2 on 2014-07-06
Looking at the FOSS instructions they seem to be the same as the ones I used.

The issue seems to be with Pepperflash.

Until I install pepperflash Chromium works fine - but won't play flash files - Youtube stuff etc.

When I install Pepperflash and then fire up Chromium I get the "System Error" message I reported earlier  i.e. Chromium won't even load.

---

### Post by cwlinux2 on 2014-07-09
[COLOR=#000000]Having installed with PPA Chromium fires up OK but if I look at a site with embedded youtube video I get a message saying I need to install Adobe Flash player.

The problem seems to be with embedded Youtube videos.[/COLOR][COLOR=#000000][COLOR=#000000]
If I go to Youtube and play a video it works OK but if I go to a page that has that same video embedded then I get the message Adobe Flash Player required.

Anyone got any suggestions about this ? [/COLOR][/COLOR]

---

### Post by fida_hussain on 2015-02-04
thanks, solved!

---

