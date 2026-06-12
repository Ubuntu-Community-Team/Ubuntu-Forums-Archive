---
title: "Pepper flash. Chromium reports incorrect plugin version"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by tomsam2 on 2014-09-10
[COLOR=#000000][FONT=Droid Sans]Hi,

today (Wed, Sep 10, 2014), I installed a clean chromium, started it, and 
was wondering at first, why the pepperflash plugin had not been installed.

So, I did

**sudo apt-get install pepperflashplugin-nonfree**
**sudo update-pepperflashplugin-nonfree --install**
**sudo /usr/sbin/update-pepperflashplugin-nonfree --status**

which results in 

**Flash Player version installed on this system  : 15.0.0.152**
**Flash Player version available on upstream site: 15.0.0.152**

However, chrome://version (see below) and also chrome://plugins state
that the installed flash plugin version is** 11.2.999.999**

So I had a look at** /etc/chromium-browser/default **which contains

-------------------
# part for pepperflashplugin-nonfree : begin

flashso="/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so"

if [ -f $flashso ]
then
        flashversion=`strings $flashso|grep ^LNX|sed -e "s/^LNX //"|sed -e "s/,/./g"`
        CHROMIUM_FLAGS="$CHROMIUM_FLAGS --ppapi-flash-path=$flashso --ppapi-flash-version=$flashversion"
fi


# part for pepperflashplugin-nonfree : end
-------------------

On the command line:

**$ flashso="/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so"**
**$ strings $flashso | grep ^LNX**

does not result in any output.

If I just search for LNX , however, I get the following output:

**$ strings $flashso | grep LNX**
**[@LNX 15,0,0,152**

So it seems, the way the script is trying to retrieve the current version is 
incorrect  !

[/FONT][/COLOR]**$ strings ****$flashso**[B] | grep LNX | sed -e 's/.*LNX //' 
 [/B][COLOR=#000000][FONT=Droid Sans]
might work for now, so a line 

[/FONT][/COLOR]**flashversion=`strings $flashso|grep LNX|sed -e "s/.*LNX //"|sed -e "s/,/./g"`**


[COLOR=#000000][FONT=Droid Sans]in the chromium default file . Better solutions are welcome.


I report this here, since  dpkg says, this is an ubuntu package

**$ dpkg -l | grep pepper**
**ii  pepperflashplugin-nonfree                                   1.3ubuntu1                                 amd64        Pepper Flash Player - browser plugin**

If this is not the correct place, please let me know, where I have to 
address this issue.
 
Thanks
tomsam

----chrome://version---------------------------
**Chromium    37.0.2062.94 (Developer Build 290621) Ubuntu 14.04**
OS    Linux 
Blink    537.36 (@180557)
JavaScript    V8 3.27.34.14
**Flash    11.2.999.999**
User Agent    Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Ubuntu Chromium/37.0.2062.94 Chrome/37.0.2062.94 Safari/537.36
Command Line    /usr/lib/chromium-browser/chromium-browser --ppapi-flash-path=/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so --ppapi-flash-version --enable-pinch --flag-switches-begin --flag-switches-end
Executable Path    /usr/lib/chromium-browser/chromium-browser
Profile Path    /home/tomsam/.config/chromium/Default
Variations    24dca50e-455c9cca
ca65a9fe-91ac3782
246fb659-5c63917a
f296190c-2502111b
4442aae2-a90023b1
ed1d377-e1cc0f14
75f0f0a0-a5822863
e2b18481-3a9ae350
e7e71889-e1cc0f14


---chrome://plugins----
**Adobe Flash Player - Version: 11.2.999.999**
Shockwave Flash 11.2 r999
Name:    Shockwave Flash
Description:    Shockwave Flash 11.2 r999
**Version:    11.2.999.999**
Location:    /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so






[/FONT][/COLOR]

---

