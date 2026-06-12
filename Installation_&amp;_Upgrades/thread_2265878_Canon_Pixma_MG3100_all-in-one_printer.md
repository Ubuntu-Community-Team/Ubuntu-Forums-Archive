---
title: "Canon Pixma MG3100 all-in-one printer"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by gordon99 on 2015-02-18
Last October I was shown, on this forum, how to install a driver for a shared Canon Pixma MG3100 all-in-one printer. I needed this because the database driver on Xubuntu, a CUPS + Gutenprint, caused the shared printer to perform at a snails pace when printing from my Xubuntu OS. The Canon driver worked a treat.

Unfortunately I have recently had to re-install Xubuntu and, amateur that I am, I failed to back up some settings resulting in the need to re-install the Canon printer driver.
I have followed the previous guidelines for installing the Canon driver but, when I go through the "Add Printer" procedure, the option to use the Canon driver does not show and I am stuck with the Gutenprint driver. As I originally installed Xubuntu during August, or thereabouts, last year I rather assume that there have been no significant changes to the OS. I would be grateful for any help in retrieving the situation.

 I give below the commands I previously used which worked then but seemingly not now. You will see that it involved installing "libtiff4" and Canon driver 3.60.

[COLOR=#000000]"as it is the 3.6 version, it needs libtiff 4 that ubuntu has withdrawn, so get the libtiff4 from Debian [/COLOR][ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/)[COLOR=#000000] and go about 14 down the list to find either the 32 or 64bit".
[/COLOR]
[COLOR=#000000]"Go here [/COLOR][http://support-asia.canon-asia.com/c...02.html?r=s&q=]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html?r=s&q=")[COLOR=#000000] and download and SAVE what is [/COLOR][COLOR=#008000]cnijfilter-mg3100series-3.60-1-deb.tar.gz"
[/COLOR]
[COLOR=#FF0000]cd Downloads
[/COLOR]
[COLOR=#FF0000]tar -zxvf cnijfilter-mg3100series-3.60-1-deb.tar.gz
[/COLOR]
[COLOR=#FF0000]cd cnijfilter-mg3100series-3.60-1-deb./install.sh[/COLOR][COLOR=#FF0000]

 [/COLOR][COLOR=#000000].....first can we check that libtiff4 is installed 

[/COLOR][COLOR=#000000][I][COLOR=#FF0000]dpkg -l | grep libtiff4
[/COLOR]
[/I][/COLOR][COLOR=#000000]if you get a yes, then move on to the below 
[/COLOR][COLOR=#000000]
[/COLOR]*[COLOR=#FF0000]cd Downloads/cnijfilter-mg3100series-3.60-1-deb/packages/[/COLOR]*

*[COLOR=#FF0000]sudo dpkg -i cnijfilter-common_3.60-1_amd64.deb[/COLOR]*[COLOR=#000000]
[/COLOR]
[COLOR=#000000]*[COLOR=#FF0000]sudo dpkg -i cnijfilter-mg3100series_3.60-1_amd64.deb[/COLOR]*[/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000]......... that should install the drivers and should create the needed entries.                                           
[/COLOR]

---

### Post by pdc on 2015-02-18
Hi gordon99;

so you need libtiff4 installed; I hope the how-to for that works; 

to install the driver, get from where advised: if I paste the commands to install below: each is pasted line by line into the terminal and hit ENTER after each paste .............

[COLOR="#FF0000"]cd Downloads

tar -zxvf cnijfilter-mg3100series-3.60-1-deb.tar.gz

cd cnijfilter-mg3100series-3.60-1-deb

./install.sh[/COLOR]

crucially that last command activates the install script; you shouldn't need to "ADD A NEW PRINTER" as the install script should do all that for you; 

if you look in CUPS after the script has finished; [http://localhost:631/printers/](http://localhost:631/printers/)

............that lists the printer registrations that have been setup in *lpadmin* so look to the leftmost column: [COLOR="#0000FF"]Queue Name[/COLOR] and then to the rightmost column: **Make & Model**

the Canon drivers will be listed in column 4 as Canon MG3100 series Ver.3.60 so identify the name they have been given from the leftmost column and I would suggest selecting that each time; 

and with if you open the PRINTERS option in the menu you can see which is set as default printer and you could change that too....................let us know how it all goes

---

### Post by gordon99 on 2015-02-20
Hello again pdc.
 Thank you for once again for coming to my assistance with this printer problem. This time, unfortunately, I seem to be getting nowhere. Can I firstly show you the outcomes, from terminal, for the libtiff 4 and the Canon printer-driver installations.

" gordon@gordon-Presario-CQ56-Notebook-PC:~$ dpkg -l | grep libtiff4
ii  libtiff4:amd64                              3.9.6-11                              amd64        Tag Image File Format (TIFF) library (old version)
gordon@gordon-Presario-CQ56-Notebook-PC:~$ "


"gordon@gordon-Presario-CQ56-Notebook-PC:~/Downloads/cnijfilter-mg3100series-3.60-1-deb$ ./install.sh
[sudo] password for gordon: 
==================================================


Canon Inkjet Printer Driver
Version 3.60
Copyright CANON INC. 2001-2011
All Rights Reserved.


==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.60-1_amd64.deb
(Reading database ... 190888 files and directories currently installed.)
Preparing to unpack .../cnijfilter-common_3.60-1_amd64.deb ...
Unpacking cnijfilter-common (3.60-1) over (3.60-1) ...
Setting up cnijfilter-common (3.60-1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
Command executed = sudo dpkg -iG ./packages/cnijfilter-mg3100series_3.60-1_amd64.deb
(Reading database ... 190888 files and directories currently installed.)
Preparing to unpack .../cnijfilter-mg3100series_3.60-1_amd64.deb ...
Unpacking cnijfilter-mg3100series (3.60-1) over (3.60-1) ...
Setting up cnijfilter-mg3100series (3.60-1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
status: Unknown job: cups


#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key."

If I then go to 'localhost:etc' it shows 'No Printer.' If I next go through the 'add printer' routine I am given no alternative to the Gutenprint driver and 'localhost' shows the printer and Gutenprint driver.
As I said in my first message, I had to re-install Xubuntu which now shows as version 14.04.1 whereas the first version I installed was 14.04. However I always download software updates so I was probably using v.14.04.1 when something went seriously wrong necessitating an OS re-install. I see, by the way, that there seems to be a libtiff4-dev available in Ubuntu Software Centre but I have ignored this. Maybe this is why Terminal says [old version].
I am doubtless making an elementary mistake(s) somewhere along the line but cannot even guess where.

---

### Post by pdc on 2015-02-21
.............so seems like libtiff4 is installed and available; that's good

so this is a usb connection: printer to computer? If you could type ```
lsusb
``` in a terminal to verify the computer sees the device; and if you could paste this command ```
/usr/sbin/lpinfo -v
```    .........it is asking the info section of lp (linux printing) for a full (v=verbose) printout of any and all printers linked to it 

I think this message > [COLOR="#FF0000"]status: Unknown job: cups[/COLOR]  is concerning..............when I google on it, various complex issues are reported; that surfaced with 14.04

---

### Post by gordon99 on 2015-02-22
Good morning pdc.

I confirm that the printer is connected to the host PC by cable .

Please see the results below of the Terminal enquiries made with the the printer and host PC both switched on:

gordon@gordon-Presario-CQ56-Notebook-PC:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05c8:0213 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
gordon@gordon-Presario-CQ56-Notebook-PC:~$ /usr/sbin/lpinfo -v
network ipps
network https
network ipp14
network http
network socket
network ipp
network lpd
direct hp
network smb
direct hpfax
gordon@gordon-Presario-CQ56-Notebook-PC:~$

---

### Post by pdc on 2015-02-22
when I type ```
lsusb
``` .........in the terminal........with the printer turned on..........our Canon printer shows up as .........

> Bus 001 Device 010: ID 04a9:1752 Canon, Inc.

......... I can't see yours saying hello to us all; so.............not plugged in.......not turned on.........cable not connected........usb hub interfering in some way.......... the usual suspects.....I think you need it to show up on lsusb ..................

_____________________________--

similarly, it does not feature on ```
/usr/sbin/lpinfo -v
```            even if not registered, it should feature in that list ..........

eg our Canon shows up as > direct usb://Canon/MG3100%20series?serial=402E18&interface=1

..........and that type of ID then allows you to register the printer saying ........that is the one I want you to use............with that ppd file .......................

---

### Post by gordon99 on 2015-02-23
The fact that the printer works, be it ever so slowly, shows that the connections are there I would assume. I will, however, go back very carefully over the set up procedures. The fact that I was able to install the Canon driver and thereby solve the printing speed problem just a few months ago leads me to believe it can be done again. Thank you for your time and trouble. I will keep this thread open for the present and report back if (and how) I have success.

---

### Post by pdc on 2015-02-23
thanks Gordon; would you consider swapping some of the usb connections around; ........is the Canon connected to a mult-port hub? .........it would be very reassuring to have it recognised on the ```
lsusb
``` command; ...............sort of like a school rollcall ..... present and correct sir ...

---

### Post by gordon99 on 2015-02-25
Good afternoon (or whenever it is where you are) pdc. After five hours or so of trial and error I seem to have found a solution as follows:-

When adding a printer one gets to the "Choose a Driver" page where one can (a) Select a printer from the database, or (b) Provide a PPD file, or (c) Search for printer driver to download.
Normally I have been selecting  (a) anticipating that the Canon proprietary driver would show up, as it did before, though not now. I have been selecting (c) a few times of late in the hope that the Canon driver would just appear but it never did. In fact it usually caused things to freeze while the system searched for the driver it never found.
Today I tried to find out a bit more about PPD files.  Most of what I read went over my head, but I was at the stage when I would follow any lead to solve the problem. I googled 'Where are PPD files in Xubuntu' and in 'Linux Questions' I found an answer which was "usr/share/cups/model/". This revealed the file 'canonmg3100.ppd'.

I then went back to option (b) and clicked the folder icon which is within the option (b) answer box. This brought up the HOME/USERNAME file list and a click to the left of HOME got me into the File System file list within which I was able to navigate to the 'canonmg3100.ppd' file. Opening this file put its address into the option (b) answer box and selecting 'Forward' followed by 'Apply' added the printer to the system.
With fingers crossed I tried  printing two .odt documents and to my surprise and pleasure I found that the printer churned out the documents at normal speed. I then entered the commands 'lsusb'  and '/usr/sbin/lpinfo -v' in Terminal, but neither came up with replies showing the Canon printer.
Whether the PPD file will allow the printing of files other than documents I have yet to investigate and why the Canon driver is not appearing in 'Select a Printer from the database' is a mystery to me .
If anyone has any observations regarding the use of the PPD file I would be pleased to read them.

---

### Post by pdc on 2015-02-25
well done Gordon;

when one does a command line registration of a printer: meaning one is saying to the computer: when I tell you to print with the printer I call MYFRED please use this ppd file; and by the way, you can find MYFRED at this address ..............his device-uri .......so you know where he hangs out ..

the language is ```
 /usr/sbin/lpadmin -p [printer_name] -m [PPD_filename] -v [device-uri] -E
```

so that means you are telling lpadmin to use MYFRED and use the MYFRED.ppd file and by the way he lives at MYFRED_CAFE  ```
 sudo /usr/sbin/lpadmin -p MYFRED -m MYFRED.ppd -v MYFRED_CAFE -E
```

__________________

so you have used CUPS to do that; so very well done; and very well done to sort it all out; .................there is something awry with printer registration at present; we got a new MG5500 recently; and when I ran the Canon install script; it could not find the printer; even though lsusb showed it; so something, somewhere, is aberrant ............ your printer should be fine and enjoy!

PS as I think you started the thread, you can edit THREAD TOOLS and mark it SOLVED

---

### Post by gordon99 on 2015-02-25
Thank you very much pdc.

---

