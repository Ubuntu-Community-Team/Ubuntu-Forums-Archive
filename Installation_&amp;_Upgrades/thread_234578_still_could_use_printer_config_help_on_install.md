---
title: "still could use printer config help on install"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by lamtarrah on 2006-08-11
I got some help here on configuring my printer after just installing ubuntu, but it wasn't enough to solve my problem,  I still don't have my printer working.  I'm re-stating my problem here again.  I'll appreciate any help.

The install went very easily, except that my printer wasn't automatically detected.  I don't understand what to do through the cups tool.  

I have an epson stylus color 850 hooked up by a parallel port cable.

Could someone guide me through the three steps of adding a new printer under system, administration, printing?  I am particularly baffled by what to put down for location at step 3.  I chose local printer at step 1 and epson parallel port at step 1.  I selected my printer at step 2 , and didn't click the install driver button, but just went to step 3.

Thanks for your help.

---

### Post by goatflyer on 2006-08-11
Hi, and welcome to the forum.

I had a similar problem deciphering instructions when installing a printer (coincidentally, another epson)

[http://www.ubuntuforums.org/showthread.php?t=225026](http://www.ubuntuforums.org/showthread.php?t=225026)


Basically, I used gnome-cups-manager to install it. Quite easy actually.

First, go into System>Administration>Synaptic Package Manager
Click Reload
Click Search, type in gnome-cups-manager
if the box next to the name is green, then it already installed.
if the box is grey, 
 Click Mark for Install, then 'mark'
 Click Apply
 (the application is now downloaded and installed)

To use it, look either under System>Printers or System>Administration>Printers  (I'm not at my desktop now)

Its a 3 step process, and you don't need any driver files, just pick your printer, type in a description, and you're done.

-EDIT-

To test it, open gimp and load a picture, select File>Print, select Add Printer (if it isn't one of the choices).  This only adds a queue to the previously installed printer.  Then print.

To test text, open OpenOffice Writer

---

### Post by lamtarrah on 2006-08-11
Yes, it's that easy three step process I'm having troubles with.  At step 3, besides a description, I'm asked for a location.  What do I put there?

At step 1, do I go with local printer or network?  I'm at home with a single machine.

At step 1 also, do I select "use another printer by specifying a port"?  If so, should I select, "parallel port 1 9epson)"?

At step 2, after I select my printer, do I just go to step 3 or do I need to select "install new drivers"?

Thanks for your help.

---

### Post by goatflyer on 2006-08-11
At step 1, choose Local

Also at step 1, if it offers you more than one choice, choose the epson at the port you are connected (lp #1 based on what you wrote)


At step 2, just select your printer - don't do anything else. The suggested driver should automatically switch to gutenprint.  That's what you want.  Don't click 'Install Driver'. Then proceed to step 3


The 'location' in step 3 is a comment field.  write 'the printer by my desk' if you can't think of something more colorful :)

By the way, according to the info below, your printer is supported by exactly the same gimp-print/gutenprint driver as mine.

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_850](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_850)

---

### Post by lamtarrah on 2006-08-11
That did it.  Thanks so much for your help.

---

