---
title: "Installation for Epson Artisan 837 on Ubuntu 12.04"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by sgravy on 2012-11-26
Everytime I think that I have found a driver to install my Epson printer I download, write to disc, try and install and nothing happens. Wow, maybe I just need a step by step on how to install this printer? 

Any help would be great!

---

### Post by Arcturus691 on 2012-11-27
From what I understand, you should be able to plug it in and have ubuntu install the drivers automatically.  I am assuming you tried that so the next thing is to go to the epson site.  They have linux drivers at: 

[http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=182960&infoType=Downloads&platform=OSF_O_LINUX]("http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=182960&infoType=Downloads&platform=OSF_O_LINUX")

I noticed if you click on the more info link on that page they have a linux manual and the linux drivers.   

I just bought this printer and as soon as the order comes in I will be installing it on kubuntu 12.10

---

### Post by pdc on 2012-11-27
hi sgravy:

as the previous post said, 

if you start here

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

and enter 837 you get here

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

and if you click on the top line for a download of the printer driver you get

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16835&DSCCHK=533066162390ff672db35fb2000e2efed4d1536a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16835&DSCCHK=533066162390ff672db35fb2000e2efed4d1536a)

click accept and you get

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16835&DSCCHK=533066162390ff672db35fb2000e2efed4d1536a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16835&DSCCHK=533066162390ff672db35fb2000e2efed4d1536a)

........problem is you don't tell us if you have 32bit or 64bit installed....

...... as you are using Ubuntu, you need either the [COLOR="SeaGreen"]i386.deb[/COLOR] or the [COLOR="SeaGreen"]amd64.deb[/COLOR] when you remember which version you installed

.......as you click to download, gdebi installer should jump in and offer to help ............let it...........

you can then install the scanner drivers ...........

.........from here..........

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5)

but you **MUST FIRST INSTALL THE** > [COLOR="Magenta"]iscan-data_1.19.0-1_all.deb[/COLOR] ..... it is at the BOTTOM of the page !!

.........then ......install 

..either ...........[COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb[/COLOR] for 32bit 

.. or ..............[COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb[/COLOR] for 64bit

..... *you can also see there are ltd3.deb and ltd7.deb packages available in both the 32bit and 64bit flavours: you need the [COLOR="SeaGreen"]ltd7[/COLOR] as it is for newer kernels*....

....let us know how it all goes

---

### Post by sgravy on 2012-11-27
Thanks. I just got the info and I will be working on it.... hopefully tonight. I will let you know how it goes!

---

