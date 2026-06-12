---
title: "Wine Questions"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-12-11
I have a few questions about wine.  I am using Feisty.

**1. ** How can I install Wine [COLOR=Red]**without**[/COLOR] having to compile anything?

**2.** I would like to use Gimp 2.4 and to be able to print photos.  Since Gimp 2.4 is not realistically available for Feisty is there anybody who has used the windows version of Gimp 2.4 under wine?  

**3**. Do you install windows **[COLOR=Red]print drivers[/COLOR]** so a wine/windows application will print as it does under windows?

**4.**  Will windows software that came with a digital camera run under wine?

Thanks

If anyone has actually done this please state that in your reply.

---

### Post by Xbehave on 2007-12-11
1) add the wine repo on thier site
3) i doubt it wine doesnt do drivers, it does seam to link to my printers in linux though so somethings working
4) only the non-driver part (check on winehq i has lists of software that work/sort of work)

---

### Post by stchman on 2007-12-11
> **measekite said:**
> I have a few questions about wine.  I am using Feisty.

**1. ** How can I install Wine [COLOR=Red]**without**[/COLOR] having to compile anything?

**2.** I would like to use Gimp 2.4 and to be able to print photos.  Since Gimp 2.4 is not realistically available for Feisty is there anybody who has used the windows version of Gimp 2.4 under wine?  

**3**. Do you install windows **[COLOR=Red]print drivers[/COLOR]** so a wine/windows application will print as it does under windows?

**4.**  Will windows software that came with a digital camera run under wine?

Thanks

If anyone has actually done this please state that in your reply.

1.  [http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

2.  What does The GIMP 2.4 do that 2.2 does not do?  You can download 2.4 source and build it.

3.  What printer do you have?  Most printers are supported in Ubuntu.

4.  Running windows software under WINE is hit or miss.

Most digital cameras and nearly every memory card is supported under Ubuntu.  If you want to run windows apps then run Windows.  Ubuntu is not Windows.

I use my digital camera all the time with Ubuntu.  Windows is not really needed IMO.

---

### Post by measekite on 2007-12-13
> **stchman said:**
> 1.  [http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

2.  What does The GIMP 2.4 do that 2.2 does not do?  You can download 2.4 source and build it.

3.  What printer do you have?  Most printers are supported in Ubuntu.

4.  Running windows software under WINE is hit or miss.

Most digital cameras and nearly every memory card is supported under Ubuntu.  If you want to run windows apps then run Windows.  Ubuntu is not Windows.

I use my digital camera all the time with Ubuntu.  Windows is not really needed IMO.

2. For one it has a better crop tool that will crop and keep the aspect ratio.  It also has a better resize and scale tool.  It supports profiles as well.

3. I have a Canon IP4000 for photos.

4.  I would like to use the Canon Zoombrowser software under wine since Canon does not support Linux.  I do not think any Camera maker does.  It has a better and faster editor than Picasa.

---

### Post by stchman on 2007-12-13
> **measekite said:**
> 2. For one it has a better crop tool that will crop and keep the aspect ratio.  It also has a better resize and scale tool.  It supports profiles as well.

3. I have a Canon IP4000 for photos.

4.  I would like to use the Canon Zoombrowser software under wine since Canon does not support Linux.  I do not think any Camera maker does.  It has a better and faster editor than Picasa.

According to the open printing your printer is supported.

[http://openprinting.org/show_printer.cgi?recnum=Canon-iP4000](http://openprinting.org/show_printer.cgi?recnum=Canon-iP4000)

You can try to  install the Canon Zoombrowser under WINE.  The software may work under WINE.

---

### Post by Mark Phelps on 2007-12-13
Maybe my experience with Wine under Feisty was unique, but of the half-dozen apps I tried (none of which were MS apps), about half failed to install properly and the other half failed to run once installed.

So, I bit the bullet and learned how to do stuff using Linux apps -- and discovered that I can do about 95% of what I used to without resorting to Windows.  For that 5%, I keep a dual-boot config and can boot into Windows.

I also tried Crossover Office and found it to be no better than Wine.

So, as others have said, if you want to run Windows apps, then stay with Windows.

---

### Post by Steveway on 2007-12-13
You should consider using Gutsy.
It comes with Gimp 2.4 and has better printing-support.
Also before you try to use your windows-programs, try Linux-native programs first.

---

### Post by measekite on 2007-12-14
> **stchman said:**
> According to the open printing your printer is supported.

[http://openprinting.org/show_printer.cgi?recnum=Canon-iP4000](http://openprinting.org/show_printer.cgi?recnum=Canon-iP4000)

You can try to  install the Canon Zoombrowser under WINE.  The software may work under WINE.

[FONT=ms sans serif, helvetica]Since the guntenprint version 5.0.0 there's a better support for this printer within this driver.
This includes CD-R cover printing and DUPLEX printing

If you have some problems with this printer and gutenprint drivers, please make sure, 
that you are using stable version (not release candidate) of gutenprint drivers, 
because 5.0.0-rc2 has various problems with this printer (look at [https://launchpad.net/bugs/37985](https://launchpad.net/bugs/37985)
 for more info)

[COLOR=Red]**But printing photos is still not good (low resolution)**[/COLOR]. (gutenprint 5.0.0-rc3)

What I did is install the Japanese driver for the
 PIXUS IP4100 in Gimp 2.2 under Fiesty as a Postscript 
driver.  I gained very high resolution but lost duplex 
and border less printing.

Zoombrowser needs certain libs and will not install.

I did install Gimp 2.4 under wine.  It installed and I was
 able to IPL but al of the text and menus was corrupted.  
The icons wsere ok.  It is not ready for prime time.

Since the documentation is not ready for Gimp 2.3 and the 
only decent book (even though  it says 2.4) is illustrated
only for 2.2 (I consider this a fraud) I am going to wait.

I will probably stay with feisty until I build a new network and
system 3rd Qtgr 2008 and then use a new loing term release.

boo
[/FONT]

---

### Post by measekite on 2007-12-14
> **Mark Phelps said:**
> Maybe my experience with Wine under Feisty was unique, but of the half-dozen apps I tried (none of which were MS apps), about half failed to install properly and the other half failed to run once installed.

So, I bit the bullet and learned how to do stuff using Linux apps -- and discovered that I can do about 95% of what I used to without resorting to Windows.  For that 5%, I keep a dual-boot config and can boot into Windows.

I also tried Crossover Office and found it to be no better than Wine.

So, as others have said, if you want to run Windows apps, then stay with Windows.

That is what I quickly learned.

---

