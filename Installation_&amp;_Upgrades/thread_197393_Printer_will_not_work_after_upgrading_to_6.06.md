---
title: "Printer will not work after upgrading to 6.06"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Corvair on 2006-06-15
Hello everyone,
I cannot use my HP LasserJet 3p w/PCL5 since I upgraded from breezy. In my printer register I had an indication of my printer being ready . After trying to print I have an indication: printing 1 jobs.

My printer is printing this information contineously page after page until  the paper tray is empty:
%!PS0Adobe-3.0
                       %%BoundingBox:(atend)
                                                         %%Creater:OpenOffice.org 2.0
%%For: claude
                     %%CreationDate: Thu Ju


This is what I have in the    [http://localhost:631/printers/](http://localhost:631/printers/)     site
for information  	

Search in Printers: Clear

Showing 1 of 1 printer.
  	Sort Descending 	 
LaserJet-3P-w/-PCL5 (Default Printer) "Sending print file, 16384 bytes..."
	Description: LaserJet-3P-w/-PCL5
Location:
Make and Model: Local Raw Printer
Printer State: processing, accepting jobs, published.
Device URI: parallel:/dev/lp

HP Device manager tells me I have no installed printer driver.
When I try installing the printer, when asked for my user name and password, I am given an error.

I would appreciate very much if someone understands what is going on and if you can help me out on this one.

Claude

---

### Post by stlutz on 2006-06-15
To get the localhost:631 working, I added the line "RunAsUser No" to my /etc/cups/cupsd.conf file.  I can't remember if it was necessary to restart the cups service or not (which you can do by rebooting).  I was then able to reconfigure the setup of my HP PSC 1610 (which wouldn't print at all after the upgrade).

---

### Post by Corvair on 2006-06-16
Thanks for taking the time to answer my request.
I tried opening the file by going to a terminal and doing this:

sudo /etc/cups/cupsd.conf and I am told: command not found

What sould I do different?

---

### Post by handaxe on 2006-06-16
[quote=Corvair]Thanks for taking the time to answer my request.
I tried opening the file by going to a terminal and doing this:

sudo /etc/cups/cupsd.conf and I am told: command not found

What sould I do different?[/quote]

sudo gedit /etc/cups/cupsd.conf  - that is, you need to specify an editor

---

### Post by Corvair on 2006-06-16
OK,
I was able to open the cupsd.conf file, finaly.
This is a big file, where exactly should I add <RunAsUser No>?

---

### Post by Corvair on 2006-06-16
To my fellow helpers,

I added <# RunAsUser No>
as the last line in cupsd.conf and I dont' get that garbage line printed out
but the printer keeps feeding paper without printing anything and my job
remains in the jobs register.

Any clues?

---

### Post by Corvair on 2006-06-18
Hello everyone,
I was finely able to get my printer to work properly.

I removed the default installation that CUPS had given me during the upgrade from breezy to 6.06 and made a new printer installation, using LPT-1 as the port and to my surprise the printer is working normal again.

CUPS still does not recognise my username and password.

Thanks to those who tried to help.

---

### Post by chunk on 2006-07-20
same problem here

I think the breezy->dapper upgrade process screws up a lot of permissions, because I my cd drives aren't working anymore either except as root.

---

