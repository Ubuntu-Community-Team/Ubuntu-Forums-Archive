---
title: "Black screen after 7.10 fresh install, No Grub!"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by siulca on 2008-05-11
After many fruitless tries at getting the 8.04 upgrade working, I decided to go back to 7.10.

In an attempt to keep my data and configuration, I installed 7.10 on the root partition without formating the /home partition. The installation went fine but on boot **Grub didn't load**, leaving me staring at a completely black screen. And to make matters worse, after this I couldn't even load from 7.10 Live CD (yes with CD-Rom selected as the first boot device in the BIOS).

After much head scratching I managed to boot from the Live CD by either physically removing the hard drive from my machine or by selecting a USB drive as the primary drive in the BIOS boot settings.

Booting from the Live CD I re-installed Grub to the both the MBR and the partition but the same problem persisted. 

So I decided to backup my data, completely format the drive and install 7.10 from scratch while letting the installer to partition automatically.

Well, after rebooting I still got the same greeting, a black screen freeze with no grub nor error message. 

My guess is that the MBR is corrupt? But I don't understand how Ubuntu would damage it! Nor do I know how to restore it!

I read half of the internet this weekend trying to fix this problem, tried a load of possible solutions even thought I can't find the exact same problem anywhere. :confused:

Now I ran out of ideas, so please please please tell me you have a fix. 


Ty.

---

### Post by siulca on 2008-05-12
Bump...

I'll pay a few drinks (via paypal) to whoever finds a solution to my problem. :)

---

### Post by siulca on 2008-05-12
I'll pay a few drinks to whoever finds a solution to my problem described here:
**[http://ubuntuforums.org/showthread.php?t=790886](http://ubuntuforums.org/showthread.php?t=790886)**

;)

(Sorry for the duplicate thread, I couldn't edit the title of the original thread.)

---

### Post by housam on 2008-05-12
Try to use the [[COLOR="Red"]_Super grub disk _[/COLOR]]("http://supergrub.forjamari.linex.org/"), it may help.

---

### Post by siulca on 2008-05-12
> **housam said:**
> Try to use the [[COLOR="Red"]_Super grub disk _[/COLOR]]("http://supergrub.forjamari.linex.org/"), it may help.

Housam, thanks for the link. I'll try to burn it at work and will give it try when I get home tonight. :)

However, at the first glance Super Grub Disk doesn't seem to do anything that I am not able to do (and have done already) from the Live CD. 

How do you think I can use SGD to fix my issue?

---

### Post by housam on 2008-05-12
Do this 
[COLOR="Red"]_[COLOR="Red"][COLOR="Red"][U][http://www.supergrubdisk.org/wiki/SGD_Howto_make]("http://www.supergrubdisk.org/wiki/SGD_Howto_make")_[/COLOR][/COLOR][/U][/COLOR]

Then , Either you have a Super Grub Disk Cdrom, Floppy or USB what you have to do is insert Cdrom, Floppy or plug the USB just before starting your computer. If SGD appears at boot you do not have to do anything. 

If SGD does not appear you should tweak your BIOS settings so that the SGD where device is installed boots in the first place. 

Then follow this 
[COLOR="Red"]_[COLOR="Red"][COLOR="red"][U][http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Ntldr_is_missing]("http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Ntldr_is_missing")_[/COLOR][/COLOR][/U][/COLOR]

---

### Post by siulca on 2008-05-12
> **housam said:**
> Do this 
[COLOR="Red"]_[COLOR="Red"][COLOR="Red"][U][http://www.supergrubdisk.org/wiki/SGD_Howto_make]("http://www.supergrubdisk.org/wiki/SGD_Howto_make")_[/COLOR][/COLOR][/U][/COLOR]
Then follow this 
[COLOR="Red"]_[COLOR="Red"][COLOR="red"][U][http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Ntldr_is_missing]("http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Ntldr_is_missing")_[/COLOR][/COLOR][/U][/COLOR]

Thanks for the quick reply Housam.

I don't have nor ever had windows installed on this laptop but I'll give that a shot anyway and will let you know how it goes.

---

### Post by housam on 2008-05-12
> **siulca said:**
> 
My guess is that the MBR is corrupt? But I don't understand how Ubuntu would damage it! Nor do I know how to restore it!
Ty.
The above sentence gave me the impression that you have a dual boot with windows.

use the same steps but point to the line Gnu/Linux

---

### Post by siulca on 2008-05-12
> **housam said:**
> The above sentence gave me the impression that you have a dual boot with windows.

use the same steps but point to the line Gnu/Linux

Hi Housam,

I tried the disk and followed the steps as you suggested but I still couldn't boot my hard drive if my hard drive is set as the **primary hard drive** in the BIOS (not to be confused with the primary BOOT device in the BIOS).

So in order to be able to boot the CD I set up a USB pen as my primary hard drive in the BIOS. The pen gets identified by grub as hd(0,0) and my HD as hd(1,0). So I installed Grub onto my USB pen and voila, now I can boot my hard drive. :) This is obviously a workaround but proves that Ubuntu was installed and is working fine.

HOWEVER, this means that now I must have the USB pen inserted in order to boot the HD, which is a bit of a pain. Do you have any clue how I can get around this? 

Many thanks for your help so far :)

---

### Post by housam on 2008-05-13
**Using the Ubuntu Desktop/Live CD**
Quick Start
This option will use the Desktop/Live CD to install Grub into your MBR (Master Boot Record)in order to boot Ubuntu  

1. Boot from the CD with the use of your usb pen

2. Open a terminal  

3. Start grub as root with the following command : 
```
sudo grub
```


4. You will get a grub prompt (see below) which we will use to find the root partition and install grub to the MBR (hd1,0) 
```
[ Minimal BASH-like line editing is supported.   For 
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
```
   
Type the following and press enter:
```
find /boot/grub/stage1
``` 


Using this information, set the root device: 
```
grub> root (hd1,0)
```

Install Grub: 
```
grub> setup (hd1)
```

Exit Grub: 
```
grub> quit
```

5. Reboot (to hard drive). Grub should be installed and Ubuntu should have been automatically detected. 





Also read this guide. It will help restoring grub to your hard :
[[COLOR="Red"]_https://help.ubuntu.com/community/GrubHowto_[/COLOR]]("https://help.ubuntu.com/community/GrubHowto")

---

### Post by siulca on 2008-05-13
Thanks for the reply Housam.

That's exactly what I did after I managed to log into Ubuntu. 

However this still leaves the boot precess dependent on having the USB key inserted. If I remove it my hard drive becomes hd(0,0) (instead of hd(1,0)) and grub fails to load again!

---

### Post by adrian15 on 2008-05-15
> **siulca said:**
> Housam, thanks for the link. I'll try to burn it at work and will give it try when I get home tonight. :)

However, at the first glance Super Grub Disk doesn't seem to do anything that I am not able to do (and have done already) from the Live CD. 

How do you think I can use SGD to fix my issue?

#1 Try with **Choose Language & Help -> English Super Grub Disk -> Boot & Tools -> Activate Partition -> Choose the first partition**.

#2 If it does not work you should install your Ubuntu manually with a 300 /boot partition at the hard disk beginning. There is an example at the [Linux Installation Do Not Boot (Super Grub Disk Wiki)](http://www.supergrubdisk.org/wiki/Linux_Installation_Do_Not_Boot)

#3 If you get your Ubuntu to boot make a donation to Super Grub Disk's project (Didn't you say something about "paying"? ) :).

adrian15

---

