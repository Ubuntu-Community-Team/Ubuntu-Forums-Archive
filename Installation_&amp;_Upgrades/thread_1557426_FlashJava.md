---
title: "Flash/Java"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Zirts on 2010-08-20
Hi,

I recently decided to install all of them over, but the moment I had all of them removed, ALL of them, I chose to check how videos work. Now on Windows the Flash videos would have told me to get my self a Flash ASAP, but in Ubuntu, all the videos still work, with no performance change whatsoever too(Flash vid's are alwayz taking 100% CPU for me).

Now my question is, why do I even need to install that Flash when all the Flash apps still run without it?

---

### Post by tommcd on 2010-08-20
Well, it seems odd that flash videos would work without flash. To be sure flash is uninstalled, open a terminal and run:
```
aptitude search flash
```
A "p" before a package means it is purged (i.e., not installed) An "i" before a package means it is installed.
Also, do you have the libflashplayer.so plugin in /usr/lib/mozilla/plugins or /usr/lib/firefox/plugins? If you are on 64bit Ubuntu then also look in /usr/lib64/mozilla/plugins or /usr/lib64/firefox/plugins if you have those directories.
And have a look at about:plugins if firefox to see if it lists the flash plugin.
Are youtube videos working for you without the flash plugin?
Did you restart firefox after removing flash?

---

### Post by Zirts on 2010-08-20
```
v   abrowser-flashblock             -                                           
v   abrowser-flashgot               -                                           
pi  adobe-flashplugin               - Adobe Flash Player plugin version 10      
v   firefox-flashblock              -                                           
v   firefox-flashgot                -                                           
v   flashblock                      -                                           
p   flashgot                        - transitional dummy package                
p   flashplugin-installer           - Adobe Flash Player plugin installer       
p   flashplugin-nonfree             - Adobe Flash Player plugin installer (trans
p   flashplugin-nonfree-extrasound  - Adobe Flash Player platform support librar
p   flashrom                        - Identify, read, write, erase, and verify B
p   flashybrid                      - automates use of a flash disk as the root 
p   m16c-flash                      - Flash programmer for Renesas M16C and R8C 
p   python-webflash                 - Portable flash messages for Python WSGI ap
v   seamonkey-flashgot              -                                           
v   thunderbird-flashgot            -                                           
p   vrflash                         - tool to flash kernels and romdisks to Agen
p   xul-ext-flashblock              - mozilla extension to block Adobe Flash con
p   xul-ext-flashgot                - Turns every supported download manager int
v   xulrunner-flashgot              -                                           

```

The one with the PI before the description got a aptitude remove from me just in case too, also I'm using Google Chrome and I have completly uninstalled Firefox.

But now even if the Chrome has a Flash plugin it self, my question is, should I install the Flash v.10 too or not? Will it make any bigger difference now than it did before.

---

### Post by tommcd on 2010-08-21
So you removed the one in the aptitude list that said:
```
pi  adobe-flashplugin  - Adobe Flash Player plugin version 10
```
And the flash videos still work on Chrome?
Perhaps Chrome stores it's own flash somewhere in it's own plugin directory. I thought Chrome just used the same flash plugin from firefox though. Did you install gnash perhaps?
Anyway, if the videos play ok I would just leave it alone. If not, then reinstall flash.

---

### Post by Zirts on 2010-08-21
No gnash is installed, checked it now.

I guess that Google Chrome indeed does have a built-in flash then, and I'm not gonna install any other Flash programs on my PC now.

Thank you for the help.

Solved.

---

### Post by tommcd on 2010-08-22
> **Zirts said:**
> 
I guess that Google Chrome indeed does have a built-in flash then, and I'm not gonna install any other Flash programs on my PC now.

Well, I finally decided to break down and google this to find out. I googled:
```
google chrome flash plugin
```
And, lo and behold, the very first link was:
[http://googlechromereleases.blogspot.com/2010/03/dev-channel-update_30.html](http://googlechromereleases.blogspot.com/2010/03/dev-channel-update_30.html)
> The Google Chrome Dev channel has been updated to 5.0.360.4 for Windows and Mac and 5.0.360.5 for Linux.
This release includes:
* An integrated Adobe Flash Player Plug-in. ...
That link was from March 2010. So I suppose the Chrome you installed must include this integrated flash.
See also:
[http://www.zatznotfunny.com/2008-09/google-chrome-bundles-adobe-flash/](http://www.zatznotfunny.com/2008-09/google-chrome-bundles-adobe-flash/)

I played around with Chrome for a while on my Slackware system that also has Firefox and flash installed. This was quite a while ago. As I recall, Chrome used to just link itself to Firefox's flash. This is what I thought anyway.
 I always had Firefox and flash installed, so I never thought that Chrome may have it's own built in flash. It looks like it does now though. I have not been keeping up with the development of Chrome lately though.

Apparently, at one time it was necessary to manually enable flash support for Chrome on Ubuntu 9.04:
[http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04](http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04)

So, just out of curiosity, what version of Chrome do you have, and where did you get it from? And how did you install it on Ubuntu?

---

### Post by Zirts on 2010-08-22
I'm using: Google Chrome 5.0.375.127.

At first I used the open-source Chromium but it was missing something, don't remember what, anyway I installed the Google Chrome from Google's homepage. (Didn't find it in Ubuntu's packet manager on that time.)

Zirts

---

