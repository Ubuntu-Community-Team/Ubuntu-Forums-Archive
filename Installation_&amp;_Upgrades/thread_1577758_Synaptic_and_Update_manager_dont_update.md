---
title: "Synaptic and Update manager dont update"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by Kurtius on 2010-09-19
When I try to update though package manager I get a message saying:
An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.'

Synaptic also comes up with an error:

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

If I try to update through the Terminal using 'apt-get update' I get 
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

Ubuntu software centre doesn't display any software either if I search for it i.e search 'wine' and it says 0 items are available and if i click the individual categories the same thing happens . Yet strangely it says 23114 items are available...

I'm using Ubuntu Netbook remix and its not a hardisk space issue I have a 250gb hard drive which is almost totally empty. Thanks in advance and I'm clearly a total n00b so be nice :P

---

### Post by a_posse_ad_esse on 2010-09-19
Minor point- are you running apt-get using sudo?

---

### Post by Kurtius on 2010-09-19
Yeah I use 'Sudo apt-get update'
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
loading package lists... 30%
and then 
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

---

### Post by a_posse_ad_esse on 2010-09-19
I'm not sure if this is a hardware error or not based on the I/O error.  You might want to download the UBCD ([http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)) and use the appropriate diagnostic tool to make sure that your drive is working properly.

---

### Post by tesaba on 2010-10-31
i get these same error's all the time. Am going to try your advice with the UBCD. Hope it works. Thanks.:(

---

