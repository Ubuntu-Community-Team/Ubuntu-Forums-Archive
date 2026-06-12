---
title: "[SOLVED] Virtualbox won't start"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bcasanov on 2008-10-27
After installing Ubuntu Intrepid, I ran the Cruft Remover, which wiped out some third-party applications I had installed, including Opera and Virtualbox (non-Open-source direct from the Virtualbox repository).  I had to reinstall Opera.  Now, I just reinstalled Virtualbox, this time the Open-source edition, but when I go to its icon in the Applications menu and click on it, it won't open.  When I put "virtualbox" in the terminal, I get: "Could not find VirtualBox installation. Please reinstall."

What could possibly be going wrong?

---

### Post by bcasanov on 2008-10-27
I uninstalled Virtualbox and then reinstalled it, but to no avail.  I still have the same problem.

---

### Post by roosta69 on 2008-10-27
I was just having this issue and I uninstalled virtualbox, installed dkms, then reinstalled virtualbox and it worked fine.

---

### Post by bcasanov on 2008-10-27
dkms for me is already installed, and I again reinstalled Virtualbox just to make sure, but it was a no-go for me.

---

### Post by diablo75 on 2008-10-28
I am also having problems with Virtualbox and have started a thread about my issue here:  [http://ubuntuforums.org/showthread.php?t=961053](http://ubuntuforums.org/showthread.php?t=961053)

Is my problem similar to the issues you were having when you tried to run VB on 8.10 RC?

---

### Post by bcasanov on 2008-10-28
Well, I don't exactly get the error you get when you try to start Virtualbox.  When I click on the Virtualbox icon, nothing happens.

---

### Post by xeriouxi on 2008-10-28
> **bcasanov said:**
> Well, I don't exactly get the error you get when you try to start Virtualbox.  When I click on the Virtualbox icon, nothing happens.

I know there was an update to Virtualbox the other day which moved the icon from System Tools to Accessories. Maybe that update might not have worked correctly perhaps? Just a wild guess and will probably not be correct but it's all I can think of! =)

---

### Post by bcasanov on 2008-10-28
I upgraded to the Release Candidate, so I guess the update was already implemented.  I'm not sure the change in location on the menu would cause Virtualbox to not open.

---

### Post by bcasanov on 2008-10-28
Does anyone else know what could be causing Virtualbox to not even open?

---

### Post by adder1972 on 2008-10-28
Hi guys,

I had the same problem.  Upgraded to VirtualBox 2.0.4.  Everything OK now.

---

### Post by risu_vk on 2008-10-28
remove virtual box then delete /home/username/.VirtualBox

and try installing again.

---

### Post by risu_vk on 2008-10-28
type VirtualBox in a terminal and check the messages..

---

### Post by bcasanov on 2008-10-28
> **adder1972 said:**
> Hi guys,

I had the same problem.  Upgraded to VirtualBox 2.0.4.  Everything OK now.

The version in the Intrepid repository is 2.0.4.  

> **risu_vk said:**
> remove virtual box then delete /home/username/.VirtualBox

and try installing again.

I have my XP installation in the folder, along with the snapshots and all my configurations.  Why would it take deleting the .VirtualBox folder to get VirtualBox to start?

When I enter "VirtualBox" in the terminal, the result is: "Could not find VirtualBox installation. Please reinstall."

---

### Post by adder1972 on 2008-10-28
Hi,
I didn't use the OpenSource version, but used the closed source one from the Sun-site.

---

### Post by bcasanov on 2008-10-28
In the Virtualbox downloads page, [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads), there is no download link for Ubuntu Intrepid.  Should I download the version for Hardy?

---

### Post by Fire_Chief on 2008-10-28
> **bcasanov said:**
> After installing Ubuntu Intrepid, I ran the Cruft Remover, which wiped out some third-party applications I had installed, including Opera and Virtualbox (non-Open-source direct from the Virtualbox repository).  I had to reinstall Opera.  Now, I just reinstalled Virtualbox, **this time the Open-source edition,** but when I go to its icon in the Applications menu and click on it, it won't open.  When I put "virtualbox" in the terminal, I get: "Could not find VirtualBox installation. Please reinstall."

What could possibly be going wrong?

Why did you change from the closed version from Sun to the Open Source edition? There are some components that are left out of the open source edition. Did you try re-installing the closed source version to see if Vbox would startup then?

Cheers!

---

### Post by bcasanov on 2008-10-28
Hey, I finally got it to work!  I installed the Hardy Heron version, and wuala...I got it VirtualBox to open!  Thank you guys so much for your help and considerate support.  I'll mark this thread as solved.

---

