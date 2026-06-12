---
title: "firefox crash"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by x1a4 on 2007-11-12
Hi,
Sure-fire way to crash Firefox (exit code 139) on my Xubuntu after upgrade to Gutsy is to visit ubuntuforums.org, then there are random crashes, making Firefox virtually unusable.  

How do I fix this? 

Thank you.

---

### Post by por100pre1 on 2007-11-13
Try reinstalling Firefox:

```
sudo aptitude reinstall firefox
```

Check if using a fresh profile works fine:

```
firefox -ProfileManager
```

---

### Post by x1a4 on 2007-11-13
Reinstalling Firefox didn't help.  It's not a profile issue.  Firefox crashes regardless of the profile or user accounts it's running on.  Visiting ubuntuforums.org will crash it everytime.

---

### Post by por100pre1 on 2007-11-13
Open Firefox from command line and try again. Post any error messages you may get. :-k

---

### Post by eosha on 2007-11-14
```
me@me:~$ firefox
Segmentation fault (core dumped)
```

Not very helpful...

---

### Post by ddrichardson on 2007-11-14
Segmentation faults might not necesseraly be caused by the application that is crashing. If this is an upgrade, I'd be inclined to think its a conflict between something that is installed previously - although the first thing to eliminate is to disable all Firefox extensions.

The other thing that springs to mins is to disable javascript - which the forum uses in the menus and see if the segfault is related to javascript.

---

### Post by x1a4 on 2007-11-14
```

[x1a4:tcsh]~/% firefox
/home/x1a4/.gtkrc-2.0:2: Unable to find include file: "(null)/Xfce/gtk-2.0/gtkrc"

(gecko:10591): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Tahoma 9'

Segmentation fault (core dumped)
Exit 139
[x1a4:tcsh]~/% 

```

---

### Post by ddrichardson on 2007-11-15
Have you got the mscorefonts installed?

---

### Post by elliio on 2008-01-24
:popcorn:I just had this fun and ugly experience with firefox and xubuntu gutsy! :-)
 
After reading up on some forums and reinstalling, rebooting, purging, etc, even installing "other" firefox browsers like swiftfox, flock, and icecat, I still would crash when accessing:
 
[www.ubuntu.com]("http://www.ubuntu.com")
[www.ubuntuforums.org]("http://www.ubuntuforums.org")
 
 
etc...
 
 
I started loading firefox from the terminal to try and get some "feedback" on the crashes, and apparently Pango didn't like Tahoma 9 on the websites.
 
My fix: I specified all the fonts to be Bitstream Vera xxx and (I'm sure you could use any NON-msttcorefont) (I've since removed the package) and disallowed websites to use fonts other than those I have specified.
 
 
To accomplish the same in firefox on any ubuntu-family installation (for the record, I am currently on xubuntu-gutsy)
 
01. Launch Firefox.
02. Go to the Edit menu and select Preferences.
03. Select the Content tab.
04. In the "Fonts & colors" section, click on the Advanced button.
05. Specify the fonts you would like to use as the defaults, as well as their size.
06. Uncheck the checkbox "Allow pages to use their own fonts, instead of my selections above."
07. Restart Firefox
 
You should be free of the ubuntu.com/ubuntuforums.org crashes, however you won't be seeing any of the cool fonts the web designers used.
 
I hope an Ubuntu admin reads this and forwards the info to the appropriate dev team.
 
I'm so fresh and new at xubuntu, Ubuntu and GNU/Linux in general it IS funny. Seriously though I've only been using Ubuntu since Feisty, and have had a wonderful Windows-ditching experience!
 
Hopefully this workaround will be of use to somebody other than Yours Truly.
 
Best, elliio

---

### Post by davmaz on 2008-01-27
I have a problem where I "suspect" Firefox is locking up my whole system (Dell Dimension E5150 running gutsy). Since I always have Firefox open or have opened it from time to time, it seems it might be the cause.

Now this is not a Firefox crash, it's a COMPLETE system lockup (with the exception of the mouse curser can be moved on the screen -- period -- that's it). I need to hold the power button in for X seconds until it takes it down. This one really has me stumped.

I'm ready to install Widnoze back on the machine to see if it's a hardware problem since it seems so unpredictable.

Here's a strange hint: when it "locks up" I can still hear the machine running (disk chug, even sometimes the fans on the processor spinning up like if it's now "loaded" more than usual)!

Any suggestions?

---

### Post by hbbk on 2008-03-24
hi

I had a similar pb (see [http://ubuntuforums.org/showthread.php?p=4573420#post4573420](http://ubuntuforums.org/showthread.php?p=4573420#post4573420) ) and, as I wrote there, my way to solve it was to **remove** the ubuntu packaged firefox then install it "by hand" from **mozilla.com tar.gz package**. Then it works perfectly without changing anything in my profile, extensions, plugins (I symlinked all the ubuntu installed plugins libraries to the plugins dir of my new ff), font selection, whatsoever ... the pb came without any doubt from the ubuntu package installation (some kind of optimization maybe ?:()

---

### Post by lajevardi on 2008-04-02
try this:
```

sudo apt-get install --reinstall ttf-bitstream-vera libpango1.0-0 libcairo2

```

---

### Post by ewinslow on 2008-04-15
Great tip.

That cured it for me.

> **lajevardi said:**
> try this:
```

sudo apt-get install --reinstall ttf-bitstream-vera libpango1.0-0 libcairo2

```

---

### Post by jgt157 on 2008-04-17
I'm having this same problem with ubuntu gutsy on my laptop as well.  Strange thing is, I had kubuntu gutsy installed previous to this and had no problems with lockups on it.

---

