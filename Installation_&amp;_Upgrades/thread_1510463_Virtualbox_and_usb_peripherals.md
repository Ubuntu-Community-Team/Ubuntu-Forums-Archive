---
title: "Virtualbox and usb peripherals"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by dakkar9999 on 2010-06-15
I have Virtualbox installed from the Ubuntu repository.  As I just found out, I can't access any USB connected devices (printer, scanner...)  It seems I can get these USB peripherals to work by using a different Virtualbox repository.  Anyway to do this without loosing the OS installation that I have already setup in Virtualbox?

Thanks!

---

### Post by lechien73 on 2010-06-15
It's because you're downloading the OSE (Open Source Edition) from the repositories. Do a complete removal of this version, and then download the PUEL edition from:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

That should fix your problem. Even a complete removal will retain your virtual operating system settings. 

I have more information here:

[http://blog.mattrudge.net/2010/03/15/usb-devices-greyed-out-in-virtualbox/](http://blog.mattrudge.net/2010/03/15/usb-devices-greyed-out-in-virtualbox/)

---

### Post by fallenshadow on 2010-06-15
You should have the guest OS installed on a virtual harddrive inside the .virtualbox folder.

In your new virtualbox click on settings and in the hard drive option browse to where your virtual hard drive is.

---

### Post by dakkar9999 on 2010-06-16
Is there a repository I should add to get the updates and patch for this new Virtualbox PUEL?

Thanks!

---

### Post by dakkar9999 on 2010-06-17
Done!  Thanks for the help!

BTW, your blog seems quite interesting, so I subscribed to it!

---

### Post by dakkar9999 on 2010-06-18
Ok, small problem.  I see the usb device (Pentax DSMobile 600), but it is grayed out.  Is it because no driver is installed for it?  How do I gain control of it?

---

### Post by dakkar9999 on 2010-06-18
Never mind.  Found the answer.  Needed to add myself to the VBoxusers under System/Administration/Users and Group.

All is working!

---

