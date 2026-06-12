---
title: "Dapper freezes with recent update"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by jmaslyn on 2006-07-19
Hey everyone,

I had an Ubuntu installation up and running perfectly since the beta release of Dapper. Within the last week (I'd guess about 3 or 4 days ago, possibly longer?) I downloaded an update and after rebooting as instructed, I logged in.

Everything appeared normal but after about a minute, everything aside from the mouse freezes. I cannot do anything, I have to do a hard shutdown to get out.

My only thought is that there might be a new network driver or something that is causing this because whenever I would attempt to make changes to my Linksys WUSB45G v.4 through Dapper's GUI, the same freezing problem occurred and I could only hard shutdown to escape.

Any thoughts or possible fixes? I am relatively new to Linux and specifically Ubuntu so any suggestions would be thoroughly appreciated.

Thanks!

---

### Post by mzoller on 2006-07-19
> **jmaslyn said:**
> Hey everyone,
My only thought is that there might be a new network driver or something that is causing this because whenever I would attempt to make changes to my Linksys WUSB45G v.4 through Dapper's GUI, the same freezing problem occurred and I could only hard shutdown to escape.


Well more infos or logfiles would be nice but I would start out like this: 

1.) I would avoid a GUI to configure the network card. Is it just the GUI that will lock the computer or will it lock after 10min no matter what?

2.) Open a terminal an read through what dmesg tells you. (You will have to use dmesg | more to see everything) If the GUI itself is not the problem you will most likely see whats wrong with your setup here. If you can't make sense of it post the relevant parts of it in the forum. 

3.) Configure your network card directly via the /etc/network/interfaces file.

---

### Post by jmaslyn on 2006-07-19
Thank you for your quick response!

The problem is no longer configuring my interface. I learned to do that through the config file and now have it setup and working.

The new problem is that with a recent update, approximately one minute after logging in my computer is completely unresponsive! I attributed this to the network interface because previously that could cause hanging too before I solved that issue.

Just a bit ago though, I booted, started Firefox and before FF even loaded, I lost the computer's response to my mouse but after a few seconds, FF loaded and pulled up Google.

To me, that says my network interface is fine and something else is causing the hang that got changed during the update. Right now, I am posting this from recovery mode and everything is respong appropriately.

I read that these sudden hangs would not be logged by Ubuntu. Is that true or is there still a log I should check?

---

### Post by mzoller on 2006-07-19
> **jmaslyn said:**
> 
I read that these sudden hangs would not be logged by Ubuntu. Is that true or is there still a log I should check?

I would always check /var/log/messages and /var/log/syslog first with any problem and then go from there.

1.) deactivate network card -> computer still freeze after reboot?
   -> yes: continue deactivating stuff unit you find it
   -> no: it is the network card. Unfortunatly wlan cards can be tricky
2.) after it freezes can you log in remote (via ssh)? That would enable you to work on the problem "as it is happening" 
3.) have top running in a terminal so you can see what the computer ist doing- maybe that way you can see a process/daemon that goes haywire freezing your computer. 

Michael

---

### Post by votresivain on 2006-07-19
Thanks again for a prompt reply.

Strangely enough, I unplugged my WLAN device per your instructions and it booted fine. I plugged it in after a minute or two, got full network connection and suffered no hang.

Something at boot just does NOT want to play nicely with my card.  Would either of the two logs you suggested show what is not playing nicely? I tried reading through each of them but it was such jibber-jabber to me and I had no luck finding anything.

At least now I am able to use my system and even have network/internet connection.  But I would like to know what's fighting with my card. Any other ideas, but please prioritize others' issues as I am now functional. Thanks so much for your attention!

---

### Post by votresivain on 2006-07-19
Apparently I am both jmaslyn and votresivain. Peculiar?

---

