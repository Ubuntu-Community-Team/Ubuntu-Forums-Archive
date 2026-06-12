---
title: "Canon Pixma iP1900 series"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by tjandracom on 2008-11-13
does anyone know where to find Dapper/Hardy driver for Canon Pixma iP1900 series. (Exact model is Pixma iP1980).
i have tried driver for Pixma iP1800 and it doesn't work. thanks.

---

### Post by tjandracom on 2008-11-15
^^^^bump^^^^

---

### Post by tjandracom on 2008-11-18
It works now (but only on Hardy), using Canon ip1800series driver from:

[http://caletalinux.blogspot.com/2007/07/canon-ip1800-drivers-en-ubuntu-feisty.html](http://caletalinux.blogspot.com/2007/07/canon-ip1800-drivers-en-ubuntu-feisty.html) 

i guess it will never work on Dapper. i have tried to convert the package with alien in Dapper, but still doesn't work. :(

---

### Post by styven on 2009-02-07
Hi there,

I found these .debs on the Canon website,they are for Version 3 of the Debian Linux printer driver. They are for the ip1900 canon printer.

Would these work and on which distribution dapper, hardy, heron, feisty?

Steve.

---

### Post by tjandracom on 2009-04-06
thank's. but since i have migrated to hardy, i can't tell whether these will work on dapper or not. 

edgy, and feisty is no longer supported, and dapper and gutsy will be obsolete soon, so i guess the problem will naturally disappeared as the time move on. so i will mark this as solved.

---

### Post by cancuen on 2009-04-09
Hi. I've installed, properly this printer, after a while. I'm a Kubuntu Intrepid User. Greetings from Guatemala.

If you have troubles installing this printer, delete all references/tries/fails/etc related to this printer. Let's do it as we just brought from the store knowing all we need to know.

Turn off the printer (and/or unplug if necesary/wanted).

You have to download the drivers in canon-europe's site. The drivers are at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp). 
Find under "Operating System > Linux" and download "Debian Linux Printer Driver (3.0)".
Download to a folder (it's own folder) anywhere (better desktop). Then, let's go to konsole (or equivalent).

First we must install libcupsys2 with the following order:
$ sudo apt-get install libcupsys2
Next go to folder we used to download the driver:
$ cd /path/to/your/folder
Next we need to untar the dowloaded file
$ tar -xf iP1900_debian_printer.tar
Now we will have 3 files on this folder (+ original tar downloaded file).
(In my case I've untargz the "tar.gz" file inside, but don't think that this is necessary, how ever if you wanted or need to doit:
$ tar xvzf cnijfilter-common-3.00-1.tar.gz)
Then let's install:
$ sudo dpkg -i *deb
This will install the two deb packages included in the downloaded tar file that will install the proper drivers in the computer database.

Now that are installed, exit the konsole and then let's go to CUPS web manager in our favorite browser (firefox rocks) to [http://127.0.0.1:631](http://127.0.0.1:631)

In the page go to Admin and find the button that says "Find new printer" and then follow the assistant. 

Hope this helps someone. If you have troubles finding out what to download, this is the file my browser reports as downloaded:
[http://software.canon-europe.com/files/soft31335/software/iP1900_debian_printer.tar](http://software.canon-europe.com/files/soft31335/software/iP1900_debian_printer.tar)

Feed back with comments.

Mario Soto
mariosoto [at sign here] cancuen [dot here] net

---

### Post by tjandracom on 2009-04-15
thanks cancuen. welcome to the forum, don't hesitate to post more on this forum.

as far as i know, this printer is just work in hardy and later (including Intrepid) without needing additional drivers.
but thanks for the info anyway. i just know that canon is officially releasing driver for linux. and because this driver is came from canon, it's supposedly better than the common driver included in the ubuntu packages.

---

### Post by luispic on 2009-05-19
Gracias! cancuen, I'm kindda new to this ubuntu and stuff, just installed the 9.04 "Jaunty Jackalope" (what is the deal with those names!!??) and my canon ip1900 didn't work but after installing the .deb downloaded from the canon website you gave, I switched my printer again it recognized it automatically and its now working.

(I'm only using english to keep the "universality" of the forum) I'm also from Guate!!

cheers!

---

### Post by hrimhari on 2009-05-27
Hello,

Please update your post if your problem has been solved or even to mention that it works for some people. The information in this reply will probably be useful to other people, so you may like to include it too.

My system is Ubuntu 8.04 Hardy on AMD64 .

I got the debian package from the Canon website: [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp) . It gives a TAR ball with 2 deb packages within and incomplete source. Since I'm on AMD64, it didn't want to install right away (it's for i386).

I used dpkg --force-architecture -i <package> on both deb packages, reopened the Printers dialog and modified the printer to use the new driver. It's in the end of the list (iP1900).

Seems to work just fine.

Best regards,
hri

---

### Post by mahela007 on 2009-06-22
Cancuens HOWTO worked like a charm. Thanks a LOT!

---

### Post by mrfotheringham on 2009-06-22
I have been trying to install my ip1900 on Jaunty for over a week. Tried old archives numerous posting. Googled PPD files and among results was a polish ubuntu forum posting. Used translate and followed one thread

cnifilter-common 3.00-1 and cnijfilter-ip1900 series 3.00-1 i386 

worked!!

---

### Post by oskandaria on 2009-07-06
Hi, I've succeed installing driver for Canon iP1980, but now I have a problem, my printer cannot print with legal size paper. I mean it can print but if I choose legal as the paper size it print same as when I've print with letter size. I have setting the printer size and the page size of the document with the same legal size, but it doesn't work at all and it always print using letter size. 

As a note, the printer does not have a problem if I've set page size and printer size using paper size smaller than legal or F4.

Could anyone help me to solve the problem. Please email me at [email]oskandaria@yahoo.com[/email].

Thanks for your help
Regards,


OSKANDARIA

---

### Post by artisan on 2009-08-25
Would just like to say that "how to" worked.

Thank you.

---

### Post by fauzie on 2009-08-30
If anybody get a constant blinking orange light problem, try to hold the button with the orange light for a long time (about 6 seconds), and let it go. If you are lucky, the printer will work immediately.

By the way, anybody knows how to set the resolution other than the default 600dpi?

---

### Post by fauzie on 2009-08-30
To get more option, edit the appropriate file at /etc/cups/ppd

And add or edit the following lines. (They might be already available, but incomplete)

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution
 
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 5
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

---

### Post by kva on 2009-08-30
> **hrimhari said:**
> Hello,

Please update your post if your problem has been solved or even to mention that it works for some people. The information in this reply will probably be useful to other people, so you may like to include it too.

My system is Ubuntu 8.04 Hardy on AMD64 .

I got the debian package from the Canon website: [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp) . It gives a TAR ball with 2 deb packages within and incomplete source. Since I'm on AMD64, it didn't want to install right away (it's for i386).

I used dpkg --force-architecture -i <package> on both deb packages, reopened the Printers dialog and modified the printer to use the new driver. It's in the end of the list (iP1900).

Seems to work just fine.

Best regards,
hri

Mine is not working, help please..

---

### Post by weaklegs on 2009-10-28
Hi...

Thanks...this is very helpful and very easy to understand...

> **cancuen said:**
> Hi. I've installed, properly this printer, after a while. I'm a Kubuntu Intrepid User. Greetings from Guatemala.

If you have troubles installing this printer, delete all references/tries/fails/etc related to this printer. Let's do it as we just brought from the store knowing all we need to know.

Turn off the printer (and/or unplug if necesary/wanted).

You have to download the drivers in canon-europe's site. The drivers are at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp). 
Find under "Operating System > Linux" and download "Debian Linux Printer Driver (3.0)".
Download to a folder (it's own folder) anywhere (better desktop). Then, let's go to konsole (or equivalent).

First we must install libcupsys2 with the following order:
$ sudo apt-get install libcupsys2
Next go to folder we used to download the driver:
$ cd /path/to/your/folder
Next we need to untar the dowloaded file
$ tar -xf iP1900_debian_printer.tar
Now we will have 3 files on this folder (+ original tar downloaded file).
(In my case I've untargz the "tar.gz" file inside, but don't think that this is necessary, how ever if you wanted or need to doit:
$ tar xvzf cnijfilter-common-3.00-1.tar.gz)
Then let's install:
$ sudo dpkg -i *deb
This will install the two deb packages included in the downloaded tar file that will install the proper drivers in the computer database.

Now that are installed, exit the konsole and then let's go to CUPS web manager in our favorite browser (firefox rocks) to [http://127.0.0.1:631](http://127.0.0.1:631)

In the page go to Admin and find the button that says "Find new printer" and then follow the assistant. 

Hope this helps someone. If you have troubles finding out what to download, this is the file my browser reports as downloaded:
[http://software.canon-europe.com/files/soft31335/software/iP1900_debian_printer.tar](http://software.canon-europe.com/files/soft31335/software/iP1900_debian_printer.tar)

Feed back with comments.

Mario Soto
mariosoto [at sign here] cancuen [dot here] net

---

### Post by mrfotheringham on 2009-10-31
> **weaklegs said:**
> Hi...

Thanks...this is very helpful and very easy to understand...
[B]Result!

[/B]Fantastic explanation it works.

Many Thanks

---

### Post by DavisYZA on 2009-11-04
Small problem... 
The console says:

"Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version."

But these cannon ip1900 drivers aren't working with **libcups2**. The drivers are reported by Ubuntu as "broken packages". Too bad, Karmic is so cool... so sad 	:cry:.

---

### Post by s_raiguel on 2009-11-05
Though it now appears to be supported by Ubuntu, I originally had trouble finding a workable driver for my Canon i6500. A German company, ZedoNet,  makes very good Linux drivers, under the name Turboprint, for almost every imaginable printer, but you have to pay for the Turboprint program. It was about 20 or 30 euro, but I feel I got my money's worth.

---

### Post by hkboy2004 on 2010-01-04
QUOTE=fauzie;7868706]To get more option, edit the appropriate file at /etc/cups/ppd

And add or edit the following lines. (They might be already available, but incomplete)

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution
 
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 5
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality[/QUOTE]



Iam using ubuntu 910 and my ip1980 can't print greyscale photos
It could do it in 9.04
There is no greyscale option in colour mode(only RGB is available)
Is it possible to edit ppd file? HOW?
Thanks for help

---

### Post by PauricTheLodger on 2010-01-28
> **DavisYZA said:**
> Small problem... 
The console says:

"Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version."

But these cannon ip1900 drivers aren't working with **libcups2**. The drivers are reported by Ubuntu as "broken packages". Too bad, Karmic is so cool... so sad 	:cry:.

I've got the same problem :( Anyway around it?

---

### Post by weaklegs on 2010-02-25
ey...does anybody know how to set the printing to fast draft like windows? ky baga ra au ang print niya and kalas au ug ink...

---

### Post by sp8bql on 2010-03-01
To add draft you need to modify as administrator ip1900.ppd (/usr/share/ppd) file
and add lines like:
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

after modyfing lines go to:
[http://localhost:631/printers/](http://localhost:631/printers/)        

and choose
'Modify printer option'

Click Next 2 times and then enter a location to modified ppd file
Click Modify and restart cups by 

sudo /etc/init.d/cups restart

after that again logon to cups by 
[http://localhost:631/printers/](http://localhost:631/printers/)   

and choose 'Default options'
There will be new option available with printing quality.

-----------------------
To add grayscale printing find in ppd file something like:

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: black
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagede$

*CloseUI: *ColorModel

and before *CloseUI: *ColorModel line add: 

*ColorModel Gray/Grayscale: "<</cupsColorOrder 0/cupsColorSpace 3/cupsCompression 2>>setpagedevice"

------------------------
New resolution options can be added easily by finding and adding lines as below:

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 100dpi/100 dpi: "<</HWResolution[100 100]>>setpagedevice"
*Resolution 300dpi/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

---

### Post by kadm on 2010-05-07
Just used the Karmic drivers and howto from [http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900](http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900) to set up the printer under Lucid. So far, no problems.

---

### Post by arayilpdas on 2010-05-10
(duplicate message)

---

### Post by arayilpdas on 2010-05-10
everything went fine as you instructed, but when given a test page the light blinks on the printer, window says job is completed but the printer wont budge!
i am a lay user, and said bye to mr. gates just yesterday
please try to keep it very very simple :)
thanks in advance
dr das
(i use 10.04)

---

### Post by arayilpdas on 2010-06-02
Cancuens instructions were easy as opening a bottle :)

had to download  libcupsys2 from 

[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/) 

& download 

[**libcupsys2_1.3.9-17ubuntu1_all.deb**]("http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu1_all.deb")

then download printer drivers from here

[http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)

move the .tar to home folder
rt click extract here
find two .deb files, double click and install both of them

end with

system > admin > printing > add new printer > follow instructions

cheers :D my first troubleshoot

dr das

---

### Post by Sam Fallow on 2010-06-10
/\/\/\/\/\/\/\

thanks dr das, 

concise, to the point and it works a charm. Nice!

---

### Post by joanfrank on 2010-10-15
I found help that worked with "How to install Canon Pixma iP1800 or iP1900 on Ubuntu".  blog de znupii - Mozilla Firefox. I tried many and this one worked for me, and I am a total newbee to Linux.
thanks for assistance

---

### Post by mammuthus on 2011-01-06
As a newcomer I simply want to say big thank you to cancuen for the post #6, which helped me to set up my printer under Hardy, and to arayilpdas for #28, which helped me to sort out the problem with the driver after upgrading to Lynx!

---

### Post by texla on 2011-03-28
> **fauzie said:**
> To get more option, edit the appropriate file at /etc/cups/ppd

And add or edit the following lines. (They might be already available, but incomplete)

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 100/100 dpi: "<</HWResolution[100 100]>>setpagedevice"
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
 
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 5
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality


Thanks, Fauzie!  This is the best printer fix I've used for my Canon Pixma 330!  I made two extra copies of my printer in the printing settings and then used your fix in all three of them - (with a slight number adjustment to go between 100-600 like above - then I went to printing options and set one to GRAYSCALE 100dpi - Standard quality, then one to Color 300dpi - Normal quality and one to hires color 600dpi - high quality - yes,for me 600 is as hi res as it gets!.  Now I can hit any of them with one click of printer choice and get the settings I want.

---

