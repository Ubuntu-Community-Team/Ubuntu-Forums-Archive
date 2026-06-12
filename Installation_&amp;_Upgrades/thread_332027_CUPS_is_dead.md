---
title: "CUPS is dead"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by polc1410 on 2007-01-05
Sorry this is a duplicate post - this seems a better place to post though.

Problem1: I've killed CUPS. I have no idea what i've done but CUPS will not talk at all.

localhost:631 just fails to do anything (browser never shows a fail but never shows anything)

Code:

sudo /etc/init.d/cups restart

gives:
* Restarting Common Unix Printing System: cupsd [ ok ]

and
Code:

sudo /etc/init.d/cups status

gives:
Status of Common Unix Printing System: cupsd is running.

All programs hang when trying to print.

Launching GNOME or KDE print manager nearly kills the system

Not sure when the problem arose, or what I did (haven't printed for a few days.)

Recent upgrade of kernel so I've tried using older version - no different.

Anyone got any suggestions - cause I'm completely stuck

---

### Post by Sully on 2007-01-05
In Ubuntu, localhost:631 usually gets you a webpage, but the functionality has been removed by canonical.  So your situation is not normal; it seems like a permission problem to me.

What happens when you navigate System | Administration | Printing ?

---

### Post by polc1410 on 2007-01-07
Swirly circle (egg timer thing) and then nothing... ](*,)

---

### Post by SlayerMan on 2007-01-14
I've got the same problem on one of my machines.

In order to get CUPS to work again I did:

sudo apt-get remove cupsys
sudo rm -rf /etc/cups

and then:

sudo apt-get install cupsys

However, it seems that I fscked my CUPS installation with the above procedure. The package now doesn't install anymore as some post-install script fails. I'll post the output of apt-get later here.

Regards
Steffen

---

### Post by polc1410 on 2007-01-14
I decided to try something simillar to this myself yesterday. (I was alwasy told the windows 'uninstall' 'Reinstall' way of bug fixing doesn't usually work in linux)

I used Synaptic to do complete package removal and (not just remove) and then re-installed.  I took out everything begining CUPS on the list. (Watch it takes out a couple of desktop dependancies - which also need re-installed.)

I would guess your re-install problem MIGHT be that you installed CUPSYS but not some other CUPS program.  Then you deleted /etc/cups and possibly took out  the other cups programs which your package manager thinks are still there, so doesn't down load them as dependancies?

That said although cups is working and I can [http://localhost:631/](http://localhost:631/) (and it found all my old printers) I still can't print - but haven't tried tweaking yet!!

Calum

---

### Post by polc1410 on 2007-01-14
Can no longer localhost:631 BUT can print to my networked printer!  ](*,) 

You need to manually create:
 /etc/cups/cupsd.conf (if you've deleted the directory)

Mine has 3 things which don't seem normal compared to non ubuntu machines: the ports are set in the conf file and not a seperate file. (although I have that file too for good measure!)

Some of my security is probably weak.

And I am working to a remote CUPS so I have 'Server 192.168.1.50' which is the machine where the remote printer is in a file called /etc/cups/cups.d

Also check that you have /var/spool/cups/certs (and mine started looking for /var/run/cups/certs and there should be a symbolic link from /etc/cups/certs (the folder can be empty cups stores stuff there temporarily.)

cupsd.conf file below: ```
# Sample information for cupsd.conf
# This will allow anyone on your local network to cancel, hold, or release jobs without a password
# It will also allow people to browse jobs without a password
# You still need to be authenticated for other administrative tasks (adding a printer, for example)
Listen localhost:631
<Location />
Order Allow, Deny
Allow From All
</Location>

<Location /jobs>
AuthType None
AuthClass Anonymous

Order Allow,Deny
Allow From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

<Location /admin/?op=cancel-job>
AuthType None
Order Deny,Allow
Deny From all
Allow from 192.168.1.*
Allow From 127.0.0.1
</Location>

<Location /admin/?op=hold-job>
AuthType None
Order Deny,Allow
Deny From all
Allow from 192.168.1.*
Allow From 127.0.0.1
</Location>

<Location /admin/?op=release-job>
AuthType None
Order Deny,Allow
Deny From all
Allow from 192.168.1.*
Allow From 127.0.0.1
</Location>

<Location /admin>

AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1

</Location>

<Location /printers>
Order Allow,Deny
Allow From All
</Location>

```

Calum

---

