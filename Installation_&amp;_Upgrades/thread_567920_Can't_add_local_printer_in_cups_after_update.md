---
title: "Can't add local printer in cups after update"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by fahim on 2007-10-05
Hi @ all,

it seems to be a bug that I cann't add local printers in kubuntu 7.10.
Please check my screenshot:
[[IMG]http://img528.imageshack.us/img528/5716/snapshot1vc9.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=snapshot1vc9.jpg)

I already tried to uninstall/reinstall cupsys... does anybody know how to fix this?

Thank you very much

---

### Post by fahim on 2007-10-07
After the bigger update today it is still not possible to add local printer. I thin that is a bug or?

---

### Post by fahim on 2007-10-07
It was my fault... I did forget to put in the USB cable =)

---

### Post by corck on 2007-10-20
Hi,
After upgrading to Gutsy I have the problem that I can't add any local printers, its like in the picture above.
Had my brother hl-2030 printer (usb) working fine with feisty, but now I can't connect to it. I tried different solutions from other threads. 
lsusb lists the printer
Bus 002 Device 005: ID 04f9:0027 Brother Industries, Ltd
but still I cant select it.

I tried this thread
[http://ubuntuforums.org/showthread.php?t=123539](http://ubuntuforums.org/showthread.php?t=123539)
cups lists me the printer, but it says it can't connect to it, when I try to print a page

any ideas


HL2030 "Drucker ist nicht verbunden, erneuter Versuch in 30 Sekunden &#8230;" - cant connect, trying in 30seconds
Beschreibung: HL2030
Ort:
Marke und Modell: Brother HL2030 for CUPS
Druckerstatus: verarbeitend, Aufträge akzeptieren, publiziert. - accepting, publishing
Geräte URI: usb:/dev/usb/lp0

---

### Post by camiguin on 2007-11-05
I have the same problem with a Brother printer/scanner after Gutsy upgrade. The scanner part does work, and the printer did under Feisty, but when I try to install the printer now in Gutsy, the "local, usb," option is greyed out, like in the picture above. Also "lsusb" lists the printer, but "lpinfo -v" does not (I understand it should).  Anyone with ideas?

---

### Post by renatkh on 2008-01-28
Exactly the same problem, has anyone found fix for it? None of the solutions I tried so far worked.
The same printer works on another computer with the same version of kubuntu. I am very confused.

---

### Post by corck on 2008-01-28
Hi,
got it solved copying the cups config from the my laptop to my desktop pc. I guess it was some kind of security restriction. Haven't had a closer look what exactly caused the problem, however it fixed it.

---

### Post by renatkh on 2008-01-28
That fix did work!!!!!
Thank you.

---

### Post by salepa on 2008-01-29
Hi

I have maybe same problem...

I can't add my windows samba printer after update... I try reinstall cups, but still same.

local printer (serial, USB)
shared SMB printer (Windows)
serial (fax/modem printer)

all these is gray... what can I do? :confused:

---

### Post by candtalan on 2008-03-07
Add Printer - Local printer - greyed out

I have this problem now. I installed gutsy (NEW INSTALL, and immediately updated) on a friends toshiba laptop and even with the printer not connected at all, the add printer wizard for local printer is greyed out. 

I also have gutsy installed on my desktop (with no local printer at all, only network printers) and when I use the configuration facility, the local printer item is available and not greyed out!

Someone here says they copied the cups config file between computers and it worked.
I am out of my depth with that, but can try it. 

Question 1:
Is the file in question
/etc/cups/printers.config    ?

Question 2:
Can I take a copy of th efile from any other computer and use it? Are the entries in printers.config unique to the PC in any way?

(kubuntu gutsy, but ubuntu comments also appreciated)

tia

---

### Post by candtalan on 2008-03-08
bump.
Anyone please?

---

### Post by Wolf-Ekkehard on 2008-05-08
Have you gotten that resolved candtalan?  I ran into the same problem and fixed it for me, but haven't really figured out root cause (yet).  So rather than me posting a "quick fix", I'd prefer a proper solution from someone who knows what they are doing (in particular, somebody who knows how to hack a /etc/cups/cupsd.conf file).  If you still can't print, let me know and I'll post my suboptimal solution that works for me but might break something else for you.  If you meanwhile figured out how to fix it right, please let us know too.

---

### Post by candtalan on 2008-05-09
> **Wolf-Ekkehard said:**
> Have you gotten that resolved candtalan?
No I have not got it solved yet, and do not know really what to do about it. Fortunately, the friends laptop, and one of my own too, which have this problem are machines which currently do not have printing demands on them, but it could be a serious problem in future.

I would be very happy to try a (quick dirty?) fix if you have one.......?

---

### Post by Wolf-Ekkehard on 2008-05-09
k - here is what I have done:

I snooped around in /etc/cups and found a very minimalistic backup of cupsd.conf that something was kind enough to leave there.  I replaced a very elaborate cupsd.conf (written by Michael Goffioul, at least so it says in the header) with the minimalistic backup, and the grayed-out options magically re-appeared (I did a reboot - not sure whether it was needed).  Of course, the right thing to do is find out which line exactly grayed out the "Local printer (parallel, serial USB)" option in my KDE add printer wizard (some threads suggest it has something to do with permissions), but I didn't have time yet to do that as upgrading to Hardy took way too much of that already - still haven't gotten Samba file sharing to work :confused:.

Here are the active lines (I stripped empty lines and comments to reduce bandwidth) of my current /etc/cups/cupsd.conf that does the trick for me:

```

LogLevel warning
SystemGroup lpadmin
Listen localhost:631
Listen /var/run/cups/cups.sock
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  Order allow,deny
</Location>
<Location /admin>
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

Again, caveat emptor, it works for me, but I don't know why, and your mileage may vary...

---

### Post by petersk on 2008-07-12
I'm having the same problem with Hardy.  I appreciate you posting your cupsd.conf.  I think I might have an old backup of mine before the dist-upgrade (keeping my fingers crossed), that I might revert back to.  Nope.. don't have an old one.
  I noticed my /etc/cups directory has a cupsd.conf.feisty in there, so I'm going to see if reverting to that helps.
  well... it looked like the feisty one was just generic, so I used the one you posted here and it worked (after a /etc/init.d/cupsys restart); I have the ability to add a local printer again.
  Thanks!

Kurt

---

