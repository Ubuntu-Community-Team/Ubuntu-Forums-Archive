---
title: "How to Install A Networked Printer"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by savilash on 2006-07-10
Hello Again

Having installed my first Linux OS (I chose Ubuntu on a recommendation), I am trying to install a networked printer.

The printer I have is a Lexmark E230 which is connected to the network via a HP JetDirect Print Server.  I have managed to download a printer driver from Lexmark which is for Debian.  Since I read Ubuntu is based on Debian, I thought this will work).  I stored it on my user drive, right clicked and used the Deb something to install the driver.

If I now go back to adding a printer, the printer driver that I installed does not appear.  I used a wrong driver previously and printed garbage.  So I know that the process of installing the printer is correct.  I simply do not know how to find the drivers that I installed.

Could someone help please ?

Thanking you all in advance.

---

### Post by atothedb on 2006-07-10
i'm having the exact same problem, but with a canon printer... i'm befuddled as to how to find the driver.

---

### Post by savilash on 2006-07-11
I have just found out that installing the Lexmark driver leaves a print.lexmark file in /usr/local/lexmark folder which when I try to run and/or install, the OS complains that it is unable to open the file.  Can anyone help at all, PLEASE ?





> **savilash said:**
> Hello Again

Having installed my first Linux OS (I chose Ubuntu on a recommendation), I am trying to install a networked printer.

The printer I have is a Lexmark E230 which is connected to the network via a HP JetDirect Print Server.  I have managed to download a printer driver from Lexmark which is for Debian.  Since I read Ubuntu is based on Debian, I thought this will work).  I stored it on my user drive, right clicked and used the Deb something to install the driver.

If I now go back to adding a printer, the printer driver that I installed does not appear.  I used a wrong driver previously and printed garbage.  So I know that the process of installing the printer is correct.  I simply do not know how to find the drivers that I installed.

Could someone help please ?

Thanking you all in advance.

---

### Post by fatmatt on 2006-07-11
I'm using CUPS and while there isn't a printer driver for exactly your lexmark, there are many lexmark drivers there (a lot of laserjet drivers for most manufacturers just point to the linux hp laserjet driver anyway).

Are you using the web based "http://localhost:631" CUPS to set up the printer? There's an option there for a custom ppd file as well which I think is the driver.

---

### Post by dspivey on 2006-07-11
is this a postscript or raster printer?  did you restart cups after you installed the driver?  to restart cups, open a terminal and type "/etc/init.d/cupsys restart", then hit Enter

the best way to install a printer on any Linux distribution that uses CUPS is using the CUPS web interface ([http://localhost:631)](http://localhost:631)).  
you will need to enable the root user first in a terminal, because you will be prompted for a username (root) and password before you will be allowed to add the printer in the web interface.  after you've enabled the root user, stay in the terminal.  type "su" and hit Enter, then type in the root password.  Next type "adduser cupsys shadow" and hit Enter (this allows root access to the CUPS web interface).  Add the printer using HP/JetDirect.

---

### Post by savilash on 2006-07-11
Thank you.  You are a life saver.  Will try it when I get home tonight.




> **dspivey said:**
> is this a postscript or raster printer?  did you restart cups after you installed the driver?  to restart cups, open a terminal and type "/etc/init.d/cupsys restart", then hit Enter

the best way to install a printer on any Linux distribution that uses CUPS is using the CUPS web interface ([http://localhost:631)](http://localhost:631)).  
you will need to enable the root user first in a terminal, because you will be prompted for a username (root) and password before you will be allowed to add the printer in the web interface.  after you've enabled the root user, stay in the terminal.  type "su" and hit Enter, then type in the root password.  Next type "sudo adduser cupsys shadow" and hit Enter (this allows root access to the CUPS web interface).  Add the printer using HP/JetDirect.

---

### Post by indulis on 2006-07-14
...e.g. Windows 

Then you need to set up a "raw" printer under CUPS.

Add user cupsys to group shadow in /etc/group

Then open up [http://localhost:631](http://localhost:631) in a browser

Define a printer called "raw_q" (no quotes), choose "raw" as the printer type, "raw" for the queue.

Point your Windows system (or other Linux system) to [http://your_print_server_name:631/printers/raw_q](http://your_print_server_name:631/printers/raw_q)
by setting this in the Windows printer port setting (URL section)

[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html]("http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html")

I borrowed this from somewhere, can't find the site now

First, 

```
sudo cp /etc/cups/cupsd.conf etc/cups/cupsd.conf.backup
```

```

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.234.*
Allow From 192.168.135.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow from 192.168.234.*
Allow from 192.168.135.*
</Location>

```

Make your /etc/cups/cupsd-browsing.conf look like this
```

#
# Browsing: whether or not to broadcast and/or listen for CUPS printer
# information on the network.  Disabled by default.
#

Browsing On

```

Check your firewall is not stopping port 631! On your client, your server, and your network switch!  I suggest using the latest Firestarter (not the one that comes with Breezy), download it and install it using ```
dpkg -i
```

Have fun!

Indulis

PS THis is the result of a VERY late night last night getting this working

---

### Post by indulis on 2006-07-14
...e.g. Windows 

Then you need to set up a "raw" printer under CUPS.  I had to do this, as my printer was printing the actual postscript raw text (i.e. CUPS translating the postscript to text) rather than sending the postscript directly to the printer.

All of the steps below are done on the server (runnning Breezy) with the printer attached.  Except where indicated ;-)

On your print server, add user cupsys to group shadow in /etc/group using either an editor or the Admin-Users and Groups menu item.

Then restart CUPS

```
sudo /etc/init.d/cupsys restart
```

Then open up [http://localhost:631](http://localhost:631) in a browser

Define a printer called "raw_q" (no quotes), choose "raw" as the printer type, "raw" for the queue.

Point your Windows system (or other Linux system) to [http://your_print_server_name:631/printers/raw_q](http://your_print_server_name:631/printers/raw_q)
by setting this in the Windows printer port setting (URL section).  Note that if you don't have your server name set in your own DNS, or in the C:\WINDOWS\SYSTEM32\DRIVERS\ETC\HOSTS, then you can just use your server's IP address inseat of your_print_server_name

[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html]("http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html")

I borrowed this from somewhere, can't find the site now

First, 

```
sudo cp /etc/cups/cupsd.conf etc/cups/cupsd.conf.backup
```

Then edit your /etc/cups/cupsd.conf to look like this (change the network addresses to match your network addresses!)

```

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.23.*
Allow From 192.168.13.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow from 192.168.23.*
Allow from 192.168.13.*
</Location>

```

Make your /etc/cups/cupsd-browsing.conf look like this
```

#
# Browsing: whether or not to broadcast and/or listen for CUPS printer
# information on the network.  Disabled by default.
#

Browsing On

```

Then restart CUPS

```
sudo /etc/init.d/cupsys restart
```

Check your firewall is not stopping port 631! On your client, your server, and your network switch!  I suggest using the latest Firestarter 1.0.3 (not the version that comes with Breezy), download it  from [http://www.fs-security.com/download.php]("http://www.fs-security.com/download.php") and install it using ```
dpkg -i
```

You do **not** have to uncomment the line starting with *application/octet-stream* in /etc/cups/mime.types and /etc/cups/mime.convs despite what you read elsewhere- as you are using a "raw" printer CUPS wont try to figure out what the print stream is.


Have fun!

Indulis

PS THis is the result of a VERY late night last night getting this working

---

### Post by savilash on 2006-07-16
Thank you for your ideas.  Will try them tonight when I get home.

---

### Post by tonywhelan on 2006-08-26
Not sure if you are still having trouble with this but I also have a Lexmark E230 connected to a fairly old and dumb print server box and also was a bit stumped trying to print from Ubuntu 6. 

Ended up using the generic driver for PCL6/PCL-XL as suggested by another forum user. I then chose "HP Jet Direct" from the network printer method dropdown list, and typed the IP address of my print server box into the "host" field and left the port number at the default (9100). Much to my surprise it worked. 

The margins are not quite right but it will do for now.

Tony Whelan
Canberra
----------------------

> **savilash said:**
> Hello Again

Having installed my first Linux OS (I chose Ubuntu on a recommendation), I am trying to install a networked printer.

The printer I have is a Lexmark E230 which is connected to the network via a HP JetDirect Print Server.  I have managed to download a printer driver from Lexmark which is for Debian.  Since I read Ubuntu is based on Debian, I thought this will work).  I stored it on my user drive, right clicked and used the Deb something to install the driver.

If I now go back to adding a printer, the printer driver that I installed does not appear.  I used a wrong driver previously and printed garbage.  So I know that the process of installing the printer is correct.  I simply do not know how to find the drivers that I installed.

Could someone help please ?

Thanking you all in advance.

---

### Post by savilash on 2006-08-27
Tony,

Thank you muchly for your reply.  

My reason for trying Ubuntu (or Linux) was to find a viable, easy to use alternative to Microshmuck's Windows.  It was also to setup a computer, separate from my main computer, to use for things like testing RAS, LimeWire etc.

I have come to the conclusion that to start delving in Linux, one has to be an "intermediate" user.  With Windows, you can be a "beginner" and still be able to install and use apps or devices.

Therefore, for the time being, I have decided to nuke the computer and go back to Microshmuck.  I haven't given up on Linux but may need to find an easier to use distro than Ubuntu or wait until Linux becomes more user-friendly.  I can now see why the take up of Linux in the corporate world is so low (I think).

Thanks all the same..


Sujay Vilash
Melbourne, Australia

---

