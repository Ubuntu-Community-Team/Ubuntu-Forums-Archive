---
title: "CANON PIXMA IP2600 Photo Printer - Driver Installation"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by mas_sergio on 2010-10-22
First of all before we begin you should all be warned that this will require some work in the terminal for those of you who dread the terminal worry not... I will go step by step to make things as seamlessly as possible. The rest of our work will be done by GUI so it's some what 50/50 balanced of copy and paste action and a few clicks to install this monster of a printer wich has giving many people headaches.

This is how I sucessfully got a test page to print in full color in Ubuntu Studio AMD 64 installation (this guide should work for any UBUNTU x64/AMD edition).

The problem is the printer I have does not have drivers available for my arcitechure x64 only for x32 ubuntu. What we are going to do (we being IP2600 photo printer owners) is force an installation of x32 drivers into an x64 architecture via the terminal.

For people running a x32 bit version of ubuntu/linux please do not attempt these instructions as your arcitechture should be supported. If you are a x32 bit ubuntu user and you are lost as to configuring your SUPPORTED printer then please by all means skip to the last section of this Installation Guide. CTRL F and paste Configuring Printer in your web browsers search feature. That should jump (32x bit) users to what they need if you are a x64 bit user continue reading as you are requiered to do the following before configuring your printer.

**x64 bit ****[COLOR="DarkRed"]USERS ONLY![/COLOR]**
First you will need some deb files. Always becareful when downloading .deb files as they can contain viruses etc. It happens in linux to..just not as frequently as MS Windows so be cuatious. xD

DOWNLOAD these drivers onto your system:
click these URL's and click save.

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html)

 [http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)

after that is done we still need to download 1 last file.

There is a problem with new version of cups it just for what ever reason (people say it's the name change) won't work giving you an error in the terminal when ever you attempt to force a 32bit install claiming your missing dependancies. So what you need now is the OLD cups version. I tried forcing an older version of cups in synaptic but woe no luck. None of the version in synaptic were old enough. Luckly google was my friend in this department and I found the dependacies and installed them.

you can get that here (not sure if direct linking is allowed).. download the old cups version ound install it.

URL:
[http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)


now you have the dependancies so we can continue with the install of the CANON IP2600 Photo Printer's x32 drivers wich aren't available in x64 bit. :KS


Now what you need to do is move all your downloaded .deb files into the DESKTOP (you don't have to do this but for the sake of making things easy i recommend you just do so.)

next open the terminal (from accesories) and type w/o quotations "cd Desktop"
the tittle bar ontop of the terminal window should have changed, if it did then GOOD JOB, your doing well so far.

If your paranoid or something and your wondering what we just did basically we told your terminal to open up a directory i.e. your DESKTOP. So now when we run the following command it will look for the files I told you to move to the desktop earlier. See I make things easy for the newbs (I'm one to lol so I'm not hating). :)

**DON'T CLOSE THE TERMINAL (DESKTOP) YET** **[COLOR="DarkRed"]WE'RE NOT DONE![/COLOR]**

Next in the terminal we need to get some work done, those debs I made you download, there in the desktop right? And you made sure to install "libcupsys2_1.3.9-17ubuntu3.9_all.deb" by double clicking it? Good!

Now if that's done your ready run/copy and paste this command into the terminal:


sudo dpkg -i --force-architecture cnijfilter-common_2.90-1_i386.debcnijfilter-ip2600series_2.90-1_i386.deb


after that's done (should only take a second) run the following command in the terminal this should be easy as cake. Just copy and paste. :p


sudo dpkg -i --force-architecture cnijfilter-ip2600series_2.90-1_i386.deb



just so you guys and ladies don't freak on me the message your terminal should spit out may look like this: 

"@ubuntu:~/Desktop$ sudo dpkg -i --force-architecture cnijfilter-ip2600series_2.90-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-ip2600series.
(Reading database ... 291818 files and directories currently installed.)
Unpacking cnijfilter-ip2600series (from cnijfilter-ip2600series_2.90-1_i386.deb) ...
Setting up cnijfilter-ip2600series (2.90-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
"


Don't worry about that your doing fine. Just disregard that as a false alarm. I got some what worried becuase I didn't understand if it meant my install went sucesful or what but it worked out fine. :)

Now you have sucessfully installed your printer DRIVERS. This now means your computer can actually communicate with your printer. That's a big must for getting things to work. We still have a few things to do though to get the printer up and running. :D


==========================================================
Configuring Printer:
Turn on your printer now give it a few seconds as this model printer takes several seconds to fully turn on.  When you see the green power light finally stay stable (not blinking) take your USB cord and plug your printer directly to the USB.

Now in the Gnome menu you need to look for "printing - configure printers"

sorry I can't list the exact directory as I'm using ubuntu w/ the linux mint menu installed but if your on LM just type "Printing" in search. It should be somewhere in administration but I'm not sure.


After your bringing up "Printing" you may see something that says "Printing - Local Host" on the top menu don't worry about it.

I want you to click ADD
a new window will pop up.

-New Printer-
Under Devices click your printer
CANON iP2600 (or what ever you see named canon)

CLICK FORWARD!

-Searching for drivers-

next you should arrive at a window that says printer name or w.e

Canon-iP2600-series- is what you may see.

Leave it like that or change the info if you wish but remember this is what will show up as your printers name so if you change it make it something memorable if you have multiple printers.

thats fine how it is to me so I clicked apply.

If your not seeing what I'm describing above and you see a config asking what version you have select pixma ip2600, then select (on the right pane) reccommended and forward then you should arrive at that menu.

After that menu you should be asked to print a test page... go ahead and do so.

For me it took several minutes as to the odd way this printer warms up or something to print (it takes a few minutes in windows to at start up). Make sure the papper's loaded and wait like 5minutes after you try a test page. Everything should come out black white and with colors. You should see UBUNTU (R) at the top of the page.

If you get that then sucess. Last step of this installation guide is to Praise me if this works darn it. =D>=D>

---

### Post by rgiskard01 on 2010-11-03
The download links for the 64bit debs appear to not be working anymore.

Any chance you could post them somewhere?

---

### Post by fantasm!c on 2011-01-16
Hmm i've tried this in 10.10 x64 and no luck. I can print, but only black/white. No color :'(

The only difference i do have is that my canon printer is on the network (windows 7 machine, shared) and not directly connected to my ubuntu machine.

---

### Post by torontopronto on 2011-02-04
The link [http://packages.ubuntu.com/jaunty/al...psys2/download]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download") doesn't work !!!

Help.... help.... I need to get my Canon Ip2600 printer up and running

---

### Post by Sneakysolidbake on 2011-03-30
Thanks a million. Everything worked great except the libcupsys2 download. This one worked for me: [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.9_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.9_all.deb)

---

### Post by headmower on 2011-08-14
[http://security.ubuntu.com/ubuntu/po...ntu3.9_all.deb]("http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.9_all.deb")
I got an error - page not found on apache server port 80, no what??????? get another printer?

---

