---
title: "driver for Lexmark Prospect pro205 for ubuntu 12.04"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by shuster on 2012-11-24
Hi,
I have problems installing my Lexmark Proscpect Pro205 in my newly upgraded ubuntu 12.04. It used to work in 11.10, but now, when installing the printer in a usual way (network printer etc.) the printer seems to be installed but does simply nothing, also no test page printing.
When I try to install the printer via terminal via the downloaded printer utility "lexmark-printer-utility-1.0-2.i386.deb" this strange message pops out!:

..:~/Downloads$ sudo dpkg -i lexmark-printer-utility-1.0-2.i386.deb
(Reading database ... 273687 files and directories currently installed.)
Preparing to replace lexmark-printer-utility 1.0-1 (using lexmark-printer-utility-1.0-2.i386.deb) ...
Unpacking replacement lexmark-printer-utility ...
Setting up lexmark-printer-utility (1.0-1) ...
Installing %%JARVIS_VENDOR_PREFIX%%hcp backend ...
cp: cannot stat `/usr/local/lexmark/printer_utility/bin/%%JARVIS_VENDOR_PREFIX%%hcp': No such file or directory

EU waste electronics information
********************************

The WEEE logo signifies specific recycling programs and procedures for
electronic products in countries of the European Union. We encourage
the recycling of our products. If you have further questions about
recycling options in European Union countries, please refer to the
document listed below.

  /usr/local/lexmark/docs/EU_Waste_Electronic_Information.pdf


I cannot find anything like this in the net (Looks like advertisement), so its time for me to put a thread and ask you guys.
I'm really new here and not the pc expert, so please be kind :-)
ciao,
Rob.

---

### Post by hhall on 2013-01-05
Same problem here. Did you manage to solve it?

---

### Post by offgridguy on 2013-01-05
Not sure if this helps , but you could try here.

[http://driverscollection.com/?H=Prospect%20Pro205&By=Lexmark](http://driverscollection.com/?H=Prospect%20Pro205&By=Lexmark)

---

### Post by lifeboy on 2013-03-18
Lexmark have been very sneaky if not downright devious with this.  I contacted support regarding this.  The drivers that work for pre 12.04 releases, that they had since a few weeks ago where these (I put them up, since Lexmark removed them):

[lexmark-inkjet-legacy-1.0-1.i386.deb]("https://dl.dropbox.com/u/12668653/lexmark-inkjet-legacy-1.0-1.i386.deb")
[lexmark-printer-utility-1.0-2.i386.deb]("https://dl.dropbox.com/u/12668653/lexmark-printer-utility-1.0-2.i386.deb")
[lexmark-scan-legacy-1.1-1.i386.deb]("https://dl.dropbox.com/u/12668653/lexmark-scan-legacy-1.1-1.i386.deb")

These all worked 100% on Ubuntu 11.10 provided you first uninstall the older drivers.  I could print & scan over wifi (I set a fixed ip address for the printer in my DHCP)

On another laptop running 12.10 though I could print, but not scan.

After upgrading the first laptop to 12.04 I could not scan anymore from there either.

So I contacted Lexmark support and asked them to help.  The persistently claimed that they do not have support for Ubuntu.  I repeatedly insisted that they check their own website and provided proof that the Debian and Ubuntu drivers are there.  They just kept denying the facts!

When I went there this morning, lo and behold, they had removed all the Linux distro's except Fedora 10 and OpenSuse 11.0 & 11.1.

What makes a company so foolishly and proud (of their failure?) that they blatantly lie to a client, then remove the files without even an acknowledgement or apology and pretend nothing happened?

I suggest you contact there support desk and complain and insist they fix the mess they created and they provide documentation for the driver (which they didn't before)

Try these drivers above and see if you can at least print.  
Below is a blog entry I wrote about the previous version of the drivers.  
I'll probably update that with the details of a fix once I get one.

[http://lifeboysays.wordpress.com]("http://lifeboysays.wordpress.com/2011/06/07/ubuntu-lexmark-pro-200-series-printing/")

---

