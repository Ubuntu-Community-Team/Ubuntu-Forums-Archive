---
title: "Cannot install Canon Pixma MG 2450"
date: 2014-03-12
forum: Installation &amp; Upgrades
---

### Post by adriansimo on 2014-03-12
Hello,

I try to install a Canon Pixma MG 2450. 

I get error: Printer 'Canon-MG2400' requires the '/usr/lib/cups/filter/pstocanonij' program but it is not currently installed.  Please install it before using this printer.

I am new in Linux.

Please help.

Thank you.

---

### Post by Mark Phelps on 2014-03-12
Welcome to the forums ...

But, you need to appreciate that the more you tell us, the more we can help you.

So, we need to know, in detail what > I try to install a Canon Pixma MG 2450.  means -- in other words, what exactly did you do?

---

### Post by adriansimo on 2014-03-12
Hello,

I have connected the printer to computer.
In Ubuntu 12.04 LTS in system settings in Printing I try to add printer.
I see in New Printer in Devices the printer. I click Forward. it start to search for printer driver. After a while New Printer, Choose Driver window opens. I select Provide PPD file. I select this file from printer driver I have downloaded from Canon site. After that it appears the error windows ¨Missing Driver¨, ¨Printer 'Canon-MG2400-series' requires the '/usr/lib/cups/filter/pstocanonij' program but it is not currently installed.  Please install it before using this printer.¨. I don´t know what to do further. I try to google for it but I was not able to find something helpful.



I have downloaded cnijfilter-source-4.00-1 from Canon site.
Under Add printer I select

---

### Post by pdc on 2014-03-12
Mark has very rightly asked if you can give us some information about what you did

If you were going to install the drivers that Canon supply for this printer you would go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100550001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550001.html)

and download and save [COLOR="#008000"]cnijfilter-mg2400series-4.00-1-deb.tar.gz[/COLOR] to your [COLOR="#0000FF"]Downloads[/COLOR] directory

the commands to install; that you would copy from here; and paste into a terminal; would be

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mg2400series-4.00-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg2400series-4.00-1-deb[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]

________________

if you haven't used a terminal, see here [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) and find it using Dash

_______________________

Canon supply [COLOR="#0000FF"]**ScanGearMP**[/COLOR] to run the scanner; (so SimpleScan will likely not work with this new device)

get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100551701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100551701.html)

and it comes down as [COLOR="#008000"]scangearmp-mg2400series-2.20-1-deb.tar.gz[/COLOR]

close the terminal after doing the above;

open it again and paste in 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf scangearmp-mg2400series-2.20-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd scangearmp-mg2400series-2.20-1-deb[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]

that should install it .........to run it.........

to open it, 

> [COLOR="#FF0000"]scangearmp[/COLOR]

and if you get a GUI and it runs, then you need to set up a launcher

---

### Post by adriansimo on 2014-03-12
@pdc

Thank you very much.

---

