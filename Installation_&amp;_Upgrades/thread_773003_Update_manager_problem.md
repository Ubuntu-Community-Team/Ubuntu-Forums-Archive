---
title: "Update manager problem"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by fquist on 2008-04-28
I have received the following error while trying to open update-manager in order to upgrade to hardy.

'E:The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.'

A few days ago I had tried to install a driver for my Brother MFC4800 printer but was unsuccessful.  Apparently, update-manager is now hung up and won't let me do anything.  As soon as I close the error message window, update-manager closes.

How can I fix this problem so that I can upgrade to hardy?

---

### Post by Pumalite on 2008-04-28
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by fquist on 2008-04-28
I still get the message "E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it." and there is no further action.  Somehow I need to tell the update manager to quit trying to fix mfc4800lpr.

---

### Post by bapoumba on 2008-04-28
mfc4800lpr is not in the ubuntu repos. Where did you first install it from ?

---

### Post by fquist on 2008-04-28
I got it from the Brother (printers) website.  It is supposedly a linux driver for my Brother printer.  BTW, thanks for taking the time to help.  I'm new at this linux stuff.

---

