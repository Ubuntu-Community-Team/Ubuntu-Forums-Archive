---
title: "Software updater not reliable"
date: 2021-04-29
forum: Installation &amp; Upgrades
---

### Post by diablogamer on 2021-04-29
Hi,

It seems that the feature "software updater" is not reliable. Worst, it makes you think you're all good, but you're not....

OS Name: Ubuntu 20.04.2 LTS
OS Type: 64-bit
GNOME Version: 3.36.8
Windows system: X11

Today I had a notification saying that I have updates ready for the computer and I did them and rebooted just to be sure. I then add to do a check regarded Wine I was installing so I went to Terminal and did: sudo apt update. And guess what? I got a message saying things were still in need to be updated. I'm including a screen capture  of Terminal.

Also, I'm very new to Linux/Ubuntu. So How do I do the mentioned updates?

Thanks in advance for the help!
[ATTACH=CONFIG]288395[/ATTACH]

---

### Post by grahammechanical on 2021-04-29
What do you see when you run

```
sudo apt upgrade
```

Whether we use the terminal or Software Updater we will be notified of packages that can be upgraded. This will sometimes include packages that are being held back for some reason. So, we update/upgrade and think the job is done and then find that there are still packages needing to be updated. There is way to force the update of held back packages but it runs the risk of breaking parts of the system as the method used will upgrade those packages even if it means removing other packages that are causing conflict. Not recommended as we get to keep what we break.

Regards

---

### Post by Dennis N on 2021-04-29
Software Updater (a.k.a. "Update Manager") uses "Phased Updates" and has for quite a while. So it is not in agreement with apt regarding what is available for update at that moment.

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

However, the plan is to also use phased updates with apt starting with 21.04 release!

---

### Post by bkline on 2021-05-03
In answer to the O.P.'s second question -- you might want to take a look at [https://linuxhint.com/update_all_packages_ubuntu/](https://linuxhint.com/update_all_packages_ubuntu/).

---

