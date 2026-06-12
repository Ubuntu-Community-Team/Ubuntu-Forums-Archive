---
title: "Installation of the AWN-applet-stacks doesnt work"
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by goebelj on 2013-12-18
Thats the error:
[PHP]it@it:~$ sudo apt-get install awn-applet-stack 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 awn-applet-stack : Depends: python-gnomedesktop but it is not installable or
                             python-gnome2-desktop but it is not installable
E: Unable to correct problems, you have held broken packages.

[/PHP]

I am using the ppa from there:[http://www.webupd8.org/2013/11/avant-window-navigator-gets-new.html](http://www.webupd8.org/2013/11/avant-window-navigator-gets-new.html)

It is not related to anything i installed or changed, im at the live disk right now getting the exact same error i get on my live system.

---

### Post by Frogs Hair on 2013-12-18
Hello and Welcome

This lines below make me think the applet isn't gnome 3 compatible yet . If the packages are held try the following.  ```
sudo apt-get update  &&  sudo apt-get install awn-applet-stack 
``` Broken and held packages are part of the risk involved with using a ppa.


[COLOR=#0000BB][FONT=Ubuntu Mono]The following packages have unmet dependencies[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]:
 [/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]awn[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]applet[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]stack [/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]: [/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]Depends[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]: [/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]python[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]gnomedesktop but it is not installable [/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]or
                             [/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]python[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]gnome2[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]desktop but it is not installable
E[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono]: [/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]Unable to correct problems[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono], [/FONT][/COLOR][COLOR=#0000BB][FONT=Ubuntu Mono]you have held broken packages[/FONT][/COLOR][COLOR=#007700][FONT=Ubuntu Mono].  [/FONT][/COLOR]

---

