---
title: "Upgrade to Ubuntu 22 lts didn't work - crashed my system"
date: 2022-04-21
forum: Installation &amp; Upgrades
---

### Post by jmichaels29 on 2022-04-21
I used terminal to force an update from 20.04 lts to the new lts (22.04)

At the end it told me to restart the computer.

It said  something was still active and wouldn't restart or allow me to authenticate and restart.  I let it sit there for a half hour, then...

I eventually turned the computer off and tried to restart, but it wouldn't boot up 

I had to reinstall Ubuntu 20.04 and my files that took hours.

So, now I'm hesitant to upgrade even graphically when software update tells me it's available.

---

### Post by jerry47 on 2022-04-21
Sorry your upgrade went bad. I try to avoid upgrades but I have successfully done it. My test system has 10 SSD's. So I dedicated one to 22.04 a week ago. Found a couple of small things but overall it seems to work fine. I would get another SSD for your computer and swap it out to try 22.04. I keep all my files on a NAS. If something goes wrong, its the time to set up a new system. Running 20.04 on test machine and my second PC. My wifes machine is running 20.04. Have no plans to upgrade at this juncture. I have her files backed up on the NAS as well.

---

### Post by jmichaels29 on 2022-04-24
How do I telll Ubuntu 20 to update to 22 lts using the GUI.  When I tried to tell it upgrade with the terminal, it didn't go well.

---

### Post by QIII on 2022-04-24
> ... didn't go well ... gives us precious little diagnostic information.  

What happened?  It is not likely that any GUI process would fare any better than a terminal session.

---

### Post by jmichaels29 on 2022-04-24
> **QIII said:**
> gives us precious little diagnostic information.  

What happened?  It is not likely that any GUI process would fare any better than a terminal session.

[URL="https://ubuntuforums.org/showthread.php?t=2474065"]https://ubuntuforums.org/showthread.php?t=2474065

[/URL]p.s. I'm curious why neither of my computers asks if I want to upgrade to the latest lts version, even though I have told it to notify me of latest lts version in setiings (?))

---

### Post by QIII on 2022-04-24
Threads merged.  

If you don't get a response to a thread in about 12 hours, please do not start a new thread.  That just spreads things out and waters down the community's ability to help.

You may bring your thread back to the top of the heap by simply adding a new post with the word "bump".

---

### Post by grahammechanical on 2022-04-24
This thread has relevant information about this situation.

[https://ubuntuforums.org/showthread.php?t=2474227](https://ubuntuforums.org/showthread.php?t=2474227)

Basically, upgrading to 22.04 by GUI is not available and as experienced in the present thread upgrading by the terminal is not advised at the present time.

Regards

---

### Post by jmichaels29 on 2022-04-24
> **grahammechanical said:**
> This thread has relevant information about this situation.

[https://ubuntuforums.org/showthread.php?t=2474227](https://ubuntuforums.org/showthread.php?t=2474227)

Basically, upgrading to 22.04 by GUI is not available and as experienced in the present thread upgrading by the terminal is not advised at the present time.

Regards

Yea, I went through the entire upgrade process using terminal.  At the end it said to restart at my convenience.  But it wouldn't liet me restart.  It kept saying a task was running and asked for my password to authenticate to force a restart.  So I thought I'd let it sit there a while before trying to restart again.  Let it sit there 30 minute, hoping whatever task was running would finish.  It never did finish and kept asking for password authentification to restart.  But it never would accept my password attempt to restart.  So I shut the computer down manually & tried to boot up.  That's when I experienced a situation where it simply wouldn't boot.  

I'm curious if many others have experienced this trying to upgrade....

---

### Post by Rex Bouwense on 2022-04-26
Upgrades from one LTS to the next should not be attempted until the first point release.  If you want the new version quicker it is recommended that you do a fresh install after backing up your data.  A fresh install rarely takes more than 12-15 minutes.

---

### Post by jmichaels29 on 2022-04-26
> **Rex Bouwense said:**
> Upgrades from one LTS to the next should not be attempted until the first point release.  If you want the new version quicker it is recommended that you do a fresh install after backing up your data.  A fresh install rarely takes more than 12-15 minutes.

Please tell me what a "first point release" is.

Is this it:  [https://en.wikipedia.org/wiki/Point_release](https://en.wikipedia.org/wiki/Point_release)
Or in other words, after the first bug/security updates are released  (?)

---

### Post by Rex Bouwense on 2022-04-26
The first point release for Ubuntu 22.04 would be Ubuntu 22.04.1 and it should be released in August.  In answer to your question, yes.

---

