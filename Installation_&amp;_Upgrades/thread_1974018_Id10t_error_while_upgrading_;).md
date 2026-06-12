---
title: "Id10t error while upgrading ;)"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by baconmaker on 2012-05-05
My mom (who is 81) crashed her computer while upgrading to 12.04.
Now when I start her computer I get to grub I can see Ubuntu, Ubuntu recovery and Windows.  Windows boots fine. Ubuntu does nothing but a black screen with a flashing cursor.  Prior versions tell me I need to load a kernel first.  I can get to the screen to edit commands and I can get a command prompt.  I tried sudo apt-get dist-upgrade -f to see if I could finish the upgrade and it tells me it does not recognize the sudo command.  Any suggestions on how to recover her OS would be greatly appreciated.

If more details are needed please let me know and I will try to provide them.  Thanks

---

### Post by dino99 on 2012-05-05
boot on recovery mode, then select repair (second line), and finally select the first line to finish

---

### Post by oldfred on 2012-05-05
What video card? often that is an issue.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

nVidia also released a version that does not work with some older nVidia cards - . I think they just released a fix to that, and Ubuntu should be adding it soon.

NVIDIA 295.49 Fixes Linux Performance Regression
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ)
Fixing the performance regression of the 295.40 driver that affected GeForce 6 and GeForce 7 series hardware. 

Warning for nVidia GeForce 6, 7, and 8800 cards with 12.04 Precise
[http://ubuntuforums.org/showthread.php?t=1969754](http://ubuntuforums.org/showthread.php?t=1969754)
serious issue with the GeForce 6, 7, and 8800 GTS/GTX cards, K/Ubuntu 12.04, and their latest 295.40 driver.

---

### Post by baconmaker on 2012-05-05
> **dino99 said:**
> boot on recovery mode, then select repair (second line), and finally select the first line to finish
This is what I see at the grub screen
  Ubuntu, with Linux 2.6.38-12-generic
The results when I enter the above line
  Black screen with flashing cursor.  After about a 20 second pause this comes up  init: unreadahead main process (274) terminated with status 5

If I try recovery mode I get this
  loading initial ramdisk
it then scrolls a lot of stuff past and ends with a flashing cursor

If I go down to previous version and use the top one which is
   Ubuntu, with Linux 2.6.38-11-generic
I get this result
   error: file not found
   error: you need to load the kernel first
If I used recovery mode for 2.6.38-11-generic is get
   loading initial ramdisk
   error: you need to load kernel first

---

### Post by baconmaker on 2012-05-05
> **oldfred said:**
> What video card? often that is an issue.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

nVidia also released a version that does not work with some older nVidia cards - . I think they just released a fix to that, and Ubuntu should be adding it soon.

NVIDIA 295.49 Fixes Linux Performance Regression
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ)
Fixing the performance regression of the 295.40 driver that affected GeForce 6 and GeForce 7 series hardware. 

Warning for nVidia GeForce 6, 7, and 8800 cards with 12.04 Precise
[http://ubuntuforums.org/showthread.php?t=1969754](http://ubuntuforums.org/showthread.php?t=1969754)
serious issue with the GeForce 6, 7, and 8800 GTS/GTX cards, K/Ubuntu 12.04, and their latest 295.40 driver.
The video card is a NVidia GEForce 8400 GS

---

### Post by oldfred on 2012-05-05
I do not know if bug applies to your or not.

I have a 9600GT and it works, but after install I have to do this:

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by baconmaker on 2012-05-05
Deleting quiet and splash with nomodeset gave 5 different lines of commands and then stopped with a flashing cursor

---

### Post by baconmaker on 2012-05-05
For what it is worth the grub version is
   1.99~rc1-13ubuntu3

---

### Post by oldfred on 2012-05-05
You should be getting many lines, several screens full should scroll by as it loads everything. 

You may need other boot options in addition to nomodeset.

What are PC's model & specs?
What version was she upgrading from?

If you get to grub menu, then grub is done and you are booting Ubuntu and it is issues with loading modules or drivers.

Is grub showing. that is from 11.04?
Ubuntu, with Linux 2.6.38-12-generic

you should be seeing version 3.2 if you have upgraded. Or upgrade never completed.

You may be able to chroot into system and run updates.

---

### Post by tschill on 2012-05-05
Not that I can add anything valuable. But want to send out some greetings to your mother. I like it, that she tried linux at her age. ):P

---

### Post by baconmaker on 2012-05-05
Thanks, With Ubuntu I do not need to spend near as much time keeping things up to date and secure.

---

### Post by baconmaker on 2012-05-05
> **oldfred said:**
> You should be getting many lines, several screens full should scroll by as it loads everything. 

You may need other boot options in addition to nomodeset.

What are PC's model & specs?
What version was she upgrading from?

If you get to grub menu, then grub is done and you are booting Ubuntu and it is issues with loading modules or drivers.

Is grub showing. that is from 11.04?
Ubuntu, with Linux 2.6.38-12-generic

you should be seeing version 3.2 if you have upgraded. Or upgrade never completed.

You may be able to chroot into system and run updates.
It is a Systmax which is pretty close to the same as mine (I am 40 miles away at my place now). My specs are 2gb memory, AMD Athlon processor (not sure of the speed) Nvidia graphics 32 bit. She was upgrading from 11.10. I am seeing Ubuntu, with Linux 2.6.38-12-generic.  I believe upgrade never completed.  I was not there to see what happened, but tried to coach her on the phone to do an update (I am the administrator).  I think what she did was enter my password and clicked on upgrade rather than update, then got impatient because it was taking so long and pressed the restart button on the computer. Hence, I think she crashed an upgrade somewhere in process.

---

### Post by oldfred on 2012-05-05
You may be able to chroot into the install and run it again or finish. If crashed you may have to use liveCD or USB to run e2fsck to make sure it is ok. 

Otherwise it is use liveCD to backup whatever you have not backed up if possible and install from scratch.

See post #5 for similar chroot & try to update.
[http://ubuntuforums.org/showthread.php?t=1973868](http://ubuntuforums.org/showthread.php?t=1973868)

---

### Post by baconmaker on 2012-05-12
I finally was able to get a new 12.04 cd and was able to load live cd.  Then backup the things I needed.  Finished the upgrade.  Everything seemed fine and on restart I found I had lost my ability to boot into windoze.  After some looking I stumbled upon Boot-Repair at

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Ran the two sudo commands in terminal, clicked on Recommended repair and all is well again.  

Thank you all for the help and suggestions.

---

