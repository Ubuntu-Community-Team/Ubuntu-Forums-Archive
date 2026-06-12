---
title: "Upgrade from 8.04 to 8.10 complete but stalls after logon"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by NotonyourNelly on 2008-10-31
Hi

I completed the upgrade OK. Rebooted and got to logon screen, entered login details, these were accepted, screen is usual pale brown, cursor is just an arrow, the hard drive works for a bit then stops. Nothing more happens just stays like this.

Any suggestions?

details: 32 bit ubuntu 8.04 to 8.10 on Thinkpad R31, encrypted harddrive upgraded online

---

### Post by ajackm on 2008-10-31
I have the same issue but on a desktop.

Ati Radeon 9800 Pro, with two Dell 1704FPV screens connected.

It looks like the Xorg.conf file is messed up as it has set itself up with vesa drivers, however changes just get reverted back.

Adam

---

### Post by slakkie on 2008-10-31
You guys might want to post your xorg logs:

/var/log/Xorg.0.log

---

### Post by NotonyourNelly on 2008-10-31
I'm a newbie more or less - can you guide me through how to retrieve this log?

---

### Post by billstei on 2008-10-31
I had this same thing after upgrading to Intrepid.  Try login to Gnome fail safe mode (pick this on the login screen menu), and turn off (some) startup programs in System->Preferences->Sessions->Startup Programs.  Wish I could tell you exactly what program is the problem, but I only know that (for me, YMMV) this allowed Gnome (non-fail safe) to startup normally.  In my case I had a lot of KDE applets that duplicated Gnome applet functionality that were not needed. 

Bill

---

### Post by Bevano on 2008-10-31
I had the same problem after upgrading. Selecting "Gnome" instead of "XClient Script" in GDM resolved it for me.

Now I did a clean installation and XClient Script works fine again. I don't know, if there is a big difference between both entries.

---

### Post by NotonyourNelly on 2008-10-31
Thank for the tips - though I decided that I am going to reformat hdd install 8.04 and wait for a few weeks and hope that 8.10 will settle down.

---

