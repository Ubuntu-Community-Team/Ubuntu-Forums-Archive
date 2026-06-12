---
title: "Karmic: PDF not being recognised"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2009-12-10
I created a pdf via the pdf cups printer. 

Adobe 9 says it can not open it because it is either damaged or not supported.

Okular opens the file.

As I wish to email the file I need to be sure that it is a pdf. 

I would have expected the cups to work. Is there something I should have done to ensure it printed a pdf. I ticked the save to file box. Was I wrong?

What is the best way to print to a pdf?

---

### Post by jobix on 2009-12-11
I have Hardy, not Karmic, on my machine. So, maybe things are a bit different. Anyway, there is a separate option for printing as PDF. It simply shows up in the list of printers as "PDF". I don't have to explicitly check any "save to file" box.

Having said that, if you have to use "print to file," you can try this:
1- Choose the Postscript option and save your file as a .ps file, e.g., hello.ps
2- Having done that, use a utility such as "pd2pdf" or "convert" to convert hello.ps to hello.pdf:
     -- ps2pdf hello.ps
     -- convert hello.ps hello.pdf
3- Use the file command to verify that it is a PDF document:
     -- file hello.pdf

---

### Post by Robbyx on 2009-12-11
Thank you. Assuming I can get a solution to why pdf's are not being saved, I will follow your suggestion.

---

