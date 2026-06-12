---
title: "How To Install Ubuntu Inside Windows 8"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by SoLikeHey01 on 2013-02-16
Hi Everyone, 
 
I made this thread because I notice people are having problems installing Ubuntu inside of Windows 8.
 
Windows 8 has changed there boot partition to a GUI interface so Ubuntu (Wubi) does not know where to implant its bootloader. 
 
[IMG]http://img138.imageshack.us/img138/9427/17171628.png[/IMG] 
You may receive an error like this in Windows 8 when trying to install Ubuntu with Wubi. 
 
[SIZE=4][COLOR=orange]Now Lets Do It! ):P[/COLOR][/SIZE]


[SIZE=2][COLOR=black]You will need:[/COLOR][/SIZE]
[LIST]
[*][SIZE=2]Administrative Permissions[/SIZE]
[*][SIZE=2]Internet Connection[/SIZE]
[*][SIZE=2]Windows 8, Any Edition[/SIZE]
[*][SIZE=2]Your brain :KS[/SIZE]
[/LIST][SIZE=2]1. On an Administrative Account, Go Online to [http://neosmart.net/Download/Register/1](http://neosmart.net/Download/Register/1) and download the Free EasyBCD. [COLOR=red]We are going to use this to change the bootloader to a Windows 7 look-a-like. Don't worry, you will still be able to boot into Windows 8! :)[/COLOR][/SIZE]

[SIZE=2][COLOR=black]2. Download, and Install EASYBCD. Once finished you should be here.[/COLOR][/SIZE]
[[IMG]http://img842.imageshack.us/img842/486/captureevca.png[/IMG]]("http://imageshack.us/photo/my-images/842/captureevca.png/")
Uploaded with [ImageShack.us]("http://imageshack.us")
 
Click on BCD Deployment and you should be here..
[[IMG]http://img198.imageshack.us/img198/6471/dks.png[/IMG]]("http://imageshack.us/photo/my-images/198/dks.png/")
Uploaded with [ImageShack.us]("http://imageshack.us")
 
**_NOW PLEASE READ CAREFULLY_**
**[COLOR=red]This is your Boot loader.[/COLOR]**

**[COLOR=black]If you have a SYSTEM RESERVED partition, Do NOT Delete unless you are SURE you do not use that partition. [/COLOR]**
 
**If you have a PQSERVICE or RECOVERY partition, Do NOT click "Install BCD" on those partitions.**
 
With that said, Press, Install BCD on your HARD DRIVE PARTITION. It should be 2 Partitions if you have System Reserved and Your Local Disk. To find out which one is your local hard disk, it is the one with the most space. :P 
 
When BCD is installed Correctly, you will get a screen* EasyBCD has successfully converted the selected disk into a bootable drive. In Order To Configure... blah blah.... *Press YES on the confirmation screen and now You have the Windows 7 Bootable Screen Again! 
 
[SIZE=4]You are not finish so DO NOT CLOSE BCD or your computer will FAIL![/SIZE]

[SIZE=3]Now you should be back at a screen like this.[/SIZE]
[[IMG]http://img9.imageshack.us/img9/1852/flkdflskf.png[/IMG]]("http://imageshack.us/photo/my-images/9/flkdflskf.png/")
Uploaded with [ImageShack.us]("http://imageshack.us")
 
You have nothing to boot in to. BUT not to worry, 
 
[COLOR=darkorange]Click on "Add New Entry" and at the top, you should see Operating Systems; Windows Vista/7/8 and the Default Name should be Microsoft Windows 7. Change it to anything you like! Either "Windows 8", "Windows", or "I like Pizza" [/COLOR]
[SIZE=4]Now Windows 8 can now boot into your Windows 7 GUI. You can now safely restart your computer if you want to test. But with that said, Wubi can now be installed because it feels like it is installing on a Windows 7 PC. You will have no worries. [/SIZE]


[SIZE=2][COLOR=red]I made this guide because all these steps helped me. I hope it all helps you! [/COLOR][/SIZE]

---

### Post by PIE09gbLmgG6 on 2013-02-16
Thanks for the help...

I made a decision will at costco playing with windows 8...I really don't like it at all...some of the machines didn't even have a touch screen...which I feel would get tedious...and even with touch...it was't doing anything for me.

When I tried ubuntu last year I wasn't entirely sold...but this latest version hits the mark...my real excitement is the new mobile phone version coming out...I'm looking forward to not having to lug anything around...just a phone that does it all...

Thanks again for the tutorial. 

ego-

---

