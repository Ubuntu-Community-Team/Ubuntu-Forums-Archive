---
title: "Custom installer (live cd)"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by alienprdkt on 2010-11-04
Will try to explain best what I would like to accomplish.

I have already setup a working configuration of how I would like to replicate my custom builds. These include a LAMP setup with already installed and running webapps. 

What I would like is something similar to google's Chromium OS. I like the idea of being able to access everything from the browser. I already have custom icons for the terminal and the power options, and have a set default home page. Can I get help here to lock this home page (so others cant change it) or will I need to go to google forums for that?

What I need help with is making the Chromium Browser unable to close, and auto start upon login. Also stipping the desktop of everything else. Only need it to run the Chromium Browser.

And also is there a way to make my current hard drive into a live cd, since I have everything the way I want it setup on my hard drive now?

I realize that this may not be possible, is it then possible to customize the server install iso?
[I]To have it copy my web apps and other configuration files to the drive after it runs through the install process.
Then to have it install the gui + chrome[/I], and finally remove all the apps and menus but chrome? 

I realize that one person may not have an answer for all of my questions. Any help with any of this is greatly appreciated.
Thanks in advance,

---

### Post by P4man on 2010-11-04
remastersys is the answer to all your questions. Note that maverick isnt officially supported yet, but from user reports it appears to work okay.

---

### Post by alienprdkt on 2010-11-05
> **P4man said:**
> remastersys is the answer to all your questions. Note that maverick isnt officially supported yet, but from user reports it appears to work okay.

Thanks I have found this... 
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.htmlcd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.htmlcd-with-remastersys.html")

will try it out over the weekend.

---

### Post by VraiChevalier on 2010-11-05
> **P4man said:**
> remastersys is the answer to all your questions. Note that maverick isnt officially supported yet, but from user reports it appears to work okay.

I just used remastersys an hour ago to make an .iso image of my Ubuntu 10.10 install and then used Startup Disk Creator to make a bootable usb from the image and it worked like a charm. Remastersys worked great with my Ubuntu install on an Acer Aspire One netbook.

---

