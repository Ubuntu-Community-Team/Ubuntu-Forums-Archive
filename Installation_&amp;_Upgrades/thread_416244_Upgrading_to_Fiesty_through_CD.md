---
title: "Upgrading to Fiesty through CD"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by tuxy on 2007-04-20
Hi,

I am using Edgy Efty on my laptop and I want to upgrade it to Fiesty Fawn through CD. I have downloaded Fiesty ISO from the website and copied to a CD. How to upgrade from Edgy to Fiesty from this CD without any hassle. I don't want to install through CD by wiping off all the old data. I know this way.

I have tried adding the CD to sources.list through **apt-cdrom** add and disabled all the other 'web' links in /etc/apt/sources.list so that the upgrade takes only from the CD-ROM. Then I have done **apt-get update**. Then **sudo update-manager -c -d**, but nothing happens!!

---

### Post by shakyone on 2007-04-20
Below is my response a few minutes ago to another similar post.  I think you may find it helpful.

Shakyone.

[INDENT]After upgrade with alternate CD Update Manager asks for Install CD!
I had this same problem plaguing me. After updating from 6.10 to 7.04 via the alternate install CD let the system reboot. The "updates available" icon will show new stuff available. When you try to use the update manager it starts looking for the normal install CD rom.

Don't panic. There is an easy fix!

Just close that window, and open the System>Administration>Software Sources window.

The active tab should be: Ubuntu Software. At the bottom of the window is a check box next to "Cdrom with Ubuntu 7.04 'Feisty Fawn.'

Un-check this box.

Then open the System>Administration>Update Manager and check for updates. It should work now.

The same problem occurs with the upgrade from 6.06 to 6.10. I finally remembered it.

Hopefully it works for you. The above steps are much too complicated for me, and were not necessary.[/INDENT]

---

### Post by shakyone on 2007-04-20
Oops, forgot the other part of that post.  

Download and create the alternate CD.  Use it to update in place, and maintain all your settings and files.

While viewing your Ubuntu desktop, insert the alternate CD and wait for a window to open.  It should ask if you want to upgrade.  Select upgrade and you should be all set.  Then follow the previous post to fix your update manager.  If the window does not open, then open a terminal window and type:

gksu "sh /cdrom/cdromupgrade"

Per the recommended upgrade methods.

Shakyone.

---

### Post by shakyone on 2007-04-21
Oops, forgot the other part of that post.  Download and create the alternate CD.  

After you reboot normally just insert the CD and a window should open asking if you want to update.  Select the option and you should be all set.   If the window does not open, then open a terminal window and type: 

gksu "sh /cdrom/cdromupgrade"

Per the recommended upgrade methods.

After the upgrade follow my previous post. 

Shakyone.

---

