---
title: "Karmic Gnome vs KDE"
date: 2009-05-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by freeman2000 on 2009-05-15
I'm running a dual Karmic, both Ubuntu (gnome) and Kubuntu (kde) within the same partition on my HP laptop.  Within gnome everything works perfectly (so far).  It automatically recognizes everything I have connected - USB modem, printer, webcam, etc. and all works well.  

However, when I boot up into KDE the fun begins.  I'm getting some conflicting info.  The "Device Notifier" on the panel/tray (looks like a monitor with a USB symbol in it) states that I have NO devices connected, even though the USB modem, printer, and webcam are all connected.  Also "Network Management" popup states that ttyUSB0 (USB modem) is not connected, and the "Network" icon on the panel/tray states that the Ovation U720/MCD3000 is disconnected. Also, everytime I leave KDE to go back into gnome, it "mutes" my sound, so that once gnome installs, I have to "un-mute" my sound and restart gnome to get sound. 

When I go into "lsusb" it shows the USB modem (Ovation U720/MCD3000), the printer, and the webcam  all being connected.  The printer and the webcam both work.  However, I can't get the modem working in KDE even though it works great in gnome.  Any ideas?


[edit]  My search/research has come up empty.  Maybe I'm not using the proper keywords.  Thanks.

---

### Post by taavikko on 2009-05-15
Device notifier is meant for mass-storage devices, AFAIK.

There's a bug in network-plasmoid that disables the use of 3G modems
[https://bugs.launchpad.net/bugs/334122](https://bugs.launchpad.net/bugs/334122)

---

### Post by krazyd on 2009-05-15
Give it a chance.. KDE 4.3 is in beta and Karmic is in alpha! ;)

---

### Post by Reiger on 2009-05-15
KDE 4.3 isn't even fully packaged yet... There are still packaging issues like certain packages failing to be properly configured requiring help from dpkg -i --force-overwrite if you want them. :p

---

### Post by freeman2000 on 2009-05-16
Heh, what fun!!!  Trying to mate a beta with an alpha!  According to the link, I guess KDE is having problems with USB modems, or is it the other way around?  I will / I must persist though.  I now can get a connection for a nanosecond!

I went into "wvdial" from the Kontrol panel (KDE version of terminal) and got the message that there were no valid phone #, no valid login name, and no valid password.  I then went into "gksu gedit /etc/wvdial.conf" to check, and there were semi-colons at the start of those 3 lines.  I removed those, saved it, and that seems to give me a nanosecond of connection.  In Network Management (the little black & white phone in the tray), it shows "Connecting In:0 Out:0 Disconnecting".  

I then go back into Kontrol again and type in "wvdial" again.  More fun with humor this time.  I get the message:  "Unable to run /usr/sbin/pppd.  Check permissions or specify a 'PPPD Path' option in wvdial.conf. Don't know what to do!  Starting pppd and hoping for the best!"  Now somebody had a sense of humor when they input that error message!  

So I input "gedit /etc/wvdial.conf" and found that the line "New PPPD = yes" is there as it should be.  I then went into Dolphin and found that "pppd" is in fact where it should be at /usr/sbin/pppd and that it is a 271k executable.  

I have some progress, but I'm still stumped.  Maybe I will have to wait this one out for the USB bug in the beta/alpha world of *buntu. But then with this new info, maybe someone will have some ideas.  Thanks.

---

### Post by taavikko on 2009-05-16
> **freeman2000 said:**
> Heh, what fun!!!  Trying to mate a beta with an alpha!  According to the link, I guess KDE is having problems with USB modems, or is it the other way around?  I will / I must persist though.  I now can get a connection for a nanosecond!

I went into "wvdial" from the Kontrol panel (KDE version of terminal) and got the message that there were no valid phone #, no valid login name, and no valid password.  I then went into "gksu gedit /etc/wvdial.conf" to check, and there were semi-colons at the start of those 3 lines.  I removed those, saved it, and that seems to give me a nanosecond of connection.  In Network Management (the little black & white phone in the tray), it shows "Connecting In:0 Out:0 Disconnecting".  

I then go back into Kontrol again and type in "wvdial" again.  More fun with humor this time.  I get the message:  "Unable to run /usr/sbin/pppd.  Check permissions or specify a 'PPPD Path' option in wvdial.conf. Don't know what to do!  Starting pppd and hoping for the best!"  Now somebody had a sense of humor when they input that error message!  

So I input "gedit /etc/wvdial.conf" and found that the line "New PPPD = yes" is there as it should be.  I then went into Dolphin and found that "pppd" is in fact where it should be at /usr/sbin/pppd and that it is a 271k executable.  

I have some progress, but I'm still stumped.  Maybe I will have to wait this one out for the USB bug in the beta/alpha world of *buntu. But then with this new info, maybe someone will have some ideas.  Thanks.


If you have trouble with network-plasmoid, wvdial and 3G modems, please start a new thread. Paste the content of /etc/wvdial.conf to there.

---

