---
title: "Firefox Offline Mode Hardy Heron"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Pudwud on 2008-04-29
After the upgrade to Hardy Heron when I start Firefox I get this message:

“Firefox is currently in offline mode and can't browse the Web.”

Is there a way that I can set it up so that the default is online mode?

Thanks.

---

### Post by Roger Steiner on 2008-05-01
It sounds like the modem or lan card is not set up. The computer is not attached to the internet.

---

### Post by daka on 2008-05-03
me too.... can't seem to figure out how to resolve this...

also Vodafone Mobile Connect card much more problematic in Heron ... needing to do the following:

modprobe usbserial vendor=0x12d1 product=0x1003
 then disconnecting and reconnecting the modem
then
sudo modprobe -r ehci_hcd

before Huawei E220 will initialize

Anyone else experiencing these problems with modem being recognized... who maybe has  a better fix for the problem?

Daka

---

### Post by Pudwud on 2008-05-04
You might want to try Firefox 2 to solve the "offline" problem.

---

### Post by nowhere@cox.net on 2008-05-05
> **Pudwud said:**
> You might want to try Firefox 2 to solve the "offline" problem.

Sorry Pudwud but I wouldn't call this a solution. Perhaps a workaround. I do believe you are correct tho. This does seem to be a Firefox 3 problem. If a LAN or WLAN connection is not detected, FF3 defaults to offline mode. This means if you are using dialup, even after a suspend and restart of firefox, it defaults up to offline. 

I just have to uncheck the Work Offline menu item on the File menu to get back online but it is a pain. If I can figure out where, I will report it as a bug unless there is a setting I am missing to fix it.

---

### Post by be4truth on 2008-05-09
This bug is already filed.
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889")

---

### Post by jenkinbr on 2008-05-12
I found this link in a closed hardy development thread:
[https://bugzilla.novell.com/show_bug.cgi?id=175896#c14](https://bugzilla.novell.com/show_bug.cgi?id=175896#c14)

It appears that there is a hidden preference in about:config.

[COLOR=Red]**I wouldn't bother trying this, it didn't work. :( **[/COLOR]
[possible_workaround]
[LIST=1]
[*]In firefox, go to about:config
[*]Enter "browser.ignoreNM" into the filter bar (finds the pref, if it is set already)
[*]If the pref does not exist, r-click -> new -> boolean and name it "browser.ignoreNM"
[*]Ensure that it is set to 'true'
[*]Restart Firefox.
[/LIST]
[/possible_workaround]

Note: My home machine is not online, but I run an apache2 web server for developmental purposes, so this behavior is very annoying for me, as well.

**[edit]** Now that I have gotten a chance to give this a try...

At first, when I did this, it appeared to be unsuccessful.  However, I continued to play around a bit, and as suggested above, disabled ubufox, and clicked restart.

It worked!  Just for kickes, I re-enabled ubufox and restarted, and it still worked fine.  Maybe firefox required some sort of reload that went beyond the scope of simply closing out the browser and launching it again.

Now for the true test.  I hit [ctrl]+[backspace] to restart X and logged in again.  Launched firefox, and realized that my success was short-lived.  Disableing ubufox again, I restarted firefox, and it was in online mode.  Again, however, the settings didn't stick, as they should.  Restarting X and logging in brought me back to that beautiful "Firefox is in offline mode and cannot browse the web" page I've come to purely enjoy. :P

Long story short, this really accomplished little more than nothing.  In fact, all it accomplished for me was more frustration, wasted time, and a disproved workaround.

Oh yeah, [size=40]name here[size] + any other tab-lovers:  Try switching the browser to online mode, then r-click on one of your open tabs and select the option "Reload all tabs".  Works a charm, even when you have even a small number of tabs open.  Makes it slightly less annoying, but still...

---

