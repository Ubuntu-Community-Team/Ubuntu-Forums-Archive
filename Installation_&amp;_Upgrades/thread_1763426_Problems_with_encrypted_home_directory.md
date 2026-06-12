---
title: "Problems with encrypted home directory"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by memilanuk on 2011-05-20
I have been running various releases of Ubuntu for a while now, usually either in VirtualBox on my Macbook or on a small home file server.  Finally with a new (to me) HP laptop available I opted to set up a dual boot system for the first time in a long, long time.  I thought being a laptop, the option for encrypted home directory sound like not such a bad idea...

Everything went fairly smoothly... except the suspend/hibernate function kept locking up the system.  I'd get a mouse cursor, but no log-in window to get back into my desktop.  Had to either do a hard reset or open a virtual terminal to shutdown the system gracefully.  Finally just turned off the screensaver and disabled hibernate/suspend functions and things worked fine there after.

Until I wanted to set up LAMP w/ per-user home directories so I could do a little web development.  Did everything by the book, but still got 403 errors.  Did a bit of digging around, and found a lot of people had the same issues, and while there were work-arounds I kind of gave up in disgust when I started finding threads that stated that *both* problems were basically directly attributable to the encrypted user home directory interfering with system daemon access to files in the user home.

Neither of these seem to be exactly new problems w/ 11.04... I'm kind of surprised that neither the Ubuntu install guide nor the on-screen guide/hints during install give any *hint* of what kind of problems may lay in store i.e. 'this option may not be suitable if you intend to...'.

Seems a little misleading/irresponsible on Ubuntu's part, at least in my mind.  The rest of the distro seems great, and I really like having my regular wi-fi, my mobile broad-band cell modem, and the web-cam on the laptop all 'just work' without having to **** around with them for hours/days - things I've been waiting literally *years* for.  This just seems like a booby-trap that should have been a little better documented.

Monte

---

