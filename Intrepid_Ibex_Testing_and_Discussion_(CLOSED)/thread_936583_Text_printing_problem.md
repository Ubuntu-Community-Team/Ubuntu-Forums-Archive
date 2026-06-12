---
title: "Text printing problem"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rbmorse on 2008-10-02
I have discovered a regression in the print subsystem, but I'm not sure which package to file against. 

Symptoms:  Printing from a text based application like text editor to my HP ColorLaserJet 2605Dn (Postscript) results in various characters being represented as boxes.  The number "8", the "/" character and the eol char seem to be most affected. 

Changing the font does not correct the problem, but it does cause different characters to be substituted with boxes. 

My other printer, which is an HP P1215 inkjet (non-Postscript) works normally. 

The Laserjet works fine in Hardy. I tried copying the .ppd from hardy into Intrepid, but the problem remains. 

If I load the generic Postscript driver for the printer I lose some control features but what does print is correct. 

Which package should I file the bug against?  HPLIP?

---

### Post by kansasnoob on 2008-10-03
I fiddled around today and I'm reasonably sure it's an HPLIP problem. Not positive though!

I had to remove hplip using synaptic and clear all history of previously installed printers. Then when I restarted cups had me printing again.

---

### Post by rbmorse on 2008-10-03
I looked at CUPS and there is a defective entry for an unnamed printer in the list that will not delete. Do you know where CUPS stores printer definitions?

---

### Post by rbmorse on 2008-10-03
see bug # 277404 for a possible work-around.

---

### Post by rbmorse on 2008-10-03
> **rbmorse said:**
> I looked at CUPS and there is a defective entry for an unnamed printer in the list that will not delete. Do you know where CUPS stores printer definitions?

/etc/cups/ppd/

---

### Post by rbmorse on 2008-10-14
> **rbmorse said:**
> see bug # 277404 for a possible work-around.
With the latest update to the openprinting.ppd package, the workaround of substituting the Hardy .ppd for the Intrepid .ppd no longer works. 

The next best work-around I've found is to open system > administration > printing, right clicking on the printer and selecting "properties"  and then click on the "change" button on the printer "Make and Model" line. Then select "generic postscript" as the driver.

This results in correct output from the printer, but certain functions are no longer available (the duplexer, for starters).

---

### Post by billstei on 2008-10-26
I have an HP Laserjet 5L and there is garbage on the first few lines (or about 1 inch on the top if graphics).  Switched to the Generic PCL5 driver (Generic PCL 5 Printer Foomatic/gutenprint-ijs-simplified.5.2) and this tests ok as a workaround.

Bill

---

