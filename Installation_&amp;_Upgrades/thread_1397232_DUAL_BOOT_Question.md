---
title: "DUAL BOOT Question"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by napsterdj on 2010-02-03
Hello All, 

I wanna know how to modify the boot screen which allows me to select windows or ubuntu at the startup.

Here is what I've done : 
----------------------------

1. I had Vista Installed on my machine earlier on. I partitioned the HD and installed Ubuntu 9.04. It was working like a charm and everytime my computer started , I would get two options :
1. Windows
2. Ubuntu


2. After a while I upgraded to Windows 7 and Ubuntu stopped working.

3. So I uninstalled Ubuntu , deleted the partition , created a new partition and installed Ubuntu on that.

4. Now when my computer starts , I get many options at the start and I cant even remember what they are called.

I want to modify these options so that I can get my old style of boot up back , i.e 

1. Windows
2. Ubuntu

Can you guys help me solve this ? Any help is appreciated. ;)

---

### Post by napsterdj on 2010-02-03
Ok here is what the new boot screen looks like : 

**** Kernel ***** some numbers ***
**** Kernel ***** [ recovery mode]
Other operating Systems :
Windows Vista
Windows Vista


I'm really sorry guys, i have a bad memory and i forgot to take down exactly what it said hence the ****'s .

---

### Post by napsterdj on 2010-02-03
And also on previous ocassion when I had vista installed , i could see the partition allocated for ubuntu on my computer. But now i cant see the Ubuntu partition from Windows. Any suggestions to fix this as well ?

---

### Post by yogesh.girikumar on 2010-02-03
Hi,


       Those options you see in the boot menu serve some purpose.


       The Menu options let you boot into Ubuntu in Safe Mode in case you run into any trouble. It also has a recovery mode and an option possibly for testing your RAM for defects. These options come in handy if Ubuntu crashes and help recover critical data. So it is recommended that you keep these options intact, unless you're very familiar with 'passing boot parameters'.


       You can remove it by editing the grub configuration file. But doing so is VERY RISKY. You might end up messing up the boot settings. You have been warned !


       If you're still compelled to do so, check the following links:


       **For Ubuntu Karmic 9.10**

       [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)
       
**If you're running any earlier release of Ubuntu Other than Karmic Koala:**

       [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[URL="https://help.ubuntu.com/community/GrubHowto"]
[/URL]    HTH,

---

### Post by napsterdj on 2010-02-03
Hey there ,

Thanks for answering my question. I did find out that this happens because of the settings in the grub file. I managed to locate it and played with it by just changing the names. 

I do realize its important now.

But is there an option which is pointing to Windows OS by default and the timer is going down in the boot screen ? 

So that it boots to windows by default without me having to press any key.

> **yogesh.girikumar said:**
> Hi,


Those options you see in the boot menu serve some purpose.


The Menu options let you boot into Ubuntu in Safe Mode in case you run into any trouble. It also has a recovery mode and an option possibly for testing your RAM for defects. These options come in handy if Ubuntu crashes and help recover critical data. So it is recommended that you keep these options intact, unless you're very familiar with 'passing boot parameters'.


You can remove it by editing the grub configuration file. But doing so is VERY RISKY. You might end up messing up the boot settings. You have been warned !


If you're still compelled to do so, check the following links:


For Ubuntu Karmic 9.10

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Gr...Menu%20Entries](https://help.ubuntu.com/community/Gr...Menu%20Entries)

If you're running any earlier release of Ubuntu Other than Karmic Koala:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

HTH,

---

### Post by Sef on 2010-02-03
> 2. After a while I upgraded to Windows 7 and Ubuntu stopped working.


That happened because Windows only sees Windows oses.   You have to reinstall GRUB to get it to see both.

---

### Post by yogesh.girikumar on 2010-02-04
Hi,
> But is there an option which is pointing to Windows OS by default and the timer is going down in the boot screen ?       This can be done by editing the file /etc/default/grub

> 

[LIST=1]
[*]GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric or "saved"
[LIST]
[*]GRUB_DEFAULT=saved - Sets the default menu entry with whatever was selected last. If the menu is displayed during boot, the last entry selected will be highlighted. If no action is taken, this selection will be booted at the end of the timeout or if the menu is hidden. grub-set-default is enabled when this value is set to saved. You can quickly change the default OS/kernel with this command.
[/LIST]

[LIST=1]
[*]
[LIST]
[*] The format is "sudo grub-set-default X, with X being the menuentry position (starting with 0 as the first entry) or the exact menu string. Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.31-14-generic"
[*]+ To obtain the existing menuentry choice number (starting from 0) or the menuentry "string", run "grep menuentry /boot/grub/grub.cfg"
[/LIST]
 
[/LIST]

[LIST]
[*]GRUB_DEFAULT="xxxx" - An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"
[/LIST]
 
[/LIST]
       So here's what you can do:

   **OPTION 1:**

[LIST]
[*]     Edit the /etc/default/grub file```
$ sudo vim /etc/default/grub
```
[/LIST]

[LIST]
[*] Change the value for GRUB_DEFAULT to saved. This is how the line is supposed to look like.```
GRUB_DEFAULT=saved
```
[/LIST]

[LIST]
[*] Whatever boot menu option you choose will be saved and your system will boot off this menu.
[/LIST]
**OPTION 2:**

[LIST]
[*] If you want to set it as permanent option,
[/LIST]

[LIST]
[*] Edit the /etc/default/grub file and set GRUB_DEFAULT=saved
[/LIST]

[LIST]
[*] In terminal type:
[/LIST]
 ```
$ sudo grub-set-default X
```**Where X is the position of the menu entry that you want to set as the option selected by default**
**0 is the first entry**

For e.g. If you want to select the third entry as the default boot option, type:
```
 $ sudo grub-set-default 2
``` Or you can even type the "exact menu string"s. E.g
```
$ sudo grub-set-default "Ubuntu, Linux 2.7.27-14-generic" 
```Include the quotes.  

You can also edit the /etc/default/grub file to set

```
GRUB_DEFAULT="Microsoft Windows 7" 
```or something similar

     Please make sure it's **exactly** the same string as shown in the boot menu entry. Capitalization and punctuations matter.

       I referred to this very resourceful link: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  

HTH

---

### Post by napsterdj on 2010-02-07
> **yogesh.girikumar said:**
> Hi,
       This can be done by editing the file /etc/default/grub

    So here's what you can do:

   **OPTION 1:**

[LIST]
[*]     Edit the /etc/default/grub file```
$ sudo vim /etc/default/grub
```
[/LIST]

[LIST]
[*] Change the value for GRUB_DEFAULT to saved. This is how the line is supposed to look like.```
GRUB_DEFAULT=saved
```
[/LIST]

[LIST]
[*] Whatever boot menu option you choose will be saved and your system will boot off this menu.
[/LIST]
**OPTION 2:**

[LIST]
[*] If you want to set it as permanent option,
[/LIST]

[LIST]
[*] Edit the /etc/default/grub file and set GRUB_DEFAULT=saved
[/LIST]

[LIST]
[*] In terminal type:
[/LIST]
 ```
$ sudo grub-set-default X
```**Where X is the position of the menu entry that you want to set as the option selected by default**
**0 is the first entry**

For e.g. If you want to select the third entry as the default boot option, type:
```
 $ sudo grub-set-default 2
``` Or you can even type the "exact menu string"s. E.g
```
$ sudo grub-set-default "Ubuntu, Linux 2.7.27-14-generic" 
```Include the quotes.  

You can also edit the /etc/default/grub file to set

```
GRUB_DEFAULT="Microsoft Windows 7" 
```or something similar

     Please make sure it's **exactly** the same string as shown in the boot menu entry. Capitalization and punctuations matter.

       I referred to this very resourceful link: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  

HTH

Thanks a ton mate. Will try this as soon as im done completing my programming project. 
Will keep you posted on this. :)

---

