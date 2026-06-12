---
title: "Canon Pixma MP550 - how to?"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by uhappo on 2009-11-18
Well, that's about it, is there a way to get it going on?

I don't have it, my father has it and I'm not able to "take care of it" at the moment, soon. Any solutions how to manage it, printing and scan?

---

### Post by uhappo on 2009-12-29
Haven't tried it yet, but goosh batman, there seems to be some light ahead...

[http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One%20Printers&series=All-in-One%20Printers&model=PIXMA%20MP550&menu=Download]("http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One%20Printers&series=All-in-One%20Printers&model=PIXMA%20MP550&menu=Download")

---

### Post by matttbe on 2010-01-12
Hello !

I don't know if you've resolved your problem but this is what I've done on computers (32/64bits) which use my new Canon Pixma MP550 : (hope it can also help other people ;) )
[LIST=1]
[*]Firstly, download drivers from Canon Australian website : for the [printer]("http://support-au.canon.com.au/contents/AU/EN/0100236402.html") and the [scanner]("http://support-au.canon.com.au/contents/AU/EN/0100237702.html") (drivers for the scanner are now a bit useless because you can directly use the scanner with Simple Scan, GScan2PDF, Xsane, etc.).
[*]Extract these two tarballs (e.g. in your 'Home' folder)
[*]Install it :
[LIST]
[*]For 32bits (most people): simply use gdebi (double-click on all deb files) but start with the deb file which has '*common*' in its name.
If you're using **Ubuntu Natty (11.04) or newer**, you've to force the installation of these packages because there are a bit old... Simply open a terminal, go to the repertory of deb files and launch the dpkg command: ```
 cd cnijfilter-mp550series-3.20-1-i386-deb/packages/
 sudo dpkg --force-architecture --force-depends --force-depends-version -i cnijfilter-*.deb 
``` (you've to write your password, it's invisible ;) )
Then install all dependences with this command: ```
 sudo apt-get install libc6 libcups2 libpopt0 libatk1.0-0 libcairo2 libfontconfig1 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libpng12-0 libtiff4 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 
```
[*]For 64bits: you've to force the installation (I've tested and it works perfectly ;) ):
[LIST]
[*]Open a terminal, go to the repertory of deb files and force the installation :```
 cd cnijfilter-mp550series-3.20-1-i386-deb/packages/
 sudo dpkg --force-architecture --force-depends --force-depends-version -i cnijfilter-*.deb 
```
[*]For scangears :```
 cd ../../scangearmp-mp550series-1.40-1-i386-deb/packages/
 sudo dpkg --force-architecture --force-depends --force-depends-version -i scangearmp-*.deb 
```
[*]Donwload and install GetLibs in order to add some 32bits dependences: [GetLibs]("http://frozenfox.freehostia.com/cappy/getlibs-all.deb") (simply double click on the file in order to install it !)
[*]Use GetLibs for scangears:```
getlibs /usr/bin/scangearmp 
```
[*]I don't remember if it needs some others dependences but you can use this command: ```
 sudo apt-get install libc6 libcups2 libpopt0 libatk1.0-0 libcairo2 libfontconfig1 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libpng12-0 libtiff4 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 
```
[/LIST]
[/LIST]
[/LIST]

[CENTER]*****[/CENTER]

Now you should connect your printer **but** it can be interesting to change some things for the better parameters:
[LIST]
[*]Edit this file : */usr/share/cups/model/canonmp550.ppd* with an editor with root right, e.g. ```
 sudo gedit /usr/share/cups/model/canonmp550.ppd 
```
[*]Add these lines at the end of the file for having some options about the quality and the grayscale : ```
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CloseUI: *CNQuality

*OpenUI *CNGrayscale/Grayscale: PickOne
*DefaultCNGrayscale: false
*CNGrayscale false/Off: "false"
*CNGrayscale true/On: "true"
*CloseUI: *CNGrayscale
```
[*]If you want more resolution choices, replace : ```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 600dpi/600 dpi: "«/HWResolution[600 600]»setpagedevice"
*CloseUI: *Resolution
``` by ```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 300dpi/300 dpi: "«/HWResolution[300 300]»setpagedevice"
*Resolution 600dpi/600 dpi: "«/HWResolution[600 600]»setpagedevice"
*CloseUI: *Resolution
```
[*]You can now restart Cups:
[LIST]
[*]For Karmic/Lucid ```
 sudo service cups restart 
```
[*]For Jaunty/Intrepid ```
sudo /etc/init.d/cups restart    
```
[*]For Hardy ```
sudo /etc/init.d/cupsys restart 
```
[/LIST]
[*]Simply plug the USB connector of your printer. A new window will be displayed. If not, go to *System -> Adminitration -> Printers* and add a new printer with *Canon MP550 series Ver.3.20* drivers (or with the path of this ppd file : */usr/share/cups/model/canonmp550.ppd*).
[*](If you had already installed your printer and you change the .ppd file, you've to 'reinstall' your printer by removing it and adding it in *System -> Adminitration -> Printers*)
[/LIST]
About the **scanner**
[LIST]
[*]You can use scangear (a tool of Canon) that you can launch with *scangearmp* (use Alt+F2 shortkey ;) )
[*]**But** you can also sane (e.g. with simple scan, xsane or the excellent gscan2pdf) but you have to use the latest version of *sane-backends* (installed by default in Ubuntu Natty 11.04 (and Maverick?))
[LIST]
[*]You can have a look to this tutorial: [http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html")
[*]Or (for [Karmic]("https://launchpad.net/~matttbe/+archive/ppa/+sourcepub/925121/+listing-archive-extra") or [Lucid]("https://launchpad.net/~matttbe/+archive/ppa/+sourcepub/925130/+listing-archive-extra") only) you can download *libsane* and *sane-utils* packages from my ppa (this is an update of sane-backends (1.0.21cvs)) : [https://launchpad.net/~matttbe/+archive/ppa/+packages]("https://launchpad.net/~matttbe/+archive/ppa/+packages") (It's maybe not recommended to add this ppa if you don't want to install some 'non official' packages ;) )
[/LIST]
[/LIST]
I hope it can help you an other people ;)

---

### Post by uhappo on 2010-01-13
YEAH!

Great info, some new things for me. But..

But the ability to use sane/xsane is top notch thingy, YEAH!

---

### Post by eucryphia on 2010-03-06
> **matttbe said:**
> Hello !

I don't know if you've resolved your problem but this is what I've done on computers (32/64bits) which use my new Canon Pixma MP550 : (hope it can also help other people ;) )

<big snip>

I hope it can help you an other people ;)

Thank you very much matttbe :KS

The printer drivers worked a treat, right out of the box, to an MP550 shared on a networked Win XP box.

My PC is:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.18) Gecko/2010021501 Ubuntu/8.04 (hardy) Firefox/3.0.18

I haven't worked out how to connect to the scanner remotely, more surfing required :D

---

### Post by HandleWithCare on 2010-03-06
You saved me a lot of time searching and tweaking, thank you! One more question though. Do you know whether or not it is possible to enable direct scanning from the device?

---

### Post by matttbe on 2010-03-06
> **HandleWithCare said:**
> One more question though. Do you know whether or not it is possible to enable direct scanning from the device?
Yes I think it's possible if you install a newer version of sane-backend. Look at the end of my previous post ;)
I know that you can change something about buttons with gscan2pdf but I can't test right now.

If you find something about that, please share this information, it can be useful :)

---

### Post by HandleWithCare on 2010-03-06
I have found that you can use the buttons for scanning to get multipage scanning (see here: [http://mp610.blogspot.com/2007/12/multi-page-scanning-using-mp610.html]("http://mp610.blogspot.com/2007/12/multi-page-scanning-using-mp610.html")) but so far no luck on automatic scanning, so without having to open xsane for example.

---

### Post by HandleWithCare on 2010-03-18
Hi, when I try to print a photo on glossy II paper, nothing happens. That is, the job is "processing" and also the lcd on the printer shows "preparing" but in the end nothing happens? Any clues?
Btw, no luck on the buttons so far.

---

### Post by micronetic on 2010-03-20
Hi there,

I am completely new to Ubuntu and would like to know how to force the installation of the two files, the Scangear and the printer driver. I got the files in a folder on my desktop but when I copy your code into the terminal it says wrong path, I don't know how to get to the folder with the files.

Can you guys help me please?

---

### Post by achookang on 2010-04-11
I am still having trouble getting the Canon MP550 to work. I am using Unbuntu Karmic. 

I downloaded and installed the drivers mentioned earlier in this thread. They appeared to install OK. Then I plugged in the printer and it said it was looking for drivers. It then gives me a table with a long drop down list of manufacturers and when I choose Canon and then click forward, the only option is MP500 not MP550. If I try the 500 option it doesn't seem to work.

Can anyone help a frustrated Ubuntu newbie?

thanks

---

### Post by matttbe on 2010-04-17
Hello,
Are you sure that you have follow this message : [here]("http://ubuntuforums.org/showpost.php?p=8655287&postcount=3")?
E.g.: is this file existed => /usr/share/cups/model/canonmp550.ppd ?
Can you use this ppd file for printer config?

---

### Post by achookang on 2010-04-17
> **matttbe said:**
> Hello,
Are you sure that you have follow this message : [here]("http://ubuntuforums.org/showpost.php?p=8655287&postcount=3")?
E.g.: is this file existed => /usr/share/cups/model/canonmp550.ppd ?
Can you use this ppd file for printer config?

Hi, yes I followed the instructions at that message, for 32bit version, i.e. I clicked the .deb file with "common" in the filename. It appeared to install (some boxes came up saying it was installing), but when I checked the location the.ppd file is not there. In fact there is no "model" subdirectory under "cups".

Don't know what to do about that. :(

---

### Post by achookang on 2010-04-17
(Update) - thanks to the Mattbe, I checked for the missing ppd file and re-checkde what I had done following the instructions provided. Turns out I only installed one of the two files/packages needed.

I am a klux! :)  Anyway I now have the ppd file so I am hopeful that the driver will work. I don't have the laptop near where the printer is so I cannot check it right now, but I will do so asap.

thanks again for help.

---

### Post by achookang on 2010-04-19
OK, I can now confirm that after following the instructions properly :) I now have the Canon MP550 working with Ubuntu Karmic Koala. Also the ScanGear program is up and running. I haven't yet delved into the mysteries of trying to update SANE to use alternative scanning options but that will have to wait til another day.

Thanks for the help!

---

### Post by CBR1100XX on 2010-05-09
> getlibs /usr/bin/scangearmp> getlibs: command not found
Am I doing something wrong here?   I'm trying desperately to get my MP550 printer to work!

**Edit**
Never mind, got it to work. :)

---

### Post by uhappo on 2010-05-16
Yeah, this thing works:

My father has one (MP550) and he has been using it in vista and it REALLY doesn't work the way it's supposed to be.

I installed .deb drivers from Australian Canon site and installed the debs in Karmic 32bit, then attached USB and voilla, this thing works.

Yeah!

---

### Post by jcuesta on 2010-08-03
Hi, I'm new in Ubuntu (and my english is bad, sorry :(), I use 10.04 version (the last, I think), and your instructions work fine for me, except for the scanner: Ubuntu says "no scanner detected", but scangearmp-common_1.40-1_i386.deb and scangearmp-mp550series_1.40-1_i386 are installed. For the printer, I needed go to Administration->Printers after install the drivers, otherwise Ubuntu not detected printers; perhaps is necessary make similary operation with scanner? Thanks a lot!

---

### Post by matttbe on 2010-08-03
Hi,

As said in the tutorial ;)  either you install and use "scangearmp" (e.g. launched from Alt+F2 menu), or you install a newer version of sane => [http://ubuntuforums.org/showpost.php?p=8655287&postcount=3](http://ubuntuforums.org/showpost.php?p=8655287&postcount=3)

---

### Post by wolfworx on 2010-08-22
This How to is excellent thank you, pretty much worked except for a stupid little thing:

I am trying to print 4" x 6" borderless (from Picasa) In the printer setup i have chosen the 4x6 borderless paper, 2400dpi, normal quality etc, it prints beautifully except for a 3 to 4 mm white border all round ! arrrggh

Have i missed something ? is there something in the cups driver that has editable borders ?

---

### Post by wolfworx on 2010-08-22
> **wolfworx said:**
> This How to is excellent thank you, pretty much worked except for a stupid little thing:

I am trying to print 4" x 6" borderless (from Picasa) In the printer setup i have chosen the 4x6 borderless paper, 2400dpi, normal quality etc, it prints beautifully except for a 3 to 4 mm white border all round ! arrrggh

Have i missed something ? is there something in the cups driver that has editable borders ?

Mmmmm Prints perfectly from F-Spot, I guess its a Picasa problem !!

---

### Post by luotinen on 2010-09-11
Thank you for the instructions, Matttbe! :)

I have a problem when printing on 4" x 6" (102mm x 152mm) photo paper (Photo Paper Plus Glossy II).

When I print from GIMP it prints 29,04 mm x 43,56 mm and refuses to print any larger (the controls are greyed out). When I print from Eye of Gnome (default picture viewer) it prints 29 mm x 44 mm and refuses to print any larger (the controls are greyed out). I haven't tried F-Spot yet, but I would like to get by without it anyways. Printing straight from GIMP would be the most convenient option for me.

Printing works perfectly, but I would sure like to print larger than 29mm x 44mm.. What settings are you using?

Here's the workflow I use:
1. File - Page Settings...
Canon Pixma MP550 / 4" x 6" / Apply
2. File - Print
Paper Type: Photo Paper Plus Glossy II / Print

---

### Post by matttbe on 2010-09-15
@luotinen: I'm sorry, I really don't know what's wrong.
On Ubuntu Maverick 10.10 with gThumb and after having set 4"x6" size, I can increase the size to 102mm x 152mm (if my picture has a 4x6 ratio)

---

### Post by vocalfons on 2010-12-30
@matttbe:

your directions are so clear, that tonight I installed the printer of my associate, 100miles away,using teamviewer. It immediately worked. Well done and thanks a trizillion!!!

---

### Post by Neolinux on 2011-01-07
Hello !
Thank You Very Much !!!! :D
My printer and my scan work perfectly !!!
I have just a pb to save the modification in the file, i have find the solution in an other forum page : sudo gedit, and paste the file into, so that the root rights.

Thanks a lot !!! :P

bye

Neolinux

---

### Post by Mohrphium on 2011-01-15
@matttbe
Printing worked fine (Ubuntu 10.04 Netbook 32-bit), scanning not but I was able to scan directly to an USB drive an since I don't scan very often that's ok. Thank you very much, you just made my life a bit easier \\:D/

---

### Post by matttbe on 2011-01-15
> **Mohrphium said:**
> @matttbe
Printing worked fine (Ubuntu 10.04 Netbook 32-bit), scanning not but I was able to scan directly to an USB drive an since I don't scan very often that's ok. Thank you very much, you just made my life a bit easier \\:D/
@ Mohrphium: did you install a newer version of sane-backends?
> About the **scanner**
[LIST]
[*]You can use scangear (a tool of Canon) that you can launch with *scangearmp* (use Alt+F2 shortkey ;) )
[*]**But** you can also install sane (e.g. with xsane or the excellent gscan2pdf) but you have to use the latest version of *sane-backends*
[LIST]
[*]You can have a look to this tutorial: [http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html")
[*]Or (for [Karmic]("https://launchpad.net/~matttbe/+archive/ppa/+sourcepub/925121/+listing-archive-extra") or [Lucid]("https://launchpad.net/~matttbe/+archive/ppa/+sourcepub/925130/+listing-archive-extra") only) you can download *libsane* and *sane-utils* packages from my ppa (this is an update of sane-backends (1.0.21cvs)) : [https://launchpad.net/~matttbe/+archive/ppa/+packages]("https://launchpad.net/~matttbe/+archive/ppa/+packages") (It's maybe not recommended to add this ppa if you don't want to install some 'non official' packages ;) )
[/LIST]
[/LIST]

---

### Post by Black_Parrot on 2011-02-03
Hello...
matttbe, thank you very much for you manual... 

But i have a question about printing resolution...
I replaced what you say... but what it do??
Where i can change printing resolution? I try to change it in administration-printers... but there is only 600dpi!!
I even try to change default resolution in canonmp550.ppd, but it change nothing in administration-printers...

Sorry for my english...

---

### Post by matttbe on 2011-02-04
Hello,
I think you've to modify canonmp550.ppd file and then add a new printer with this ppd file. (But I'm not sure that printing with big resolutions works well)

---

### Post by Black_Parrot on 2011-02-05
> I think you've to modify canonmp550.ppd file and then add a new printer with this ppd file.
It works! :)

> But I'm not sure that printing with big resolutions works well
I try... and now i'm not sure too... :D

Maybe 32bit Ubuntu help?

---

### Post by matttbe on 2011-05-10
Hello,

Just to note that I've updated my first comment here by adding a tips for Ubuntu Natty 11.04 users! (It seems the packages has to be rebuilded... don't hesitate to report this bug to Canon developpers!)

---

### Post by Ineke050 on 2011-05-11
Thanks a lot.
It worked fine

---

### Post by avdheiden on 2011-05-11
There is a great repository for the canon pixma multi-devices. Look at the ubuntu tweak page.

---

### Post by plattypus1 on 2011-05-12
I've got a Pixma 560 finally working on Natty 64 bits, and I wanted to share how I did it.

It seems that the Canon-supplied drivers have bad dependency metadata which makes it so that they won't install easily under 64 bits, and there's a bug in Natty's dpkg that makes --force-depends not work properly. Fortunately, the bug has been fixed in the next version of dpkg. Unfortunately, the next version hasn't been applied to Natty yet. So here's what you need to do:

1. Add the line ```
deb http://us.archive.ubuntu.com/ubuntu oneiric main
``` to your /etc/apt/sources.list

2. Run ```
sudo apt-get update
```
**DO NOT APT-GET UPGRADE**. I don't know what it'll do, but you may end up reverting a good chunk of your system's packages manually.

3. Run ```
sudo apt-get install dpkg
```

4. Go into Synaptic (System-Administration-Synaptic Package Manager), search for dpkg. Select dpkg.

5. Under "Package," choose "Lock Version."

6. Remove or comment out the oneiric line from your /etc/apt/sources.list

7. Run ```
sudo apt-get update
``` again.

8. In the install.sh script from the Canon drivers, change ```
dpkg -iG
``` to ```
dpkg -iG --force-all
```

9 Run the install.sh script.

---

### Post by Catbells on 2011-05-13
A tip for printing envelopes:-

Check that the corners aren't curling.  Envelopes go in the rear tray, face up with the short edge at the top and the flap (the Canon web site says you're not allowed to use envelopes with two flaps) on the right.  When you've done it, it looks like it's standing tall.

[ I kept putting an envelope in the rear tray with the long edge at the bottom and became quite frustrated when the printer kept spewing it out with nothing printed on it. ]

---

### Post by kokolores on 2011-10-20
you can copy the ppd file that comes with turboprint 30 day trial. [http://www.turboprint.info/](http://www.turboprint.info/)
go to /usr/share/turboprint/ppd/ 
There are many printer configurations. The one for Canon Pixma MP550 is /usr/share/turboprint/ppd/Canon_PIXMA_MP550.ppd

---

