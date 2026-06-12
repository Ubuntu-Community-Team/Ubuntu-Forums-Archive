---
title: "Problem Adobe reader Install Hardy"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by IronArjen on 2008-06-18
I get an error trying to install Adobe Reader. I have had this before on my AMD Athlon 64 in Feisty, now I have it in AMD Phenom, Hardy. Below you ll see it asks for a script, this is Kilz famous script to run flash, java and adobe via a 32 bit Firefox on a 64 machine install. I get the same error if I type y here, with an additional :

trap: 634: SIGINT: bad trap


I will post this same problem on the 64 bit forum if here nobody has a clue (and later  if provided the solution).

Thanks Arjen

arjen@Comparative_Genomics:~/Desktop/Software_downloads/AdobeReader$ sudo ./INSTALL
[sudo] password for arjen: 
 
This installation requires 95 MB of free disk space.
 
Enter installation directory for Adobe Reader 7.0.5 [/usr/local/Adobe/Acrobat7.0] 
/usr/local/Adobe/Acrobat7.0
 
Installing platform independent files ... Done
 
Installing platform dependent files ... Done

Do you want to install the browser plugin ? [y/n] n
Please login again for changes to MIME types and icons to take effect.

---

### Post by IronArjen on 2008-06-19
I do not know what I did but it works, albeit with an error message refferingto the lack of PPKlite.api. This is the same as I used to have on Feisty except that on Fisty it prevented reader from running, here it simply works.

I will again look for the PPKlite.api...........

---

### Post by sowhat12345 on 2008-06-19
Why did you installed Adobe Reader . It is working very slowly . It use very memory and cpu. Ubuntu has already installed free programs to open the pdf files. Also has free programs in Add/remove programs....
Can we open all pdf files properly ? or we should use adobe reader ?

---

### Post by IronArjen on 2008-06-19
It is easier make snapshots since it has its own snapshot tool that allows direct copy-pasting figures. Besides copying text is more correct when working with column PDFs and indeed certain new PDF versiosn render problems in for instance evince.

I found no threads with the PKKlite and since it works I leave it to this.

---

