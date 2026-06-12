---
title: "Installing my Epson printer"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Vincenso Andolini on 2010-10-18
Hi all,

I am trying to install my Epson NX420 printer. I downloaded a driver from openprinting.org. However the installation seems to have stopped and is waiting at "installing dependencies..."

What does this refer to?; and why is it stopped?; and how can I get the installation to finish?

Also I have the option to select "Terminal" and I am prompted to choose a mail server configuration. I'm not sure what this has to do with printers, and am not sure what to choose or why.

Anybody with some experience please help. 

Thanks,

Vincenso

---

### Post by stuartjm on 2010-10-18
Vincenso,
I am also trying to install an Epson NX 400 series printer.  If you wouldn't mind, could you contact me when you possibly get it figured out?  I will do the same for you, however, I am somewhat computer ignorant.  If by some stretch of the imagination I can get it figured out, I will let you know.

Thanks,
Jill

---

### Post by sisco311 on 2010-10-18
Did you try installing the driver(s) from [http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/) ?

They provide .deb packages for Ubuntu....

---

### Post by Vincenso Andolini on 2010-10-18
I didn't install from that website. Is it a different file? What is ".deb"?

Vincenso

---

### Post by Vincenso Andolini on 2010-10-18
"http://avasys.jp/eng/linux_driver/download/"

This link doesn't have my particular printer. Thanks though. 

Do you have any other ideas which might be of help?

Thanks,

Vincenso

---

### Post by sisco311 on 2010-10-19
> **Vincenso Andolini said:**
> "http://avasys.jp/eng/linux_driver/download/"

This link doesn't have my particular printer. Thanks though. 

Do you have any other ideas which might be of help?

Thanks,

Vincenso

Here is another link:
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

Scroll down the page & download epson-inkjet-printer-escpr_1.0.1-1lsb3.2_i386.deb. Once it's downloaded double click the file to install it.

---

### Post by Vincenso Andolini on 2010-10-19
Great thanks, there are a whole bunch of files to download, what do I do next? 

I've tried the first choice, and in it is an executable file. I didn't think linux could use ".exe".

So I tried the second file, and the OS tells me the installation completed. Woo-hoo!

Now, If I could only get the printer to show in System>Preferences> Default Printer or under System>administration>Printing than I should be off to the races.

Do you know how to get the OS to display the printer as a choice? or why it isn't being displayed?


Your help is very much appreciated.
Vincenso

---

### Post by sisco311 on 2010-10-19
Try to add the printer via the web interface, go to [http://localhost:631/admin](http://localhost:631/admin) -> *Add Printer* or *Find New Printers* and follow the instructions.

---

### Post by Vincenso Andolini on 2010-10-19
Ok, great, it's showing up now, and the printer is working perfectly!

Thanks a gazillion,

Vincenso

---

### Post by sisco311 on 2010-10-19
You're welcome!

---

### Post by dulce on 2010-11-05
we just did this also and it worked perfectly. thanks.

---

### Post by sisco311 on 2010-11-05
> **dulce said:**
> we just did this also and it worked perfectly. thanks.

My pleasure.

---

### Post by malibusurfer2 on 2010-12-28
I have a Epson Stylus NX305 USB printer connected to my Ubuntu 10.04 Lucid desktop computer. The printer is installed and shows up as my default printer with Device URI: pipslitelp:/var/run/pipslitelp0.

The problem is that every time the computer restarts, another printer is added named Stylus NX300 that points to the same printer as my 305 - ie. a duplicate - but with cups URI. 

How can I stop this second copy from reappearing?

---

