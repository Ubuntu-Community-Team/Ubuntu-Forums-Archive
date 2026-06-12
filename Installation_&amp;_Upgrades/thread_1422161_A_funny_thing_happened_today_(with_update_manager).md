---
title: "A funny thing happened today (with update manager)"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by FokkerCharlie on 2010-03-05
Goooooood day to you!

Something a bit unusual has happened with my updates today.

The manager popped up in its usual, charming way, and offered me some updated packages, but also this message:

[B]Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.

This can be caused by:
etc etc[/B]

This is all very well, but I didn't want to upgrade to Lucid or anything just now.  Also, my firefox has changed into an iceweasel, and Cuil is now my default search engine!

Update-manager is also offering new linux-generic, linux-image-generic and linux-headers-generic packages, that it doesn't want to install.

What on earth is going on?

Bueller?

All input appreciated!

Charlie

Running Karmic 64 on my Intel C2D setup.

---

### Post by rcragun on 2010-03-05
I have the exact same issue.  I tried installing some of these and they wouldn't install.  In the process I got a message that I was trying to install updates that were not from Ubuntu.  I'm wondering if this is an indication of some sort of virus or hack?

FYI, I'm running 32-bit Ubuntu on an AMD 4-core processor.

---

### Post by rcragun on 2010-03-05
I just checked my repositories.  I had added a repository for some software I wanted to try out that I found on Debian's website.  Once I deleted that repository, the updates disappeared.  I'm wondering if there was some error with the depository.  

The repository I deleted was for flightgear via Debian.org:
[http://packages.debian.org/sid/i386/flightgear/download](http://packages.debian.org/sid/i386/flightgear/download)

Actual repository:
[ftp.us.debian.org/debian]("http://ftp.us.debian.org/debian/pool/main/f/flightgear/flightgear_1.9.1-1.1_i386.deb")

I'm wondering if there was some sort of mismatch here as Ubuntu is based on Debian.  Ergo, Synaptic thought updates for Debian were updates for Ubuntu, thus it wanted me to install them even though Ubuntu had not issued the updates.

Would you mind checking to see if this is your problem as well?

---

### Post by FokkerCharlie on 2010-03-05
Hi

Thanks for the responses.

Unfortunately, I seem to be having a different problem.  I don't have that repo in my system (although I DO have FlightGear installed), and have even disabled most of the extraneous other repos to no good effect.

Is it possible to see what repo a packaged marked as upgradeable is hosted in?  I can't see how, but it would be useful to know!

Charlie

---

### Post by FokkerCharlie on 2010-03-06
Update:

I allowed update manager to install the packages it was offering, and all seems well so far.  I still have Iceweasel in place of Firefox, but I can't tell the difference... so I guess that's OK.

Charlie

---

