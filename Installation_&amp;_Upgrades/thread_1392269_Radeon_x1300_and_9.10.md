---
title: "Radeon x1300 and 9.10"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by espmartin on 2010-01-27
Hello All,

Just wondering if peeps have successfully installed/upgraded 9.04 to 9.10 - having the Radeon x1300 video card?

---

### Post by espmartin on 2010-02-03
Bump(ity-bump)

---

### Post by Mark Phelps on 2010-02-03
Sorry no one got back to you earlier but while 9.10 WILL work with your card, it will use the default open source drivers.  There are no ATI drivers available for your card that will work with 9.10.  So, as long as you're not running 3D games that need hardware accelerated video, you should be fine.

---

### Post by espmartin on 2010-02-03
Thanks Mark. I did run 9.10 - but the response was DEAD SLOW. I initially did an upgrade, but system response was DEAD SLOW. So I backed up my /home, and did a format/install. Same deal ;-/

---

### Post by Rrogers on 2010-02-06
I am running 9.10 with
lspci ...
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)

Dual monitor x86_64.   What Mark said is still true (3d etc..), but I get very good performance; after doctoring up xorg.conf.  I will send my copy if you want.  It's simple because I prefer to have the X11 programs do most of the work.
A problem is the level of kernel modules.  The operation comes and goes with the version level.  For unknown reasons 2.6.31-19 didn't even get to the grub menu; whereas -18 does.  Some of the earlier kernels would almost get to login and go away; others worked fine.
I probably should work harder on the analysis but I reported this earlier and have seen no response.
If you want I can test the booting with any of the recent kernels.
Ray

---

### Post by espmartin on 2010-02-06
Yes, please send your xorg.conf. I was able to "get things working" - but wwwaaaaaaaaaayyyyyyy ssssssllllllooooooooowwwwwwww lol

---

### Post by Mark Phelps on 2010-02-08
Using open source drivers should not cause your overall Ubuntu performance to be slow.  I've had to restort to the same drivers with Ubuntu 9.10 because I have one of the "legacy" cards, too.

If your overall performance is really s..l..o..w, there is some other problem at work other than the open source drivers.

---

### Post by Rrogers on 2010-02-09
Here is the xorg.conf.
[http://docs.google.com/leaf?id=0Bzqv7EjKjtaCNmUyN2Y3M2QtODg2OC00NDYyLWFkNDgtZDYxMTNkODkxYWQy&hl=en](http://docs.google.com/leaf?id=0Bzqv7EjKjtaCNmUyN2Y3M2QtODg2OC00NDYyLWFkNDgtZDYxMTNkODkxYWQy&hl=en)

To repeat: doesn't work with 2.6.31-19 generic (and some earlier ones) 
To correct my earlier post; it does get through grub2 and the ubuntu icon but then the monitors turn off.  I suppose I could run -19 and then reboot with the DVD to send a bug report with whatever is in the log files.
2.6.31-18 generic  does work.
The real reason for the custom xorg was 
1)The default hardware cursor was trashed; BTW the exact form I have is necessary.  The xorg instructions have some misleading statements.
2) The dual monitors 
The commented out statements are suggestions I picked up on the internet that didn't help; and some even caused a failure.
lspci
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)


Ray

---

### Post by Rrogers on 2010-02-09
BTW: the propitiatory drivers don't seem to work and if you try them you have to go through a special procedure (by hand) to purge them; believe me, I have had to do it twice.  If you need the procedure I will look it up.  It's on the ubuntu (or debian) site somewhere.
Ray

---

### Post by espmartin on 2010-02-09
Thanks Rrogers. I'll check out your xorg and .... MAYBE try this. I'm running 9.04 with Compiz and LOVE it. So maybe I'll just stay here until 3d is supported - OR when I buy a video card that IS supported. Any advice on a card?

---

### Post by efflandt on 2010-02-09
What cpu do you have. I have a 512 MB X1300 running a 32" 1080p HDTV on DVI to HDMI with 64-bit Ubuntu 9.10 using standard modules on an early Athlon64 3200+ from 2004.  I have no xorg.conf and desktop effects are set to None.

01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)

My cpu lacks the lahf_lm instruction so I had to use flashplugin-lahf-fix to use 64-bit flash.  But Hulu changed something that broke 64-bit flash in a browser, and Hulu desktop that may still work with 64-bit flash does not see flashplugin-lahf-fix, so I fell back to flashplugin-installer (32-bit flash with nswrapper).  If I knock my resolution down 1280x720 Hulu is playable full screen with some dropped frames.  A flash test I tried was 17-18 fps.

Even in Windows the X1300 has passed on to a legacy group of ATI cards.  For some reason in WinXP displayed 1080p underscanned roughly 1" black boarders, but the most recent Catalyst app had an adjustment for that to fill the screen.  X in Ubuntu used full screen at full 1080p resolution automatically (DVI to HDMI).

I thought maybe my 2 year newer 1.66 GHz dual core laptop was faster (Intel integrated video), but apparently not by much.  It averages 19 fps in the flash test.

---

### Post by Rrogers on 2010-02-10
I have no suggestions but...
I found:
**Ubuntu 9.10/Karmic**

 Cards in Group 1 have accelerated 2D/3D/Xv. Cards in Group 2 have accelerated 2D/Xv support. 3D acceleration for Group2 cards can be enable by installing a recent kernel >= 2.6.32 and using packages from the xorg-edgers PPA (see that section). 

On page: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

I will probably try this, but not till the end of Feburary 
2.6.32  Installation: [http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

OTOH: If I wait long enough maybe these changes will appear in the regular updates notification.

Ray

---

### Post by espmartin on 2010-02-10
Wow, thanks Ray! That link makes me trigger-finger happy and ALMOST ready to move to 9.10

---

### Post by Scott L on 2010-07-11
It appears that certain ATI cards will have problems.

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers)

Look under "Installing Drivers Manually".

To put it simply, AMD has moved several cards into "legacy" status which means that the 9.3 version of the driver is the last to support them apparently.

Unfortunately, the 9.3 driver doesn't support xorg-xserver-1.6.

I'm running Lucid and Maverick (development), and as I understand it, I will not be able to use the ATI drivers for my ATI X1300 because the xserver is 1.7.6.

Really unfortunate because Blender now moves at the speed of smell without the ATI driver.

---

### Post by espmartin on 2010-07-11
So basically, is it the consensus that in order to move to Ubuntu 10.x and have a really great response as far as video goes, I need to throw out my Radeon x1300 and buy something else?

---

### Post by Scott L on 2010-07-27
I had remembered using Blender before and have the screen not take five or six seconds for a menu to pull down.  So I tested this by installing Jaunty (i think it was) on a second hard drive to see how the video worked with Blender and besides seeming to bork my grub the video drivers worked.

But I think if you check, Juanty had an older x.org that allowed the ati driver to be installed.

So I think the answer is yes.

---

