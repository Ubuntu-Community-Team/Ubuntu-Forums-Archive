---
title: "after upgrade to 14.04 (12.04) my kodak esp5250 aio printer stopped printing"
date: 2014-08-27
forum: Installation &amp; Upgrades
---

### Post by btodd012 on 2014-08-27
I have an esp5250 that was working fine in 12.04. After I upgraded, it stopped working. It looks OK. I looked at network printer troubleshooting and ran all the cmds there - looks fine (to me).

todd@todd-GX270:~$ lpq
Eastman-Kodak-Company-KODAK-ESP-5200-Series-AiO is ready
Rank    Owner   Job     File(s)                         Total Size
1st     todd    17      apache-notes                    14336 bytes
2nd     todd    20      Test Page                       1024 bytes

I think there is a new driver for 14.04 - but am not sure how to check that. The old driver was c2esp16. If I try to print from command line it looks like it completes - but just sits in the queue.

Lots of tips I read say go to System/Administration/Print Settings - or similar (Gui). I have no app there with anyting that mentions printer - Am I missing something?

Under system settings there is a Gui for Printers. If I open that it shows the queue etc. Looks OK. If I click on printer trouble shooting, its says **Server Not Exporting Printers**. It says - Enable the "Publish shared printers connected to the system" option using the **printing administration tool**. in the System->Administration print settings from the main menu... and again - **I don't have or see that anywhere**.  When I go forward -  get the staus message "Render competed".  Again - looking OK.

I don't know where to go from here???

Also - have been searching for cmd line commands to see what driver is being used etc...
I found 
sudo ubuntu-drivers list
and 
sudo ubuntu-drivers devices

When I run these cmds - they do "something" for a while and then just end. No output... no man pages... ???

I could really use some help and direction...

O yes - I can ping, traceroute nmap the printer and the route looks good. The printer is wireless also but it is connected to my router.

Thanks

---

