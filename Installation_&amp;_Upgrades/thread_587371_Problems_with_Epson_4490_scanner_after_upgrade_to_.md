---
title: "Problems with Epson 4490 scanner after upgrade to 7.10"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by rziegler72 on 2007-10-22
Still having issues with my Epson 4490, after upgrading from 7.04 to 7.10.  It worked fine in 7.04.

I've installed the libsane-extras and sane-utils packages.

sane-find-scanner shows:
found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:003:002

I added this to /etc/udev/rules.d/45-libsane.rules :
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0119", MODE="664", GROUP="scanner"

I added this to /etc/sane.d/epson.conf :
usb 0×04b8 0x0119

Rebooted.  Still no go.  Any ideas or other info I can provide?

Thanks,
~Rick

---

### Post by lampilux on 2007-10-25
I had the same problem with a "4490 photo" model and I have removed the old driver and reinstall it in order to let the scanner working.

For installation instructions I follow a VERY GOOD post of Ron Morse that I cutted below because with google i didn't find it again on the web (i have saved it on my computer).

I hope for you it will work even with your model.

Good luck!

Tony

p.s.

(Sorry for my english... i'm italian)

CUT
On Saturday 17 March 2007 20:12:44 Denis Gaulin wrote:
> 	My problem is .. I have an EPSON scanner,  4490 perfection 4490 PHOTO that
> I use with my Mac IBOOK G4 and I want to switch to these new OS and I do
> not know how to install it on these computers because Kubuntu or UBUNTU do
> not recognize the scanner.
> 	The Kubuntu Documentation is  silent about scanner package.... nothing in
> the official Documentation.

This is you lucky day.  I just bought one of those units and worked out how to 
get it working on Kubuntu Edgy (also works for Feisty).   

The usual source for Linux scanner help and support is the SANE project at 

[http://www.sane-project.org/](http://www.sane-project.org/) 

Unfortunately, the Perfection 4490 Photo is not directly supported by SANE. 
The good news is that Epkowa, the parent company for Epson in Japan, does 
provide a Linux driver and a limited control software application for this 
unit.  

step 1.  From the Ubuntu repositories for your version, Install sane and 
related packages (libsane, libsane-extras, sane, sane-utils, xsane, 
xsane-common, quiteinsane) All of these may not be strictly required, but I 
do not know which ones are and which are not. That is just a list of what I 
have installed. 

step 2. Connect and power up the scanner. Wait 60 seconds for the scanner to 
warm up -- this seems to be important as it won't report it's presence until 
it is ready.  

step3. make sure the scanner is detected. In a terminal window run:

sane-find-scanner

it should report :

    found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) 
at libusb:001:006

or, run (also from a terminal window)

scanimage -L

and it should report finding an Epson Perfection 4490 flatbed scanner 

The libsub address will probably be different depending on which port you have 
connected the scanner.  If sane-find-scanner or scanimage -L do not find a 
scanner at all, stop. You have to solve that problem first. 

step 4. Get the 4490 linux package from the Epkowa site: 

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

Answer their questionnaire. Select Perfection 4490 Photo. I told them I was 
using Debian and selected "other" in the version dialog. Clicking on 
the "next" button will take you to a download page 

step 5. The source code tarball will not build on Edgy or Feisty, so take the 
two .rpm files (you need both the iScan and the driver package) from the 
appropriate GCC version section for your distro. For Edgy or Feisty the GCC 
3.4 files work.  

step 6. If you haven't already done so, install alien from repository to 
convert the .rpm files to .deb. (sudo apt-get install alien). 

step 7. Convert the .rpm files.  In a terminal window change to the directory 
where the two downloaded driver files are located then: 

sudo alien iscan_2.5.0-0.c2.i386.rpm
sudo alien iscan-plugin-gt-x750_1.0.0-1.c2.i386.rpm

This should produce the two .deb packages:

iscan_2.5.0-0.c2.i386.deb
iscan-plugin-gt-x750_1.0.0-1.c2.i386.deb

Ignore any errors that you may see here. 

step 8. Install the two .deb packages from a terminal window with dpkg, doing 
the main iscan package first.

sudo dpkg i- scan_2.5.0-0.c2.i386.deb
sudo dpkg -i iscan-plugin-gt-x750_1.0.0-1c2.i386.deb

Step 8a.

If the main iscan package will not install cleanly because it reports file 
conflicts with certain sane-related packages previously  installed, just go 
ahead and force dpkg to overwrite 

sudo dpkg i- --force-overwrite iscan_2.5.0-0.c2.i386.deb

The plugin should not have a conflict.

This completes the installation.  To test things out make sure the scanner is 
powered up and connected and then type 

iscan

from a terminal, It should start and identify the scanner.  Note the 4490 
takes awhile to warm up, so don't do thing too quickly and don't be surprised 
if things just sit there for a few moments before anything starts to happen.  

Once iscan is installed, the xsane and quiteinsane front-ends also should find 
and control the scanner. I prefer iScan to quiteinsane, but you can try them 
all and decide what best meets your needs. 

Ron Morse
END CUT

---

### Post by rbmorse on 2007-10-25
I updated my original post to correct a few details:

The usual source for Linux scanner help and support is the SANE project
at 

[http://www.sane-project.org/](http://www.sane-project.org/) 

Unfortunately, the Perfection 4490 Photo is not directly supported by
SANE. The good news is that Epkowa, the parent company for Epson in
Japan, provides a Linux driver and a limited control software
application for this unit. Both are available for no charge. 

step 1.  From the Ubuntu repositories for your version, Install sane and
related packages

sane
libsane
libsane-extras    <--- required!
sane-utils
xsane (optional)
xsane-common (required for xsane)

step 2. Connect and power up the scanner. Wait 60 seconds for the
scanner to warm up.

step 3. make sure the scanner is detected. In a terminal window run:

sane-find-scanner

it should report :

    found USB scanner vendor=0x04b8, product=0x0119 at libusb:001:006

The libsub address will vary depending upon which port the scanner is
connected. Ignore the suggestion to run scanimage -L as that will not
work until the scanner driver is installed (below). 

If sane-find-scanner does not find a scanner at all, stop. You have to
solve that problem first.

step 4. Get the Perfection 4490 Photo Linux driver from the Epkowa
site: 

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

Answer their questionnaire. Select Perfection 4490 Photo. I told them I
was using Debian and selected "other" in the version dialog. Clicking on
the "next" button will take you to a download page 

step 5. The source code tarball will not build on Ubuntu(?) so take the
two .rpm files from the appropriate GCC version section for your distro.
For Edgy or Feisty the GCC 3.4 files work. The driver is required, but
iScan is a nice front end for the 4490. 

step 6. If you haven't already done so, install 

alien 

from repository to convert the .rpm files to .deb. (sudo apt-get install
alien) 

step 7. Convert the .rpm files.  In a terminal window change to the
directory where the two downloaded driver files are located then: 

sudo alien iscan_2.5.0-0.c2.i386.rpm
sudo alien iscan-plugin-gt-x750_1.0.0-1.c2.i386.rpm

This should produce the two .deb packages:

iscan_2.5.0-1_i386.deb
iscan-plugin-gt-x750_1.0.0-2_i386.deb

Ignore any errors that may show while alien is doing its thing. 

step 8. Install the two .deb packages from a terminal window with dpkg.

sudo dpkg -i iscan-plugin-gt-x750_1.0.0-2_i386.deb
(optional, but recommended) sudo dpkg -i iscan_2.5.0-1_i386.deb

If the main iscan package will not install cleanly because it reports
file conflicts with certain sane-related packages previously installed,
just go ahead and force dpkg to overwrite 

sudo dpkg -i --force-overwrite iscan_2.5.0-1_i386.deb

The plugin should not have a conflict.

This completes the installation.  To test things out make sure the
scanner is powered up and connected and then type 

sudo scanimage -L

from a terminal, It should start and identify the scanner.  Note the
4490 takes awhile to warm up, so don't do thing too quickly and don't be
surprised if things just sit there for a few moments before anything
starts to happen.  

Use 

sudo iscan (if installed) 

to test. Otherwise, you can test with xsane by typing

xsane

---

### Post by moschops on 2007-10-29
Awesome - this worked with my Epson 3490 too - it was working with Feisty but stopped after a Gutsy upgrade, after 6 months I'd forgotten how I got it working in the first place so I'm glad I found this topic.

---

### Post by kellner on 2007-11-03
thanks for the detailed description! I never got the epson 4490 to work with 7.04, but following these instructions it now works just fine.

---

### Post by Tux Aubrey on 2007-11-07
Thanks for this how-to.

I just spent hours making it NOT work by downloading the wrong driver rpm!  (the one for the 4990 instead of the 4490).  How's that for stupidity?!

Anyway, as soon as I got the right one, everything worked.  Saved me from booting Windows!  Thank you!

---

### Post by tquerette on 2007-11-09
[FONT="Century Gothic"]Did work with my epson CX4900. _No need _to download the Avasys driver witch does not compile under Gibbon/64bits.!!

Thanx[/FONT]

---

### Post by crgutierrez on 2007-12-29
:KSGRACIAS Ron Morse!! Works also for **_[COLOR="Red"]Epson V350 Photo[/COLOR]_** (while I was going insane why it didn't work after the **upgrade from 7.04 to 7.10** and was about to pay somebody $40 for Vuescan......](*,)

---

### Post by luca.mg on 2008-02-23
try [http://ubuntuforums.org/showthread.php?p=4389626#post4389626](http://ubuntuforums.org/showthread.php?p=4389626#post4389626) 

ciao luca

---

### Post by Rollerbob on 2008-04-13
Does anyone know if rbmores's howto will work on an AMD64 machine? Also, I'd be interested to know if anyone's got this working for the Epson V750 scanner, which is the upgrade to the 4990.

---

### Post by antonymous21 on 2008-04-15
Just wanted to leave a quick note to thank Ron for his sooo-helpful guidance. I've got the 4490, I've just switched to Ubuntu 7.10 (a total newbie!) from XP and my main hesitation was whether my scanner would work ok. Feels so nice to be reminded what the Linux community is all about - and great to have the scanner up and running, of course :KS

---

### Post by ryancshih on 2008-05-28
This is great -- got my scanner running. Ran into a small problem while doing the alien conversion since I'm running Hardy Heron, but found the fix with a bit of help from Google: [https://bugs.launchpad.net/ubuntu/hardy/+source/dpkg/+bug/206790](https://bugs.launchpad.net/ubuntu/hardy/+source/dpkg/+bug/206790)

For those who want the one stop quick summary:
Edit your /usr/share/perl5/Dpkg/Changelog/Debian.pm, line 260:
Original: $entry = Dpkg::Changelog::Entry->init(); 
New: $entry = new Dpkg::Changelog::Entry;

Save it and give it another go. Happy scanning!

---

