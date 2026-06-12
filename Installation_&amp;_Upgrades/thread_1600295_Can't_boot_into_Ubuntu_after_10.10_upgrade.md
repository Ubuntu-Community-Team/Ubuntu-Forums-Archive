---
title: "Can't boot into Ubuntu after 10.10 upgrade"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by jtomlinson on 2010-10-18
I initially installed 10.04 using the Ubuntu Windows Installer and everything was running fine. When I would boot up the computer it would first hit the Windows Boot Loader and give me the option of booting Windows 7 or Ubuntu. When I chose Ubuntu GRUB (I believe) would then load asking if I wanted to load Ubuntu or Windows 7. This was fine as it would work and that's all I cared about.

Now after running the 10.10 upgrade from within Ubuntu (not from a CD) when I select Ubuntu from the Windows Boot Loader it acts as though Ubuntu is going to load, the screen goes black and then the computer reboots itself. I would prefer to fix the problem, if possible, instead of doing a fresh install.

Any help with this would be greatly appreciated.

---

### Post by blueabysm on 2010-10-18
It seems that many people have this problem. Actually, it is better not to upgrade to 10.10 if you **installed your Ubuntu with wubi**. because there are some known bugs og wubi.

you can try to use Windows 7 CD to recover your boot menu. 

Hope helpful & Good Luck

---

### Post by bcbc on 2010-10-18
See here for workaround/possible fix [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by jtomlinson on 2010-10-18
> **bcbc said:**
> See here for workaround/possible fix [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

I found that the following did work, thanks.

[QUOTE=bcbc]PS I noticed some reports that copying c:\ubuntu\winboot\wubildr over c:\wubildr fixed the problem. It's not a guaranteed fix but has been confirmed to work for many users, and it's easy to try without using live CD. (If you installed on another 'drive' change as appropriate). Backup the C:\wubildr before trying as a precaution.[/QUOTE]

---

### Post by bcbc on 2010-10-18
Great, thanks for the feedback.

---

### Post by Iwnda0 on 2010-10-18
Ok. I started with Lucid 64 bit and upgraded to Maverik beta 64 bit. IT looked nice! I used it for a whole day and shut it down for the night. It would not start back up in the morning. I got and error: [26.360434] [drm:intel_crtc_mode_set] *ERROR* couldn't find PLL settings for mode!   and   [26.360439] [drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on crtc ffff8801185f800. I said to myself "why would you ever upgrade to beta on your only laptop with all of your belongings?" I popped back in the 10.04 LTS disc and reinstalled it as a 32bit OS, placing my old files into a partition. This partition is viewable on the desktop when mounted. I try to open it up and it looks empty. The properties say it is empty. I know it is not empty. How do I open this as root? Is that what I need to do? Help! Thank You in advance.    :confused:

---

### Post by bcbc on 2010-10-18
> **Iwnda0 said:**
> Ok. I started with Lucid 64 bit and upgraded to Maverik beta 64 bit. IT looked nice! I used it for a whole day and shut it down for the night. It would not start back up in the morning. I got and error: [26.360434] [drm:intel_crtc_mode_set] *ERROR* couldn't find PLL settings for mode!   and   [26.360439] [drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on crtc ffff8801185f800. I said to myself "why would you ever upgrade to beta on your only laptop with all of your belongings?" I popped back in the 10.04 LTS disc and reinstalled it as a 32bit OS, placing my old files into a partition. This partition is viewable on the desktop when mounted. I try to open it up and it looks empty. The properties say it is empty. I know it is not empty. How do I open this as root? Is that what I need to do? Help! Thank You in advance.    :confused:
I advise to create a new thread - I think this is unrelated and you'll probably get more help if it's separate from the wubi upgrade issue. But... since I have no idea what you may have overwritten when you reinstalled, and this might be a dirty recovery mission, I would recommend using something like [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) (it's better to run this from a live CD with an external USB to save the output - otherwise you could be trashing your data while recovering files). 

It just doesn't sound like this empty partition contains what you are looking for. Or else describe a little better how you managed to back up your data while reinstalling Ubuntu.

---

### Post by Iwnda0 on 2010-10-19
I believe I backed it up by seperating it in a seperate partition from the reinstall. Does the partition read empty for security purposes? I am stumped.

Anyway bcbc. I appreciate your help very much. I am going to try the cd-usb drive technique. Thank you thank you.

---

### Post by Iwnda0 on 2010-10-19
Anyway bcbc. I appreciate your help very much. I am going to try the cd-usb drive technique. Thank you thank you.

---

### Post by bcbc on 2010-10-19
> **Iwnda0 said:**
> I believe I backed it up by seperating it in a seperate partition from the reinstall. Does the partition read empty for security purposes? I am stumped.

No, unless it's encrypted you should be able to see the data - if you've mounted the partition, then you can also check the used space (df /dev/sdaY)e.g.:
```
df /dev/sda2
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             61866308  55986020   5880288  91% /media/10ACE996ACE9769E
```

If it looks empty, then it probably is - or else - perhaps the data is there but the inodes are corrupt. I have no idea. That's why I recommended photorec as it can pick up data files even on formatted disks.

---

### Post by Iwnda0 on 2010-10-19
> **bcbc said:**
> No, unless it's encrypted you should be able to see the data - if you've mounted the partition, then you can also check the used space (df /dev/sdaY)e.g.:
```
df /dev/sda2
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             61866308  55986020   5880288  91% /media/10ACE996ACE9769E
```

If it looks empty, then it probably is - or else - perhaps the data is there but the inodes are corrupt. I have no idea. That's why I recommended photorec as it can pick up data files even on formatted disks.
Here is what it looks like. > [IMG]http://ubuntuforums.org/home/no_name/Desktop[/IMG]

---

### Post by bcbc on 2010-10-19
> **Iwnda0 said:**
> Here is what it looks like. [IMG]http://ubuntuforums.org/home/no_name/Desktop[/IMG]

Whatever that image was - it's not displaying.

---

### Post by Iwnda0 on 2010-10-19
> **bcbc said:**
> I advise to create a new thread - I think this is unrelated and you'll probably get more help if it's separate from the wubi upgrade issue. But... since I have no idea what you may have overwritten when you reinstalled, and this might be a dirty recovery mission, I would recommend using something like [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) (it's better to run this from a live CD with an external USB to save the output - otherwise you could be trashing your data while recovering files). 

It just doesn't sound like this empty partition contains what you are looking for. Or else describe a little better how you managed to back up your data while reinstalling Ubuntu.

> **bcbc said:**
> Whatever that image was - it's not displaying.

Sorry, needed to reformat. This should work...
or
[http://i119.photobucket.com/albums/o134/iwnda0/Screenshot.jpg](http://i119.photobucket.com/albums/o134/iwnda0/Screenshot.jpg)

---

### Post by bcbc on 2010-10-19
> **Iwnda0 said:**
> Sorry, needed to reformat. This should work...
or
[http://i119.photobucket.com/albums/o134/iwnda0/Screenshot.jpg](http://i119.photobucket.com/albums/o134/iwnda0/Screenshot.jpg)

In the picture, /dev/sda2 is not mounted, so df won't tell you anything meaningful. If it's the disk saying 16K used then that's probably just the file system control blocks and index entries - no data.

Again - before you do anything just run photorec and see what it gets for you. The more you use the drive the more likely you are destroying data. I can't really advise any more as I am not a data recovery expert - but this really has nothing to with the thread and if you want to get more help you really should create a separate thread with a meaningful title.

---

### Post by Iwnda0 on 2010-10-19
> **bcbc said:**
> In the picture, /dev/sda2 is not mounted, so df won't tell you anything meaningful. If it's the disk saying 16K used then that's probably just the file system control blocks and index entries - no data.

Again - before you do anything just run photorec and see what it gets for you. The more you use the drive the more likely you are destroying data. I can't really advise any more as I am not a data recovery expert - but this really has nothing to with the thread and if you want to get more help you really should create a separate thread with a meaningful title.

OK. I will follow your instructions. Thanks again friend!

---

### Post by format_LIFE on 2010-10-27
[B]New Solution
I have windows 7 ultimate and i install ubuntu 9.04 with wubi. Everything works fine howeve i update ubuntu 10.10 and i got boot error... when i choose ubuntu from boot screen it restart the computer.. and i didnt found solution. i just find myself... follow these steps;
1-)boot linux with live CD. and open terminal type "sudo apt-get install lilo"
2-)sudo lilo -M /dev/sda mbr
3-) after then close terminal we finish with terminal
4-)Go Places->Computer->File System->host
5-) They are 2 file "wubildr" and "wubildr.mbr" copy that files.
6-) again Go [/B][B]Places->Computer->File System->host->Ubuntu->disks->boot->grup-> and paste these 2 files in here. (if you get error about permission, you should open terminal and copy these files with sudo)
7-) restart Computer and select Ubuntu... after selecting ubuntu i got error message but your ubuntu will open..:D

NOTE: in windows 7, I install ubuntu with Wubi in this directory(c:/Ubuntu).. so if you install ubuntu somewhere else you must copy these file into where you installed ubuntu...

This solution works for everyone.. i dont know.. but it works on me..;)

Good luck with your problems..:P

[/B]

---

