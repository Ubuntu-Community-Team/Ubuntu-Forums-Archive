---
title: "Problem with adobe reader and firefox"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by mastergunner on 2008-06-27
Guys I have adobe reader installed. Everytime I try to open a pdf file through firefox I can only save it to disk. I do not have the adobe reader option when it asks what program to use to open this file. Any help is appreciated.

---

### Post by mastergunner on 2008-06-27
Can anyone help me here?????

---

### Post by DeaconBlues on 2008-06-27
You tried checking your file associations for .pdf files?

If not:

Save a .pdf file to Desktop/wherever.

Right-click on it and select "properties".

Go to the "open with" tab and make sure it's set to open with Document Viewer.

---

### Post by forger on 2008-06-27
I wouldn't use adobe acrobat/reader if I were you:
(1) CRITICAL: Adobe Acrobat JavaScript Remote Code Execution
Affected:
Adobe Reader versions 8.1.2 and prior
Adobe Acrobat versions 8.1.2 and prior

Description: Acrobat and Reader are Adobe's Portable Document Format
(PDF) viewers. They contain a flaw in their handling of certain
JavaScript constructs. A PDF document containing embedded JavaScript
could trigger this flaw, creating a buffer overflow condition.
Successfully exploiting this buffer overflow would allow an attacker to
execute arbitrary code with the privileges of the current user. Note
that, depending upon configuration, PDF documents may be opened by the
vulnerable applications upon receipt without first prompting the user.
Reports indicate that this vulnerability is being actively exploited in
the wild.

Status: Vendor confirmed, updates available.

References:
Adobe Security Advisory
[http://www.adobe.com/support/security/bulletins/apsb08-15.html](http://www.adobe.com/support/security/bulletins/apsb08-15.html)
Wikipedia Article on the Portable Document Format
[http://en.wikipedia.org/wiki/Portable_Document_Format](http://en.wikipedia.org/wiki/Portable_Document_Format)
SecurityFocus BID
[http://www.securityfocus.com/bid/29908](http://www.securityfocus.com/bid/29908)

---

