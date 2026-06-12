---
title: "Thinkpad T61 Unable to Boot from CD"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by shalomshachne on 2013-05-24
I burned install CD for Ubuntu 12.04, and tried to run it in my Lenovo Thinkpad T61. The purplish welcome screen appears, but when I select "Try Ubuntu without Installing", it just goes to a blank screen.  I've read a bunch of posts describing ways to get around this.  For example [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) .   I tried suggestion to get to boot into text mode by updating the boot line, 2 different ways:

[FONT=courier new]text or s

nosplash vga=771 text[/FONT]

but both had the same result.  (Actually one of them cause the laptop to shut down and restart). 

A possible other problem with boot is that the laptop does not have a working hard drive.  I was hoping that I could run with the CD until I can get replacement hard drive working (formatted, etc), so possibly that is the problem.  

This is my first time trying to install/run Ubuntu (although I do use Centos Linux on servers in my office, but I am by no means an expert.)  Any suggestions are appreciated!

Thanks.

---

### Post by 2F4U on 2013-05-24
Can you post some more information about your hardware and in particular about the graphics card? A blank/black screen is often due to the graphics card. Did you try the grub kernel parameter nomodeset?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by shalomshachne on 2013-05-24
To answer your questions:
- this is a Lenovo Thinkpad T61 laptop. On [Lenovo's web site]("http://support.lenovo.com/en_US/detail.page?LegacyDocID=migr-67883#vid") they say:

[LIST]
[*]Intel PM965/GM965 graphics
[*]128MB nVidia Quadro NVS 140M
[/LIST]

I tried nomodeset both using the F6 menu (selecting no modeset from menu), and also by editing boot text.  It didn't work either way.  

Procedure I am following, from purple start screen, I press F6, then edit the boot command line with the options.  Then press <ENTER>.  Result so far is always the same, black screen of death.

---

