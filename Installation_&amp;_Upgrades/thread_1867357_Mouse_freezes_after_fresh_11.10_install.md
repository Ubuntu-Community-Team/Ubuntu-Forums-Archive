---
title: "Mouse freezes after fresh 11.10 install"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by SkyeFerret on 2011-10-22
I've installed 11.10 a few times now whilst tinkering with it, and every time I start it up for the first time after the install and try to run a program, my mouse cursor locks in place. Haven't gotten a chance to test this on the desktop yet, so I'm guessing it's just a trackpad issue, but it's really difficult when you're trying to fix something and your mouse locks up. Only way to control the computer afterward is, obviously, via keyboard (or firm power button press, lol). 

I know it's minor, but is anyone else having this problem, what's causing it, and how can it be fixed?

---

### Post by prioritymail on 2011-10-22
I am having this problem. It doesn't happen every time I start up. My mouse is not frozen at the login page. Only after I log in to my account does it freeze. If I log in to guest account (where wi-fi oddly does not work) it is not frozen. If I log out and log back in to my account, it is still frozen. No amount of hitting the "mouse freeze" button makes a difference. Restarting after the mouse has frozen tends to result in the mouse still being frozen upon log-in. Only after numerous restarts and clicking the "mouse freeze" button on and off after logging in does the mouse finally become unfrozen. I did not have this problem before upgrading from 11.04 to 11.10. I have no idea what's causing it. If you figure it out, please let me know. Also it is interesting that when the mouse is working normally the "mouse freeze" button usually works, and when I hit the button to unfreeze, a drop down box thing appears under where the time is on the desktop but the box is just a black bar with nothing in it. I wonder if the problem has something to do with this button...I forget now but it seems like in 11.04 if you had the mouse lock on when booting, you had to command line something in order to get it unfrozen so maybe in an attempt to resolve that issue this new one has been created. Not sure. I don't use this button so I don't think hitting the button is a trigger.

---

### Post by avpap on 2011-10-23
Same problem is happening here. Mouse freezes from time to time and only restart is the option. It must be a bug of Ubuntu Oneiric.

---

### Post by Pabbajati on 2011-10-23
Just to show anyone whose developing that I had the same problem immediately after upgrade.  Worked ok after re-starting.

---

### Post by raja.genupula on 2011-10-23
Hi 
   I have got this.I hope that gonna help you.

[click!]("http://ubuntuforums.org/showthread.php?t=1852081")

All the best.

---

### Post by SkyeFerret on 2011-10-25
> **raja.genupula said:**
> Hi 
   I have got this.I hope that gonna help you.

[click!]("http://ubuntuforums.org/showthread.php?t=1852081")

All the best.

Thanks. Just for confirmation, does this thread also apply to 32-bit Ubuntu?

---

### Post by FirstByté on 2011-10-26
Just to bring the solution to a single location:

[here]("http://ubuntuforums.org/showpost.php?p=11326444&postcount=25")

```
synclient TouchpadOff=0
```

Hope this helps anyone still having this issue (and also that this is finally fixed permanently)

---

### Post by SkyeFerret on 2011-10-27
> **FirstByté said:**
> Just to bring the solution to a single location:

[here]("http://ubuntuforums.org/showpost.php?p=11326444&postcount=25")

```
synclient TouchpadOff=0
```

Hope this helps anyone still having this issue (and also that this is finally fixed permanently)

Alright, thanks everyone. Making this as solved. <3

---

