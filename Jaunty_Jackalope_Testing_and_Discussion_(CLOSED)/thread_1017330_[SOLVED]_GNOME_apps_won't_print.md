---
title: "[SOLVED] GNOME apps won't print"
date: 2008-12-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rbmorse on 2008-12-20
Jaunty Alpha2 (plus updates) 64-bit 

Installed Alpha2 and then updated the system today.  GNOME apps cannot print to my networked HP 2605DN Color Laser Printer.  

Firefox prints fine
The Printer test page from system > administration > Printing > right click on printer prints fine
The printer test page from the CUPS server prints fine
Evolution prints

Gedit does not print
GnuCash does not print
The printer test page from HPLIP does not print
OpenOffice.Org Word processor does not print

I can access the printer's built-in web interface and can execute the printer's internal test page in that manner. 

No error messages are displayed. Commanding the print works fine, HPLIP indicates a new job has been sent to the printer. The status light on the printer's front panel blinks once or twice, then returns to steady green (ready). HPLIP indicates the print job completed successfully, but not output is produced nor does the printer look like it's trying to print anything. 

The CUPS log(s) do not show any obvious (to me) errors. 

An HP Photosmart 1215 attached to a USB port works correctly, so I'm not in extremis here, but I am about of ink.

---

### Post by rbmorse on 2008-12-21
CUPS update 1.3.9-2ubuntu6 fixes this in 64-bit Intrepid, so I imagine when that propagates into Januty's tree the issue will resolve here as well.  Marking this as solved.

---

