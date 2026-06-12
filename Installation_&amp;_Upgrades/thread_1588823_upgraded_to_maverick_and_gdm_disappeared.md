---
title: "upgraded to maverick and gdm disappeared"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2010-10-05
I updated to development release of maverick.
Rebooted every thing worked fine for 24 hours.
Today after noon installed some more updates 
rebooted (had to) do not get a login screen of gdm to login.
ps -el does not shows gnome running.
Though I do see a black screen on which I can just login.
I tried startx :1
startx :-1,
/etc/init.d/gdm start
/etc/init.d/gdm restart
all these attempts went in vain.
What do I need to be able to get back the screen.

/var/log/Xorg.0.log can be seen here
[http://paste.ubuntu.com/506604/](http://paste.ubuntu.com/506604/)
and 
/var/log/gdm/
one of the logs is 
[http://paste.ubuntu.com/506602/](http://paste.ubuntu.com/506602/)

---

### Post by andrewthomas on 2010-10-06
This is not the xorg.log from a maverick boot.  The kernel and x server are probably from jaunty.
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux tapas-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
```
The other log is from maverick
try to boot into failsafe and disable desktop effects.

---

### Post by tapas_mishra on 2010-10-06
By the time your message came I had lost all my hopes hence I formatted the system and switched to an older version.
But do let me know if I face this situation in future then what should I be doing?
I have a hobby of booting latest unstable development release of Ubuntu on one of the partitions.For serious work I have a different partition where I do not mess up.
> **andrewthomas said:**
> 
try to boot into failsafe and disable desktop effects.
How is this done?

---

### Post by efflandt on 2010-10-06
You might want to consider a USB hard drive (or eSATA if you have that port) for testing new or unreleased distributions.  I am posting this from 10.10 beta updated to RC I think, booted from a USB hard drive (WD Passport).  Then if something does not work you can try to troubleshoot that before installing to your main hard drive.

I am glad I did that before installing 10.04 LTS on my old desktop PC because its motherboard did not like partions on new MB boundaries instead of cylinder boundaries (had to use partman/alignment=cylinder), and its legacy ATI X1300 video card did not like KMS (slow video and interferes with suspend/hibernate), so I had to use nomodeset or radeon.modeset=0 kernel boot parameter to fix that.

So far 10.10 works fine on my new PC, but I have not tested it much with my old PC except to make sure that it booted properly, because I am using nvidia drivers for the new PC.  The only issue I had with the new PC is that with flashplugin-installer, flashplayer.so segfaults on a 64-bit system crashing npviewer.bin in Firefox 3.6.10, but that apparently was not a big issue because I did not even notice that it was doing the same thing in Lucid until I checked /var/log/messages in that (maybe just broken flash ads).  Real 64-bit flash (10.2 r161) installed manually eliminates that issue on both 10.04 and 10.10.

What video card do you have?  What video driver are you running and was it from Ubuntu or some other source installed manually?  And what error do you get when you simply run **startx** from the console (without any switches, because **echo $DISPLAY** from a terminal in X usually returns **:0.0** )?

---

