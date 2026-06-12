---
title: "Xubuntu and P II 400mhz Install Freeze"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by EMoShunz on 2006-10-03
I run an AMD-64, installed Ubuntu 64 bit 6.06 after talking to a friend and loved it! (He calls Edgy a Vista killer).
So, to make my daughters system run faster (currently XP for the USB wireless support) I figured Xubuntu was the way to go (she loves the little mouse logo btw).
Her system:
P II 400, 256 RAM, 6gb HDD (I know, but hey, it's paid for)
-I ran the standard disk, it would go through the boot screen, then just a flashing cursor in the top left and beep 4 times.
-Read some forums, said try the alternate.
-Ran the install with the alternate, worked great but couldn't install the boot loader.
-Read more forums, said I may have not used the MBR (not sure what that is, but from my mild geekyness I assumed I used the wrong partition thinking Master Boot Record)
-Ran the install again, ran without a hitch (may daughter squeeling in the background cause her system will run faster now), but when I reboot it would go through the boot screen, then just a flashing cursor in the top left and beep 4 times.

I'm stuck, please help.

---

### Post by klytu on 2006-10-03
> **EMoShunz said:**
> I run an AMD-64, installed Ubuntu 64 bit 6.06 after talking to a friend and loved it! (He calls Edgy a Vista killer).
So, to make my daughters system run faster (currently XP for the USB wireless support) I figured Xubuntu was the way to go (she loves the little mouse logo btw).
Her system:
P II 400, 256 RAM, 6gb HDD (I know, but hey, it's paid for)
-I ran the standard disk, it would go through the boot screen, then just a flashing cursor in the top left and beep 4 times.
-Read some forums, said try the alternate.
-Ran the install with the alternate, worked great but couldn't install the boot loader.
-Read more forums, said I may have not used the MBR (not sure what that is, but from my mild geekyness I assumed I used the wrong partition thinking Master Boot Record)
-Ran the install again, ran without a hitch (may daughter squeeling in the background cause her system will run faster now), but when I reboot it would go through the boot screen, then just a flashing cursor in the top left and beep 4 times.

I'm stuck, please help.

When you state "it would go through the boot screen", do you mean the BIOS boot screen? Does Ubuntu begin to load? If your answer is "yes" to the first question and "no" to the second, the four beeps you mentioned might be the BIOS warning you that it can't find a valid operating system to load. If you have successfully installed Ubuntu, I would suggest that you check your BIOS settings and make sure that it is set to boot from the drive on which you installed Ubuntu.

---

### Post by EMoShunz on 2006-10-03
It loads up the xubuntu logo, lists a bunch of things, checks them all OK (which my other system does) but where mine would then jump to the log in screen, the P II 400 does the flashing cursor and beep thing.

---

### Post by Jallu59 on 2006-10-03
Well

Your daughters computer is enough for Xubuntu. But have You been able to run Xubuntu as  a LiveCD system ?

I´ve run the Xubuntu Live CD on 450 MHZ/192MB/6MB laptop and I intend to install Xubuntu or Ubuntu on it instead of trojanpoisoned W2k. My parents-in-law have only 333MHz/256MB/10GB desktop computer and I have installed a full Ubuntu system with Gnome for them. At home I installed Ubuntu on a 4GB HD.

My guess is that the problem lies in display adapter configuration for X windowing system. You can try different setups for that display adapter by selecting F4 options in the Xubuntu boot menu. When you have found the operating configuration, you can try to install again, and give correct display parameters for it.

Yours
Jallu59

---

### Post by EMoShunz on 2006-10-04
I did not try the live CD prior to install on her system.
Please forgive my ignorence, but the boot you are talking about, do I press F4 during the POST screen, or the xubuntu screen where it does the checks?
Then, from there, is it like changing settings in a bios or like a windows environment.
I have been a windows guy for a long time (but I have always prefered apple, just couldn't afford one :P), so I know it quite well, but I am new to the wonderful world of linux.

Oh, side thing, I have a friend that says I say it wrong, is it linux like linen-ux, or linux like lie-nux...kind of like the old umaguma argument :)

---

### Post by peterwatson on 2006-10-04
I tried Xubuntu on my Sony Vaio with no luck, I could install it but I could not for the life in me get any network connection.

I have Ubuntu running with wireless on my mums PII 400 256 Mb ram so I tried Ubuntu on my sony after some added boot options I finaly got it working.

Maybe you could try Ubuntu instead.

---

### Post by EMoShunz on 2006-10-04
Thanks.
I can't find any info on exactly how much less resources xubuntu uses compared to ubuntu, do you notice a performance gain on your mom's pc vs win xp?
Also, did you use the regular, or alternate cd to install ubuntu.  I'll maybe try this video driver thing and then up to regular ubuntu if that doesn't work.
Still open to any other ideas if someone has them, as cheap as new systems are I still would rather not buy her a new one (or have to go back to xp on it!)

---

### Post by klytu on 2006-10-04
> **EMoShunz said:**
> Thanks.
I can't find any info on exactly how much less resources xubuntu uses compared to ubuntu, do you notice a performance gain on your mom's pc vs win xp?
Also, did you use the regular, or alternate cd to install ubuntu.  I'll maybe try this video driver thing and then up to regular ubuntu if that doesn't work.
Still open to any other ideas if someone has them, as cheap as new systems are I still would rather not buy her a new one (or have to go back to xp on it!)

For what it's worth, I use a 400Mhz Pentium II with 320MB RAM and a cheap Radeon 7000 64MB graphics card and I have no problems running either Ubuntu or Kubuntu. I also ran both Kubuntu and Ubuntu on the same system with an even older ATI 8MB graphics card for a while - again with no particular difficulty. Installed both from the alternate install CDs. Never tried Xubuntu.

Does your Mom's computer have a discrete graphics card or is the video built into her motherboard? If the video is sharing that 256MB of RAM on her computer, that might cause some problems with performance on Ubuntu/Kubuntu. Otherwise, Ubuntu or Kubuntu might work fine on her computer. If she doesn't have a discrete graphics card, they are fairly cheap - I got the Radeon 7000 64MB card for about $15 in the U.S. - and if you can find one for her that is compatible with Ubuntu/Linux that may solve the issues you are having.

---

### Post by EMoShunz on 2006-10-04
It is on-board video, i suppose I will have to try that if the other stuff doesn't work.  I just hate to spend money on tis machine.  I saw a sale on used systems here, $100 for a P4 1.2ghz, maybe I'll buy it on condition of successful OS install, but again...money, hence the love of a wonderful free OS like Ubuntu!

---

### Post by peterwatson on 2006-10-04
Hi

I have noticed a great improvement on my mums laptop since changing it to Ubuntu from XP, the wireless is also far faster.

The laptop is an old Dell PII 400 256mb Ram 10Gb HD, on board ATI graphics.

I installed from the Live CD. 

Maybe you could be in need of some kernel cheat codes, for example to get my sony vaio to work I had to use acpi=off.

there is a nice list of acpi codes to try here -> [http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)

---

### Post by EMoShunz on 2006-10-04
Thanks.
My 64-bit system works great, it's my PII 400 that I can't even get to install.  I will try all the suggestions people give me tonight, make my daughter happy again (well, as happy as a vegitarian can be :P ).
Thank you all for the help, keep suggestions coming.

---

### Post by dannyboy79 on 2006-10-04
use the alternate install cd. it has brought my old pentium mmx 266mhz w/ 128mb ram back to life!!!! but i did have to use the alt cd. to do the install. it's all text based instead of graphic installer.

---

### Post by K.Mandla on 2006-10-04
A flashing cursor in the upper left part of the screen is sometimes a video issue. Usually that video will snap back to the terminal screen, but I imagine if it's sufficiently confused it might just sit there for eternity. ...

Try pressing ALT+F1 to get to a terminal screen, and see if there's anything you can tinker with in the /etc/X11/xorg.conf file. Try changing the video driver to 'vesa' and see if you can get X to start. 

Anyway, an idea. ... :)

---

### Post by louieb on 2006-10-05
I am writing this on a PII 400 running Ubuntu. If you can get to the grub screen boot into recovery mode. This will place you at the command prompt as the root user. at this point you want to enter ```
 dpkg-reconfigure xserver-xorg 
```.
Go through the setup process using the defaults this may fix it. Reboot to find out. 
If not then try to reconfigure it again. Only this time when it gets to the point where it asks if you want to use some of the main memory for video do it. I have a 4 meg pci video card. What I did to get x to work was tell it to 2048 kb of main memory. Maybe this will work for you.

---

