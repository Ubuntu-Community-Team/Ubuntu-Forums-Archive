---
title: "Hanging at: &quot;* Starting Hotplug System&quot;"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by asearle on 2006-03-02
I have been running Ubuntu fine on my old laptop but it seems to have a problem with my new one ...

I have an ASUS Z9200VA and so first tried to get the 'Live CD' version of 5.10 running (just to see if everything works).  Most of the start-up seemed to run through OK (i.e. selecting keyboard, language and display) but the start-up hung at "* Starting Hotplug System" and just wouldn't go any further.

Maybe someone out there can help me diagnose what might be blocking the startup?  Are there diagnostics that I can run or is there a log-file that I can check?

Or should I try directly with the installation?  This would be possible but I'm reluctant to do this until I have checked the system with the live CD.

Any tips would be gratefully received.

Regards,
Alan Searle.

---

### Post by asearle on 2006-03-03
I have been experimenting and tried starting with acpi=off (to disactivate automatic recognition, I imagine) and the system still hung at the same place.

Does anyone have any other ideas of things that I might/should check.

Many thanks,
Alan Searle

---

### Post by EKa on 2006-03-03
Hi Alan,

I have struggled with the same and noticed that unplugging wlan stick lets me pass the point. Why? I don't know yet. I'm also trying to configure the wireless connection with no success so far. The stick is OK for sure.

---

### Post by asearle on 2006-03-04
Thanks for your tip and, yes, I also thought/think it might be a peripheral that is blocking my startup.  Unfortunately my Wireless LAN is 'on-board' :-/

I hope that someone outthere has an idea to help me get past this silly block?

Regards,
Alan

---

### Post by EKa on 2006-03-05
Now I know that the problem is wlan related. Usb bluetooh stick does not cut the boot process.

Do you, or anyone, noticed that your wlan card sends packects but does not receive anything. Can this lead to a solution?

EKa

---

### Post by EKa on 2006-03-05
Good news! 

This is finally the first message using ubuntu and the troublesome usb wlan connection. I don't know how the problem should be solved by the book, but i suceeded using kind of experimental aprroach.
But, at least i can repeat what i did so far, and get the communication work.

It seems that to get *HOME*LINE usb stick working you need two starts of the system. First cold boot the system your usb unplugged and bypass the Hotplug problem. After that System / Log out / Restart the computer to get the wlan device on board.

---

