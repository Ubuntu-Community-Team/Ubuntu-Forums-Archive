---
title: "Cannot print any more after upgrading to Intrepid"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vinhcuong on 2008-10-24
I have a printer connect through LAN, and a ppd file. I could print
normally and configure my printer when I was in Hardy.

After upgrading, I cannot print any more.
As I checked the printer's log, the jobs seem to be canceled.

The cups' log said something like
 "cupsdAuthorize: No authentication data provided."
and
 "Unable to bind socket for address 127.0.0.1:631 - Address already in use."

I have made some search, and have tried re-install cups, but it did not help. I also tried to stop cups and telnet 127.0.0.1:361, but it seems that no service was in that port.

Though, if I do not use my .ppd file, and use the Generic driver instead, I can print normally. (but cannot configure my printer..)

Could anyone give me some hint to solve this problem?

(I attached cups' log file when I tried to print test page.)

---

### Post by Sef on 2008-10-24
What is the make and model of your printer?

---

### Post by vinhcuong on 2008-10-24
It is RICOH IPSiO CX7200.

(I've also tried to re-install Intrepid, but nothing changed.)

---

### Post by kansasnoob on 2008-10-24
I've had trouble with my HP Deskjet 5440 with every step in Intrepid's development, which seems odd because it worked out-of-box in Gutsy and Hardy.

What I've had to do is install the hplip driver from:

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

Then to make HP Device Manager work now (in Applications > Accessories instead of Sys > Pref) install:

libqt4-assistant
libqt4-help
libqt4-svg
libqt4-test
libqt4-webkit
libqt4-xmlpatterns
python-qt3
python-qt4
python-qt4-common
python-reportlab
python-sip4
ttf-dustin


Seems fiddly to me since it worked out-of-box in Gutsy and Hardy.

I will say Intrepid is snappy enough to make it worth my time!

---

### Post by vinhcuong on 2008-10-24
Thank you for your advice.
I've gone to Ricoh's home page to search for a alternate ppd file if it is available. But the ppd files are only in Windowz exe file or Mac dmg file.
Then I tried to extract the ppd file from dmg file, but not succeeded. (I used dmg2img.pl script)

---

