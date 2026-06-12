---
title: "how to install a printer HL2030 from Brother with USB interface"
date: 2015-02-08
forum: Installation &amp; Upgrades
---

### Post by niko11 on 2015-02-08
I am totally new to lubuntu an want to install a Brother printer, HL2030.
The thread "[SIZE=2][Installing Brother Priners and Scanners Just Got Easier]("http://ubuntuforums.org/showthread.php?t=2246878")[/SIZE]" looks convenient but the type HL2030 is not supported there.

In the Systems menu I selected "add a printer".
Then I had the choice between parallel or serial interface or network interface. But the printer has only a USB interface. Also the laptop has only a USB interface.
So I tried "parallel" hoping that this can be changed later.
Next an equipment URI shall be input.
I have no idea about a suitable URI so I tried both of the two example URI's (ipp://cups-server/printers/printer-queue and
 ipp://printer.mydomain/ipp).
After that I could select Brother HL2030 and was happy.
But trying to print the test page resulted in error messages:
    With ipp://cups-server/... "unable to locate printer "cups-server" "
    With ipp://printer....   "unable to get printer status"

I guess that I need a special URI for the USB interface.
Who can tell me that URI or what else is wrong with my procedure for installation?

a frustrated Niko

---

### Post by Rex Bouwense on 2015-02-08
USB stands for Universal Serial Bus.  You do not have a parallel connection.
Try here [http://support.brother.com/g/b/productsearch.aspx?c=us&lang=en](http://support.brother.com/g/b/productsearch.aspx?c=us&lang=en)
to find your printer.

Does this help?
[http://www.openprinting.org/printer/Brother/Brother-HL-2030](http://www.openprinting.org/printer/Brother/Brother-HL-2030)

---

