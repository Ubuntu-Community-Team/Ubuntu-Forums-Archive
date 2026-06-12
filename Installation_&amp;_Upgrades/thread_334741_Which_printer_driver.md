---
title: "Which printer driver?"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by frrobert on 2007-01-09
I am using drapper drake with a HP 970c printer.  Everything works as it should.  I very rarely print in color so I usually do not have working color cart.  When the 970 prints greyscale It will try to use color and not print black only.

I thought I would use a laser jet driver for a 1320 or 4250  which are a black duplexing printers.  Greyscale now prints in black only which is I wanted but I lost duplexing.

Does anyone know of a HP driver that will print black only and duplex on a 970C?

---

### Post by andreas64 on 2007-01-10
Hi,

maybe you should try newer drivers from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/). The drivers included in Dapper are very outdated.

Andreas

---

### Post by frrobert on 2007-01-11
Thanks for the idea but after updating same issues.

Fr. Robert

---

### Post by 11hjpphty76lkjj on 2007-01-12
If you use the deskjet 970 ppd file can you change the 

Resolution, Quality, Ink Type, Media Type

in cups to Draft, Grayscale, Black it should print using black only and should retain your duplexing functionality.

Aaron

---

### Post by frrobert on 2007-01-12
For some reason the greyscale selection shows black plus color in the choices and if I print greyscale it will try to print greyscale using color.  There is no option for black only

---

### Post by 11hjpphty76lkjj on 2007-01-12
Replace your existing DeskJet_970C.ppd with the attached file located in /etc/cups/ppd.

ie if your ppd file is named deskjet_home.ppd do "mv DeskJet_970C.pdd deskjet_home.ppd", etc.

Go back to cups and select Grayscale, Black Cart. in the " Resolution, Quality, Ink Type, Media Type" selection.

This is a patch and will only do 600dpi grayscale/black only.  We will update the ppd file in hplip with the next release.

Do you need draft or other modes?

---

### Post by frrobert on 2007-01-12
Thanks for your help.  It worked great.  With the ppd file you provided I was able to figure out how to to create the 300dpi greyscale black only.

---

### Post by 11hjpphty76lkjj on 2007-01-13
Great.  I'll see about getting the 300 dpi black into our next release as well.

Aaron

---

### Post by reabralop on 2007-01-15
I need some help with installing the driver for my printer. I found and downloaded the driver but am confused by the directions. "Open a console/terminal and cd to the download directory"; what does it mean by "cd"? I know it can't mean compact disk. I would appreciate it if someone could help me. Thank you.

---

### Post by 11hjpphty76lkjj on 2007-01-19
"cd" means "change directory".

If you are a windows convert the idea is the same as running cmd from windows and typing "cd program files", etc.

I've tried to be as clear as possible with the install instructions as I could be and I'm always open to suggestions.  The "cd" command is a very basic terminal/old school DOS command that most users have at least some experience with.  I can't entirely start from scratch you understand.  

Hope this helps.

---

