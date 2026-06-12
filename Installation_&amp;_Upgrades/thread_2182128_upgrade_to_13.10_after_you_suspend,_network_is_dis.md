---
title: "upgrade to 13.10 after you suspend, network is disabled and cant be enabled"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2013-10-20
It requires a reboot.
This is an onboard e1000 network chip

---

### Post by coffeecat on 2013-10-20
13.10 is no longer in development and has been released now.

*Thread moved to **Installation & Upgrades**.*

---

### Post by sdowney717 on 2013-10-20
It requires a reboot.
This is an onboard e1000 network chip
any ideas?

I have the x1300 AMD video card 
After it wakes up, you see the empty network triangle and click on it says network disabled.
And the leds are off.
IF you tell it to enable, the LEDs light up but the empty triangle remains. And no network.

---

### Post by sdowney717 on 2013-10-20
I solved following this advice
[http://askubuntu.com/questions/266857/ubuntu-12-04-wifi-not-working-after-suspension](http://askubuntu.com/questions/266857/ubuntu-12-04-wifi-not-working-after-suspension)

```
Here is a technique that sometimes works:

gksudo gedit /etc/pm/config.d/config
Add a single line:

SUSPEND_MODULES="e100"
Proofread, save and close gedit. Reboot, suspend and let us have your report.
```

for me the driver is e100.
You find the driver by sudo lshw -C network

the line driver = 'the driver', the driver is what you use in that line 

SUSPEND_MODULES="the driver"

---

### Post by sdowney717 on 2013-10-20
Not solved.
This seems to work if you do a suspend and then within a couple minutes awake the PC.
I just left it sit suspended for an hour and when it awakens, the network is disabled.

---

### Post by castor_fou on 2013-10-20
Same issue here.

I can however resume network with : sudo nmcli nm sleep false

---

### Post by sdowney717 on 2013-10-21
Thanks for this. That does work.
I ran it and I got a message that says network now offline.

Then you click the icon and you see all the network cards
Then tell it to enable networking, selecting 'Auto Ethernet'
And it comes back working.

SO, how can we make this work like it should?
Anyone submitted a bug yet?

I changed the line to read 
SUSPEND_MODULES="e100 e1000" in that config file, but it has no effect.
This MB has 2 NICS onboard builtin.

---

### Post by sdowney717 on 2013-10-21
I started a bug report so if you wish to join and contribute some input there.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1242679](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1242679)

---

### Post by phaenze on 2013-10-27
I have this bug as well. I found the work-around* [here]("http://ubuntuforums.org/showthread.php?t=2182058&p=12824696#post12824696") and [here]("http://ubuntuforums.org/showthread.php?t=1652574&p=10283728#post10283728"). The basic steps are:
> sudo touch /etc/pm/sleep.d/wakenet.sh

sudo chmod +x /etc/pm/sleep.d/wakenet.sh

sudo gedit /etc/pm/sleep.d/wakenet.sh[INDENT]Insert the following lines:
[/INDENT]
[INDENT=2][COLOR=#000000][FONT=Courier New]**#!/bin/bash**[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]**case "$1" in**[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]**    thaw|resume)**[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]**        nmcli nm sleep false**[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]**        ;;**[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]**    *)**[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]**        ;;**[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]**esac**[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]**exit $?**[/FONT][/COLOR][/INDENT]
Save

[COLOR=#000000][FONT=Verdana]

Now the interface is started upon resume. It seems to suspend/resume slower, but it works.

Peace,
Paul :cool:

*This is not the solution (as I originally wrote) but a work-around. The solution is for the bug to be fixed. Visit this [page]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1242679") and click if it's affecting you. Thanks.[/FONT][/COLOR]

---

### Post by yefymenko on 2013-10-29
> **phaenze said:**
> I have this bug as well. I found the work-around* [here]("http://ubuntuforums.org/showthread.php?t=2182058&p=12824696#post12824696") and [here]("http://ubuntuforums.org/showthread.php?t=1652574&p=10283728#post10283728"). The basic steps are:
[COLOR=#000000][FONT=Verdana]

Now the interface is started upon resume. It seems to suspend/resume slower, but it works.

Peace,
Paul :cool:

*This is not the solution (as I originally wrote) but a work-around. The solution is for the bug to be fixed. Visit this [page]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1242679") and click if it's affecting you. Thanks.[/FONT][/COLOR]

This worked perfectly for me.  Ubuntu 13.10, driver=iwlwifi, 

Hardware:
description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:90:dd:44
       width: 64 bits
       clock: 33MHz


Thanks.

---

### Post by Tommy on 2013-10-31
Anyone having this problem might also want look at bug 1184262 -- [https://bugs.launchpad.net/bugs/1184262](https://bugs.launchpad.net/bugs/1184262) -- as of yesterday there's a software package with a patch to try to fix it, which has helped some and not others.

EDIT: The updated software HAS helped me.

---

### Post by Atcold on 2013-11-03
> **phaenze said:**
> I have this bug as well. I found the work-around* [here]("http://ubuntuforums.org/showthread.php?t=2182058&p=12824696#post12824696") and [here]("http://ubuntuforums.org/showthread.php?t=1652574&p=10283728#post10283728"). The basic steps are:
[COLOR=#000000][FONT=Verdana]

Now the interface is started upon resume. It seems to suspend/resume slower, but it works.

Peace,
Paul :cool:

*This is not the solution (as I originally wrote) but a work-around. The solution is for the bug to be fixed. Visit this [page]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1242679") and click if it's affecting you. Thanks.[/FONT][/COLOR]
Awesome! This did the job! I was without network even after rebooting the system, but now it works fine again :)
Thank you very much

---

### Post by gacb on 2013-11-05
If any of you are using cairo-dock, disable the auto-starting, reboot and see if the problem persists. It resolved my suspend problem and the reboot/shutdown functions were reactivated as well.

I've filed a [bug report]("https://bugs.launchpad.net/bugs/1248220") indicating the conflict.

---

### Post by Tommy on 2013-11-06
> **gacb said:**
> If any of you are using cairo-dock, disable the auto-starting, reboot and see if the problem persists. It resolved my suspend problem and the reboot/shutdown functions were reactivated as well.


You might also want to look at Bug 1184262 [https://bugs.launchpad.net/bugs/1184262](https://bugs.launchpad.net/bugs/1184262) -- it could be that cairo-dock is triggering the bug merely because it puts just enough strain on the processor. On my netbook, the bug got triggered by opening a Chrome browser with a couple of dozen tabs. Try installing the updated package and see if it helps with cairo-dock.

EDIT: This week (2013-11-14) they released a fix to the systemd-shim software so if you see that update come through on your update-manager, give it a try. It fixes (or greatly reduces) the problem for many folks.

---

### Post by Dr.Death on 2013-11-23
> **phaenze said:**
> I have this bug as well. I found the work-around* [here]("http://ubuntuforums.org/showthread.php?t=2182058&p=12824696#post12824696") and [here]("http://ubuntuforums.org/showthread.php?t=1652574&p=10283728#post10283728"). The basic steps are:
[COLOR=#000000][FONT=Verdana]

Now the interface is started upon resume. It seems to suspend/resume slower, but it works.

Peace,
Paul :cool:

*This is not the solution (as I originally wrote) but a work-around. The solution is for the bug to be fixed. Visit this [page]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1242679") and click if it's affecting you. Thanks.[/FONT][/COLOR]


thanks, this work around solve my problem

---

### Post by Clemens1947 on 2013-11-26
Perfect workaround for me. Has not failed on Asus K53SC laptop. Thanks.

---

