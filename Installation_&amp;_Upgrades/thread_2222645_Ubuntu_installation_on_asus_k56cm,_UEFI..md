---
title: "Ubuntu installation on asus k56cm, UEFI."
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by kestutis3 on 2014-05-07
Hello. I've read so many guides how to install ubuntu in UEFI mode, but none of them helped. There is no option to disable secure boot in bios. When im trying to boot it from USB, it shows a purple screen with ubuntu logo, and after some time (~1 min) i get error message - Unable To Find A Medium Containing A Live File System.

I've tried 12.04 and 14.04 versions.

---

### Post by oldfred on 2014-05-07
Unless this is one of the tiny Atom based or similar systems with totally locked UEFI, then Microsoft contract says vendors will offer ways to turn secure boot off.

       Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)

  ASUS Transformer Book T100TA that was one of the early Intel Bay Trail convertible laptops/tablets. 
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

Asus UEFI should be similar for similar models, just hardware may vary. Biggest difference would be if Intel or AMD based system.
      
 Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

 Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
      
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

---

### Post by kestutis3 on 2014-05-07
If i'm right, 14,04 version does not need secure boot to be turned off, so it should work but...

---

### Post by oldfred on 2014-05-07
If you are getting purple screen that is BIOS boot. In UEFI boot you get a grub menu, black background.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Be sure to have good backup of Windows. And a Windows repair flash drive.
Best to shrink Windows using Windows own partition tools and reboot immediately so it can run chkdsk and update itself for its new size.
Links to more info in my signature.

---

### Post by kestutis3 on 2014-05-07
I get black screen where i can select to install, or try without installing. When i choose one then i get purple screen with ubuntu logo. It is trying to load something about 1 minute and then i get error [COLOR=#000000] Unable To Find A Medium Containing A Live File System.[/COLOR]

---

### Post by oldfred on 2014-05-07
Then it sounds like it has started to boot but has errors. 
I would check that download was ok with md5sum.
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

At grub screen remove quiet splash and see if you can see what is causing error. Often not last posted entry but several above it.

What video card/chip? Sometimes that throws strange errors, not just video errors.
If you have nVidia chip and it boots using that chip, not an Intel one,  you need nomodeset.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by kestutis3 on 2014-05-07
My laptop has both, intel and nvidia cards. I will check md5 and other suggestions tomorrow, because it's late here. Thanks for help.

---

### Post by oldfred on 2014-05-07
If booting with Intel chip you may need one of these settings. 
Does your BIOS let you choose or is it one of the auto switch versions.

 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by kestutis3 on 2014-05-08
[B][COLOR=#000000]I would check that download was ok with md5sum.

[/COLOR][/B][COLOR=#000000]md5sum is ok

[/COLOR][B][COLOR=#000000]At grub screen remove quiet splash and see if you can see what is causing error. Often not last posted entry but several above it.
[/COLOR][/B][COLOR=#000000]
I get this error before booting stops. 
[/COLOR]
acpi warning \sb_.PCIO.PEGO.PEGP._DSM: Argument #4 type mismatch -Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)

[B][COLOR=#000000]Does your BIOS let you choose or is it one of the auto switch versions.

[/COLOR][/B][COLOR=#000000]I can't choose.





I've tried booting using theese commands with no success:
[/COLOR][COLOR=#000000]nomodeset
[/COLOR][COLOR=#000000]acpi=0
[/COLOR][COLOR=#000000]nouveau.blacklist=1


Trying to boot with nomodeset shows me theese messages [/COLOR]http://postimg.com/149000/2014-05-08-112328-148706.jpg


**SOLVED!!! Used rufus to create bootable USB and it worked! I've tried UUI and unetbootin before.**

---

