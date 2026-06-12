---
title: "Extra Visual Effects on a laptop?"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by jhyland87 on 2008-05-19
Hey guys, so I am trying to install compiz config on ubuntu 7.10, First I wanted to test the extra visual effects, im on the Acer 5920 laptop, here are the specs

> Additional Specifications
Processor Brand: 	INTEL
Processor Type: 	Core 2 Duo
Hard Drive Size: 	160GB
System RAM: 	3072 MB
Operating System: 	Vista Home Premium
Display
Display Type: 	15.4" TFT
Widescreen Display: 	Yes
Max Resolution: 	1280 x 800 ( WXGA )
Processor
Multi-Core Technology: 	Dual-Core
Processor: 	Intel Core 2 Duo T5450 / 1.66 GHz
Chipset Type: 	Mobile Intel GM965 Express
Data Bus Speed: 	667 MHz
Cache Memory
Type: 	L2 cache
Installed Size: 	2 MB
Storage
Hard Drive: 	160 GB - Serial ATA-150 - 5400 rpm
RAM
Installed Size: 	3 GB / 4 GB (max)
Technology: 	DDR II SDRAM
Configuration Features: 	1 x 1 GB + 1 x 2 GB
Optical Storage
Type: 	DVD±RW (±R DL) / DVD-RAM - integrated
Read Speed: 	24x (CD) / 8x (DVD±R) / 6x (DVD±R DL)
Write Speed: 	24x (CD) / 8x (DVD±R) / 4x (DVD±R DL)
Networking
Data Link Protocol: 	Ethernet, Fast Ethernet, Gigabit Ethernet, IEEE 802.11b, IEEE 802.11a, IEEE 802.11g
Wireless LAN Supported: 	Yes
Video
Video Memory: 	Dynamic Video Memory Technology 4.0
Graphics Processor / Vendor: 	Intel GMA X3100
Audio
Audio Input: 	Stereo microphone
Operating System / Software
OS Provided: 	Microsoft Windows Vista Home Premium
Software: 	NTI CD-Maker, CyberLink PowerProducer, Acer GridVista, Adobe Reader, Acer Empowering Technology, Microsoft Works 8.5, Norton Internet Security 2007 (90 days subscription), Microsoft Office 2007 Home and Student Edition (Trial), Acer Arcade Deluxe, Acer Crystal Eye
Battery
Technology: 	6-cell lithium ion
Installed Qty: 	1
Notebook Camera
Camera Type: 	Integrated
Product Dimensions
Width: 	14.3 in
Height: 	1.7 in
Depth: 	10.6 in
Weight: 	6.6 lbs
Card Reader
Supported Flash Memory Cards: 	SD Memory Card, Memory Stick, Memory Stick PRO, MultiMediaCard, xD-Picture Card

Here is the exact laptop: [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=320248323608&ssPageName=STRK:MEWA:IT&ih=011](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=320248323608&ssPageName=STRK:MEWA:IT&ih=011)

when I try to activate  the Extra Visual Effects it says: **Desktop Effects Could Not Be Activated**

Does anyone know why??

---

### Post by dtrot55 on 2008-05-19
I know this may seem noobish..but did you enable the video driver or download and install it?  Just trying to start from the beginning.

---

### Post by iaculallad on 2008-05-19
You could try following up this [thread]("http://ph.ubuntuforums.com/showthread.php?t=698256"), and maybe, some of their suggestion might work your case.

---

### Post by jhyland87 on 2008-05-19
> **dtrot55 said:**
> I know this may seem noobish..but did you enable the video driver or download and install it?  Just trying to start from the beginning.
Ummm no, but I have ubuntu installed on my desktop, have been using it for a very long time, never had to download and install the acer drivers, so I didnt do it on here, but in the restricted drivers manager, its enabled..

Nothing seems to be working on this laptop with ubuntu, I tried to install wine..

> justin@justin-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine
justin@justin-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

But this is the EXACT same cd I used on my desktop
> **iaculallad said:**
> You could try following up this [thread]("http://ph.ubuntuforums.com/showthread.php?t=698256"), and maybe, some of their suggestion might work your case.

Will do, thanks!



Edit:
What the heck, I cant even install flash, why cant i install ANYTHING?

---

### Post by iaculallad on 2008-05-19
For the [WINE]("http://www.winehq.org/site/download-deb") installation problem (Perform this on the Terminal):

sudo wget [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)
sudo dpkg -i wine*.deb

If you have a dependency error, input this on your terminal:

sudo apt-get install libgtk1.2

---

### Post by jhyland87 on 2008-05-19
> **iaculallad said:**
> For the [WINE]("http://www.winehq.org/site/download-deb") installation problem (Perform this on the Terminal):

sudo wget [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)
sudo dpkg -i wine*.deb

If you have a dependency error, input this on your terminal:

sudo apt-get install libgtk1.2
Tried that :(
> justin@justin-laptop:~$ sudo dpkg -i wine*.deb
dpkg: error processing wine*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine*.deb

justin@justin-laptop:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk1.2
justin@justin-laptop:~$ 


---

### Post by jhyland87 on 2008-05-19
Something is wrong, for sure, cant install wine, flash players, java, or anything else for that matter.

---

### Post by iaculallad on 2008-05-19
Ok. did you enter the first line which says:

sudo wget [http://kent.dl.sourceforge.net/sourc...ehq-1_i386.deb](http://kent.dl.sourceforge.net/sourc...ehq-1_i386.deb)

if you did and still get the errors. Try doing this: Navigate through "System-> Administration-> Software Sources" Make sure that you "Installable from CDROM/DVD" is uncheck, and, place check marks on Main, Universe, Restricted, and Multiverse (from the Downloadable from the Internet). Click on close and perform the installation again.

---

### Post by jhyland87 on 2008-05-19
> **iaculallad said:**
> Ok. did you enter the first line which says:

sudo wget [http://kent.dl.sourceforge.net/sourc...ehq-1_i386.deb](http://kent.dl.sourceforge.net/sourc...ehq-1_i386.deb)

if you did and still get the errors. Try doing this: Navigate through "System-> Administration-> Software Sources" Make sure that you "Installable from CDROM/DVD" is uncheck, and, place check marks on Main, Universe, Restricted, and Multiverse (from the Downloadable from the Internet). Click on close and perform the installation again.

Yeah I did type that command, previous to the other two and it didnt work, but I checked the Main, Universe, Restricted, and Multiverse options, that seems to have done something, I couldnt find the "Installable from CDROM/DVD" option though.

Installing wine, getting something to eat, brb

Thanks so much for the help so far.... let me know how I can pay you back :)

---

### Post by iaculallad on 2008-05-19
> **jhyland87 said:**
> Yeah I did type that command, previous to the other two and it didnt work, but I checked the Main, Universe, Restricted, and Multiverse options, that seems to have done something, I couldnt find the "Installable from CDROM/DVD" option though.

Installing wine, getting something to eat, brb

Thanks so much for the help so far.... let me know how I can pay you back :)

> let me know how I can pay you back :)
-Some bottles of beer maybe :-)
"Installable from CDROM/DVD" is located within the "Ubuntu Software Tab", just below the "Download From:" option. Just uncheck it if it's checked so that it will not locate any installable packages on your CDROM/DVD.

---

### Post by jhyland87 on 2008-05-19
> **iaculallad said:**
> -Some bottles of beer maybe :-)
"Installable from CDROM/DVD" is located within the "Ubuntu Software Tab", just below the "Download From:" option. Just uncheck it if it's checked so that it will not locate any installable packages on your CDROM/DVD.

awesome, unchecked, however, still cant enable desktop effects.. :(


Edit: I just turned 21, BEER IT IS! lol

also, I restarted x to see if that would change anything, it did... for the worse, see attachment.

---

### Post by iaculallad on 2008-05-19
> **jhyland87 said:**
> awesome, unchecked, however, still cant enable desktop effects.. :(


Edit: I just turned 21, BEER IT IS! lol 


Got some bad news for you regarding your desktop effects. Seems like compiz included your video adapter on its [hardware blacklist list]("http://wiki.compiz-fusion.org/Hardware/Blacklist").

For the Nautilus-Bonobo error try doing this:

Re-install nautilus-data using Synaptics. Then on the terminal, ran the following to add the location to bonobo:

sudo bonobo-activation-sysconf --add-directory=/usr/lib/bonobo/servers

---

### Post by jhyland87 on 2008-05-19
> **iaculallad said:**
> Got some bad news for you regarding your desktop effects. Seems like compiz included your video adapter on its [hardware blacklist list]("http://wiki.compiz-fusion.org/Hardware/Blacklist").

For the Nautilus-Bonobo error try doing this:

Re-install nautilus-data using Synaptics. Then on the terminal, ran the following to add the location to bonobo:

sudo bonobo-activation-sysconf --add-directory=/usr/lib/bonobo/servers

How do I fix it if its on a blacklist? why the heck is it on a blacklist, can I use something else?
 
Edit:trying to bypass it using you link

---

### Post by iaculallad on 2008-05-20
> **jhyland87 said:**
> How do I fix it if its on a blacklist? why the heck is it on a blacklist, can I use something else?

Meaning, it's not yet supported. Follow the link above, you still have the option of disabling it.

---

### Post by jhyland87 on 2008-05-20
> **iaculallad said:**
> Meaning, it's not yet supported. Follow the link above, you still have the option of disabling it.

I changed ~/.config/compiz/compizconfig/config to this

> [gnome_session]
profile = 
plugin_list_autosort = true
SKIP_CHECKS=yes compiz

Restarted X, and its still the same :(

---

### Post by iaculallad on 2008-05-20
> **jhyland87 said:**
> I changed ~/.config/compiz/compizconfig/config to this



Restarted X, and its still the same :(


One perfect solution would be for you to upgrade from your current 7.10 to 8.04 since it's not blacklisted on this version (for you to enjoy the Desktop-Effects). Or, do a clean install on Hardy since you had just started installing 7.10. (If that's the case)
Good Luck.

---

### Post by jhyland87 on 2008-05-20
> **iaculallad said:**
> One perfect solution would be for you to upgrade from your current 7.10 to 8.04 since it's not blacklisted on this version (for you to enjoy the Desktop-Effects). Or, do a clean install on Hardy since you had just started installing 7.10. (If that's the case)
Good Luck.

whats the fastest way to just update, I dont want to burn it at the moment

Edit: nevermind

---

### Post by iaculallad on 2008-05-20
With your situation right now, there's no easy way to update. Just be patient in checking your 8.04 iso for errors (MD5) and burn it at a low speed (4x). Then, do a clean install.

---

### Post by jhyland87 on 2008-05-20
> **iaculallad said:**
> With your situation right now, there's no easy way to update. Just be patient in checking your 8.04 iso for errors (MD5) and burn it at a low speed (4x). Then, do a clean install.

I Upgraded it using the update manager, why is a clean install better? I will if you can tell me why its better.

Wine doors is being an *** as well, I can download dreamweaver, photoshop, steam, etc, but the files dont go anywhere, but it says they are installed.

---

