---
title: "2-6-20-16 kernel upgrade &amp; Xorg fail -- How to get back"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Shinobi326 on 2007-05-30
I've been a new Ubuntu user since Feisty came out.  When I logged in the other day it wanted to upgrade a boat load of things including the kernel and I clicked ok.  Well after reboot, as others have described neither my .15 or my .16 in my grub menu will NOT boot fully into Xserver.  I've been into the recovery mode for both, tried to recompile the Nvidia drivers using the v9755 of the drivers and that seems to work.

However, when I reboot the regular options for .16 and .15 still do not work.  I again can go into recovery mode and manually startx and things appear to be ok but why can't I get the regular (not the recovery modes) grub kernel menu options to work?

I just started to get things humming along quite nicely and it appears we all got hit with something with the kernel upgrade.  Is this a normal thing to expect when using Linux and/or Ubuntu distro?  I have loved my experience with Ubuntu thus far and I normally have patience to troubleshoot many things but this particular thing is one of the fastest ways to turn off new Ubuntu users.  What about all of the new Dell folks buying Ubuntu machines, they turn them off, get a message to upgrade, they click and their machine doesn't boot... nice.

Anyway, can someone help me try to get my regular menus to work.  How do I get a working Xorg.conf settings to take for those menu options?  I don't remember it being this hard to get this working on original setup.  What am I missing?

---

### Post by gmc on 2007-05-30
Hi,  You might want to update/re-install your nvidia drivers. Sounds like the .16 kernel can't find them for whatever reason, and the update some how broke .15 from finding them too. Just a thought...  Gord

---

### Post by awaldram on 2007-05-30
> **Shinobi326 said:**
> 

I just started to get things humming along quite nicely and it appears we all got hit with something with the kernel upgrade.  Is this a normal thing to expect when using Linux and/or Ubuntu distro?  I have loved my experience with Ubuntu thus far and I normally have patience to troubleshoot many things but this particular thing is one of the fastest ways to turn off new Ubuntu users.  What about all of the new Dell folks buying Ubuntu machines, they turn them off, get a message to upgrade, they click and their machine doesn't boot... nice.



Ubuntu seems more prone than most to issuing updates that break production releases, which I think if I'm counting straight is 3 breaks in 2 years.

I've been running Debian constantly for 11 Years in thats time the system has only ever been down for upgrades.

On Debian testing I know of one major break since its inception during the x upheaval but as this is a Beta release thats pretty good

Sid breaks fairly regularly but as thats debian development core that too is OK. 

I think Ubuntu have been caught by their own dreams , they want to get to the stage where it doesn't matter if your using ide or Scsi, Drives have their unique Id and so will never break, Unfortunately they are not there yet and it appears a flaw has switched a lot of people from libata (ata_piix) back to native ide which has renamed all drives from /dev/sdxx to /dev/hdxx with knock on consequences throughout the OS.

---

### Post by travsraven on 2007-05-30
GMC has hit on the very problem I have everytime I do a kernel update, it's ALWAYS the nvidia driver that's the problem for me. It just cannot find it's way to where the driver files are etc etc.

Since I have been using Edgy I have everytime had problems when the kernel upgrade is introduced especially with my graphics card. Like everyone else I come in here to try and find the fix for it. The fixes people give out seem to be a hit and miss for me, I don't know why plus truthfully I really don't have the time as off late to faffle around and figure it out. 

I found a sure fire way for me that works everytime. ( By the way I don't know if this works for ATI drivers - I just know it works for my NVIDIA

1) When you get a kernel upgrade - continue installing it and then click on reboot. If you get Xorg file error 

2) Reboot then hit escape and it will take you to the options of choosing which kernel you want to boot into.

3) Click on your previous kernel which was working ok - so in this case it be 2-6-20-15

4) Once you have loaded up - click on applications - click on ENVY ( providing you have it installed and click on automatical uninstal Nvidia driver.

5) Once uninstalled - reboot totally - then let it boot up normally. In this case as the graphics driver file is totally removed - you should be able to load up properly with the newly updated kernel.

6) Once logged in - Click on applications - click on Envy and either install automatically or manually install your driver. This will take a few minutes to recongfigure.

7) At the end it will ask you something like whether you wish to accept the newly updated configurations - click yes - and it will ask again the same thing and click yes again.

8) Totally reboot and then you should be able to boot up normally with no errors on your new kernel...

( IF you haven't got envy installed - i am not sure if you can install it then use that to remove the driver - I am sure someone will pipe up ) 

To the purists out there - like I said - I just haven't the time as off late to play about and figure out why the fixes given out in forums is a hit and miss with me. I will learn - that is my intention but for now this fix does the trick for me without pulling my hair out. 

Hope this helps

---

### Post by Shinobi326 on 2007-05-30
Thanks guys!  I hope to try that step-by-step there later tonight.

Since the Kernel update also appended my Grub file with 2 new entries, the default used to be WinXP so my wife can just turn on the PC and go into Windows but now it's Memtest so she keeps telling me "I hate this computer because it's broken".  So I obviously need to fix my Grub file but I need to fix my darn video driver hell first...grrrrr!

---

### Post by stchman on 2007-05-30
> **Shinobi326 said:**
> I've been a new Ubuntu user since Feisty came out.  When I logged in the other day it wanted to upgrade a boat load of things including the kernel and I clicked ok.  Well after reboot, as others have described neither my .15 or my .16 in my grub menu will NOT boot fully into Xserver.  I've been into the recovery mode for both, tried to recompile the Nvidia drivers using the v9755 of the drivers and that seems to work.

However, when I reboot the regular options for .16 and .15 still do not work.  I again can go into recovery mode and manually startx and things appear to be ok but why can't I get the regular (not the recovery modes) grub kernel menu options to work?

I just started to get things humming along quite nicely and it appears we all got hit with something with the kernel upgrade.  Is this a normal thing to expect when using Linux and/or Ubuntu distro?  I have loved my experience with Ubuntu thus far and I normally have patience to troubleshoot many things but this particular thing is one of the fastest ways to turn off new Ubuntu users.  What about all of the new Dell folks buying Ubuntu machines, they turn them off, get a message to upgrade, they click and their machine doesn't boot... nice.

Anyway, can someone help me try to get my regular menus to work.  How do I get a working Xorg.conf settings to take for those menu options?  I don't remember it being this hard to get this working on original setup.  What am I missing?

The simplest solution is to forget compiling the drivers.  You can use the Restricted nvidia drivers in Feisty to enable 3D acceleration of your video card.  I did that on both my ATI and Nvidia equipped PCs and when the kernel was upgraded from -15 to -16.

At first I did not think that I was going to like Feisty as a lot of people were having problems with it.  I have (4) computers running Feisty and they all run excellent.

---

### Post by disrupta on 2007-07-04
had the exact same problem

ENVY works and is an excellent fix. so thanks for that. 

as for the new kernel and updates messing up the grub menu. that is still a major problem for me at moment. why does it have to delete entries that are already existing and working perfectly. 

unfortunately fixing that has turned into something more complicated than fixing the menu.lst file. it seems the boot menu is no longer the existing menu.lst file that was in the grub directory and i was editing before.that menu is showing no changes. mayb they have made a new file in some new location i cant find yet. or its called something different.

in future after all this i'm not upgrading my kernel anymore. especially on my main everyday working pc. 
ENVY is fantastic. tho i must say i didn't find it that difficult installing the nvidia driver's in the first place manually. 

this whole thread was really important to me to read, as i didn't know it was the nvidia driver's in the first place that needed fixing. but i can confirm that that is indeed the reason it doesn't boot in the grub menu. and this ENVY fixes that nice and easily. thankyou !

---

### Post by Shinobi326 on 2007-07-06
Those are all good suggestions if you have NVidia video cards that will work with either [COLOR="Red"]restricted drivers[/COLOR] or [COLOR="Red"]Envy[/COLOR].  The 8800 series are notorious for being non-compliant with both options and I have no other way to get the Nvidia drivers working except for manually compiling them.

Since I can't see myself having any other video cards for quite sometime I guess I'm stuck with my dual 8800GTS and the finicky problems. :(

---

