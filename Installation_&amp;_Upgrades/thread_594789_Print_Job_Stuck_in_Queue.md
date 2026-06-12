---
title: "Print Job Stuck in Queue"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-10-28
Feisty 7.04
Printing from Moneydance

Initially I tried to print from Moneydance, a Java application and like many others I received the error message "No Print Services Found".

After some research I found that there is a conflict between Java 1.6 (and 1.5) and Cups 1.2.
[B]
[COLOR=Green]On the Cups website I found the following article #433.[/COLOR][/B]

[http://www.cups.org/articles.php?L433+I0+TFAQ+M10+P1+Q](http://www.cups.org/articles.php?L433+I0+TFAQ+M10+P1+Q)

After following solution #2 I retried to print.  I did not get an error message but Moneydance did put up the printing dialog box providing me choices for the correct printer.

However the job did not print.  I issued the command /usr/bin/system-config-printer-applet --no-tray-icon and found the print job with a status of "stopped".  Right clicking on the print job offered me a choice of cancel.  The remaining choices like release etc was grayed out.

**Who out there can rise to this challenge and solve this problem? :confused:**

From my reading the original problem happens with any software product that was written using JDK6 or JDK5 and users running JRE6 or JRE5 and using CUPS 1.2 that is included in Feisty.   I do not know about other releases of Ubuntu but I know it is happening in other distros.

---

### Post by Zeosa on 2007-10-28
I'm relatively new to ubuntu, but have been running linux servers for years....

That said, I'm more apt to use command line utils before gui apps, so there may be a better way in the gui...

open a terminal window and type lpq ...it should list print queues and jobs for each (if you have more than one queue).....the jobs will have numbers beside them....

After getting the job number, type lprm <jobnumber>.....

---

### Post by measekite on 2007-10-28
> **Zeosa said:**
> I'm relatively new to ubuntu, but have been running linux servers for years....

That said, I'm more apt to use command line utils before gui apps, so there may be a better way in the gui...

open a terminal window and type lpq ...it should list print queues and jobs for each (if you have more than one queue).....the jobs will have numbers beside them....

After getting the job number, type lprm <jobnumber>.....

lpq returned job 92

lprm 92 did nothing.

I then did lpq and the job was no longer there and it said Deskjet ready.

I can print from all other applications.

---

### Post by Zeosa on 2007-10-28
> **measekite said:**
> lpq returned job 92

lprm 92 did nothing.

I then did lpq and the job was no longer there and it said Deskjet ready.

I can print from all other applications.

I should have told you, lprm doesn't typically return outpu if successful. It if the second lpq didn't show any jobs then it has been removed as directed..

As for your printing problem, I really don't know what the problem is off the top of my head

---

