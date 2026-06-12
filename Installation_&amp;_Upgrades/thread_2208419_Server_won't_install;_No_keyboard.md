---
title: "Server won't install; No keyboard"
date: 2014-02-28
forum: Installation &amp; Upgrades
---

### Post by Enforcer83 on 2014-02-28
I am attempting to install the 13.10 server installation.  I am, however, having a problem.  I get the initial request for language and then the menu.  I select "Install Ubuntu" and it gets to the next language selection screen.  It is at this point my keyboard stops working.  Keyboard is USB.  any suggestions on what I can try to do?  If you need more information about my rig,  I will provide it just let me know what you need to know.

---

### Post by tgalati4 on 2014-02-28
Sometimes you can set "Support Legacy USB Devices" in BIOS, otherwise track down a PS2 keyboard.  That assumes you have a PS2 port on your server.

---

### Post by Enforcer83 on 2014-02-28
Checked BIOS and it is set already.  I was hoping I wouln't have to track a PS2 keyboard.  Those things are ancient now days :???:

---

### Post by David_Etcell on 2014-03-03
I'm suffering the same issue! I am using a brand new HP Proliant N54L, which has NO ps/2 ports.
 
I am (trying) to install Ubuntu Server 13.10 from a USBstick also. The keyboards I have tried are both pretty standard Microsoft USB, but I have noticed the laser in an attached Microsoft wired mouse goes out at the same stage if I attach one. I even have spare PS/2 keyboards as well as PS/2 adapters laying about, but all are useless as the N54L doesnt have any PS/2 ports. 

I have enabled the amibios equivalent of legacy support, still does the same thing - though the keyboard works initially, so I'm not sure if it is actually halting the system at that second language screen or just turning off the USB ports.

I have tried moving the keyboard to all the different USB ports, but still no luck. Really hoping to get Ubuntu server to replace NAS4Free. I installed that last week and its just dreadful.

edit: Just tried with the keyboard going through a USB hub (I tried 2 differnt ones, one powered, one not) and while the Num lock was going off at the 'fail' point, it stays on if connected to either hub. The keyboard is still useless and unresponsive though.

edit2: seems fixed in the daily build from [http://cdimage.ubuntu.com/ubuntu-server/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/daily/current/)

---

### Post by Enforcer83 on 2014-03-03
I ended up finding a PS2 Keyboard from a local repair shop.  It worked fine.  I would still like it if someone from Canonical would speak up about this.  Could this be a potential bug?

---

### Post by David_Etcell on 2014-03-03
It almost certainly is a bug, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244176)

They do appear to have fixed it, at least in the 14.04 daily I grabbed...

---

