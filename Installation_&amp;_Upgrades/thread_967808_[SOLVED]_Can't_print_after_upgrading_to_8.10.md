---
title: "[SOLVED] Can't print after upgrading to 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by coalcracker on 2008-11-02
I upgraded to 8.10 from 8.04, everything went flawless except for visual effects and printing. I can live without the visual effects but I need to print. During the upgrade I got a message asking if I wanted to keep the old CUPS file, to which I said yes. Now when I click on Default Printer, I get an error message saying "The CUPS Scheduler is not running". I tried restarting the CUPS service with "sudo /etc/init.d cups restart" but I get "command not found". After doing some investigating I found my CUPS shell script in /etc/init.d has a broken link. Not sure if this is the problem. If this is the problem, how do I fix it? Any help would be greatly appreciated. I'm a relative newbie to Linux and Ubuntu, so excuse my naiveness.

---

### Post by coalcracker on 2008-11-04
> **coalcracker said:**
> I upgraded to 8.10 from 8.04, everything went flawless except for visual effects and printing. I can live without the visual effects but I need to print. During the upgrade I got a message asking if I wanted to keep the old CUPS file, to which I said yes. Now when I click on Default Printer, I get an error message saying "The CUPS Scheduler is not running". I tried restarting the CUPS service with "sudo /etc/init.d cups restart" but I get "command not found". After doing some investigating I found my CUPS shell script in /etc/init.d has a broken link. Not sure if this is the problem. If this is the problem, how do I fix it? Any help would be greatly appreciated. I'm a relative newbie to Linux and Ubuntu, so excuse my naiveness.

I installed CUPS 1.3.8 from source

---

