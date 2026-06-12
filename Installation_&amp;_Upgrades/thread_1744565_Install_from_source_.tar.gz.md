---
title: "Install from source .tar.gz"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by thunderbirdje on 2011-04-30
Hi Everyone,

I just managed to install tesseract-ocr 3.0 from source. I want to OCR Chinese :D

I downloaded the .tar.gz to my desktop, extracted it to my Deskop (which created the directory). Then run the commands ./configure
make, make install from within that directory residing on my Desktop.

However I am wondering (because it's not working yet) if:

- I can delete the folder from the Desktop? Is it 'installed into some 'standard place'? Do I have to copy it myself? Or can't I? Like in Windows there is such a nasty beast called 'registry'... 
- If the program would be installed into the path (maybe it's a windows term), I mean if I can run it from within 'bash'?

I'm new to installing from source in Ubuntu and would love to learn the Ubuntu way! :D

Thank you!!!

---

### Post by oldos2er on 2011-04-30
There are instructions here: [http://wiki.openkm.com/index.php/Third-party_software_integration:_OCR](http://wiki.openkm.com/index.php/Third-party_software_integration:_OCR)

Note the warning about the PPA, if you decide to enable it.

---

### Post by thunderbirdje on 2011-04-30
> **oldos2er said:**
> There are instructions here: [http://wiki.openkm.com/index.php/Third-party_software_integration:_OCR](http://wiki.openkm.com/index.php/Third-party_software_integration:_OCR)

Note the warning about the PPA, if you decide to enable it.

Adding PPA: worked

apt-get update: worked (of course ;-))

apt-get install -> failed: can't find the Chinese language data (should be tesseract-ocr-chi_sim according to the tesseracts's wiki)...

So can I just subtract the .tar.gz to my Desktop? Or should I place it first somewhere in /user/share?

Thank you for helping me so far!

---

### Post by thunderbirdje on 2011-05-01
Managed to install tesseract-3.00 from source on Ubuntu 10.10 :D

Seems that the language data files works with an absolute path to the directory which is: /usr/share/tessdata.

My tesseract-3.00 directory resides on my Desktop, due the absolute path to tessdata it didn't found that directory, so installation from source failed.

---

