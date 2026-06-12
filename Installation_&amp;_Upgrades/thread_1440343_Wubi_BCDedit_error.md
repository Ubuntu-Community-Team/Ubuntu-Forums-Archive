---
title: "Wubi BCDedit error"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by dstar on 2010-03-27
I can not install Ubuntu9.10 With Wubi.It gives me following error:

[IMG]http://img404.imageshack.us/img404/245/errorv.png[/IMG]
I looked into this post [http://ubuntuforums.org/showthread.php?t=1434508&highlight=Wubi+BCDedit+error](http://ubuntuforums.org/showthread.php?t=1434508&highlight=Wubi+BCDedit+error)
but it does not help much

[IMG]http://img176.imageshack.us/img176/1000/cmd.png[/IMG]
Shot at 2010-03-27
[IMG]http://img260.imageshack.us/img260/6678/regedit.png[/IMG]

---

### Post by coolcaseley67 on 2010-03-27
Hi 

- pease  could you tell me  what did and did not work on the post   [http://ubuntuforums.org/showthread.p...+BCDedit+error ]("http://ubuntuforums.org/showthread.php?t=1434508&highlight=Wubi+BCDedit+error")

thanks

---

### Post by dstar on 2010-03-27
> Step 1: Try and uninstall Ubuntu via Wubi and note down the part of the error shown in the image above.
I copied the key {723ed238-140e-11df-84cb-a1e8bb1b8261}


> Step 2: Download EasyBCD 2.0 (Google), install it and create a boot entry. To do this, launch EasyBCD and goto Add/Remove Entries. Now click the Linux/BSD tab and set the Type to "Wubi" and give it the name "Ubuntu". Finally, click "Add Entry".

I downloaded and installed the EasyBCD2.0 build90. and added the entry
> Step 3: Now close EasyBSD and enter "cmd.exe" in the Windows search box on the start menu. Right click cmd.exe and select "Run as Administrator". Now, type "bcdedit.exe" into the Command Prompt window and hit enter.

It will spew a lot of writting into the Command Prompt but we want the end of it (Real-mode Boot Sector). Find the entry named "Ubuntu" and note down the identifier.
This step also works fine..here is my output
```
Real-mode Boot Sector
---------------------
identifier              {723ed23f-140e-11df-84cb-a1e8bb1b8261}
device                  partition=C:
path                    \NST\AutoNeoGrub0.mbr
description             Ubuntu
```
> Step 4: Close cmd.exe and now search for "regedit.exe" the same way as we did cmd.exe. Now goto Edit > Find and then search for the bit of text we took note of in the error at the beginning.

If all is well you should get a screen like the one shown below. We are going to edit the "VistaBootDrive" entry. Right click on it and select "Modify". Now delete the text shown in the box and replace it with the identifier you took note of from the Command Prompt earlier and click OK.
I did the same but I got different screen as shown in screenshot..?

---

### Post by coolcaseley67 on 2010-03-27
hi

make sure you run  redit   with admin power .
 what's difference  ? for the VistaBootDrive ?? bit 

sorry

---

### Post by dstar on 2010-03-27
> make sure you run redit with admin power .

I tried again no luck:(
> what's difference ? for the VistaBootDrive ?? bit
Which build of EasyBCD2.0 was the author of the orignal post using??I am using latest build which is 90

---

### Post by coolcaseley67 on 2010-03-27
hi 
 
-look for your key which is the bold in my post after this one 
hope it helps

---

### Post by coolcaseley67 on 2010-03-27
[QUOTE=dstar;9036006]I copied the key {723ed238-140e-11df-84cb-a1e8bb1b8261}
 
 This step also works fine..here is my output
```
Real-mode Boot Sector
---------------------
identifier             ** {723ed23f-140e-11df-84cb-a1e8bb1b8261}**
device                  partition=C:
path                    \NST\AutoNeoGrub0.mbr
description             Ubuntu
```

---

### Post by dstar on 2010-03-28
When I searched for the key here are the results:
[IMG]http://img121.imageshack.us/img121/1614/12735612.png[/IMG]
[IMG]http://img229.imageshack.us/img229/7029/f21g.png[/IMG]
[IMG]http://img176.imageshack.us/img176/2488/f212.png[/IMG]
============================================
Then in HKEY local Machine=>BCD00000000=>Objects=>{723ed23f-140e-11df-84cb-a1e8bb1b8261}(This has two more items)1)Description
      2)Elements=>1)11000001
                  2)12000002
                  3)12000004
Here is the screebshot:
[[IMG]http://img337.imageshack.us/img337/516/newp.png[/IMG]](http://img337.imageshack.us/i/newp.png/)

None of the Registry Editor entry contains require information as shown by orignal poster in orignal thread?

---

### Post by coolcaseley67 on 2010-03-28
hi

- i can not help you here send a  piv email to [Scott.57215]("http://ubuntuforums.org/member.php?u=1037774")   , ask him of more help.

sorry

---

### Post by dstar on 2010-03-28
O.K
Thanks for reading and helping me.......:)
I think I will have to use Ubuntu Live

---

### Post by coolcaseley67 on 2010-03-28
Hi

- no prob's :-# 

happy ubuntu-ing

update : 
- this should be fixed in Ubuntu 10:04

---

