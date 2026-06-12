---
title: "Fresh Install, Monitor says &quot;frequency out of range&quot;"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by stifler on 2006-09-04
So I just tried to install Dapper on my 2nd hard disk, but my screen remains dark after starting the graphic installer with the message "frequency out of range". 

Changing the different VGA-Modes or trying to install in "safe vga mode" doesn't help either. Even tried vga=771 as boot parameter, didn't help.

I'm aware that I can reconfigure an already installed Ubuntu by editing xorg.conf but what can I do during a fresh install?

Any hints are welcome!

**EDIT:** My monitor is an [ASUS MM17DE]("http://www.asus.de/products4.aspx?l1=10&l2=85&l3=0&model=742&modelmenu=1")

---

### Post by john_spiral on 2006-09-04
Hi,

At what stage during the install does your system become unusable?

Try booting off the ubuntu CD and editing the xorg.conf file.

john

---

### Post by stifler on 2006-09-05
> **john_spiral said:**
> 
At what stage during the install does your system become unusable?

The only thing I'm able to see is the splash screen telling me what ubuntu is actually loading&preparing, after this the splash screens goes away, I've shortly a (approx. 2-3 secs) blinking cursor in the upper left corner and then my monitor tells me that the frequency is out of range, I can still hear the CD-drive & harddisk working for at least 1-1,5mins but the screen remains dark.

Of course I'm able to switch between the different text consoles via CTRL-ALT-Fxx but when it comes to the graphics installer desktop via CTRL-ALT-F7 -- darkness / out of range.

> **john_spiral said:**
> 
Try booting off the ubuntu CD and editing the xorg.conf file.


How do you mean that? Should I switch to a text console and edit the xorg.conf end restart the xserver somehow after the cd-boot phase?

Just to clarify: I have no running ubuntu :-? I'm trying to get it installed. But mayby I'm not that expirienced in linux graphics business. I've no clue if it's possible to modify the xserver running of the installation cd.

thanks in advance!

---

### Post by john_spiral on 2006-09-07
if the ubuntu CD boots, edit the file from with the live CD session using the terminal:

sudo gedit /path/to/xorg.conf  

I can't remember the path think it's in etc/X11.... something

give it a try

---

### Post by wpshooter on 2006-09-07
> **stifler said:**
> So I just tried to install Dapper on my 2nd hard disk, but my screen remains dark after starting the graphic installer with the message "frequency out of range". 

Changing the different VGA-Modes or trying to install in "safe vga mode" doesn't help either. Even tried vga=771 as boot parameter, didn't help.

I'm aware that I can reconfigure an already installed Ubuntu by editing xorg.conf but what can I do during a fresh install?

Any hints are welcome!

**EDIT:** My monitor is an [ASUS MM17DE]("http://www.asus.de/products4.aspx?l1=10&l2=85&l3=0&model=742&modelmenu=1")

If you have not gotten this fixed post back and I will tell you how I fixed this.  I had this or a very similar problem on 3 of my computers.

Am about to leave work, so it may be about 2 to 3 hours before I am back on.

---

### Post by socko on 2006-09-07
If I'm not mistaken, "frequency out of range" usually means that your monitor is on, but receiving no input from a video card.

---

### Post by stifler on 2006-09-08
> **wpshooter said:**
> If you have not gotten this fixed post back and I will tell you how I fixed this.  I had this or a very similar problem on 3 of my computers.

Am about to leave work, so it may be about 2 to 3 hours before I am back on.


To be honest, I've had had no time yet to try the solution suggested by john_spiral but in fact it is just a hint what to do rather then a solution out of the box, so I'd be glad about telling me how you did that, because at least it's pretty frustrating gettin' stuck before having any chance to play around with ubuntu ](*,)

---

### Post by wpshooter on 2006-09-08
First another question.  When you get the out of range message, does Ubuntu go ahead and boot all the way up to the desktop or does it just hang at some point ?

---

### Post by Ocxic on 2006-09-08
your computer boots fine, the frequency out of reange error, means iether your screen resolution is set way too high, or your refresh rate is set too high, try editing you /etc/X11/xorg.conf and comment out/remove the resoution that are too high for your monitor to use.

alternatavly you can use the "sudo dpkg-reconfigure xserver-xorg" command and setup the xserver manually with the config app, by usig one of the ctrl-alt-f?? terminals.

---

### Post by stifler on 2006-09-18
> **wpshooter said:**
> First another question.  When you get the out of range message, does Ubuntu go ahead and boot all the way up to the desktop or does it just hang at some point ?

As I said - the system doesn't become unusable - the graphic installer simply doesn't show up, but I'm still able to switch between the text terminals via CTRL-ALT-F1 - F4

---

### Post by GadgetsGuy on 2006-09-30
This will solve your problem!

Please ['digg me']("http://www.digg.com/linux_unix/Easy_Fix_for_Frequency_Out_of_Range_issues_in_Ubuntu") if you wouldn't mind ...

['Frequency Out of Range' fix for Ubuntu Dapper]("http://www.hotubuntunews.com/blog_03.shtml")

:cool:

---

### Post by carmi on 2006-11-21
I am trying to install Ubuntu 6.10 also and I don't know how to run a command before the install because i install Ubuntu before i get the "frequency out of range" error. how can i change the x settings prior to Ubuntu being installed? Possibly somewhere from the beginning of the installer.
Thanks, Evan

---

