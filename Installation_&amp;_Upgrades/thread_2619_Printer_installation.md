---
title: "Printer installation"
date: 2004-10-29
forum: Installation &amp; Upgrades
---

### Post by trico on 2004-10-29
How does one install a printer?  

I used the Computer->System Configuration->Printing to open up the Printers window.  And then used New Printer to add my Canon S600 to my system (its on a parallel port).  It wanted a driver and I found one here:
[http://www.linuxprinting.org/show_driver.cgi?driver=bj8pa06n.upp](http://www.linuxprinting.org/show_driver.cgi?driver=bj8pa06n.upp)
I clicked on the generate ppd file button and downloaded the file to my system.  Then I pointed the program at it and it quit with an error.  The error is:
"The PPD /usr/share/cups/model/Canon-BJC-8200-bj8pa06n.upp.ppd is already installed"

Ok, so I back out of that and assuming that wants to install what it has - I press the accept button and get.
"The application 'gnome-cups-manager' has quit unexpectedly."

At the end, I have a S600 in my printers, but when I try to print to it from Firefox, its not showing up.

Any suggestions?

Trico

---

### Post by Joeb on 2004-10-29
There might already be a built in driver for your printer, but unfortunately, they're not installed by default.  Try using Synaptic to add the package called cupsys-driver-gimpprint and see if your printer is then listed (instead of synaptic, you could also sudo apt-get install cupsys-driver-gimpprint     from the command line).

Joeb

---

### Post by trico on 2004-10-29
Looked in Synaptic Package Manager for cupsys-driver-gimpprint and didn't find it.  

Then I tried sudo apt-get install cupsys-driver-gimpprint and got this message:
Reading Package Lists... Done
Building Dependency Tree... Done
Package cupsys-driver-gimpprint is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cupsys-driver-gimpprint has no installation candidate

Perhaps I have some configuration file that's looking in the wrong place?

Trico

---

### Post by Joeb on 2004-10-29
[QUOTE=trico]Looked in Synaptic Package Manager for cupsys-driver-gimpprint and didn't find it.  

Then I tried sudo apt-get install cupsys-driver-gimpprint and got this message:
Reading Package Lists... Done
Building Dependency Tree... Done
Package cupsys-driver-gimpprint is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cupsys-driver-gimpprint has no installation candidate

Perhaps I have some configuration file that's looking in the wrong place?

Trico[/QUOTE]


If you go into Synaptic and then go to the settings menu and then the repositories.  There should be one there called "universe"  check the box next to it.  After returning to the main Synaptic screen, you want to hit the "reload" button.

Universe contains packages that aren't officially supported by the Ubuntu developers, so there is always the warning of "use at your own risk."  But, most are very stable and the cups drivers are definately so.  

Joeb

---

### Post by trico on 2004-10-29
Looks like that worked.  I'm able to print a test page.

Thanks for the help.

One thing that still puzzles me.  I am able to print from Firefox using File->Print...
But the printer that it's going to is "Postscript/default".  I assume thats mapped to my Canon S600 somewhere.  Where is that done?

Trico

---

