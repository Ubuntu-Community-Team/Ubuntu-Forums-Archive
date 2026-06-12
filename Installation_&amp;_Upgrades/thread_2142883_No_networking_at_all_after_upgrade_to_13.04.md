---
title: "No networking at all after upgrade to 13.04"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by ianthealy on 2013-05-07
Tonight I upgraded to 13.04. I thought it went smoothly, but after the final reboot I had no networking ability at all. Everything in Network Manager is grayed out and I cannot create any new networks in it, whether wifi or ethernet. Wicd hangs and will not open. I can't figure out what to do through terminal, and it's tough because, well, I have no internet access now on the computer that needs it. I'm worried that the upgrade may have either not completed or gotten corrupted somehow, and I need to get networking back up so I can try to do a sudo update/upgrade and hopefully fix any errors that way.

I'm running a Dell Inspiron e1705 from the late mesozoic. It's been a pure Ubuntu box since 10.10. I'm not code savvy enough to know what to do next. Any help would be appreciated.

---

### Post by arrowcatcher on 2013-05-07
I had the same experience.  I worked around the problem by uninstalling 13.04 and then installing 12.10, which has better network support.  The 12.10 supported my Ralink WiFi but not the NIC, but that was OK.  Then I updated 12.10 to current with the Software Updater.  After that was done, then I upgraded to 13.04 which now works fine.  I figured other people would have the same problem I did.

---

### Post by ianthealy on 2013-05-07
I ran the software updater right before beginning the upgrade process, so I don't think that's the issue.

---

### Post by darkod on 2013-05-07
Is your wired adapter at least recognized in 13.04 live mode? You did try live mode before the upgrade, right? Always try it because it can show issues with hardware not working.

If the upgrade process is somehow stopped, there are commands to run to finish configuring the packages. But in your case if it finished successfully, it doesn't look like it will benefit from those commands.

---

### Post by ianthealy on 2013-05-07
I didn't do live mode. What are the commands to finish configuring packages? It seems to me that verifying a complete installation might be a good place to start.

---

### Post by darkod on 2013-05-07
Fixing any broken packages and finishing the configuration of all pending packages:
```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by ianthealy on 2013-05-07
Terminal was unresponsive. I am reinstalling 13.04 from a USB drive. If the problem disappears, I will chalk this up to an original upgrade issue and mark this as solved. 

If it remains, I'll report back.

---

### Post by ianthealy on 2013-05-07
The networking problem was resolved with the reinstallation of 13.04. I have a new problem, now, but I will start a new thread for that. Thanks for your help, everyone!

---

