---
title: "Possible causes for draggy Updates?"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2016-12-03
Recently, I noticed that the Reload function of Synaptic Package Manager has been dragging immediately after downloading the first two InRelease files from Launchpad.net and Canonical.com, both downloaded files being listed as zero size; the delay runs up to two minutes before the balance of the libraries, all of which have nonzero size, are downloaded and processed at the rapidity I expect.  Is there a possible problem in APT that would trigger this sort of misbehavior?  (I presume the Synaptic laggy window reflects some sort of drag in the Update function of APT; more likely a problem with the APT configuration than a bug in the supporting library files /usr/lib/apt/*.)

---

### Post by TheFu on 2016-12-04
I would begin by checking DNS performance.  I've heard of some countries picking up the wrong redirect. Might be best to manual specify the exact repo location or even a nearby country.

Is it just synaptic or do apt, apt-get, aptitude show the same issues?

---

### Post by oldos2er on 2016-12-04
Are you using a mirror? You could try switching to the main server to see if it's faster.

---

### Post by bcschmerker on 2016-12-05
Same issue encountered with sudo apt update and sudo apt-get update, always GETting the first two InRelease files.  Things fast afterwards.  Mirrors as well as Canonical servers.  Suspect a misconfiguration of files to GET in one of the etc's appropriate to APT.

**Update:**  From the Software Updater app, the main lags are "waiting" and "querying software sources"; the "downloading from..." is consistent from file to file at each server.

---

### Post by bcschmerker on 2016-12-11
**Update 2:**  During a routine Check for Updates via Synaptic Package Manager, Deb complined of duplicate Entries in /etc/apt/sources.list.  After printing out sources.list and sources.list.save, I used sudo gedit /etc/apt/sources.list to execute fixes, directing APT to download from archive.ubuntu.com and archive.canonical.com, with download.ebz.epson.com on standby in case of new drivers from Seiko Epson Corp.  Might be a few days to test overall performance before a RESOLVED declaration....

---

### Post by TheFu on 2016-12-12
Be VERY CAREFUL using *sudo gedit*. This could cause unexpected issues with your GUI programs in the future.  A better way is to use **sudoedit**.  You can use gedit as the editor, if you like by setting the EDITOR environment variable in your ~/.bashrc or ~/.profile.  Just be aware that if you ever need to use an editor without running a GUI, like over an ssh connection, gedit most likely won't work.

---

### Post by bcschmerker on 2016-12-22
**Update:**  No further problems with downloads encountered.  Considering the draggy-download issue RESOLVED FIXED.

---

