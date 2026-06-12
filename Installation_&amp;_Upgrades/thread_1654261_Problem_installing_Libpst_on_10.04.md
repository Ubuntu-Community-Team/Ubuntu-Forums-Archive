---
title: "Problem installing Libpst on 10.04"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by blueghoti on 2010-12-28
Hi all - 

I'm trying to convert some Outlook PST files to Thunderbird.  I have been recommended to install libpst, but am having some problems with this.

I am trying version 0.6.49 and have attempted the install several times.  Despite some help (from someone who knows what he's doing... unlike me!) we still can't get the package installed.  Usually there are 0 files for installation / update and 14 are "held back".  Make any sense to anyone?

I also get the following error when installing python 

checking python extra libraries... -lssl -lcrypto  -lssl -lcrypto      -L/usr/lib -lz -lpthread -ldl  -lutil
checking python extra linking flags... -Xlinker -export-dynamic -Wl,-O1 -Wl,-Bsymbolic-functions
checking consistency of all components of python development environment... no
configure: error:
  Could not link test program to Python. Maybe the main Python library has been
  installed in some non-standard library path. If so, pass it to configure,
  via the LDFLAGS environment variable.
  Example: ./configure LDFLAGS="-L/usr/non-standard-path/python/lib"
  ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them.
  ============================================================================


Any suggestions (preferably in very simple steps for a newbie) would be very much appreciated.

Thanks, 
Chris

---

### Post by davidmohammed on 2010-12-28
dont know on this issue - but if you still have outlook and windows - install thunderbird in windows.  You'll be able to import directly into thunderbird.

I believe the linux and windows versions of thunderbird as similar so you'll be able to read from the windows thunderbird database.


alternatively I believe evolution can directly import from outlook pst files.  Maybe you can then "export" from evolution into a format thunderbird can import from...

---

### Post by blueghoti on 2010-12-28
Hi David - 

Thanks for the tips.  I have uninstalled Windows, and sadly don't have access to a suitable machine to do what you suggest.

I like the idea of using evolution, but I tried that some time ago and wasn't successful.  Can't recall what the issue was - do you have any tips on how to do a PST import into Evolution?

Chris

---

### Post by davidmohammed on 2010-12-28
I know evolution was a little bit touchy for versions prior to 10.04.  Havent read any serious issues with the version in lucid.  

Give it a try - File Import - walk through the wizard selecting import from a single file.

---

### Post by blueghoti on 2010-12-28
Thanks David.  That jogged my memory - I was having problems importing larger PST files (I have one about 4 gig) and also other details such as calendar and task items :-(

---

### Post by davidmohammed on 2010-12-28
hmmm - 

as an aside libpst4 is installed by default in ubuntu lucid - why are you trying to use a slightly newer version from sourceforge?

---

### Post by davidmohammed on 2010-12-28
...

I downloaded libpst-0.6.49...rpm file

then I ran

sudo apt-get install alien


then I converted the rpm to a deb
(ignore the error message reported)

sudo alien -d libpst....rpm

then I installed the deb file

sudo dpkg -i libpst...deb

I cant test this new libpst file though since I dont have an outlook.pst file to play with.  Hope it works for you.

---

### Post by blueghoti on 2010-12-28
Thanks David.  I'll give this a try this evening when I can concentrate on it properly.  I appreciate your help / advice and will let you know how I get on.

---

