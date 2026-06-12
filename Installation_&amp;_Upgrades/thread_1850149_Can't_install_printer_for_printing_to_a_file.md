---
title: "Can't install printer for printing to a file"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by billhorne on 2011-09-25
Thanks for reading this. I have an unusual issue and I need your help.

I need to "print" a page of tabular info (my cellphone usage details) to an ASCII file so that I can import it into a spreadsheet. I do NOT want to create a PDF or PostScript file: I just need the ASCII output from Firefox. 

Here are the steps I went through:

Printer Configuration – System Settings

Clicked on “New Printer”

In “New Printer” dialog, clicked “other”, and typed “FILE:///home/myusername/prnt.txt” in the “Enter Device URI” box. (I tried it with one, two, three, four, and five solidus {forward slash} characters, so if "3" isn't right, that's not the problem).

At the next screen, I then clicked on “Select Printer from Database”, and chose “Generic” as the printer type. 

On the next screen, I chose the “text only” model and  the “Generic text-only printer [en] (Recommended) driver.

On the next screen, I entered “file-print” as the printer name, “Print to file” for the description, and I left “Thinkpad” in the “location” field, which had been filled in automatically as is my laptop's name, and clicked “OK”.

I got an error screen, labelled “CUPS server error – System Settings”. It said “There was an error during the CUPS operation: 'client-error-not-possible'.”

Searches turned up a bug concerning a bluetooth printer install, but nothing else I found was close; plenty of problems installing various kinds of printers, but not with installing a printer to print to a non-pdf, non-ps file. 

Ubuntu 11.04 (GNU/Linux 2.6.38-11-generic-pae i686) running on 
Lenovo Thinkpad Type 0578-A99.

All suggestions welcome. TIA.

Bill

---

### Post by oldfred on 2011-09-27
Cannot you just save to a file.txt? But, if it is HTML you may not get what you want anyway.

Have you tried copy & paste to a file? or to a spreadsheet?

---

