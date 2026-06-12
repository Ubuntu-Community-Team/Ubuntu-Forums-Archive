---
title: "Cant install Ubuntu on XP Professional"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by kngopi on 2010-03-18
Hi,

I have a Windows xp professional sp 3 desktop. With two hard disks of 320 and 250 each. XP is sitting on C drive on 320 gb disk. I tried to install ubuntu from a CD. 
I tried installing it on 250 gb disk and failed. I kept getting an error that windows is corrupted and cannot find a .sys file..

I did not get the grub screen, but got an option given by windows asking to chose xp or ubuntu.. when i chose ubuntu and pressed enter I kept getting same error all the time. 

There must be something wrong with windows or some file in windows which is causing this error. 

Same problem with Linux mint too..

Plz help!

---

### Post by phillw on 2010-03-18
> **kngopi said:**
> Hi,

I have a Windows xp professional sp 3 desktop. With two hard disks of 320 and 250 each. XP is sitting on C drive on 320 gb disk. I tried to install ubuntu from a CD. 
I tried installing it on 250 gb disk and failed. I kept getting an error that windows is corrupted and cannot find a .sys file..

I did not get the grub screen, but got an option given by windows asking to chose xp or ubuntu.. when i chose ubuntu and pressed enter I kept getting same error all the time. 

There must be something wrong with windows or some file in windows which is causing this error. 

Same problem with Linux mint too..

Plz help!

Hi,

As the boot screen is still the windows MBR, offerring windows or ubuntu - I'm wondering have you selected the Wubi Install option, and not a full Ubuntu Install ?

But, before we progress to ubuntu, first ensure that Windows can boot itself.

Put Windows 'back in charge' of booting --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once windows is happily booting, you can add the ubuntu installation to the second drive.

Post back once you've Windows working on the 320 Gb drive.

Regards,

Phill.

---

### Post by kngopi on 2010-03-22
Hi phil,

Thanks for ur reply.


I checked what you had said.. yeah i had chosen wubi at first, where ubuntu works fine. But later i uninstall-ed from windows and tried a full installation.  After I uninstalled wubi ubuntu, i installed it in full installation mode, where everything went fine. I also got installation successful message...( full installation on 250 gb disk)..

After reboot I am getting the same options by windows and not by ubuntu..and here again.. when i choose ubuntu.. i get "windows is missing a hal.dll file" message...

Also, Windows is booting fine when i press windows option, problem is when i press ubuntu.

So what i am saying is, after uninstalling from windows, i install it in full installation mode. The installation is successful. But No grub screen at all.. hope you got what i said..

---

### Post by oldfred on 2010-03-22
Since you have two drives you need to keep them separate. Have windows on one drive with the windows boot loader in the MBR for that drive. If you select that drive to boot first in BIOS then windows boots. If it does not work now you need to run the repair. 

Another thread discussing repairing XP hal.dll error. 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)

You then set the Ubuntu drive first in BIOS and install grub to the MBR of that drive. It will find your windows  and let you boot both.

To see your exact configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by kngopi on 2011-04-25
Sorry for this, but I fixed this issue..

Had to set boot order of hard disks right.. 

I switched to Windows 7 , same thing worked for it.. I did what oldfred said.. 

Works fine now

Thanks guys :)

---

