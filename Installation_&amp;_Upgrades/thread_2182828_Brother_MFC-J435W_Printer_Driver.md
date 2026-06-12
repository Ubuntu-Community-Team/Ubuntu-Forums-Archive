---
title: "Brother MFC-J435W Printer Driver"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by patrick_g2 on 2013-10-22
In another part of this forum I was directed to [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J435W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J435W) to find the print drivers for my Ubantu 12.04. Following the instructions there, I opened the .deb files with the software installer. For both these drivers, I got the error that this was a POOR QUALITY application and when I told to 'ignore and install' it appeared to do the job, but nothing appears in the history of the application installer. Further nothing seems to have been installed either.

I have tried directly downloading and extracting them, but no joy when it comes to finding the ppd files for setting up the printer.

Suggestions?

---

### Post by gifford on 2013-10-22
Instead follow the instructions using the terminal as outlined on the Brother site. If you follow their instructions you should not have any problem. Unfortunately, using the Ubuntu software installer is not how the drivers should be installed.

---

### Post by AlexDudko on 2013-10-22
What about executing the command:
> sudo dpkg -i your_printer_dirver_file_name.deb

---

