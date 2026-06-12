---
title: "Invalid compressed format error during install"
date: 2004-12-14
forum: Installation &amp; Upgrades
---

### Post by pwwisnes on 2004-12-14
I'm trying to install the Warty release of Ubuntu on an IBM Thinkpad T23 that just arrived with a clean install of Windows 2000 on it.  The Warty live CD works fine but when I start the installation process, right after the boot menu I get the following:

Uncompressing Linux...

invalid compressed format (err=1)

-- System halted

I am at a loss for what is going on.  I've tried a couple of boot options mentioned in the help (floppy=thinkpad, etc) to no avail.   I've also tried with BOOT_DEBUG=1 and DEBCONF_DEBUG=5 but they don't give me any additional information.   There are not any options in the BIOS related to the CD or hard disk configuration that I can change.   I have burned two cd images just to make sure it wasn't a bad image.  The only other thing I can think of to try is to try a network install but I don't currently have access to any machine I can use to serve up the install image.  

- Paul

---

### Post by jdong on 2004-12-14
Are you sure the CD's burned successfully? The first thing I'd try is a reburn, then a redownload + reburn.


Compute MD5's for the CD and the ISO. Do they match up with the official ones?

---

### Post by pwwisnes on 2004-12-14
[QUOTE=jdong]Are you sure the CD's burned successfully? The first thing I'd try is a reburn, then a redownload + reburn.


Compute MD5's for the CD and the ISO. Do they match up with the official ones?[/QUOTE]

Yes, I tried two reburns from the first image.  Then I downloaded a new image and reburned that (at 4x speed even).  The MD5's agree on all of the images and are correct.

What gets me is that the laptop boots the Ubuntu live cd fine but it won't boot the install cd.  I've booted the SuSe Linux 9.1 install DVD's and successfully installed SuSe on it.  I've also booted the Knoppix 3.7 live CD with no problems so at least one other debian based distributions seems to be ok.  

I'm currently in the process of trying to install Debian Woody with a minimal CD install image.  If that works, I'll just try to upgrade it to Warty.  

Though in the end SuSe may win out just because it actually recognized my D-Link wireless card (which Ubuntu live cd did not).  ;-) 

- Paul

---

### Post by pwwisnes on 2004-12-14
Ok, now its getting really wierd.  After SuSe install worked, I tried a Debian Woody install from a minimal CD image I found linked from Debian.org.  That seemed to work fine.

So, just for kicks I tried an Ubuntu install and it worked!  I don't know why - it was the last CD I burned and had tried before with no success.  So unless I have a intermittent cd/dvd drive, I don't know what to think.

---

### Post by jdong on 2004-12-14
heh, lol. Glad to hear you got Ubuntu installed, though.  =D>

---

### Post by pwwisnes on 2004-12-15
Yeah, thanks.  :-)  I think the final resolution is a wierd one.   The CD tray on the Thinpad T23 is really thin and a little flimsy.  I've noticed that if a disc isn't perfectly seated it can have trouble reading.  It' seems to be worse for the CD-R media I'm using since it appears to be a little thicker that the "pressed" media.  This appears to explain why the SuSe DVD's (sent to me by Novell) worked fine.  It's a wild theory but the only one that seems to fit.  I haven't had to load any other cd's so I haven't been able to test it further.

And I'm even happier since Ubuntu also seems to recognize my wireless card (D-LINK G630) using ndiswrapper and the Windows XP drivers that came on the install CD.  I also haven't confirmed this 100% since I don't have the AP set up yet (the hazards of getting all new hardware and software in at once).

---

