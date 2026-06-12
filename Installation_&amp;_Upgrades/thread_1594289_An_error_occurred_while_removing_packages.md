---
title: "An error occurred while removing packages"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Leap Frog on 2010-10-12
During a fresh install of 10.10 with no existing installations.  

Error message is:

"E: Problem executing scripts Dpkg: post-invoke 'if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [-e /var/lib/update-notifier/updates-available]; then echo > /var/lib/updates-notifier; fi',
E: Sub-process returned an error code

The following packages are in a broken state:



This may be due to using an old installer image, or it may be due to a bug in some of the packages listed above....

Responding "OK" to the prompt results in:

INSTALLER CRASHED

We're sorry, the installer crashed.  Please file a new bug report .....

******************
Reporting user comments
1) There are no packages listed above
2) Both install options (update packages, restricted codecs) selected  
3) ISO image verified
4) Live CD runs fine
5) System will not boot 

I've tried this install multiple times, with and without previously existing installations of 10.10 and 10.04, always getting this error.

---

### Post by mikechant on 2010-10-12
I think I saw a recommendation somewhere *not* to install updates during the initial install because this can cause problems - apply all updates once the install is complete instead.
Sorry I can't be more specific, was a year or two ago ago Iread this and I can't find anything with search.

---

### Post by Leap Frog on 2010-10-12
OK, I unchecked the "update packages" and "restricted codec" options and tried again.

Now the error message is:

Bootloader install failed.
Sorry, an error occurred and it was not possible to install the bootloader at the specified location.

How would you like to proceed?

******************
Reporting user comments
I tried choose a different device - there were three options listed -- sda, sdb, and sdb1.  10.10 is being installed on sdb1.  All three options return the same error message.  sda and sdb are both type MBR.  sda is empty, unformatted.  sdb has a single ext4 partition for 10.10 with a second partition for swap, both created by the installer.

---

### Post by Leap Frog on 2010-10-12
I tried again, this time skipping the bootloader installation and then using the Live CD to manually install GRUB to the MBR of sda, pointing to the /boot file on the 10.10 partition on sdb1.  That worked OK.

This seems awful messy and out of the norm that we've come to expect for Ubuntu installers.

---

