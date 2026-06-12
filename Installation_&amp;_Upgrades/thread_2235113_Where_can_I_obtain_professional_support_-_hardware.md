---
title: "Where can I obtain professional support - hardware upgrade 12.04?"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-19
I have lost over 16 hours professional time trying to get these upgrades completed.  All PCs have nVidia graphics.  One will not do nouveau because nouveau will not do 1280 x 1024 .

I have my DELL Vostro 3500 done (about 5 hours).  Another desktop took another 5 to get coorect nVidia driver to work.

I have over six hours in on my secretary's PC.  Correct driver is loaded in synaptic, but "Additional drivers" will not install it.  I need this PC running by Monday morning EDT.  Driver that was working was 304

ALL THREE PC'S WERE WORKING CORRECTLY BEFORE THIS HARDWARE UPGRADE.

Please note that any support will need to be over phone or e-mail as I cannot allow remote logins.

John

---

### Post by claracc on 2014-07-19
[http://www.ubuntu.com/support](http://www.ubuntu.com/support), here there are various ways of support.

---

### Post by tgalati4 on 2014-07-19
Join a linux user's group (LUG) in your area.  I'm sure you can find someone with linux experience to help you out.  Upgrading machines over the phone is difficult because you can't see what is going on.  What specific hardware did you upgrade?  Are you doing a 12.04 to 14.04 updgrade as well?  A clean install of 14.04 can be done in 15 minutes.

Are you doing CAD/CAM work that requires nVidia proprietary drivers?  If these computers are used for standard office functions, then the open driver (nouveau or nv) should work.  The inability to get 1280 x 1024 could be a video RAM problem.  What is the specific card model for that machine?

Open a terminal:

```
lspci | grep VGA
```

A lesson learned is not to take a working, production machine out of production, until you have a backup plan--a spare machine that you can use to rotate.  Upgrading 3 machines at once is taking a risk.  Regressions are common in linux.  Many are fixable, but it takes time and patience.  (Which is why I have the quote in Latin in my signature.)

---

### Post by cigtoxdoc on 2014-07-19
Thank you for your help.  First, upgraded one machine at a time.  Both hp/compaq DX2200m and DX2250m upgraded w/o problems.  These can be substituted for main production PCs as everything backed up off-site on SpiderOak.  Only real problem machine has been the one with the ViewSonic 926 monitor (1280 x 1024 x 24 at 60 Hz or 75 Hz).  The boot replair disk got the nouveau driver installed and machine will boot with proper resolution, but display is grainer than usual.  There is no xorg.conf file.

Correct nVidia driver is 304.108 according to [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

John



Output of lspci | grep VGA is nVidia C61 GeForce 7025 / nForce 630a (rev a2).

---

### Post by oldfred on 2014-07-19
I do not suggest ppa unless you have a very new bleeding edge nVidia card that needs the very newest driver.

And if you attempt to install different versions from ppa, nVidia or Ubuntu's repositories they all conflict. You have to totally houseclean/purge old version before trying different.

Best just to use repository and install from System Settings or command line.

       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

    
Later older nVidia cards will not be updated.
 NVIDIA is ceasing to support their older GeForce 8, 9, 200, and 300 series from their mainline driver but the NVIDIA 340.xx driver series will become a long-term legacy driver that they will commit to supporting until April of 2016. 
[http://nvidia.custhelp.com/app/answers/detail/a_id/3473](http://nvidia.custhelp.com/app/answers/detail/a_id/3473)
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/session/L2F2LzEvdGltZS8xNDAyMzMzMDI0L3NpZC9fVTZwRW9XbA%3D%3D](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/session/L2F2LzEvdGltZS8xNDAyMzMzMDI0L3NpZC9fVTZwRW9XbA%3D%3D)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by ubfan1 on 2014-07-19
Check your "other" tab in "software &Updates" dash icon, and ensure you have checked the binary for partners and maybe others too.  Not sure if that's necessary, but the nvidia-current package should get the 304.117driver, which works on my even older Nvidia chip.  Just to be sure, apt-get update before looking at the additional drivers tab in the "software & updates", and let it run until it displays (may take a minute or two).  Select Nvidia current, and that should work for you.  lsmod should list nvidia as a driver when working.

---

### Post by cigtoxdoc on 2014-07-19
Thank you yo all for your help.  Right now system is running with the nouveau drivers, the screen resolution is correct, the programs my secretary uses, and the system appears stable.  We will wait on anything nVidia for that system until I decide to get a new monitor for it or someone can make nVidia realize the ViewSonic VA926g monitor is not a laptop.

John

---

### Post by tgalati4 on 2014-07-20
The graininess could simply be that the monitor is running at 60 Hz (and interfering with fluorescent lights).  If you can't change to 75 Hz in display preferences, then you need to use *xrandr* to set the refresh rate manually.  If that doesn't work then manually make an xorg.conf and put in the gtf [modeline]("https://help.ubuntu.com/community/NvidiaResolutionXorgConf") in the correct place.

```
man xrandr
```

> tgalati4@Mint14-Extensa ~ $ gtf 1280 1024 75

  # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync


Your numbers will be different.

---

### Post by cigtoxdoc on 2014-07-25
This problem is solved.  I have purchased a 5-PC support agreement from Canonical.  Tech who assisted me on cleaning up from upgrade of 12.04 to 14.04 provide excellent service.  I probably could have done much the same after much study, and trial-and-error.  If I had had the contract in place last week, I would have saved numerous hours of work and much frustration.

John

---

### Post by bapoumba on 2014-07-26
> **cigtoxdoc said:**
> This problem is solved.  I have purchased a 5-PC support agreement from Canonical.  Tech who assisted me on cleaning up from upgrade of 12.04 to 14.04 provide excellent service.  I probably could have done much the same after much study, and trial-and-error.  If I had had the contract in place last week, I would have saved numerous hours of work and much frustration.

John

I'd be curious to know what they had you do for this cleanup.

---

### Post by cigtoxdoc on 2014-07-26
First, my consulting business takes me to numerous scientific meetings each year.  If anything happens to my secretary's PC as far as Ubuntu is concerned, my secretary will not be able to do her job until software problems are fixed or she goes to one of the other PCs where she has a login, and downloads the backup data files from SpiderOak.  So, it was clear I needed technical support just for that reason alone, as there does not appear to be professional Linux support locally.  Second, the upgrade to 14.04 trashed my /etc/fstab.  Canonocal tech made fast work of not only getting back to where I was, but also dealing with some folder permisssions.  Third, he cleaned up some other "cosmetic" issues that came in with 14.04.  Yes, I probably could have spent several hours doing this myself, but that would have meat several hours less billable time.

John

---

### Post by bapoumba on 2014-07-26
Did you write down the procedure ?

In another thread of yours, I offered to have a look at your fstab, as general ideas can translate differently for a particular install. That was easy to do. I do not think your fstab was trashed, rather the new one you set up during the install was not appropriate for your use and that was also easy to fix, should you provide the relevant info.

What do you mean by "get back to where I was" ? Go back to 12.04 or go back to a working environment ? What folder permissions are you talking about ?

I ask because other users experiment the HWE upgrade problem when running updated Precise. If you would share how you fixed your install or your reinstall, that may help others. That is what the ubuntuforums are all about.

---

### Post by cigtoxdoc on 2014-07-27
The answer to your question is not a short one, as it is based, in part, on my scientific consulting busniess, the lower cost of Linux-based applications software, and my decision to get out of Windows with the demise of XP.  I had been using Ubuntu for about five years for noncritical work, and my secretary's PC has been on Ubuntu for everything but a Brother label-printer since 2012.  I had enough experiences with Ubuntu crashing w.o simple recovery that I wanted to keep scientific data, journal article reprints, and business reports out of the Ubuntu directory.  This requires permanent disk partitions that are assigned on boot by /etc/fstab.  I got the syntax for doing that this past January from this forum.  The problem that Canonical solved was that, for example, the upgrade had taken /media/MyData1, and made it /media/john/MyData1.  Since I frequently move files (using konqueror in super user mode) among MyData1, MyData2, home/john/Downloads, having the partitions as /media/john/MyData1 was a major pain.  Canonical support person got things where the work right for me.  I use konqueror because it is much easier to set file associations to programs that are not recognized by nautilus (now files).

Hope this helps.

John

---

