---
title: "Need to  fix what I messed up"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by phantomdaz on 2010-08-19
Greetings

Recently I installed Ubuntu to a flash drive by just choosing that drive during the install.
after I did that, I get a 4 line menu after the bios boots, I have to scroll down to select the last entry to continue the boot process.

once I select that option, it boots into the windows multi boot menu where I have XP and 7 installed. All works fine from then on.

if I select the first entry, it will boot straight into Ubuntu on my flash drive and run fine.

I would like to remove Ubuntu from the flash drive but also remove the first 4 line boot option after the bios loads. I am asking if someone can help me return my pc back to the state it was before I tried to install Ubuntu on my flash drive.

a few details
I have Win 7 on one partition on a large hard drive
Win XP is on a separate hard drive.
Ubuntu is only on the flash drive

Can anyone give me some help?

also, if I remove the flash drive that has Ubuntu on it, when I boot, it gives me an error when it looks for the flash drive and I can go no further


BTW, I am very knowledgeable with windows but am a Ubuntu rookie

Thanks in advance for any assistance

Daz

---

### Post by tommcd on 2010-08-19
You probably just need to boot from your Windows XP or Windows 7 CD / DVD and run the option to fix the MBR. It sounds like grub2 from Ubuntu has taken over the MBR of your computer's hard drive, which would explain why:
> ... if I remove the flash drive that has Ubuntu on it, when I boot, it gives me an error when it looks for the flash drive and I can go no further ...
 
Once you restore your Windows MBR, you will be be back to using the same closed source proprietary operating systems you were using before.
Once you are back using your Windows, you can just reformat the flash drive to fat32 or whatever Windows uses for flash drives these days. Then your flash drive will be back the way it was also.

I would like to suggest installing Ubuntu to your computer's hard drive and giving Ubuntu / linux a chance; but it is your system. If you don't want Ubuntu, just restore the Windows MBR and all will be fine.

And welcome to the (free as in freedom) Ubuntu forums !!!

---

### Post by phantomdaz on 2010-08-19
Thanks for the reply
I will let you know if that fixes my issue

just to let everyone know, I do want to used Ubuntu and I installed it to test with programs and such  to see if I wanted to pull the plug on Windows.

I just didn't get it installed the way I wanted to and would like to start over fresh.

Ultimately, I would like to use the win boot mgr for now and have  the selection read
XP, 7 and Ubuntu for testing 

if I can not do that, I will see about loading it on  the flash drive and boot from it for testing (which is what I thought I was doing when I installed it the first time)

Thanks again, Lets see if I can totally meed this up :)

Daz

---

### Post by tommcd on 2010-08-19
See:
[http://www.youtube.com/watch?v=89vmg9SpUJE](http://www.youtube.com/watch?v=89vmg9SpUJE)
[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
If you want to dual boot with Ubuntu, I would urge you to just use grub2. It works very well for booting Windows + linux.
 I currently boot Windows XP, Ubuntu, Slackware, and Salix without problems using grub2.
However ... There have been some issues reported with booting Windows 7 from grub2. It seems that Windows 7 guards the MBR more tenaciously than XP did. These issues are not insurmountable from what I have read though. I just have no direct experience with Windows 7. There are many threads on these forums though about dual boot booting Windows 7 + Ubuntu.

EDIT: See these also:
[http://www.eddieoneverything.com/windows-xp/uninstalling-the-ubuntu-linux-boot-manager.php](http://www.eddieoneverything.com/windows-xp/uninstalling-the-ubuntu-linux-boot-manager.php)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
Hope some of this helps.

Trying out Ubuntu from the flash drive is a wise choice. You can run Ubuntu from the flash drive for a while until you are sure that you really want to use (and abuse !!!) it!
Keep on learning. That is half the fun of discovering the wild world of free software!

---

### Post by phantomdaz on 2010-08-19
Well folks

No workie :)

I booted to my Win 7 DVD, went to the command prompt and  typed bootsect /nt60 c:

it said it completed successfully

I then rebooted normally and the Ubuntu loader still loads up right after the bios finishes. Again, once I select windows at the end of the list, it loads the Win loader then I can select XP or Win 7

I guess the repair found the Win loader where it was supposed to be and over wrote it.

It had no effect on the Ubuntu loader.
I need to find out  how to eliminate or de-install the Ubuntu loader and I think all will be OK

I thought about uninstalling Ubuntu from the flash drive but I am afraid it will just give me an error because it is looking for it on the first boot loader and wont find it. That is what happens if I remove the drive and try to boot

as it stands right now, I can not remove the flash drive from my pc or it will not boot


kinda weird

Thanks

---

### Post by phantomdaz on 2010-08-19
Sorry
I left out something
I tried the Easy BCD. it just shows the XP and windows 7 loaders. It does not show Ubuntu so I can not remove it like the you tube video shows.

Thanks again for any help

---

### Post by tommcd on 2010-08-19
> **phantomdaz said:**
> 
I booted to my Win 7 DVD, went to the command prompt and  typed bootsect /nt60 c:
it said it completed successfully

I then rebooted normally and the Ubuntu loader still loads up right after the bios finishes. ...
Perhaps someone who actually uses Windows 7 may want to help out here ... I hope!
Anyway, if you google <windows 7 fix mbr> you will get a boatload of links such as:
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)
[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://technet.microsoft.com/en-us/magazine/ee851681.aspx](http://technet.microsoft.com/en-us/magazine/ee851681.aspx)
[http://www.webtlk.com/2010/02/27/how-to-fix-mbr-in-windows-7/](http://www.webtlk.com/2010/02/27/how-to-fix-mbr-in-windows-7/)
It only took me a few seconds to find all that stuff.
Do you have a *legal* Windows 7 install DVD?

---

### Post by phantomdaz on 2010-08-19
Thanks
yeah, I have done that. I don't think it is a Windows 7 issue. I think I need to find out what or where the Ubuntu boot record is and maybe point it straight to windows or some how remove it

I find articles on how to reload the Grub or loader but nothing on removing it.

It would be fine with me if it didn't look for the Ubuntu install and just skipped over it

Maybe I can troll thru the  bios to see if there is anything in there that has changed....although I doubt it

Thanks again, your help is appreciated

---

### Post by presence1960 on 2010-08-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Open the RESULTS.txt file and read the top portion.

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

If the MBR of your sda disk has GRUB 2 on it, it will look like this (except which partition GRUB is looking to for /boot/grub) at the very top of the script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 [COLOR="Red"]=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.[/COLOR]
 => Lilo is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc


```

If you have GRUB 2 in the MBR of sda you obviously want to change that to the windows bootloader. Boot to Ubuntu or boot the ubuntu Live CD. open a terminal and run ```
sudo apt-get install lilo
```

After lilo is installed run in terminal ```
sudo lilo -M /dev/sda mbr
```

Ignore the warnings and proceed. After that operation is completed reboot (without live cd if you used it above) and you should boot right to windows.

I agree with tommcd that you would be better off multi booting using GRUB. I use GRUB to boot Ubuntu, sabayon and windows 7 with no problems whatsoever.

If you are not sure then post the entire contents of the RESULTS.txt file back here so we can see what you have as far as set up and boot process.

---

### Post by phantomdaz on 2010-08-20
You are the man!

Followed your directions to the "T" and it worked perfectly

Thank you so much

now, can you help me get Ubuntu installed correctly so I can start using it? I still need my "winders: for some programs that are specific to it

Question
Can I install it and have it listed in my windows boot menu along with XP and 7?
Should I install it on my flash drive ?

I have plenty of hard drive space but it is all in one partition, 

I also would like to have a bootable version for my company laptop on a flash drive. I can not install anything on it.

Thanks again for your help

Daz

---

### Post by tommcd on 2010-08-20
> **phantomdaz said:**
> 
now, can you help me get Ubuntu installed correctly so I can start using it? I still need my "winders: for some programs that are specific to it
Here are 2 great sites for getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
Also, steal the free Ubuntu Manual:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
> **phantomdaz said:**
> 
Can I install it and have it listed in my windows boot menu along with XP and 7?
Should I install it on my flash drive ?
If you install Ubuntu and install grub2 to the MBR (master boot record) of the hard drive, which is the default location, then grub2 will control booting to Ubuntu, XP, and Windows 7. This is perfectly fine. I boot XP and several linux distros with grub2. And Presence1960 said he boots Windows 7 with grub2 with no problems, so you can also.
If you just want to play around with Ubuntu, then installing to the flash drive is fine. If you install Ubuntu to the flash drive, when you get to the part where you install grub2, you can select the advanced options and install grub2 to the flash drive. Then set the computer's BIOS to boot from the flash drive as the first boot device. This should let you boot Ubuntu when the flash drive is plugged in. When the flash drive is not plugged in you should be able to boot Windows normally.

 If you want to stay with Ubuntu you should do a real install to a dedicated partition on your hard drive. The 2 sites I linked to above discuss how to get started.
Write back if you need more help.

---

### Post by tommcd on 2010-08-20
> **presence1960 said:**
> 
If you have GRUB 2 in the MBR of sda you obviously want to change that to the windows bootloader. Boot to Ubuntu or boot the ubuntu Live CD. open a terminal and run ```
sudo apt-get install lilo
```

After lilo is installed run in terminal ```
sudo lilo -M /dev/sda mbr
```

Presence1960,
I am just curious, why did you recommend installing lilo rather than fixing the Windows MBR from the Windows CD?

---

### Post by Cavsfan on 2010-08-20
If you are now good to go, you might want to check out my tutorial for making a custom grub2 screen that is 
good for dual booting, or just plain Ubuntu. You will never have to modify the default line when a new kernel
is installed. Check it out and if you like it, spread the word. :D

There are a couple of example screens at the bottom.

---

### Post by presence1960 on 2010-08-20
> **tommcd said:**
> Presence1960,
I am just curious, why did you recommend installing lilo rather than fixing the Windows MBR from the Windows CD?

The windows CD/DVD will work fine also, but to me using lilo to restore a windows MBR is less complicated. Like the old saying goes "there is more than one way to skin a cat." Also for those who don't have a windows CD/DVD at hand this is a lifesaver.

To add another option to the list there is a Vista & a windows 7 Recovery Console CD iso that can be downloaded from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

It is always good to know  as many options as possible.

---

### Post by Cavsfan on 2010-08-21
> **tommcd said:**
> presence1960,
i am just curious, why did you recommend installing lilo rather than fixing the windows mbr from the windows cd?

[quote=presence1960;9745880]the windows cd/dvd will work fine also, but to me using lilo to restore a windows mbr is less complicated. Like the old saying goes "there is more than one way to skin a cat." also for those who don't have a windows cd/dvd at hand this is a lifesaver.

To add another option to the list there is a vista & a windows 7 recovery console cd iso that can be downloaded from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

It is always good to know  as many options as possible.[/quote]

+1 Excellent point (post)!

---

