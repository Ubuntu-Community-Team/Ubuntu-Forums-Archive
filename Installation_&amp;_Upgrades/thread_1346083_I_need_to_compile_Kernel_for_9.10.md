---
title: "I need to compile Kernel for 9.10"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2009-12-04
As the title says, I need to compile Kernel for 9.10 in order to solve the Kernel oops that tormented me for weeks. I'm just a regular computer user, so I need understandable, step by step instructions because most of the time I don't understand anything!

Please!! Or is there some .deb package that can solve my problem?

P.D: The main problem with my computer and 9.10 seems to be mounting anything, including partitions of the same disk, flash drives, etc... or just something else I can't identify, just gives me crash notice.

---

### Post by michaelzap on 2009-12-04
I posted some instructions for using the Lucid kernel here:
[http://ubuntuforums.org/showpost.php?p=8435578&postcount=27](http://ubuntuforums.org/showpost.php?p=8435578&postcount=27)

---

### Post by arashiko28 on 2009-12-04
Ok... so this is what I got from that thread correct me if I'm wrong:

1. Install Lucid kernel
2. update udev (solves USB problems)
3. Kill pulseaudio every 30 mins
4. Get Acer Aspire One (optional) [Just a joke]
5. Change to KDE (not very likely) [Also optional]
6. Receive offered solidarity - at least I'm not alone

Sorry, all that was just a joke, I'm starting to feel a bit frustrated at 9.10 right now, but the first 3 are the most important steps, right? So... I'll spend all night updating my backup to reinstall 9.10 tomorrow, actually I'm on 9.04 64-bits and works like a charm. 
But I do like the display improvements on 9.10 (no dimming and no flashing) and the sweet blinking fast boot.

---

### Post by michaelzap on 2009-12-04
> **arashiko28 said:**
> Ok... so this is what I got from that thread correct me if I'm wrong:

1. Install Lucid kernel
...

Just try that and see if you no longer get crashes. Then if you have some of the sound or other issues that I had you can try some of the other fixes. The kernel is the key.

I would recommend that you stay with 9.04, but I remember that on my laptop I also had very annoying brightness control issues with Jaunty, and personally I'm much happier with Karmic now that it works.

---

### Post by arashiko28 on 2009-12-04
I do remember from my last karmic install that the sound was too low and couldn't to much to improve it... then the crashes began... but tomorrow will be the day :d

---

### Post by arashiko28 on 2009-12-08
It took me longer than I thought, but here are the results:

As expected at the minute I plugged a USB showed up a crash report.
I updated as requested, including a new kernel in the list, it froze nearly to the end of the update and had to hard shut down.
GRUB is a HUGE mess!!! I have (2) 2.6.31-14 entries, (3) 9.04 dev5 entries.
From the 9.10, the first one does nothing, and shows something like a kernel panic. the second one goes on. 
I installed the new kernel 2.6.32.... only the image, the headers shows a mistake about dependencies not being satisfied.
Because of the first freezing, firefox doesn't work anymore. I'm trough epiphany.

Oh! And another crash report showed while installing epiphany-browser on terminal...

---

### Post by arashiko28 on 2009-12-08
> ~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9.1 (1.9.1.5+nobinonly-0ubuntu0.9.10.1) ...
Bus error
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on xulrunner-1.9.1 (>= 1.9.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5-branding:
 firefox-3.5-branding depends on firefox-3.5 (= 3.5.5+nobinonly-0ubuntu0.9.10.1); however:
  Package firefox-3.5 is not configured yet.
dpkg: error processing firefox-3.5-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.5; however:
  Package firefox-3.5 is not configured yet.
 firefox depends on firefox-3.5-branding; however:
  Package firefox-3.5-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-gnome-support:
 xNo apport report written because the error message indicates its a followup error from a previous failure.
                            No apport report written because the error message indicates its a followup error from a previous failure.
                                                      No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
                  No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              ulrunner-1.9.1-gnome-support depends on xulrunner-1.9.1 (= 1.9.1.5+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5-gnome-support:
 firefox-3.5-gnome-support depends on firefox-3.5 (= 3.5.5+nobinonly-0ubuntu0.9.10.1); however:
  Package firefox-3.5 is not configured yet.
 firefox-3.5-gnome-support depends on xulrunner-1.9.1-gnome-support; however:
  Package xulrunner-1.9.1-gnome-support is not configured yet.
dpkg: error processing firefox-3.5-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.5-gnome-support; however:
  Package firefox-3.5-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9.1
 firefox-3.5
 firefox-3.5-branding
 firefox
 xulrunner-1.9.1-gnome-support
 firefox-3.5-gnome-support
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)


Message I get on terminal, I tried to run dpkg --configure -a but only repeats something similar and does nothing.

---

### Post by michaelzap on 2009-12-08
> **arashiko28 said:**
> I installed the new kernel 2.6.32.... only the image, the headers shows a mistake about dependencies not being satisfied.

That just means that you need to install the headers-all package first. Make sure that you install all three packages and try booting from the Lucid kernel. Then go into Synaptic and clean up the mess you just made by uninstalling the kernel packages that you don't need or don't work (click on the Origin button in the bottom left and choose Local/main above that to easily find the debs that you've installed this way and mark them for removal).

---

### Post by arashiko28 on 2009-12-09
I didn't uninstalled anything, I just installed image first. The mess comes from the computer freezing during update, while installing components, I had nothing to do with it.

---

### Post by aknight on 2009-12-09
[http://www.linuxinstallhowto.co.cc]("http://www.linuxinstallhowto.co.cc/")
[http://nic.linuxinstallhowto.co.cc]("http://nic.linuxinstallhowto.co.cc/")

---

### Post by arashiko28 on 2009-12-09
> **aknight said:**
> [http://www.linuxinstallhowto.co.cc]("http://www.linuxinstallhowto.co.cc/")
[http://nic.linuxinstallhowto.co.cc]("http://nic.linuxinstallhowto.co.cc/")

Thank you, but I don't need a guide to install Linux, what I do want is to fix 9.10 kernel issues with my computer, and solve the crashes and random freezing.

---

### Post by arashiko28 on 2009-12-09
Ok, I installed the last 2 packages of the kernel, until now, no crash reports, now, how do I fix the dpkg error code 1 and the other mess caused by the freezing?

I tried to sudo dpkg --configure -a but all I get is the same error message and no chance to fix it.

I tried to reinstall xulrunner but no good, either with firefox.

---

### Post by michaelzap on 2009-12-09
> **arashiko28 said:**
> I tried to sudo dpkg --configure -a but all I get is the same error message and no chance to fix it.

You get the same error when you run sudo dpkg --configure -a as when you tried to install/update Firefox?

---

### Post by arashiko28 on 2009-12-11
> **michaelzap said:**
> You get the same error when you run sudo dpkg --configure -a as when you tried to install/update Firefox?

Yes. It's just a trial installation but I don't want to make it deffinitive without solving this, I know when I reinstall will have the same crash before I can update the kernel.

---

### Post by michaelzap on 2009-12-11
> **arashiko28 said:**
> Yes. It's just a trial installation but I don't want to make it deffinitive without solving this, I know when I reinstall will have the same crash before I can update the kernel.

That error just looks like a botched Firefox installation to me. Not sure how/why that would happen. You might just try removing and reinstalling Firefox and seeing if that helps.

---

### Post by arashiko28 on 2009-12-11
I already did it a thousand times, trough terminal, synaptic and with .deb packages.

It happened because the first thing 9.10 did was look for updates, so I accepted them and downloaded the kernels, during the installation of the updates, after all the files were downloaded, it crashed and froze I gave it about 10 mins to see if it could solve alone, but then I realized I had to hard shutdown.

So one choice is to install without internet until I have the kernels updated, the fault in this is that if I can't download it, where do I get it? every time I plug an USB drive, or mount a partition, there's a crash and eventually freezing. While looking for a solution, I'm testing all the other things. 
Sound... check! :)
Display... check!
Camera... check!
WIFI... check!
USB... check!
Memory card slot... check!

---

