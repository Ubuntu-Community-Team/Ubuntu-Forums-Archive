---
title: "Printing and Video"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-08-30
I am using LiveCD with Ubuntu.  There are two problems that keep me in the Windows Camp.  They are Video and Printing.
[B]
PRINTING:[/B]

I installed Gutenprint for a Canon IP4000 printer.  While not fully tested I did print out the test page.  There are two noticeable problems.  There is not ink monitor under properties.  There is not way to tell when a tank is low or empty so there is the possibility that you can ruin your printhead,

When you choose Custom paper size there is no place to put in the custom dimensions.

When you choose paper feed from cassette it does not work.  The only way to control the paper tray is to use the button on the printer.  The software controls do not work.

**Where can you get and install a printer driver that will work with all of the features for this printer like it does in Windows?**

**Video**

I have a 22" widescreen ViewSonic driven by a BFG Nvidia 6600.  I need to use 1680x1050 @60Hz resolution (native).  The highest on the drop down is 1024x768.  My specific monitor is not listed in Kubuntu and I could not find the listing when using Ubuntu.  I went to the Nvidia site but do not know what driver to download and there are not clear instructions to install them.  I am used to typing setup and following the menu prompts.
[B]
How can I solve this problem?[/B]

If I am having such a hard time (initially) then I assume that is the reason why Linux has not been embraced by the masses.  For other than Photoshop, Quicken, and Retrospect I expect to do everything I do in Windows (except programming in SQL Server and VB.net) in Ubuntu.*_> _*

---

### Post by forestpixie on 2007-08-30
you should be able to install the nvidia driver with
system >admin > restr driver manager

if after you have a problem getting back in use

```
sudo dpkg-reconfigure xserver-xorg
```

to reconfigure drivers. then you can use nvidia-settings to change resolutions

```
sudo nvidia-settings
```

printer - I don't know about the printing issue - have looked in the forum for that model. But you can use [turboprint]("http://www.turboprint.de/english.html"), unfortunately it's not free - but you can try it for a month.

> I am used to typing setup and following the menu prompts.

so was I - but I prefer being here now all round.

---

