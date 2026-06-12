---
title: "Linux Magazine DVD Install"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by Ashejoe on 2005-05-08
I too had read some encouraging things about Ubuntu in the newly released TUX Emagazine.  (Which is pretty good and "free")  Any how, when I seen the April 2005 issue  of Linux Magazine had a DVD containing the full release of Ubuntu 5.04, I decided to buy it and give Ubuntu a try on my PIII-733 with 256-MB and a brand new never used 60-GB Maxtor hard disk.

Well, after about an hour, it seemed to install / go to the web and update itself / etc.  But, when I tried to boot up all it would allow me to get to was what I think is called the "shell".  (you know the screen that looks reminicent of the old DOS alpha-numeric screens circa 1982.)  It never would give me either a KDE or Gnome desktop. 

How do I get it to boot into either the KDE or Gnome desktop ?

Thank You

Joe Ashe

---

### Post by Staesys on 2005-05-08
wierd that it's not going to the GUI first thing.

have you tried **startx** at the command line?

---

### Post by tonym on 2005-05-08
Try entering aptitude.  Search for package ubuntu-desktop and see if it is installed.  If not try installing it and see what happens.

---

### Post by strawberry on 2005-05-08
Other way:
sudo apt-get install gnome-desktop
It will install the desktop or tell you that it has installed already.
Let us know the result.

---

### Post by Ashejoe on 2005-05-08
Thanks all for attempting to help me get Ubuntu to load up with Gnome desktop instead of in terminal mode.  Frustratingly, none of the suggestions helped.  (sorry)

When I tried "STARTX", the system reported back "command not found"

When I tried "APTITUDE" it called something up on the screen, but wouldn't work without the ROOT password.  When I put in the ROOT password, it refused to accept it even though I was using all lower case letters.

When I tried "SUDO APT-GET INSTALL GNOME-DESKTOP" it acted like it was trying to load something, but then came right back to terminal mode.

So, in total frustration, I reformated the drive in ext3 and tried to reload Ubuntu.  Like the first attempt, I know the Full Distribution DVD loaded a ton of stuff onto my hard drive.  It gave every indication of being set to go just like on the first attempt.  But this time.... it went to a totally blank screen and stayed there !

So, at this point, I don't have a clue.  I know this Dell system can run Linux.  It has no problems loaded up Knoppix 3.8.1 or Mepis 3.3 (which is what I'm using to get on the net and enter this call for help.)

Thanks Again

Joe

---

### Post by strawberry on 2005-05-08
[QUOTE=Ashejoe]Thanks all for attempting to help me get Ubuntu to load up with Gnome desktop instead of in terminal mode.  Frustratingly, none of the suggestions helped.  (sorry)

When I tried "STARTX", the system reported back "command not found"

When I tried "APTITUDE" it called something up on the screen, but wouldn't work without the ROOT password.  When I put in the ROOT password, it refused to accept it even though I was using all lower case letters.

When I tried "SUDO APT-GET INSTALL GNOME-DESKTOP" it acted like it was trying to load something, but then came right back to terminal mode.

So, in total frustration, I reformated the drive in ext3 and tried to reload Ubuntu.  Like the first attempt, I know the Full Distribution DVD loaded a ton of stuff onto my hard drive.  It gave every indication of being set to go just like on the first attempt.  But this time.... it went to a totally blank screen and stayed there !

So, at this point, I don't have a clue.  I know this Dell system can run Linux.  It has no problems loaded up Knoppix 3.8.1 or Mepis 3.3 (which is what I'm using to get on the net and enter this call for help.)

Thanks Again

Joe[/QUOTE]

I understand an unsuccessful install can be so frustrating. I'm sorry. 
If you find and copy here the /home/<login_name>/xsession.errors file, maybe someone from the forum could help you.

---

### Post by Martin Witte on 2005-05-08
Is it maybe recognition of the video hardware? Try 'sudo dpkg-reconfigure xserver-xorg
' and choose 'vesa' as video driver, this one seems to work with most video cards.

---

### Post by Ashejoe on 2005-05-08
Yea, it could very well be a video problem.  The last time I took a look at Linux was back in the days of Redhat 6.  I know then I had major problems getting it to recognize my ATI card.  My latest computer also sports an ATI card, (Radon 9200) so, it's possible that may be it.  Intrestingly, I also tried to install Mandrake 10 and SuSe 8.0 this weekend, and had video problems with those 2 distros as well.  (Yet Knoppix and Mepis run fine.  I guess like you mentioned, they're running the VESA driver ??)

Let me pass another possibility by you.  Before I started playing around with Ubuntu, I pulled my 160GB drive out of my computer and installed a 60GB Maxtor I got on sale at Staple (brand new) for $45.00  I have the jumper set to "CABLE SELECT".  The 60GB Maxtor is the only hard drive currently installed.  Could that be causing problems with booting ?  (It loaded the program files just fine.)

Joe

---

### Post by Ashejoe on 2005-05-08
Well some good new / some bad news.....

Using the advice I received from you guys, I was able to get Linux up and running complete with the KDE Desktop.  But not in Ubuntu... In Mandrake 10 !

You were right, switching to VESA mode solved the problem.  Furthermore, in looking at other posts on this forum it appears my hunch that ATI Video Cards are not Linux friendly was confirmed ! 

Any how, I tried (for the third time) to install Ubuntu 5.0.4 from a freshly formatted / non-partitioned hard disk, but, at no point did I see anything that allowed me to change the graphics to VESA ??  I can't do it from console mode, because my system never comes up to console mode.  Just a blank screen !!

UUUuuuurrrrrrggggggggggg  I was really hoping to give Ubuntu a try this weekend.  But after well over 15 hours of fooling around, I guess it's not going to happen.  Maybe next weekend.

Thanks again everyone for you kind and patient assistance.

Joe

---

### Post by BAshworth on 2005-05-08
Too bad about your experience.  Hopefully it isn't something to do with the copy of Ubuntu that they are giving out being damaged in some way.

As an FYI, I am using an ATI 9200 myself, and have had no issues at all with it.  Even got 3D hardware acceleration to work.

You never know though, what a particular mix of hardware and BIOS settings could do.

---

### Post by jodef on 2005-05-08
> Too bad about your experience. Hopefully it isn't something to do with the copy of Ubuntu that they are giving out being damaged in some way. Could well be I have found that most times you have erratic errors that repeat on a reinstall that's the primary cause.

---

### Post by Martin Witte on 2005-05-09
The default driver for xserver is kept in file /etc/X11/xorg.conf, there is a section like below, your system probably has set this to your ATI card. If you have a multi-boot system you can mount the Ubuntu partition, if you have one OS installed you could boot your system with a live cd (Ubuntu has one, I have good experiences with the Knoppix one, also this one [http://www.sysresccd.org/](http://www.sysresccd.org/) is very helpful) then mount your drive and edit the file.

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

---

