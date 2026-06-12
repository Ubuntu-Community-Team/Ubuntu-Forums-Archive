---
title: "LibreOffice and Chronium Permission Issues After Installation"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by archer123 on 2018-05-05
I have just installed 18.04 using the minimal installation option. I then installed Chromium and some of the LibreOffice tools via Ubuntu Software  tool.  All looked ok but LibreOffice had an old style UI. Also when I tried to upload a file via Chromium to a website it would not allow me to access my NFS shares mounted under /mnt.
 I then decided to install all the LibreOffice tools by installing the LibreOffice package again using Ubuntu Software to see if the UI problem would be fixed. This did fix the UI problem but, as per Chromium, I could no longer access files mounted under /mnt. When I installed the individual tools this was not a problem.
 I have done some research and there is a possibility that apparmor  could be an issue but I don’t fully understand this tool. I have tried  disabling the LibreOffice profiles but the problem persists.
 Any advice would be gratefully received.

---

### Post by TheFu on 2018-05-05
Are these snaps or normal package installs?  There have been a few snaps that didn't allow access to HW and directories outside HOME as part of increased security.

---

