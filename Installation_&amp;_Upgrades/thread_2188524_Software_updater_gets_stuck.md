---
title: "Software updater gets stuck"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by PaulBx on 2013-11-17
I updated this laptop after a month or two without updates so there was a lot to do. It hung in the middle for some unknown reason so I killed it. Now when I run the updater it always gets stuck in "Configuring update-notifier-common". If I try to stop that it says "Cancelling" but never finishes, so I close the window. Then I have to reboot to try running updater again.

Like a fool I neglected my first rule of always doing a backup before any updates, so I'm not sure what to do now. The system seems to work otherwise. Any suggestions?

---

### Post by Rex Bouwense on 2013-11-17
Use apt-get to update your system.
```
sudo apt-get update && sudo apt-get upgrade
```
That will tell you exactly what is going to be updated.  Occasionally there is a very long update.  For instance when the Firefox flash is updated.
If you think there is a problem, back up your data before proceeding.

---

### Post by PaulBx on 2013-11-17
Partway through it gave me, 
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

I did that and now all is well. Thanks for the tip; looks like a better way to do it anyway since you can see what is going on.

---

### Post by Rex Bouwense on 2013-11-18
Great.  Glad to be of assistance.  Being able to see what is going on (among other things) is precisely why many people use that method.

---

