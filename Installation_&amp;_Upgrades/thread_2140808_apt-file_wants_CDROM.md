---
title: "apt-file wants CDROM"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by ulrichmuc on 2013-04-30
I tried to install apt-file via "apt-get install apt-file" and got the message:
Put CDROM labeled [Ubuntu_12.04.2_LTS__Precise_Pangolin__-_Release_i386_(20130213)] in the cdrom device and press [ENTER]

As I have got neither CDROM nor CD-drive (installed from USB-stick) I installed apt-file some other way.
However, when I try "apt-file update", I get again the request to insert the CD.

How to get around this?

Regards,

ulrich

---

### Post by darkod on 2013-04-30
Check if CD-ROM is enabled in /etc/apt/sources.list. If it is, disable it by putting # at the front of the line. Save and close the file. Run:
sudo apt-get update

to apply the change.

---

### Post by ulrichmuc on 2013-05-01
Thanks for the help!

ulrich

BTW: other packages that I install via apt-get do NOT request the CDROM; why?

---

