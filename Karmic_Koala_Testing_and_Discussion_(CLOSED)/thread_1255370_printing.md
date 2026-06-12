---
title: "printing"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gwenn on 2009-09-01
My printer turns to live!:D
usb epson c80
But saddly I can print only one page then freeze and use 90% cpu, however it's a step ahead...

---

### Post by Teamgeist on 2009-09-01
Should be fixed with the next update.

> cups (1.4.0-3) experimental; urgency=low

  [ Till Kamppeter ]
  * debian/patches/usb-backend-infinite-loop-on-end-of-job.dpatch: Fixed
    upstream bug of the new libusb-based CUPS "usb" backend falling into
    an infinite loop after completing the job, blocking the next job
    (LP: #420797).

  [ Martin Pitt ]
  * debian/local/filters/pdf-filters/pdftopdf/P2PDoc.cxx: Update for poppler
    0.11.3 API, thanks to Koji Otani <sho at bbr.jp>!
  * disable-pdftoopvp-with-old-poppler.dpatch: Revert above change when
    building with poppler 0.10.x.


[https://lists.ubuntu.com/archives/karmic-changes/2009-September/007774.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/007774.html)

---

### Post by personman_ on 2009-09-01
I'm running 1.4.0-3 here and still having problems with it running one print job and hanging, forcing me to kill usb.

Printer is a Canon PIXMA MX700 w/ USB.

System is running Karmic.

-Andy

---

### Post by garvinrick4 on 2009-09-02
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015)

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420797](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420797)

---

### Post by personman_ on 2009-09-02
This bug is fixed as of CUPS-1.4.0-3.1.

-Andy

---

