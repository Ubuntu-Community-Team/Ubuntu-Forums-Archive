---
title: "[SOLVED] Gutsy installation problem"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Goldpin on 2008-02-01
Don't know if this is normal, but after I installed Gutsy, the initial screen which shows the "progress meter" will get about halfway and then go into text mode.  OK, I might have a bad disk, but it happens both after a new install and after I've tried installing with the alternate CD.

Also have a problem trying to use the OpenOffice Base.  When I try to open a database form or table, Openoffice Hangs.  I know that's most likely an OpenOffice probem, but it might be related to the Gutsy install.  Can anyone tell me.

1.  Is the "problem" on bootup normal?

2.  Should I:

     a.  Format the drive and do a clean install?

     b.  Reinstall Feisty and try the upgrade CD?

3.  Has anyone else had similar problems or occurances?

Thanks in advance.

---

### Post by zvacet on 2008-02-01
> Also have a problem trying to use the OpenOffice Base

Does this mean that you are able to login after all?if that is the case type in terminal 

```
sudo dpkg-reconfigure xserver-xorg
```

and when it comes to drivers select** vesa** and continue to the end.Restart and you should have elementar graphic.Now you are in position to search driver for your video card.I think you will find it in system>restricted drivers manager.

---

### Post by Goldpin on 2008-02-01
Sorry, I did forget to mention that the login screen comes up after ubuntu boots.  I can login ok, but I need to know if this is and the problem with OpenOffice Base are bugs and what to do about it (if anything can be done).:confused:

---

### Post by Hagar Delest on 2008-02-01
Base is bugged with the Ubuntu version. You should try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Goldpin on 2008-02-05
Got the official OpenOffice download, but I'm not sure where I went wrong.

I took out all the OpenOffice files I found from the original Ubuntu installation, but I might have removed the JRE as well.  When I went into the new OpenOffice installation, there was a dialog box that came up which said I needed JRE for the OOo Base module.  Where do I go from here?

Please tell me how to install JRE ***WITHOUT *** using apt-get.  I don't have a working interntet connection yet.  I can download files elsewhere and copy them onto my computer.

---

### Post by Hagar Delest on 2008-02-05
Are you sure the JRE has been removed? In OOo, go to Tools>Options>OOo>Java, wait a while and see if there is a version detected. If so, check on of them.

Else, download the OOo tarball with JRE and install the .deb for the JRE.

---

