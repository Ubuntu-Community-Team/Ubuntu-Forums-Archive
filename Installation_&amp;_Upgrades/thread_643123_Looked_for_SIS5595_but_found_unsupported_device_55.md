---
title: "Looked for SIS5595 but found unsupported device 5597"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by greathouse on 2007-12-17
Hello,

I just downloaded Ubuntu server (v7.10) for the first time and ran in to an issue.   The CD checks out a-ok and i was able to install a lamp server ok.   When my system tries to boot up the following 
errors occur.

[ 88.677360] sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module not inserted.
[ 89.384621] sis5595_smbus 0000:00:01.0: Looked for SIS5595 but found unsupported device 5597
[ 89.385342] sis5595_smbus 0000:00:01.0: SIS5595 not detected, module not inserted.

it gets to the point where it is loading the start up scripts and then the screen goes blank.  The processor is an AMD-K6 running at 333 Mhz.  The system has a built in video on the motherboard with a SiS 5597 video chip.  

I an not sure but I believe this chip runs identically to the SiS 5595 and can use the same software driver.   Other OS's have run correctly on this system.  I beleive Win 95/98, NT4, W2K and an old version of Red Hat all used a combo 5597 / 5595 driver. 

I believe this is the same error that is found here.
[http://ubuntuforums.org/showthread.php?t=395426](http://ubuntuforums.org/showthread.php?t=395426)

If the software could be setup to expect a return code of 5595 or 5597 when it tries to load the module it should work correctly or if it could just ignore the error and load the module anyway I expect it will run just fine.

Thank You
John Greathouse

---

### Post by foolsh on 2007-12-18
Are you trying to run that in GUI* mode or CLI**?

*Graphical user interface
**Command line interface

Does CTRL+ALT+F1 after the screen goes black, bring up a login prompt?

I dunno
Benjamin Brown IL, USA

---

### Post by greathouse on 2007-12-19
I believe I am running the GUI - it is a standard out of the box installation.

If I do a Ctrl+Alt+F2   I am provided with the bash login prompt and I am able to log in ok.  

If I then do a Ctrl+Alt+F1 I am switched back to screen that shows during bootup.

Thanks
John

---

### Post by foolsh on 2007-12-19
Ok you edit the /etc/X11/xorg.conf file to use the vesa driver if your gonna use the GUI if your card is having problems

you can post your xorg.conf file if your unsure what to change, I'll help.

---

### Post by greathouse on 2007-12-27
My system doesn't have an /etc/X11/xorg.conf file.

The only thing within my X11 folder is a xkb sub folder.

I performed a 'find'  for xorg.conf and drew blanks.

Thanks for your help
John

---

