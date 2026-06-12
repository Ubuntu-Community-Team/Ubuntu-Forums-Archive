---
title: "old distro new software"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by pyrforos on 2012-11-27
Hi im using a netbook with ubuntu 11.10 but its main purpose is to read  pdfs , write in libre office, surf the web(simple things) and sometimes IM messaging.
I  dont have the time for an updrade but i ***must*** use the last version of lets say  pidgin or any other im  messenger (after the new updates of live messenger its impossible to login with an old version).
With 
```
sudo apt-get install pidgin
```
it can't be done because o have the old repositories. Do  you  have any ideas?

---

### Post by oldos2er on 2012-11-27
Look for a PPA for the updated software you need, or compile it from source.

---

### Post by ugm6hr on 2012-11-27
2.10.6 appears to be in the official Pidgin PPA for 11.10:
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)
[https://launchpad.net/~pidgin-developers/+archive/ppa/](https://launchpad.net/~pidgin-developers/+archive/ppa/)

Else, Pidgin 2.10.3 is available on getdeb for 11.10:
[http://www.getdeb.net/software/Pidgin](http://www.getdeb.net/software/Pidgin)

Not the very latest, but hopefully good enough for you.

Though, I would suggest considering an upgrade / fresh install to 12.04 in the coming months (be aware that 12.04 with Unity may be slow on an old Netbook - it was on mine - so consider other desktop environments)

---

### Post by Sunon on 2012-11-27
Straight from the pidgin site:



> Ubuntu ships Pidgin but does not update it after a release (except for security issues and high-severity bugs). For those users who desire new releases of Pidgin, we have packaged Pidgin in a PPA. If you encounter problems with these packages, try building from source and report the bug.

To setup the PPA, follow these steps:
  1. Click to download the Pidgin PPA package.
  2. Select Open with: and GDebi Package Installer. Click OK.
  3. Click Install Package.
  4. Click Close. Then close GDebi.

After doing this, check for and apply updates:
  1. Click System, point to Administration, and click Update Manager.
  2. Click Check.
  3. Click Install Updates.

Future Pidgin updates will show up in Update Manager along with the usual Ubuntu updates.

This PPA often lags behind the source releases a couple of days, so please be patient.

This PPA supports Ubuntu Lucid (10.04) and newer.


---

### Post by pyrforos on 2012-11-28
thanks guys! I will try it asap!

---

