---
title: "Printer (Canon iP4950 )and CUPS"
date: 2017-01-26
forum: Installation &amp; Upgrades
---

### Post by davethesteam on 2017-01-26
Hi again
Oh dear, there I was thinking it was sorted. An error appeared on the top right hand side of the main menu which then asked for a partial upgrade.
This is the log for partial upgrade:
Jan 25 23:34:37 david-All-Series pkexec[12264]: david: Executing command [USER=root] [TTY=unknown] [CWD=/home/david] [COMMAND=/usr/lib/ubuntu-release-upgrader/do-partial-upgrade --frontend=DistUpgradeViewGtk3]
Jan 25 23:36:30 david-All-Series polkitd(authority=local): Unregistered Authentication Agent for unix-session:c1 (system bus name :1.58, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8) (disconnected from bus)

This I did and the problem (printer not working) returned....
This time, in trying to log to:
system settings/printers/connect I was met with:
"Printing Service not available. Start the service on this computer or connect to another server"
Pressing 'connect'
error message comes up ' cups failed to connect to server'.

I have tried reloading cups.
I have worked through the 'debugging printer problems' on the Ubuntu Wiki.

All with no effect.
Is there any thing I can do to restore my printer please?

---

### Post by ajgreeny on 2017-01-26
Can you get to localhost:631 in a web browser?

It should take you to the cups-webmin page but recently when I tried I found that cups was not running.  Running command ```
sudo service cups start
``` gets everything going again; we just need to figure out why cups is not starting at boot as it normally does.

---

### Post by davethesteam on 2017-01-26
Thank you AJGreeny
Tried this and response from Printer section of the 'Cog' app was:
'Cups Server Error
There was an error during cups operation
Failed to connect to server"

Thus, still no Cups and still no printer!!!

---

### Post by davethesteam on 2017-01-26
I forgot to add:
The printer is wired connection to desktop - it is not attached to a server
I am using Ubuntu 16.04 LTS 64 bit

---

### Post by ajgreeny on 2017-01-26
Cups server is a service that runs in systems and not just in servers, so no need to concern yourself about that.

Did you run the **sudo service cups start** command I mention above then try again the localhost:631 in a browser?

---

### Post by davethesteam on 2017-01-26
Thanks for coming back.
Yes I did run the command from my Terminal.
I could not access 'localhost:631' though

Further info:
The cups server in the 'connect' dialogue box is shown as:
/var/run/cups/cups.sock

I have had a look in my 'Computer' dialogue in my Home and found the 'cups.sock' is empty.

So, do I think correctly that I need to find a way of changing that and if so, to what?

---

### Post by Geoffrey_Arndt on 2017-01-27
what browser are you using?   Firefox is best for CUPS access via typing "localhost:631" in the main URL window of Firefox.

---

### Post by davethesteam on 2017-01-27
Thank you
Yes, I am using Firefox

---

### Post by ajgreeny on 2017-01-27
I was having a similar problem with cups not keeping running; after a few minutes it would simply stop and it was then impossible to use the localhost:631 address.

A deeper search than I had used before found a bug about this at [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300) with a potential solution which so far seems to be working.

First fully update your 16.04 installation.
Enable the proposed repos in software sources and refresh.
Search for all the cups packages installed (easiest with synaptic, searching by name only) and mark them all for upgrade.
Disable the proposed repos again as you do not normally want them; they are potentially troublesome.

Hopefully you should now have a system where cups does not keep stopping, causing the problem you saw.

[COLOR="#FF0000"]EDIT:[/COLOR]
I can confirm that upgrading all the cups packages I had installed in my system with those from the proposed repos, then disabling proposed again has solved the problem for me.

I have added my comments to the bug, to which I subscribed yesterday.

---

### Post by davethesteam on 2017-01-28
Hi all
Many thanks for all your help and advise.
I ended up doing a clean install - that solved the problem - just learned the lesson NEVER do a partial upgrade

---

