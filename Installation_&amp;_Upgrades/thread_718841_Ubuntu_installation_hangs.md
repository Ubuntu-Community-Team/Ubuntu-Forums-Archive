---
title: "Ubuntu installation hangs"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by akgem1 on 2008-03-08
I’m trying to boot from CD/install Ubuntu 7.10 on a computer I just finished building and I’m having problems doing so. When I boot from CD and select the first “Install Ubuntu…” option, it goes through the Ubuntu screen with the sliding status bar, then it gets to a black screen that says the following:

* Starting deferred execution scheduler atd [OK]
* Starting periodic command scheduler crond [OK]
* Checking battery state… [OK]
* Running local boot scripts (/etc/rc.local) [OK]

That screen flickers a few times for about 20-30 seconds, then a message box pops up with “Ubuntu is running in low-graphics mode” and “Configure” “Shut Down” and “Continue” buttons. I click on “Configure” button and manually select my monitor’s brand, model and resolution and click “OK”. It goes back to the previous black screen with those same 4 lines (see above) and never gets past that point. Clicking on “Continue” instead of “Configure” from the pop-up leads to the same results. 

This is my first experience with Ubutu and Linux in general – I just figured it was time to break away from Windows and try other OSs out there. Does anyone have any suggestions on what I could do to get past this issue? This PC already has Windows Vista installed (if it makes any difference). Thanks in advance.

---

### Post by sanmeetkanhere on 2008-03-08
It seems that ubuntu is having trouble detecting your monitor settings, resolution etc. What graphics card are you using?

---

### Post by akgem1 on 2008-03-08
I have Gigabyte GA-73PVM-S2H motherboard with built-in graphics card (Nvidia GeForce 7100). I tell the installer which monitor I have when that message pops-up, and my monitor is on the list of "supported" monitors.

---

### Post by papa0tter on 2008-03-08
I am having this EXACT same problem.

MB: Gigabyte GA-P35-DS3L
GPU:GeForce 9600GT
Monitor: Soyo Topaz

I thought it was a video problem as well and after a search tried this suggestion found on these boards:

During install delete 'quiet splash' add 'vga=791'

This still didnt work for me. So I return here to post the exact message you did. 

I Will keep looking and post a solution if I get so lucky.

---

