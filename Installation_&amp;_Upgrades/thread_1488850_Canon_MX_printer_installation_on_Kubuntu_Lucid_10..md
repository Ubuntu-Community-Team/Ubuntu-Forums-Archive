---
title: "Canon MX printer installation on Kubuntu Lucid 10.04 AMD64"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by dscoggins on 2010-05-20
Canon MX320, MX330, MX860 printer installation on Kubuntu Lucid 10.04 AMD64 bit. I am sure Ubuntu Lucid is similar.

Once I upgraded to Lucid 10.04 AMD64 bit I found that getting a Canon Pixma MX printer installed was not going to be easy. So I thought it help others if I posted my experience here. To pull this off you will need both the Debian package, (.deb), and the source package from either

**Canon Europe:**
[http://software.canon-europe.com/products/0010699.asp](http://software.canon-europe.com/products/0010699.asp)

Or 

**Canon Australia:**
[http://www.canon.com.au/Support-Services](http://www.canon.com.au/Support-Services)

***NOTE: The only reason to get the source is to access the ppd files. They are in the Debian package but it is a lot more work to walk newbies through unpacking the .deb.***

Since there are errors in the source code it makes impossible to compile a driver. Therefore, you will need to install the 32bit Debian package and force the architecture, then add the correct printer driver from the ppd file in the source package. While these instructions worked for me there are a few assumption I make which mat affect your outcome. My MX860 has a wireless network connection. In other words I have no idea if this will or will not work on a USB attached printer. (If someone would be kind enough to post back if they get that configuration working that would be cool.) The other assumption is that the general reader is relatively new to Lunix and the command line interface. The commands were cut and pasted from my working kconsole, so they should work for anyone.

Here we go:
 1.Download the source and .deb packages from the Canon site

 2.Open a system console

 3.cd into the directory which contain the Canon packages

 4.Unpack Debian package – **sudo tar xzvf cnijfilter-mx860series-3.10-1-i386-deb.tar.gz**
```
/tmp/LinuxDrivers/Canon_Printer$ sudo tar xzvf cnijfilter-mx860series-3.10-1-i386-deb.tar.gz
cnijfilter-mx860series-3.10-1-i386-deb/
cnijfilter-mx860series-3.10-1-i386-deb/packages/
cnijfilter-mx860series-3.10-1-i386-deb/packages/cnijfilter-common_3.10-1_i386.deb
cnijfilter-mx860series-3.10-1-i386-deb/packages/cnijfilter-mx860series_3.10-1_i386.deb
cnijfilter-mx860series-3.10-1-i386-deb/install.sh
```

 5.Unpack source package – **sudo tar xzvf cnijfilter-source-3.10-1.tar.gz**
```
/tmp/LinuxDrivers/Canon_Printer$ sudo tar xzvf cnijfilter-source-3.10-1.tar.gz
cnijfilter-source-3.10/
cnijfilter-source-3.10/348/
cnijfilter-source-3.10/348/database/
cnijfilter-source-3.10/348/database/cnbpname348.tbl
cnijfilter-source-3.10/348/database/cifmx320.conf
cnijfilter-source-3.10/348/database/cnb_3480.tbl
cnijfilter-source-3.10/348/libs_bin/
…
cnijfilter-source-3.10/cngpij/cngpij/bjutil.c
cnijfilter-source-3.10/cngpij/cngpij/bjutil.h
cnijfilter-source-3.10/cngpij/cngpij/bjcups.h
cnijfilter-source-3.10/cngpij/cngpij/getipc.c
```

 6.Change to the *“packages”* directory of the Debian package – **cd cnijfilter-mx860series-3.10-1-i386-deb/packages**
```
/tmp/LinuxDrivers/Canon_Printer$ cd cnijfilter-mx860series-3.10-1-i386-deb/packages
```

 7.Install the general driver – **sudo dpkg --force-architecture -i cnijfilter-common_3.10-1_i386.deb**
```
/tmp/LinuxDrivers/Canon_Printer/cnijfilter-mx860series-3.10-1-i386-deb/packages$ sudo dpkg --force-architecture -i cnijfilter-common_3.10-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-common.
(Reading database ... 118452 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_3.10-1_i386.deb) ...
Setting up cnijfilter-common (3.10-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/tmp/LinuxDrivers/Canon_Printer/cnijfilter-mx860series-3.10-1-i386-deb/packages$
```

 8.Install the MX printer series driver – **sudo dpkg --force-architecture -i cnijfilter-mx860series_3.10-1_i386.deb**
***NOTE: The MX860 driver also works for the MX320 and MX330 printers***
```
/tmp/LinuxDrivers/Canon_Printer/cnijfilter-mx860series-3.10-1-i386-deb/packages$ sudo dpkg --force-architecture -i cnijfilter-mx860series_3.10-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-mx860series.
(Reading database ... 118468 files and directories currently installed.)
Unpacking cnijfilter-mx860series (from cnijfilter-mx860series_3.10-1_i386.deb) ...
Setting up cnijfilter-mx860series (3.10-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/tmp/LinuxDrivers/Canon_Printer/cnijfilter-mx860series-3.10-1-i386-deb/packages$
```

 9.You will complete the remainder of the Canon MX320 MX330 MX860 printer setup using the System Settings GUI:
***NOTE: these instructions may get a little tedious for those with more experience, but indulge me as I am writing to the “newby”***
 [INDENT]9.1.Access *“System Setting”* – Kickoff/Applications/Settings/System Settings
 9.2.Access *“Printer Configuration”* at the bottom of the window in the *“Computer Administration”* group
 9.3.Select “Printer Configuration”
 9.4.Select *“New Network Printer”* under the heading “*Add New Printer”* – Your printer will show up in the box on the left and right. Be patient it will take a little time to locate the printer . . .
 9.5.Once the window returns, you will see something like this *cnijnet:/00-00-85-F2-F2-E4* in the box under the *“Enter Device URI”*. Next select *“Forward”*
 9.6.In the next window change the selection from *“Select printer from database”* to *“Provide PPD file”* which is located at the bottom of the page
 9.7.Once selected the box under it will active, select the *“Browse”* button to the right of the active box
 9.8.In the pursuing window navigate to the *“ppd”* directory within the source package directory, in this example it's here: */tmp/LinuxDrivers/Canon_Printer/cnijfilter-source-3.10/ppd* and click on the appropriate ppd file – *canonmx320.ppd canonmx330.ppd or canonmx860.ppd*, then choose “Open”
 9.9.Next select “Forward” and print a test page. [/INDENT]

If it prints, crack open your favorite beverage and celebrate!

This How-To is adapted by me from [http://blog.fitzer.org/linux/canon-pixma-mx860-mit-ubuntu-linux-verwenden/](http://blog.fitzer.org/linux/canon-pixma-mx860-mit-ubuntu-linux-verwenden/) and translated from German to English by Google Chrome.

---

### Post by klytu on 2010-05-24
> **dscoggins said:**
> Canon MX320, MX330, MX860 printer installation on Kubuntu Lucid 10.04 AMD64 bit. I am sure Ubuntu Lucid is similar.

Once I upgraded to Lucid 10.04 AMD64 bit I found that getting a Canon Pixma MX printer installed was not going to be easy. So I thought it help others if I posted my experience here. To pull this off you will need both the Debian package, (.deb), and the source package from either

**Canon Europe:**
[http://software.canon-europe.com/products/0010699.asp](http://software.canon-europe.com/products/0010699.asp)

Or 

**Canon Australia:**
[http://www.canon.com.au/Support-Services](http://www.canon.com.au/Support-Services)

***NOTE: The only reason to get the source is to access the ppd files. They are in the Debian package but it is a lot more work to walk newbies through unpacking the .deb.***

Since there are errors in the source code it makes impossible to compile a driver. Therefore, you will need to install the 32bit Debian package and force the architecture, then add the correct printer driver from the ppd file in the source package. While these instructions worked for me there are a few assumption I make which mat affect your outcome. My MX860 has a wireless network connection. In other words I have no idea if this will or will not work on a USB attached printer. (If someone would be kind enough to post back if they get that configuration working that would be cool.) The other assumption is that the general reader is relatively new to Lunix and the command line interface. The commands were cut and pasted from my working kconsole, so they should work for anyone.

Here we go:
 1.Download the source and .deb packages from the Canon site

 2.Open a system console

 3.cd into the directory which contain the Canon packages

 4.Unpack Debian package – **sudo tar xzvf cnijfilter-mx860series-3.10-1-i386-deb.tar.gz**
```
/tmp/LinuxDrivers/Canon_Printer$ sudo tar xzvf cnijfilter-mx860series-3.10-1-i386-deb.tar.gz
cnijfilter-mx860series-3.10-1-i386-deb/
cnijfilter-mx860series-3.10-1-i386-deb/packages/
cnijfilter-mx860series-3.10-1-i386-deb/packages/cnijfilter-common_3.10-1_i386.deb
cnijfilter-mx860series-3.10-1-i386-deb/packages/cnijfilter-mx860series_3.10-1_i386.deb
cnijfilter-mx860series-3.10-1-i386-deb/install.sh
```

 5.Unpack source package – **sudo tar xzvf cnijfilter-source-3.10-1.tar.gz**
```
/tmp/LinuxDrivers/Canon_Printer$ sudo tar xzvf cnijfilter-source-3.10-1.tar.gz
cnijfilter-source-3.10/
cnijfilter-source-3.10/348/
cnijfilter-source-3.10/348/database/
cnijfilter-source-3.10/348/database/cnbpname348.tbl
cnijfilter-source-3.10/348/database/cifmx320.conf
cnijfilter-source-3.10/348/database/cnb_3480.tbl
cnijfilter-source-3.10/348/libs_bin/
…
cnijfilter-source-3.10/cngpij/cngpij/bjutil.c
cnijfilter-source-3.10/cngpij/cngpij/bjutil.h
cnijfilter-source-3.10/cngpij/cngpij/bjcups.h
cnijfilter-source-3.10/cngpij/cngpij/getipc.c
```

 6.Change to the *“packages”* directory of the Debian package – **cd cnijfilter-mx860series-3.10-1-i386-deb/packages**
```
/tmp/LinuxDrivers/Canon_Printer$ cd cnijfilter-mx860series-3.10-1-i386-deb/packages
```

 7.Install the general driver – **sudo dpkg --force-architecture -i cnijfilter-common_3.10-1_i386.deb**
```
/tmp/LinuxDrivers/Canon_Printer/cnijfilter-mx860series-3.10-1-i386-deb/packages$ sudo dpkg --force-architecture -i cnijfilter-common_3.10-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-common.
(Reading database ... 118452 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_3.10-1_i386.deb) ...
Setting up cnijfilter-common (3.10-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/tmp/LinuxDrivers/Canon_Printer/cnijfilter-mx860series-3.10-1-i386-deb/packages$
```

 8.Install the MX printer series driver – **sudo dpkg --force-architecture -i cnijfilter-mx860series_3.10-1_i386.deb**
***NOTE: The MX860 driver also works for the MX320 and MX330 printers***
```
/tmp/LinuxDrivers/Canon_Printer/cnijfilter-mx860series-3.10-1-i386-deb/packages$ sudo dpkg --force-architecture -i cnijfilter-mx860series_3.10-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-mx860series.
(Reading database ... 118468 files and directories currently installed.)
Unpacking cnijfilter-mx860series (from cnijfilter-mx860series_3.10-1_i386.deb) ...
Setting up cnijfilter-mx860series (3.10-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/tmp/LinuxDrivers/Canon_Printer/cnijfilter-mx860series-3.10-1-i386-deb/packages$
```

 9.You will complete the remainder of the Canon MX320 MX330 MX860 printer setup using the System Settings GUI:
***NOTE: these instructions may get a little tedious for those with more experience, but indulge me as I am writing to the “newby”***
 [INDENT]9.1.Access *“System Setting”* – Kickoff/Applications/Settings/System Settings
 9.2.Access *“Printer Configuration”* at the bottom of the window in the *“Computer Administration”* group
 9.3.Select “Printer Configuration”
 9.4.Select *“New Network Printer”* under the heading “*Add New Printer”* – Your printer will show up in the box on the left and right. Be patient it will take a little time to locate the printer . . .
 9.5.Once the window returns, you will see something like this *cnijnet:/00-00-85-F2-F2-E4* in the box under the *“Enter Device URI”*. Next select *“Forward”*
 9.6.In the next window change the selection from *“Select printer from database”* to *“Provide PPD file”* which is located at the bottom of the page
 9.7.Once selected the box under it will active, select the *“Browse”* button to the right of the active box
 9.8.In the pursuing window navigate to the *“ppd”* directory within the source package directory, in this example it's here: */tmp/LinuxDrivers/Canon_Printer/cnijfilter-source-3.10/ppd* and click on the appropriate ppd file – *canonmx320.ppd canonmx330.ppd or canonmx860.ppd*, then choose “Open”
 9.9.Next select “Forward” and print a test page. [/INDENT]

If it prints, crack open your favorite beverage and celebrate!

This How-To is adapted by me from [http://blog.fitzer.org/linux/canon-pixma-mx860-mit-ubuntu-linux-verwenden/](http://blog.fitzer.org/linux/canon-pixma-mx860-mit-ubuntu-linux-verwenden/) and translated from German to English by Google Chrome.

Nice post! I figured this out last March and was considering writing a How-To on it myself. 

Did you compile the sane-backend for the scanner as well? I did that and got the scanner working on the PIXMA MX330 on Kubuntu 10.04 64-bit. It works well so far, but I can only scan as root. Just curious as to if you tried this and if you had the same issue.

---

### Post by francois138 on 2010-05-28
Thank you so much for this tutorial ! 

I'm happy to say that this works for MX320 series, connected via USB. 


FYI, I'm running Ubuntu Lucid Lynx 64bit, on a HP DV6 series laptop, Intel core i7.



Thank you again.

---

### Post by Jason Argonaut on 2010-05-29
> **klytu said:**
> Nice post! I figured this out last March and was considering writing a How-To on it myself. 

Did you compile the sane-backend for the scanner as well? I did that and got the scanner working on the PIXMA MX330 on Kubuntu 10.04 64-bit. It works well so far, but I can only scan as root. Just curious as to if you tried this and if you had the same issue.



Good answers, thanks dscoggins & klytu.
Just like klytu, neither scan/sane nor fax work for me & my Pixma MX320 all-in-one.
Is this a Permissions issue (User Accounts)?    To my User permissions I added lp, sane, fax, + a few other groups, no luck.
Suggestions?

---

### Post by WinRiddance on 2010-05-29
The first 5 Ubuntus that I ever installed on 3 different machines with 3 different printers all showed the same initial result ... no printer installed. When I trid to install a printer a message told me that there were no manufacturer files available. This was all pretty confusing to me since I'd gotten used to Windows demanding manufacturer drivers for 99% of all hardware.
It wasn't until I researched this issue further that I found out that the default recommended Ubuntu driver will almost always work. Perhaps not with all of the Windows based features, but working properly nonetheless.

Since then I've installed at least 8 different printers by 5 different manufacturers with the default Ubuntu recommendations, ranging from all in one devices to B&W lasers and color laser printers. Moral of the story ... go ahead and look for manufacturer printers/files when you first install Ubuntu and a printer, but if you can't find any try the default printer settings instead. You might just be surprised ....

---

### Post by cliff01 on 2010-05-29
That worked. Thank you for the tutorial.

---

### Post by klytu on 2010-05-29
> **Jason Argonaut said:**
> Good answers, thanks dscoggins & klytu.
Just like klytu, neither scan/sane nor fax work for me & my Pixma MX320 all-in-one.
Is this a Permissions issue (User Accounts)?    To my User permissions I added lp, sane, fax, + a few other groups, no luck.
Suggestions?

I got scanning working on my PIXMA MX330 as a regular user in Kubuntu 10.04 64-bit a couple of days ago. (I don't have this problem in 32-bit Ubuntu.) I'm also unable to fax via Ubuntu or Kubuntu with the MX330 via the fax printer; but of course, faxing works fine using the unit as one would a regular fax machine.

First of all I had compiled the sane back-end as per the instructions here:

[[COLOR="Blue"]_http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html_[/COLOR]]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html")

The section "set non-root user permissions" from the linked page above gave me the clues I needed to get this working. The PIXMA scanning backend is accessed via udev in 64-bit Kubuntu (I would guess it's the same for Ubuntu as well.) I found a file named *libsane.rules* after compiling the sane back-end. I searched the file for MX330 and changed the mode from "0664" to "0666" and saved the file (as root) in the **/etc/udev/rules.d** directory as *70-libsane.rules*. Then I re-booted and could scan as a normal user. I looked at the file and found an entry for the MX320 listed right above the entry for the MX330, so something like this might work for you as well. You might need to back-up and rename an existing *xx-libsane.rules* file before trying this; I didn't need to. I've attached an unedited copy of the file "libsane.rules" to this post.

I gave just a quick summary of the steps I took, if you need more details read through the comments at the bottom of the linked web page above. Of course if you post questions here I'll help if I can.

---

### Post by rdunnion on 2010-06-05
Hi. I am attempting to get my mx860 working on Ubuntu 10.04. I have followed the above directions and am using a USB connection. I can install the printer but when I try and print a test page I get "pstocanonij failed". Also I compiled the sane backend and cannot get my scanner to be seen either. Can anyone help me with this? Thank you. - Ryan

---

### Post by rdunnion on 2010-06-05
My scanner is now working. I uninstalled the sane package that I had installed from the repo and recompiled the sane-backend. Now it works with xsane and simple scan. However I am still trying to get the printer working.

---

### Post by gengbinich on 2010-07-05
I just tried in my Ubuntu 10.04 amd64 with USB conection and  it works  for my MX320!  But it was easier.
Just follow the command line instructions given in the first post with  the USB cable disconnected.  Then, instead of going to the "printers  configuration", just connect the USB cable and it should configure  automatically :KS:KS

Thank you very much! And thank you for being newbie friendly :)

---

### Post by dhalbert on 2010-07-05
On 64-bit Lucid Ubuntu, I had to install the ia32-libs package before this would work. You may have already installed the 32-bit libraries for other reasons and would not encounter this problem. The telling thing was that the printer was not detected when using the GUI to add the printer, and running the printer detector by hand did not work:

```
$ /usr/lib/cups/backend/cnijnet 
bash: /usr/lib/cups/backend/cnijnet: No such file or directory

$ file /usr/lib/cups/backend/cnijnet 
/usr/lib/cups/backend/cnijnet: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped

$ sudo apt-get install ia32-libs
[...]

$ # now it works
$ /usr/lib/cups/backend/cnijnet 
network cnijnet:/00-11-AB-EF-22-88 "Canon MX860 series" "Canon-MX860-series_00-11-AB-EF-22-88"
```

---

### Post by GilbertOstlethwaite on 2010-09-15
Just a quick note to say that installing the MX860 drivers didn't work for me. I then tried the MX320 specific drivers with the USB unplugged using the same instructions. Then I plugged in the USB cable and the printer auto-configured and prints perfectly.

I also downloaded the scangear drivers and used the same procedure to install the common and mx320 portions - but no joy, niether Simple Scan or XSane will recognize the scanner. Any ideas?

Regards

---

### Post by klytu on 2010-09-16
> **GilbertOstlethwaite said:**
> Just a quick note to say that installing the MX860 drivers didn't work for me. I then tried the MX320 specific drivers with the USB unplugged using the same instructions. Then I plugged in the USB cable and the printer auto-configured and prints perfectly.

I also downloaded the scangear drivers and used the same procedure to install the common and mx320 portions - but no joy, niether Simple Scan or XSane will recognize the scanner. Any ideas?

Regards

Take a look at my last post in this thread (from May 29, 2010). You might be able to get Xsane to work with your scanning following that procedure.

---

### Post by sushiseru on 2010-09-16
Hm... I was going to trying the MX drivers with my MP610... but hten you posted that link :*

Problem is... every time I install it ... I seem to get broken dependencies...and I can't install anything after that because well i have broken packages >:x

You think the MX drivers would work with the MP610? Maybe not specifically with the 610, but an MP build printer.. :o?

---

### Post by klytu on 2010-09-16
> **sushiseru said:**
> Hm... I was going to trying the MX drivers with my MP610... but hten you posted that link :*

Problem is... every time I install it ... I seem to get broken dependencies...and I can't install anything after that because well i have broken packages >:x

You think the MX drivers would work with the MP610? Maybe not specifically with the 610, but an MP build printer.. :o?

Did you try the drivers found here: 

[http://software.canon-europe.com/products/0010488.asp]("http://software.canon-europe.com/products/0010488.asp")

If you did, what broken dependencies do you have?

---

### Post by Spinland on 2010-10-19
Just wanted to report full success using the original post.  Running Ubuntu 10.10 (64 bit), and successfully printed a test page to an MX860 wirelessly, never had to use a USB cable.  The only change was the location of the printer setup GUI:  System/Administration/Printing.  The network printer option discovered the wireless MX860 after only a couple of seconds.

Printer was wirelessly connected to a Cisco wireless router.

Thanks!

---

### Post by Sizarro on 2010-11-05
[FONT=Trebuchet MS][SIZE=2][COLOR=Navy]Excellent thread and work; very helpful.  I had explored the same about a year ago and the following has worked for me several times after performing clean Ubuntu installs including Ubuntu 10.10.  I too have a Canon MX860 configured wirelessly.  The procedure is similar to the original post, just slightly simpler:

[SIZE=3]Go to the Canon site in Australia and download the [Linux debian driver for the MX860]("http://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwMTg3NzAx&cmp=ABS&lang=EN").  After unpackaging the compressed driver:
[/SIZE][/COLOR][/SIZE][/FONT][INDENT][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]1. First, install cnijfilter-common_3.10-1_i386.deb[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]2. Second, install cnijfilter-mx860series_3.10-1_i386.deb[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]3. Restart Ubuntu[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]4. System -> Adminstration -> Printing -> New[/COLOR][/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=2][COLOR=RoyalBlue]It should search for and find the Canon- MX860 printer as a Network Printer with a device URI that looks like: cnijnet:/00-1E-8F-72-E6-2H[/COLOR][/SIZE][/FONT]
[/INDENT][SIZE=2][COLOR=Navy]Using the procedure above, both the printing and scanning functions work for me on the MX860.[/COLOR][/SIZE]

---

### Post by noob555 on 2010-11-10
> **klytu said:**
> I got scanning working on my PIXMA MX330 as a regular user in Kubuntu 10.04 64-bit a couple of days ago. (I don't have this problem in 32-bit Ubuntu.) I'm also unable to fax via Ubuntu or Kubuntu with the MX330 via the fax printer; but of course, faxing works fine using the unit as one would a regular fax machine.

First of all I had compiled the sane back-end as per the instructions here:

[[COLOR="Blue"]_http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html_[/COLOR]]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html")

The section "set non-root user permissions" from the linked page above gave me the clues I needed to get this working. The PIXMA scanning backend is accessed via udev in 64-bit Kubuntu (I would guess it's the same for Ubuntu as well.) I found a file named *libsane.rules* after compiling the sane back-end. I searched the file for MX330 and changed the mode from "0664" to "0666" and saved the file (as root) in the **/etc/udev/rules.d** directory as *70-libsane.rules*. Then I re-booted and could scan as a normal user. I looked at the file and found an entry for the MX320 listed right above the entry for the MX330, so something like this might work for you as well. You might need to back-up and rename an existing *xx-libsane.rules* file before trying this; I didn't need to. I've attached an unedited copy of the file "libsane.rules" to this post.

I gave just a quick summary of the steps I took, if you need more details read through the comments at the bottom of the linked web page above. Of course if you post questions here I'll help if I can.

Thank you.  I had the same scanning permission problem on Linux Mint 9 (aka Ubuntu Lucid) 32-bit and followed your instructions.  Worked like a charm.  Now I can scan to my heart's content.

---

### Post by Goody1959 on 2011-02-27
> **klytu said:**
> I got scanning working on my PIXMA MX330 as a regular user in Kubuntu 10.04 64-bit a couple of days ago. (I don't have this problem in 32-bit Ubuntu.) I'm also unable to fax via Ubuntu or Kubuntu with the MX330 via the fax printer; but of course, faxing works fine using the unit as one would a regular fax machine.

First of all I had compiled the sane back-end as per the instructions here:

[[COLOR="Blue"]_http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html_[/COLOR]]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html")

The section "set non-root user permissions" from the linked page above gave me the clues I needed to get this working. The PIXMA scanning backend is accessed via udev in 64-bit Kubuntu (I would guess it's the same for Ubuntu as well.) I found a file named *libsane.rules* after compiling the sane back-end. I searched the file for MX330 and changed the mode from "0664" to "0666" and saved the file (as root) in the **/etc/udev/rules.d** directory as *70-libsane.rules*. Then I re-booted and could scan as a normal user. I looked at the file and found an entry for the MX320 listed right above the entry for the MX330, so something like this might work for you as well. You might need to back-up and rename an existing *xx-libsane.rules* file before trying this; I didn't need to. I've attached an unedited copy of the file "libsane.rules" to this post.

I gave just a quick summary of the steps I took, if you need more details read through the comments at the bottom of the linked web page above. Of course if you post questions here I'll help if I can.
Thanks for the link! I have an MX330 working for Printing(dscoggins post), and now Scanning! (klytu post) Thank you guys. I was going nuts and probably making mistakes out of frustration till I read this thread.

---

### Post by frasier0 on 2011-07-10
I was able to install the ia32-libs and my Ubuntu 11.04 system recognized my MX-860 network printer.  I printed the test page and have not had a chance to test other features yet.
Tim

---

### Post by afrazin on 2011-10-05
I'm having a problem installing this on my machine using Ubuntu 11.04,  AMD64.  I have a Pixma MX320.  I tried following these instructions, but  i'm getting package dependencies which are odd:

```
alan@devserver:~/cnijfilter-mx320series-3.10-1-i386-deb/packages$  sudo dpkg --force-architecture -i cnijfilter-common_3.10-1_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 152767 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.10-1 (using cnijfilter-common_3.10-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386

```then when i tried to apt-get those, i got the response that they were all up to date:
```
alan@devserver:~/cnijfilter-mx320series-3.10-1-i386-deb/packages$ sudo apt-get install libc6 libcupsys2 libcups2 libpopt0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libcups2' instead of 'libcupsys2'
libc6 is already the newest version.
libpopt0 is already the newest version.
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```that's as far as i got (basically to #7).  any suggestions would be MUCH appreciated!

---

