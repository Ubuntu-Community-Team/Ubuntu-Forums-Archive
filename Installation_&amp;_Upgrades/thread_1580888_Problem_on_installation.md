---
title: "Problem on installation"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by satimis on 2010-09-24
Hi folks,

Ubuntu 10.04 amd64 built on April. 26, 2010 (mini.iso)
Gnome desktop

During installation following warning popup```

An installation step failed.  You can try to run the failing item again
from the menu, or skip it and choose something else.  The failing step is:
Select and install software

```

Repeating above step can't solve problem, still popup above warning.

Items selected;```

Print server
Virtual Machine host
Ubuntu desktop

```


Then I de-selected;
Print server
Virtual Machine host


Installation went through.  Ubuntu 10.04 started finally.

I need "Print server" and "Virtual Machine host" please advise which software I need to add?

Printer - HP Deskjet 5740

$ apt-cache search cups```

bluez-cups - Bluetooth printer driver for CUPS
cups-driver-gutenprint - printer drivers for CUPS
libgnomecups1.0-1 - GNOME library for CUPS interaction
libgnomecups1.0-dev - GNOME library for CUPS interaction (headers)
python-cups - Python bindings for CUPS
apcupsd - APC UPS Power Management (daemon)
apcupsd-cgi - APC UPS Power Management (web interface)
apcupsd-doc - APC UPS Power Management (documentation/examples)
cups-pdf - PDF printer for CUPS
cupsys-driver-gutenprint - Transitional package
eggcups - notification area icon for printing jobs
gkrellmapcupsd - gkrellm plugin displaying the current processor speed
libnet-cups-perl - Perl module for printing through CUPS
brother-cups-wrapper-ac - Cups Wrapper drivers for ac brother printers
brother-cups-wrapper-bh7 - Cups Wrapper drivers for bh7 brother printers
brother-cups-wrapper-common - Common files for Brother cups wrapper packages
brother-cups-wrapper-extra - Cups Wrapper drivers for extra brother printers
brother-cups-wrapper-laser - Cups Wrapper drivers for laser brother printers
brother-cups-wrapper-laser1 - Cups Wrapper drivers for laser1 brother printers
brother-cups-wrapper-mfc9420cn - Cups Wrapper drivers for mfc9420cn brother printers
cups - Common UNIX Printing System(tm) - server
cups-bsd - Common UNIX Printing System(tm) - BSD commands
cups-client - Common UNIX Printing System(tm) - client programs (SysV)
cups-common - Common UNIX Printing System(tm) - common files
cups-dbg - Common UNIX Printing System(tm) - debugging symbols
cupsys-dbg - Common UNIX Printing System (transitional package)
ghostscript-cups - The GPL Ghostscript PostScript/PDF interpreter - CUPS filters
libcups2 - Common UNIX Printing System(tm) - Core library
libcups2-dev - Common UNIX Printing System(tm) - Development files CUPS library
libcupscgi1 - Common UNIX Printing System(tm) - CGI library
libcupscgi1-dev - Common UNIX Printing System(tm) - Development files for CGI library
libcupsdriver1 - Common UNIX Printing System(tm) - Driver library
libcupsdriver1-dev - Common UNIX Printing System(tm) - Development files driver library
libcupsimage2 - Common UNIX Printing System(tm) - Raster image library
libcupsimage2-dev - Common UNIX Printing System(tm) - Development files CUPS image library
libcupsmime1 - Common UNIX Printing System(tm) - MIME library
libcupsmime1-dev - Common UNIX Printing System(tm) - Development files MIME library
libcupsppdc1 - Common UNIX Printing System(tm) - PPD manipulation library
libcupsppdc1-dev - Common UNIX Printing System(tm) - Development files PPD library
python-cupshelpers - Python modules for printer configuration with CUPS
cups-ppdc - Common UNIX Printing System(tm) - PPD manipulation utilities
cupsddk - Common UNIX Printing System (transitional package)
cupsys - Common UNIX Printing System (transitional package)
cupsys-bsd - Common UNIX Printing System (transitional package)
cupsys-client - Common UNIX Printing System (transitional package)
cupsys-common - Common UNIX Printing System (transitional package)
hal-cups-utils - CUPS integration with HAL
hplip-cups - HP Linux Printing and Imaging - CUPS Raster driver (hpcups)

```


$ apt-cache search 'Virtual Machine host'
No printout


TIA

B.R.
satimis

---

### Post by drpjkurian on 2010-09-24
Hi
try the command
> sudo apt-get install cupsys cupsys-client

---

### Post by satimis on 2010-09-24
> **drpjkurian said:**
> Hi
try the command

Hi,

Thanks for your advice.

Do I need "hplip-cups - HP Linux Printing and Imaging - CUPS Raster driver (hpcups)" for my HP printer?

B.R.
satimis

---

### Post by drpjkurian on 2010-09-24
Hi
try this [link]("https://help.ubuntu.com/community/KVM/Installation") for virtual machine

---

### Post by drpjkurian on 2010-09-24
> Do I need "hplip-cups - HP Linux Printing and Imaging - CUPS Raster driver (hpcups)" for my HP printer?
Not sure about that buddy

---

### Post by satimis on 2010-09-24
> **drpjkurian said:**
> Not sure about that buddy

Hi,

HP Deskjet 5740

Performed following steps

$ sudo aptitude install cupsys cupsys-client

On browser:
[http://localhost:631/](http://localhost:631/)

Administration -> Add Printer -> Select driver, etc

-> Print A Test Page

OK

Printing is now working.  Thanks

B.R.
satimis

---

### Post by drpjkurian on 2010-09-25
Happy to know that it is working

---

