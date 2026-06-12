---
title: "Update Issues in Hardy Heron"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by jb1789 on 2008-04-24
Since upgrading to 8.04, the update manager has found over 200 updates.  When I actually try to update, the update manager fails with an error that it is unable to get an exclusive lock because another package manager is already running.  Synaptic, Add/Remove, and apt-get all fail in a similar manner.

Also, Xorg is constantly using almost 50% of my CPU, which has never happened before, and there is also constant network traffic at about 500 KB/s when I am not doing anything.

I have upgraded via the Alternate Install CD method since I have had more luck with this than with a network upgrade in the past.

Does anyone know what is going on with the package managers and Xorg?

Thanks in advance.

---

### Post by jb1789 on 2008-04-24
Apparently the System Monitor uses a lot of CPU in the form of Xorg.  When I close the System Monitor and used top to monitor CPU usage, everything was fine.

On the other hand, I am still at a loss as to why all forms of updating fail.  Also, I have absolutely no idea what is using the network connection so much.  Over the past 45 minutes or so, there has been almost 2 Gigabytes of traffic, but when I turn off networking, nothing crashes, so apparently nothing "important" is being sent over the network.

I've never had these sorts of issues with Ubuntu before which is rather interesting.  On a lighter note, the sound drivers appear to be working much better than they did in Gutsy.

---

### Post by Peter09 on 2008-04-24
The update process is very slow at the moment. Are you sure you do not have an update manager running somewhere on your machine?

PC

---

### Post by jb1789 on 2008-04-24
There are no other package/update managers running.  I just killed the one instance of Update Manager and restarted it,  but the same error occurred.  Is there any way in which I could update from the install disk?

Also, do you have any idea what is going on with the network connections?

Thanks again,
JB

---

### Post by Peter09 on 2008-04-24
Try rebooting, it might clear any lock files that have been left open.

PC

---

### Post by jb1789 on 2008-04-24
I rebooted and attempted to update again.  The update should now work (thank you), but it wants to update from the 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)' cd.  I installed from the alternate cd, which has a different name, so I am assuming that the disk listed above is the desktop install disk.  Is that correct?

---

### Post by Haluci on 2008-04-24
> **jb1789 said:**
> I rebooted and attempted to update again.  The update should now work (thank you), but it wants to update from the 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)' cd.  I installed from the alternate cd, which has a different name, so I am assuming that the disk listed above is the desktop install disk.  Is that correct?

Yes.  Just burn yourself a disk and it should work just fine.

---

### Post by jb1789 on 2008-04-24
Thank you.  Would you happen to know why so much data is being transferred over my network adapters when I am not downloading anything?

---

### Post by Peter09 on 2008-04-24
you should go to Administration->software sources. Tick all except source code and CD. Let the upgrade come across the internet so you will get the latest, and also future upgrades.

You should not need your CD for upgrades unless you have no internet.

PC

---

### Post by jb1789 on 2008-04-24
Thank you for all of your help.  I am updating everything now.  Also, the weird networking stuff seems to have fixed itself.

---

