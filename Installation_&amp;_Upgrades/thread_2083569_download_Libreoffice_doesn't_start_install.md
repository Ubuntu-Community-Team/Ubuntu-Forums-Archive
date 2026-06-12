---
title: "download Libreoffice doesn't start install"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by riowg on 2012-11-13
Hi there, I'm new to Ubuntu.  I browse Libreoffice webpage in Firefox and download the latest stable 3.6.3 version rather install from the Software Centre of Ubuntu which offers 3.6.2 rc only.  After download the Debian version, it doesn't start installation but just open the gz to read inside the files and folders in the archive.

Pls advice.

---

### Post by pkadeel on 2012-11-13
> **riowg said:**
> Hi there, I'm new to Ubuntu.  I browse Libreoffice webpage in Firefox and download the latest stable 3.6.3 version rather install from the Software Centre of Ubuntu which offers 3.6.2 rc only.  After download the Debian version, it doesn't start installation but just open the gz to read inside the files and folders in the archive.

Pls advice.
I guess when you click the download button on LibreOffice site, you select "Open With" option in the download window. Instead select the Save option and then after download finishes, go to that location and unpack the .tar.gz archive. That shall give you the .deb package to install.

---

### Post by Linuxisfast on 2012-11-13
I would strongly suggest that you continue using the existing tested and integrated LO package in your Ubuntu, in case you want the latest, add the libreoffice ppa and wait for an upgrade to come through. If you are hellbent on getting the latest the you will need to do some command line work. First purge the libreoffice-core packages. Then unzip the downloaded package and via command line do a sudo dpkg -i *deb

---

### Post by Peter Maunder on 2012-11-13
If you install via the command line you will also need to install the DESKTOP INTEGRATION package contained in the main folder. Then do not forget you will also need the Language package for the language you are using and the correct language  Helppack.

Unless you are very certain about what you are doing, I agree you should stick with the current version.

---

### Post by riowg on 2012-11-14
I'm not really sure a little complicated command line installation.  I want to upgrade to 3.6.3 because the menubar is missing in 3.6.2, and I'm not sure if the latest could solve the issue.  But I'm afraid I may not get it done easily.  Thanks for the replies.

---

### Post by riowg on 2012-11-14
> **pkadeel said:**
> I guess when you click the download button on LibreOffice site, you select "Open With" option in the download window. Instead select the Save option and then after download finishes, go to that location and unpack the .tar.gz archive. That shall give you the .deb package to install.

I select Open rather Save for sure, because I didn't intend to save it and run it myself.

---

### Post by 73ckn797 on 2012-11-14
If you have downloaded and saved the LibreOffice (LO) file then right click to open and extract to a temp directory. Probably the easiest thing next is to right click on the .deb file that was extracted and select open with Software Center. That will take care of the details.

Purging the OEM LO installation may be a good thing to do first.

---

### Post by riowg on 2012-11-14
I've the menubar recovered by following [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1062757](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1062757), and so I'm not going to reinstall the whole package, though I'm ready to use 73ckn797's method.  I've just learned a bit about reinstalling from Ubuntu.  Thanks a lot for all the replies and instructions! :)

---

