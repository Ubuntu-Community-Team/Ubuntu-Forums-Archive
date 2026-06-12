---
title: "gOS: Suspend problems"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by pvravi on 2008-02-12
Hi, 

I installed gOS Rocket on a Dell Latitude L400 (P3 Coppermine), and have been having a couple of problems.

1. exalt does not work. gnome NetworkManager works, but I have to start that every time I restart. I'm sure I could find a fix for this - like putting this in /etc/rc5.d or something similar. (If anyone has a better idea for starting Network Manager, please let me know).

2. Powersave modes: Suspend from the G menu works well. 
Initially I think gOS did NOT install acpid and laptop_mode during install. I installed both later (with apt-get). However, lid state always shows "closed".
If I run acpitool -s to suspend from the command line and then bring it back up, the lid state is good, but I think the fan stays off - which might cause problems in the long run. 
In any case, although the lid state is good (open for open and closed when closed) after acpitool -s, closing the lid still does not suspend the machine -just the screen goes off, which I think is hardwired to the lid-button anyway (so acpi or Linux isn't doing anything there). 
How do I get the machine to suspend when the lid is closed, and the machine to turn on correctly (with the fan on) when I bring it out of suspend?

Someone, please, please help. 

TIA
pvravi

Edit: I had Ubuntu Gutsy on the same laptop just before my gOS misadventure, and it was perfectly OK on the suspend. Just wanted to indicate that there are no Hardware problems.

---

