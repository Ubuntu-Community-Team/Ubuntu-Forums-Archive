---
title: "Adobe Reader &amp; 15.04 &amp; PDF Printing"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by mark bower on 2016-09-20
How can I get Adobe Reader to print in Ubu 15.04.  It opens and reads PDFs just fine.  But when I request to print the document, my printer (HP Laserjet 4) experiences just one "blink" and does not print the document; no error msg is generated; print que indicates normal processing; CUPs has no problems.  Normally the printer will make a number of blinks when document is received at printer.  To restate: Adobe Reader 9.5.5 works just fine, except that it will not generate a printed document.  Via Okular, PDFs print with no problem (just can't get portrait output from a landscape input - and thus the need for Adobe).

My guess is that there is some sort of limited file/library problem?  Would there be a log indicating the problem, and if so, how would I get to it to make a print out and return here for help?

---

### Post by ajgreeny on 2016-09-20
First thing to say is that 15.04 is no longer supported and you will find it very difficult to get anyone to assist you with a problem in that version.
You should clean install 16.04 or go back to 14.04, clean install again will be needed, in order to move to a supported OS.

I do not fully understand what you mean by > Via Okular, PDFs print with no problem (just can't get portrait output from a landscape input - and thus the need for Adobe). so perhaps you can explain that in more detail, but as I said, you really should be using a version of Ubuntu that is supported or we will not be much help to you.

---

### Post by mark bower on 2016-09-20
Thanks for response.  

Okular prints PDFs just fine, except for a needed manipulation.  I receive stock confirm PDFs in landscape from investment firm.  I 3-hole punch them for filing in a 3-ring binder.  If printed in landscape (as they are received), this means rotating the binder 90 degrees everytime I want to read the statements.  If I can print and file them as portraits - just open the binder and read.  Adobe would input landscape --> print portrait, worked great.  Okular does not have that option.  (lengthly, but trust this explains)

I believe I know the problem.  It looks like the older print drivers available through CUPS no longer play friendly with Acrobat and 15.04.  I can take the statement file to my wife's MAC and it can be printed in landscape.  Probably not relevant, but I should mention that I connect to my HP Laserjet 4 printer as computer --> wifi --> router --> print server --> HP Laserjet 4.

**I do not plan on returning this thread**.  I have gone to Okular from KDE for general PDF use, and added an additional HD (Ubuntu 12.04) with acroreader to meet my landscape to portrait needs.  This is not a solution to get acroreader to play friendly with 15.04.

---

