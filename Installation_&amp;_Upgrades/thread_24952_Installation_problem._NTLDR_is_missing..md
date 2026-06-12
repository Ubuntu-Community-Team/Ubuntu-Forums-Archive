---
title: "Installation problem. NTLDR is missing."
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by gflores on 2005-04-08
I installed Ubuntu and when it restarted I got this message.
> 
NTLDR is missing


After doing a quick search, I found out that it's Windows' boot loader. So, I'm guessing that's not a good sign...

Any suggestions as to what to do? 

I'm using Windows XP SP2.

Thanks.

---

### Post by Francisco on 2005-04-08
[QUOTE=gflores]I installed Ubuntu and when it restarted I got this message.


After doing a quick search, I found out that it's Windows' boot loader. So, I'm guessing that's not a good sign...

Any suggestions as to what to do? 

I'm using Windows XP SP2.

Thanks.[/QUOTE]

 Happened to me once installing Slack on an SP2 Windows machine, Put the disk (windows install) run it, when it prompts for Remote Console say no, on the next screen you will be able to see the windows installs on the computer, you should see c:/windows well, you should be able to hit "R - Repair" hit it, and windows boot will be fixed.

 Worked for me, Recovery console is a joke.

---

### Post by gflores on 2005-04-08
[QUOTE=Francisco]Happened to me once installing Slack on an SP2 Windows machine, Put the disk (windows install) run it, when it prompts for Remote Console say no, on the next screen you will be able to see the windows installs on the computer, you should see c:/windows well, you should be able to hit "R - Repair" hit it, and windows boot will be fixed.

 Worked for me, Recovery console is a joke.[/QUOTE]
 I see, I'll try that later today. However, I would like to know why this happened, so I do not repeat my mistakes.

---

### Post by Francisco on 2005-04-08
[QUOTE=gflores]I see, I'll try that later today. However, I would like to know why this happened, so I do not repeat my mistakes.[/QUOTE]

 Usually happends when the NTLDR is corrupted or your MBR table is erased.... Check Microsoft KB for that.

---

