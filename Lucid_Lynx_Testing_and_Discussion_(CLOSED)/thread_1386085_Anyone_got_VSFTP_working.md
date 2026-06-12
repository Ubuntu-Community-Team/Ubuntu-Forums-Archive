---
title: "Anyone got VSFTP working?"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cookiecruncher on 2010-01-20
Attempted to install vsftpd using command line (sudo apt-get install vsftpd), and the installation seems to complete...but does not quite ;). CTRL-C is the only way that one gets control again.  Rebooting seems to be ok.  '/etc/init.d/vsftpd restart' too, seems to not quite finish.

Running Kubuntu Alpha2 (uptodate)

EDIT.  On rebooting, vsftp seems to be working fine tho.

---

### Post by Reiger on 2010-01-20
Installed a while ago without any problems I can remember. You can check if it runs properly by doing a ftp 127.0.0.1 and logging on as the user ftp with password ftp; then doing a ls -al (should give you a directory listing).

---

### Post by Reiger on 2010-01-20
Scratch that. I noticed it with today's update: vsftpd hangs, and you must kill it.

---

