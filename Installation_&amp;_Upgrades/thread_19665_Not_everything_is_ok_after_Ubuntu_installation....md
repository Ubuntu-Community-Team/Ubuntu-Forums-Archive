---
title: "Not everything is ok after Ubuntu installation..."
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by renevanh on 2005-03-13
I installed Ubuntu, and my first impression... isn't there yet, due to some problems.

When booting, I get a few errors:

First: "Unable to locate RSDP"
Ok.... so?!

After a minute or so, I get the next error for every single Harddisk (6 SCSI disks):
"Asking for cache data failed.
Assuming drive cache write through"

Anyway, it keeps going, and there are the next 2 errors already:

FATAL: error inserting PCIEHP (not sure about the H... I don't write really... readable )
and directly after that one:
FATAL: error inserting SHPCHP.
Both are follow by a long row of letters, codes and a path I think, but it goes to quick to write down.

Then all services are started, all drivers loaded... looks all good.
The 2 white flashes *FLASH FLASH*
Hmm...

And then the login screen...
Only unreadable and flashing constantly. Also double shown (with a black bar in the middle of the screen, splitting the screen vertical in 2 screens).

I don't know about the errors, but the flashing screen could have got something to do with the VGA adapter...
It's an onboard thing.

My system specs:

Dell PowerEdge 4200
Adaptec AIC78xx (Don't know exactly anymore)
2x PII 350MHz
512 MB RAM
6x SCSI HDD 18.1GB

What to do?!

Regards,

René

---

### Post by alastair on 2005-03-13
Relevant information for boot from :

/var/log/syslog

Let's see errors, messages etc.

lspci

To get your video card.

X config? Either :

/etc/X11/XF86Config  or
/etc/X11/xorg.conf

and any X logs :

/var/log/X*.0.log

---

### Post by Buffalo Soldier on 2005-03-13
[QUOTE=renevanh]

FATAL: error inserting PCIEHP (not sure about the H... I don't write really... readable )
and directly after that one:
FATAL: error inserting SHPCHP.
Both are follow by a long row of letters, codes and a path I think, but it goes to quick to write down.[/QUOTE]

This issue has been well documented. Try reading [http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror) 

[UbuntuGuide.org](http://ubuntuguide.org/) is a good place to go place to start looking for solution before posting questions.

And a quick search at [Google](http://www.google.com) gave a few intersting lead on your "Unable to locate RSDP" problem. One of it is [https://www.redhat.com/archives/fedora-list/2004-May/msg07682.html](https://www.redhat.com/archives/fedora-list/2004-May/msg07682.html)

---

### Post by renevanh on 2005-03-13
Thanks for the tips and the links.

I just got one more question... How do I get into the commandline, since I'm not really able to work with the graphical interface?!

Alt+F2 won't work...

I got myself into the commandline... just guess what I had to do, with al data on the screen repeated, cut off etc.
Now I'll try to solve this...

Regards,

René

---

### Post by alastair on 2005-03-13
CTRL+ALT+F1 etc. should work.

---

### Post by renevanh on 2005-03-13
The FATAL: error inserting.... errors are solved. I'm updating now (apt-get), but the video problem still exists...

How do I install a better driver, or get this away?
It's really no good to work with...

Regards,

René

---

