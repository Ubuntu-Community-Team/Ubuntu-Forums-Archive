---
title: "What the .....!"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SkullTraill on 2010-04-14
I downloaded [painfully] a Ubuntu 10.04 setup, i386, and when I was installing, I put it in a booted it, then a purple thing came, then another purple screen came with red dots, then a colourful purple BG came, and a msgbox poped up that said there was a "unrecoverable error".

WTF.
Is this a problem with my download? My CD? Or the version I downloaded? I have a 32-bit system.

---

### Post by bigsmitty64 on 2010-04-14
Are you aware that 10.04 is still a "beta" and **not** a final release? It will be out in a couple weeks as a final product though.Even having said that, it's pretty stable. What happens after the message?  Is it usable at all, or does it crash? Could be the speed at which you burned the cd. I hear that alot. Its a good idea to burn at the slowest possible speed. If it's not usable I would def "reburn" the cd and try again or maybe using 9.10 would be the route to go as it is the most recent stable "final" release, then upgrade  later. Good luck.
Smitty

---

### Post by SkullTraill on 2010-04-14
Hehe.. lol. Um after that pops up, it says to take CD out, then it reboots. Ah, damn, the CD speed.. :s
It must be that. But it might also be the download. I used IDM and paused it once. But it *is* a resumable download....

---

### Post by gastly on 2010-04-14
Make sure you downloaded the correct version, the i386 one for a 32 bit system.
And where did you download it from? From a torrent or a direct download?
In case of a direct download, you can check the md5 signature of the file to see if it's corrupt or not. Also, don't burn to a CD, I use my USB drive to install Ubuntu (Use the **Startup Disk Creator**) it's fast and you can just erase everything on the drive if something goes wrong.

---

### Post by lisati on 2010-04-14
Moved to Lucid Lynx Testing and Discussion.

---

### Post by wilee-nilee on 2010-04-14
This where I generally download from, but I use rsync now to just update the ISO. If your computer will boot with a thumb use unetbootin or if you have access to the Ubuntu startup disc creator, if you want a persistent install. 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by kansasnoob on 2010-04-14
Be sure to check the md5sum of the download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And when you boot the CD press any key to see the menu, and select "Check disc for defects".

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

---

### Post by SkullTraill on 2010-04-14
> **robert shearer said:**
> Try swapping out your keyboard. You seem to have some sticky keys.
Lol!


> **wilee-nilee said:**
> This where I generally download from, but I use rsync now to just update the ISO. If your computer will boot with a thumb use unetbootin or if you have access to the Ubuntu startup disc creator, if you want a persistent install. 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
I also downloaded from there...


> **lisati said:**
> Moved to Lucid Lynx Testing and Discussion.
Thank you, good sir.


> **gastly said:**
> Make sure you downloaded the correct version, the i386 one for a 32 bit system.
And where did you download it from? From a torrent or a direct download?
In case of a direct download, you can check the md5 signature of the file to see if it's corrupt or not. Also, don't burn to a CD, I use my USB drive to install Ubuntu (Use the **Startup Disk Creator**) it's fast and you can just erase everything on the drive if something goes wrong.
I did a direct download. And hmm.. I will also investigate this "Startup Disk Creator" got a link that points me to it?



Thanks for all helps ;)

---

### Post by SkullTraill on 2010-04-14
Hm since I used the "Current Version" link, I cannot verify through the md5sum because I did not note down what it was, and today there is probable a different MD5. :(

---

### Post by SkullTraill on 2010-04-14
Please note
============

I am trying to install Ubuntu onto an External USB Hard Disk SO please advice should be specific to that.

---

### Post by kansasnoob on 2010-04-14
What operating systems do you currently have installed?

---

### Post by SkullTraill on 2010-04-14
Only Windows 7 and XP.

---

### Post by kansasnoob on 2010-04-14
OK, when you first boot the Live CD you'll see a screen with a keyboard emblem and a human emblem, that means human action is required to see the menu, so press any key.

That should allow you to select language and then bring up a menu with options like shown here:

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

Select "Check CD for defects". It takes several minutes to run.

I'll post more later.

---

### Post by kansasnoob on 2010-04-14
If the Live CD passes the integrity test without errors then go back to the menu again and select "Try Ubuntu without changes" from the menu. That will allow you to see if Ubuntu is going to run on your hardware and also to see how Ubuntu recognizes your drives/partitions.

If you're able to run the Live Desktop then go to System > Administration > Gparted. As you can see in the following screenshot I've "toggled" the little "window" in the upper right hand corner which shows all drives:

[ATTACH]153243[/ATTACH]

It's important to know how Ubuntu recognizes your drives and/or partitions, like my drives are /dev/sda and /dev/sdb. You can usually tell by that which drive is which either by size or what's already installed on the drive.

Once you know how Ubuntu recognizes the drive you at least know "where" you want to install :)

More to follow.

---

### Post by gastly on 2010-04-14
> **SkullTraill said:**
> 
I did a direct download. And hmm.. I will also investigate this "Startup Disk Creator" got a link that points me to it?


It's located in System->Administration->Startup Disk Creator
or you can use UnetBootin (it's in the repositories), it does the same thing.
Here's a link for more information: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by wilee-nilee on 2010-04-14
> **kansasnoob said:**
> If the Live CD passes the integrity test without errors then go back to the menu again and select "Try Ubuntu without changes" from the menu. That will allow you to see if Ubuntu is going to run on your hardware and also to see how Ubuntu recognizes your drives/partitions.

If you're able to run the Live Desktop then go to System > Administration > Gparted. As you can see in the following screenshot I've "toggled" the little "window" in the upper right hand corner which shows all drives:

[ATTACH]153243[/ATTACH]


It's important to know how Ubuntu recognizes your drives and/or partitions, like my drives are /dev/sda and /dev/sdb. You can usually tell by that which drive is which either by size or what's already installed on the drive.

Once you know how Ubuntu recognizes the drive you at least know "where" you want to install :)

More to follow.

Good stuff, also OP make sure you under stand the placement of grub and the MBR with a external usb HD before you install. Chances are if you run the live CD to load Ubuntu onto the external that you will have to set the grub load in the last gui of install.

---

### Post by SkullTraill on 2010-04-15
Thank you VERY much [kansasnoob]("http://ubuntuforums.org/member.php?u=554595"). You gave some GREAT tips.
But I amready installed 8.10 onto it, and I know the process, I think it was a CD defect, so I think I can upgrade from 8.10 > 9.10 > 10.10 When it comes out right? If I can't do that, then I'll wait for the Full Version of 10.10 to come out, and then install it ;)

---

### Post by SleeplessCDN on 2010-04-16
> **SkullTraill said:**
> But I amready installed 8.10 onto it, and I know the process, I think it was a CD defect, so I think I can upgrade from 8.10 > 9.10 > 10.10 When it comes out right? If I can't do that, then I'll wait for the Full Version of 10.10 to come out, and then install it ;)

I am quite a newbie at using Ubuntu but I don't think you can update it like that unfortunately. I believe that you have to update like this: 8.10 > 9.04 > 9.10 > 10.04 unless they have changed the distro upgrading system lately. If I am incorrect then please post information to correct me as I very well could be mistaken, I am still confused about what to do with the programs which I installed for my previous distro and how they will interact with the new distro so each time a new distro comes out I burn the new one on a CD, delete my old distro and then install the new one, a lot more work but this way I know I won't have any problems with any programs I might have forgotten to remove prior to upgrading to a new distro and avoiding any possible errors it may cause.

Hope this helps, good luck and keep us informed. =o)

---

### Post by Sub101 on 2010-04-16
> **SkullTraill said:**
> Thank you VERY much [kansasnoob]("http://ubuntuforums.org/member.php?u=554595"). You gave some GREAT tips.
But I amready installed 8.10 onto it, and I know the process, I think it was a CD defect, so I think I can upgrade from 8.10 > 9.10 > 10.10 When it comes out right? If I can't do that, then I'll wait for the Full Version of 10.10 to come out, and then install it ;)

Do you mean 10.04?

If you do not intend on doing every upgrade then I would suggest you stick with the .04's (9.04, 10.04 etc) as they are the long term releases.

---

