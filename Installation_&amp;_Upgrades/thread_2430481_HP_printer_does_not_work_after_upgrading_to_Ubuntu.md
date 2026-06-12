---
title: "HP printer does not work after upgrading to Ubuntu MATE 19.10"
date: 2019-11-02
forum: Installation &amp; Upgrades
---

### Post by rpearsonii on 2019-11-02
I have an HP OfficeJet Pro 7740 all-in-one printer/scanner connected to my computer with a USB cable. It worked fine in Ubuntu MATE 19.04. After the upgrade, the scanner still works (TWAIN still works), but the printer does not. I installed the latest HPLIP driver hplip-3.19.10. I then turned off my printer and shutdown the computer. After re-booting I tried to run hp-setup. It failed. from the /media/robert/Shared/Users/Shared/Programs/config.log I see multiple errors. They seem to be invalid command line options (lines 78, 83, 142, 147), missing header files (lines 256, 277, 390, 422) invalid C code (lines 522, 564, 617).

Obviously HPLIP was never tested in an environment than the development environment and the error logs were perused at best. Errors were not checked.

hp-setup gave the following error message: error:  Printer queue setup failed.   Error : successful-ok-ignored-or-substituted-attributes
I would attach the configuration log, but your "Upload Manager" thinks a text file with a name ending in .log is an invalid file.

---

### Post by oldfred on 2019-11-02
They stopped using HPLIP by default with 18.04.
I have a smaller HP printer and have not used HPLIP since 16.04. Printer is just automatically found & driver installed.

18.04 Bionic Beaver
Driverless printing support is now available. 
PostScript Printer Description (PPD) files are created by vendors to describe the entire set of features and capabilities available for their PostScript printers.

If you do not have correct ppd file, you need to get that.

It does look like HPLIP is supposed to install correct ppd file.
[https://h30434.www3.hp.com/t5/Scanning-Faxing-and-Copying/How-can-I-use-my-OfficeJet-Pro-7740-to-scan-from-within/td-p/5881581](https://h30434.www3.hp.com/t5/Scanning-Faxing-and-Copying/How-can-I-use-my-OfficeJet-Pro-7740-to-scan-from-within/td-p/5881581)

---

