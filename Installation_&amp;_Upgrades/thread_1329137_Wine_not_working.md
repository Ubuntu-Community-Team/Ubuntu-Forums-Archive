---
title: "Wine not working"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by musaluke on 2009-11-17
help,how do i solve this?
Archive:  /home/general/Desktop/DataRecoveryPro6/fo-erp63.exe
[/home/general/Desktop/DataRecoveryPro6/fo-erp63.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/general/Desktop/DataRecoveryPro6/fo-erp63.exe or
          /home/general/Desktop/DataRecoveryPro6/fo-erp63.exe.zip, and cannot find /home/general/Desktop/DataRecoveryPro6/fo-erp63.exe.ZIP, period.

---

### Post by Mark Phelps on 2009-11-17
Are your trying to install Paretologic's Data Recovery Pro using Wine?

IF so -- good luck!! The Wine Application Compatibility site doesn't even LIST that app, let alone indicate a compatibility rating.  See link below to do your own search:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Also, according to the error messages, the file you have is a self-extracting archive, which must be run in MS Windows to export the files.  I would doubt very much that you could run such a file in Wine.

---

