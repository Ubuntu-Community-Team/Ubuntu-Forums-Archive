---
title: "Can  I  install Ubuntu on newish Windows 8 computer?"
date: 2014-12-05
forum: Installation &amp; Upgrades
---

### Post by peterinmalaga on 2014-12-05
I have had my computer for 5 months. It has Windows 8.1 installed and I have come to hate it to the point where I would probably throw the computer away rather than continue with Windows 8. I have discovered that it is by no means  easy to install Ubuntu on a computer with Windows 8 and might even be impossible. Needless to say, I would like to totally replace Windows 8. I would be really grateful for any help. I have installed Ubuntu on several computers in the past but would not describe myself as particularly tech savvy. I apologise if this question has been asked before (I imagine it has) but I was unable to find it on the forum with a search.

---

### Post by felix16 on 2014-12-05
Is it really impossible? I wasnt aware i just "did it" on my brothers computer and it worked. If i were you id check all of your hardware and stuff like your graphics card, and network card and stuff and do some snooping to make sure that theres Linux drivers available for it (Most Likely). What i do suggest is get a USB/CD and run a live image. That way you can see the compatability, and you can toy around with it. Its what i did! :p

---

### Post by oldfred on 2014-12-05
What brand/model computer & what video chip.
Some 32 bit UEFI low cost systems may not work or do not fully work well.

Many links on UEFI install, examples and details in link in my signature below.

Most important link:
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Best to start with dual booting. Some find one application or game they cannot live without and want to reinstall Windows. If you have erased system, you have to purchase a new copy as only the OEM or vendor's version will work with the product key in the UEFI.
And you should make a full image of Windows. If you later want to sell system, it probably need Windows.

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And if dual booting, you may need to repair Windows, you can make this for free, but if you have to download it, it will cost $20 to $40 depending on version ( a real rip-off in my opinion):
      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Mark Phelps on 2014-12-05
>  It has Windows 8.1 installed and I have come to hate itIf it's not Windows8 you hate but instead, the "tiles" interface, then you should check out Classic Shell.  This is free and returns the Start Menu to Windows 8 so you can use it just like the older versions of Windows.  Not saying you shouldn't use Ubuntu, but this could make your experience on Win8.1 more bearable.

---

### Post by peterinmalaga on 2014-12-06
Thanks, Felix, I shall do all that.

---

### Post by peterinmalaga on 2014-12-06
Thank you Oldfred. That's very helpful and will take me some time to work through but I have the time and want to change. 
It's an HP Pavilion 15-n223sa Notebook  64 bit. Here's the info I have:
Microprocessor Intel Core i3-3217U with Intel HD Graphics 4000 (1.8 GHz, 3 MB cache, 2 cores)
Chipset Intel HM76 Express
Memory 8 GB 1600 MHz DDR3L SDRAM (1 x 4 GB, 1 x 4 GB)
Video Graphics Intel HD Graphics 4000
Hard Drive 1 TB 5400 rpm SATA
Multimedia Drive SuperMulti DVD burner
Display 39.6 cm (15.6") diagonal HD BrightView LED-backlit (1366 x 768)
Network Card Integrated 10/100 BASE-T Ethernet LAN
Wireless Connectivity 802.11b/g/n (1x1)

---

### Post by peterinmalaga on 2014-12-06
Hi Mark. I have changed to Classic shell and that is better. I have also made some adjustments to change the touchpad gestures which are permitted. All that helps.
What bugs me is that I already have a mobile phone and a tablet and don't need a laptop with all the same features. I will certainly never buy a laptop with a touch screen and don't like the fact that the default setup of my laptop tries to force me to use it in the same way as a mobile phone with apps, screen gestures etc. That seems to be the way things are developing but it makes no sense and I know a few people who are giving Windows 8 a miss and waiting for Windows 9 before they buy a new computer. I could not wait, my old computer clunked. Normally when my computers get old, I install Ubuntu. My HP is going to get Ubuntu a lot sooner, if I can do it.

---

### Post by oldfred on 2014-12-06
HP is not particularly dual boot or Linux friendly. They modify UEFI internally so the UEFI boot entry must read Windows.

But there are a variety of work arounds. UEFI can directly boot a device like the hard drive, so you can replace the device boot file EFI/Boot/bootx64.efi with grubx64.efi and boot hard drive.
Or if only booting Ubuntu change the label that it loads grub from ubuntu to Windows.

Several other alternatives:
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

      
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP manually renamed bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

            HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

HP Touchsmart 15
 [http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041)

---

