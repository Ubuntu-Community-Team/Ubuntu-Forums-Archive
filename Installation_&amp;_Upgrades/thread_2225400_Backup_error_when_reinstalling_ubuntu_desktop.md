---
title: "Backup error when reinstalling ubuntu desktop"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by Rainshoots on 2014-05-21
After failing to upgrade to Trusty from Saucy, I decided to do a fresh install and back up by files and programs by following the instructions given on this website. 

[http://www.matthartley.com/how-to-backup-your-ubuntu-software/](http://www.matthartley.com/how-to-backup-your-ubuntu-software/)

The clean install went smoothly, but I could not get my home directory back. When I try to restore my last backup using the "Backups" program (Deja Dup?), I run into the following error: 

> Invalid data - SHA1 hash mismatch for file:
 duplicity-inc.20140424T053227Z.to.20140508T021212Z.vol51.difftar.gz
 Calculated hash: e28fd59e70f82bb126eb76b0c76b807cc03f5b27
 Manifest hash: 38e4dd60b6aac680493f03d8c8a3145474d45907

How can I get back the files in my old home folder?

---

### Post by Rainshoots on 2014-05-21
The latest backup was done on Cinnamon desktop and not Unity. Do I have to manually install cinnamon and switch to it before restoring my files?

---

### Post by Rainshoots on 2014-05-21
When I run synaptic manager to restore my programs, it gave the following error: 

> Could not apply changes!
Fix broken packages first.

When I try using the 'fix broken packages' function in synaptic, the following error message is shown: 

> E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


Upon reloading the package information, I get the following information:

> 45038 packages listed, 1807 installed, 3 broken. 1257 to install or upgrade, 9 to remove; 3290 mb will be used. 

The broken packages are: 

> cinnamon
libmuffin0
lsb-printing

Unmarking the following packages allowed me to kick off the restoration process. 

Prior to this, when I tried installing cinnamon manually, I get back the same broken packages error on terminal.

---

### Post by Rainshoots on 2014-05-21
This is the error message I get when I try to manually install cinnamon: 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: gir1.2-muffin-3.0 but it is not going to be installed
            Depends: libcogl-pango12 (>= 1.7.4) but it is not installable
            Depends: libcogl12 (>= 1.9.6) but it is not installable
            Depends: libmuffin0 but it is not going to be installed
            Recommends: nemo but it is not going to be installed
            Recommends: cinnamon-screensaver but it is not going to be installed
            Recommends: gir1.2-cjsdbus-1.0 but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by Rainshoots on 2014-05-21
Okay, I managed to install cinnamon. But restoring my files on cinnamon gave back pretty much the same errors. 

Another persistent problem is that I cannot get my Zotero database back working. The error message is below. 

> Database upgrade error

[Exception... "Component returned failure code: 0x8052000b (NS_ERROR_FILE_CORRUPTED) [mozIStorageConnection.executeSimpleSQL]"  nsresult: "0x8052000b (NS_ERROR_FILE_CORRUPTED)"  location: "JS frame :: chrome://zotero/content/xpcom/db.js :: Zotero.DBConnection.prototype.query :: line 149"  data: no] [QUERY: DELETE FROM itemTypeFieldsCombined] [ERROR: database disk image is malformed]


---

### Post by Rainshoots on 2014-05-21
I wasn't able to fall back on a previous backup because one tar.gz file was missing.

---

