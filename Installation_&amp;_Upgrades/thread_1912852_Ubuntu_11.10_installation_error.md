---
title: "Ubuntu 11.10 installation error"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by daviede on 2012-01-21
I'm trying to install Ubuntu 11.10 on my windows computer.  Here's what I did:
1) Download Ubuntu installer for Windows (Wubi)
- no errors here
2) Run the Download file
- I selected to run inside windows
- I entered my username/pass, and clicked "install."
- Halfway through the installation, I get this error:
"'WindowsBackend' object has no attribute 'iso_path'
For more information, please see the log file:
c:\users\craig~1\appdata\local\temp\wubi-11.10-rev245.log"

Anybody know what's making this error occur, and how to fix it?
Thanks

---

### Post by dino99 on 2012-01-21
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by bcbc on 2012-01-21
> **daviede said:**
> I'm trying to install Ubuntu 11.10 on my windows computer.  Here's what I did:
1) Download Ubuntu installer for Windows (Wubi)
- no errors here
2) Run the Download file
- I selected to run inside windows
- I entered my username/pass, and clicked "install."
- Halfway through the installation, I get this error:
"'WindowsBackend' object has no attribute 'iso_path'
For more information, please see the log file:
c:\users\craig~1\appdata\local\temp\wubi-11.10-rev245.log"

Anybody know what's making this error occur, and how to fix it?
Thanks
You need to post the log file (either open that entire path in notepad, or enter the %temp% directory to find it). Unfort. wubi error messages don't normally explain the problem - you have to look in said log file.

In general the easiest way to install wubi is to download the desktop CD ISO and wubi.exe from the same release and save them both in the same folder before running.

---

