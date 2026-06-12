---
title: "Upgrade mostly worked but no Kubuntu desktop"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Dritz on 2007-10-19
Not  sure how best to describe this.

Essentially my I think my upgrade worked fine I used the alternate CD to upgrade most stuff and everything else was done on a network. However I wasn't at my computer and I believe at the end of the upgrade my computer is supposed to restart only problem is I believe it did not quite restart right and I had to shutdown the computer by holding down my computers power button.

When I started up again I stalled on the Kubuntu splash screen and went to command line (ctrl alt f1) and attempted to fix things. Unfortunatly I forget the exact process but it involved some dpkg line which worked fine except I was greated with the message that acpi, kubuntu desktop, and, some power management thing were not working properly.

I tried reinstalling each (using aptitude if that helps) and was met with failure each time.

What's the proper way of getting kubuntu-desktop back? Is there a way I can use my alternate CD to somehow install the required dependencies since I can't seem to get them from the servers (at all, it's not just being slow).

* Edit * Just a bit of extra information (I really wish I could copy and paste). When I attempted to install acpid I'm told can't open /proc/acpi/event device or resource busy. I also get the error:

dpkg: error processing acpid (--configure): subprocess post-installation script returned error exit status 1

Because I can't get this to work I assume that's the root of none of my other packages installing correctly since they all depend on acpid.

*Edit 2* Screw it I'll just type out the entire error script:

[code]the following NEW packages will be installed:
   acpid
0 packages blah blah blah
Need to get ... will be used
Writing extended state information... Done
Slecting previously deselected package acpid
(Reading database ... xxx files and dir ... installed.)
Unpacking acpid from ...
*loading Acpi modules...
*Starting ACPI services...
acpid: can'topen /proc/acpi/event: Device or resource busy
invoke-rc.d: procesing acpid (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
acpid
E: Sub-process /usr/bin/dpkg returned error code (1)
A package failing to install. Trying to recover:
Settingup acpid (1.0.4-5ubuntu8) ...
* Loading ACPI modules
*starting ACPI services
acid: can't open /proc/acpi/event:device ro resource busy

---

### Post by Dritz on 2007-10-19
Found the solution 

I swear I looked around here before posting first.

---

### Post by diablozx9 on 2007-10-19
well,,, now that you posted and fixed it,,, why not post what you did to fix it?

---

### Post by Dritz on 2007-10-19
Could have sworn I did it was in [this]("http://ubuntuforums.org/showthread.php?p=3567633&posted=1#post3567633") thread

---

