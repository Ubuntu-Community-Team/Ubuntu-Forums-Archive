---
title: "Add a printer grayed out 11.10 new install"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by bhoth on 2011-11-08
Hi All,

Clean install of Ubuntu 11.10 running Gnome Classic. go to add a printer and it's grayed out.

I formatted the hard drive installed fresh again and same thing.

Any ideas?

(selected Lubuntu by mistake)

---

### Post by Rodney9 on 2011-11-09
What model and brand is the printer ?
Is it plugged in and powered on ?

Have a look here for more info - [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by bhoth on 2011-11-09
Sorry I forgot to mention that I have network printers. A Brother HL-2070N and a Brother HL-4070CDW.

---

### Post by Rodney9 on 2011-11-09
Look here - [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Your 2070 seems to be supported but maybe not the 4070 [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother)

You can try cups configuration via a browser

CUPS provides a web interface (which is sometimes called a GUI, although we rely on the web browser to provide the graphical part) that allows you to view print jobs, printers, and the online help, as well as manage your printers.

The CUPS web interface is available on your machine at the following URL:

    [http://localhost:631](http://localhost:631)

Some pages require a username and password to perform certain actions, for example to add a printer. In general you can use your login name and password, but on Mac OS X your login name is called the "short user name" which is usually your first and last name in lowercase. For example, if your name is "John Doe", your short username would be "johndoe".

For most Linux and BSD distributions, you must use the "root" username and password to add, modify, or delete printers or classes.

Note: Your cups.org username and password are not used by the CUPS web interface. Only accounts on your system can be used.

Further info - [http://www.cups.org/documentation.php/doc-1.5/network.html](http://www.cups.org/documentation.php/doc-1.5/network.html)

Rodney

---

### Post by ArgAthens on 2012-02-04
I had this happen to me too with clean install.  I ran it from the command line and it worked.

sudo system-config-printer

---

### Post by sports supplement on 2012-03-26
I have just has the same problem and running it from the command line fixed it for me.  I am running 11.10 with Gnome3.

---

