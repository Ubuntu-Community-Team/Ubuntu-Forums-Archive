---
title: "Cancelled wubi install, now can't reinstall"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by deangl on 2010-07-27
Attempting to install Ubuntu 10.04 Netbook from USB flash drive.  (as a side note, the live USB boot seems to work fine on this netbook, but all four primary partitions are in use and I thought I would use wubi as a quick way to get 10.04 installed on this netbook).

Started wubi install on a new HP 210 Netbook (running Win7Starter) by following instructions in the wiki: [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")
Wubi displayed dialog with the 3 buttons.  I selected install.
A few minutes later, wubi started downloading the iso file.  My connection is not very fast, and since I already had it on a local system, I cancelled the wubi install.  I transferred the iso to the same folder as wubi (my flash drive) and started the wubi again.
Now there are only 2 buttons on the dialog ("Demo and full installation", and "Learn more").  I am not sure what happen to the install in windows choice?  I followed uninstall procedures in wiki, and tried wubi again, to no avail...
Can someone tell me how to get back to a wubi dialog that has the "install" in windows option available again?
Are there wubi command line options that I could use here to force desired behavior?  How do I find out what all the command line options are on wubi?

Any help would be greatly appreciated.
Thanks,
Dale    :(:)

---

### Post by deangl on 2010-07-27
.

---

### Post by bcbc on 2010-07-28
Place wubi.exe in a folder. Place the downloaded .iso in the same folder. Run wubi.exe (with administrator privileges). Running wubi.exe will only install wubi.

Make sure you select the ubuntu flavor corresponding to the .iso or else it will download a new .iso.

---

### Post by deangl on 2010-07-28
> **bcbc said:**
> Place wubi.exe in a folder. Place the downloaded .iso in the same folder. Run wubi.exe (with administrator privileges). Running wubi.exe will only install wubi.

Make sure you select the ubuntu flavor corresponding to the .iso or else it will download a new .iso.

I believe I followed your instructions correctly - no joy in mudville...
Booted netbook in Win7, logged, created new folder on desktop, copied wubi.exe and ubuntu-10.04-netbook-i386.iso into new folder.  Doubleclicked new folder, right clicked on wubi.exe and "Run as Administrator".  The following attachment shows only two buttons in the dialog - would like to have the install wubi button back.  What am I doing wrong?

Thanks,
Dale

---

### Post by deangl on 2010-07-28
My attachment...

---

### Post by bcbc on 2010-07-28
> **deangl said:**
> My attachment...
strange... download wubi.exe from [http://wubi-installer.org/](http://wubi-installer.org/) and see if that works.

---

### Post by deangl on 2010-07-28
I am not sure why, but things are working now.
I moved the iso out of the folder (to the desktop), and tried wubi.exe again.  No diff.
I moved the iso file back into the folder, and tried wubi.exe again.
This time the wubi startup dialog was displayed as desired.
Just for grins I cancelled the install, and tried with and without the network cable connected.  Seem to work either way...
So, I requested 30Gb space and continued the install.
It finished, requested a reboot.  Rebooted and the installation continued as desired.  
Then rebooted again.  All as the wiki describes that should happen.
Things now seem to be working as expected.
Thanks for your suggestions.  Maybe on of them solved this problem, although it is difficult for me to be precise.  

Thanks,
Dale

---

