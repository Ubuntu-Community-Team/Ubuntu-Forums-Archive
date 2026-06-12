---
title: "SUCCESS - Dapper Drake loaded on external USB drive! [taken from DaBruGo Breezy post]"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by hoops on 2006-07-31
This is the procedure I took for a brand new install of Dapper Drake based on the procedures from [DaBruGo's Breezy post]("http://www.ubuntuforums.org/showthread.php?t=80811").

**Disclaimer:** This way worked for me, but I'm a complete noob and this  was my first ever install of any flavor of Linux.

FYI, this was a clean install on a 30GB USB drive I didn't care about formatting/losing data on.  I screwed up the MBR (master boot record) using the method for Breezy and completly freaked out. Fixed it using one of the MBR tools [Partition Table Doctor] on Hiren's BootCD.

** It goes w/o saying, backup all your stuff first **

**( STEP 1 )** Download Ubuntu Dapper Drake 6.06 - Alternate Install CD. [Haven't tried it with the regular Desktop CD]  Burn the image. Restart your computer leaving the CD in.

**( STEP 2 )** Change the boot order in your BIOS to: CD, USB, Hard Drive. Press F2 or whatever your computer setup is.  Plug in your USB drive and save changes.  You're computer should restart.

**( STEP 3 )** Your computer should now boot the CD.  At the boot prompt select the first option to Run/Install Ubuntu [You may also want to come back here and try the safe graphics mode if these steps don't work].

**( STEP 4 )** You should now be at the Ubuntu desktop.  Click on the Install icon. 

*** CAREFULLY READ DaBruGo's post steps 2 and 3 ***

**( STEP 5 )** Follow the prompts and complete the information.  When at the Partition screen MAKE SURE TO SELECT SDA/SCSCI drive, NOT THE HDA (your hard drive on the computer).  I selected Erase the entire disk option. Proceed, it should now start to install everything.

**( STEP 6 )** When the Install has completed you will be prompted to either Continue or Restart.  Select Restart.

**** THIS IS WHERE THIS PROCEDURE IS DIFFERENT FROM DaBruGo's ****

***RESTART WITH CD EJECTED*** and leave your USB drive plugged in.

**( STEP 7 )** GRUB should have loaded.  Select the first (of three - others are rescue and memtest).

**SUCESS!** That was it.  I downloaded a ton of updates and had a wonderful day!

No code editing for me! :D 

Shant

ps. Big ups again to DraBruGo for his [original Breezy USB drive install post]("http://www.ubuntuforums.org/showthread.php?t=80811").

---

### Post by dschulz on 2006-07-31
excelent. I'll try asap! ;)

---

### Post by NamShubCMX on 2006-08-02
I want a "portable" ubuntu that I can use from different computers. Will it be possible to boot the correct drivers (hotplug?) everytime it is discovered? (for instance, load nvidia or ati when necessary, depending on which computer I'm using)

Also is it possible to boot the USB OS from, say, VMWare?

Thanks.

---

### Post by raintheory on 2006-08-03
Tried this method but it isn't working for me.

After following the installation instructions, when I reboot and set the BIOS to boot from "Removable Drive" the screen says "GRUB", but then just sits there with the flashing cursor and doesn't go anywhere..  

Any suggestions?

EDIT: Also, with the alternate install CD I don't see "Run/Install" (though I do see this with the Live CD)..  I only see "Install in Text Mode", "Install in OEM mode", "Install a Server"...  etc.

---

### Post by markcorbyn on 2006-09-28
I am having the exact same problem as raintheory above. I installed from the DVD iso.

Please help.

---

### Post by Oen386 on 2007-03-02
Same issue here. I see "GRUB _" where the _ blinks. 

I have tried this drive on other computers though, and it has worked well. So not sure why it doesn't work on some, but works on others.

---

### Post by Oligator on 2007-08-12
Hi, 

I am running in a problem related to this thread I believe.
I have installed Ubuntu 7.04 on a usb-drive plugged to my laptop without realizing that the Grub would be installed on my main hard drive containing XP. Now, I cannot start XP without having my usb-drive connected which is kind of annoying. :(
Is anyone who could help me to relocate the Grub on my usb-drive?
Being new to linux, a pretty detailed procedure would be a great help.

Thanks to anyone replying.

---

### Post by Oligator on 2007-08-12
ok, I think I can give more information.
I think my problem come from the bios... When my usb-drive with Ubuntu is not connected, I have the messages: Grub loading stage1.5
Grub loading, please wait
Error 21

This error is related to "21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.". This info comes from [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Well I am still stuck with my problem...

---

### Post by Oligator on 2007-08-12
I think I am getting more info.

I understand that the real problem is that the Grub is installed on the MBR of the internal hard drive. The only way to solve my problem would be to uninstall it from it and to put it on my usb drive...

Would anyone know how to do that?

Thanks

---

### Post by Keen101 on 2007-08-13
I would try to use a **super grub disk** to fix the MBR of the normal computer. Once you have fixed that, and it boot into windows or whatever again, then you can continue...........

[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

(I have never used one, but I hear they are easy to use)


You will need to re-install Ubuntu to the external HDD. This time unplug the internal HDD, so it will not interfere this time.  Then continue normally.  This time the internal drive will not be available for GRUB, so in theory it should then use the external by default.



...tell me if this works. I just bought an external HDD for myself, to use at school. I am hoping to have a potable Ubuntu system too.


-keen101

---

### Post by jim_p on 2007-08-13
One thing that... bugs me a bit

> ( STEP 4 ) You should now be at the Ubuntu desktop. Click on the Install icon.

How do you get to a desktop from the alternate install cd? :|
I think you confused the  installation methods and cds.

---

### Post by Keen101 on 2007-08-14
> **jim_p said:**
> One thing that... bugs me a bit



How do you get to a desktop from the alternate install cd? :|
I think you confused the  installation methods and cds.


hoops instructions seem to be for the Live-CD version. 

When using the alternate CD, there is no GUI interface. There is only text, and it does not go to the Gnome desktop. In my opinion if you want to install Ubuntu, then the alternate cd will do a faster job.

---

### Post by hikeb on 2007-09-25
> **NamShubCMX said:**
> I want a "portable" ubuntu that I can use from different computers. Will it be possible to boot the correct drivers (hotplug?) everytime it is discovered? (for instance, load nvidia or ati when necessary, depending on which computer I'm using)

Also is it possible to boot the USB OS from, say, VMWare?

Thanks.

Did you ever got an answer as to how to have a portable ubuntu?

---

