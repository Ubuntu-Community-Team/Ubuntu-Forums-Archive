---
title: "[SOLVED] GRUB Error 17 (then 21)"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by Finny33 on 2008-09-18
Hello.
I've read various solutions to the above errors but none of them have worked for me so I thought I'd try and see if there's an easy solution that I am missing, due to my lack of knowledge of Ubuntu and GRUB.

Basically, possibly due to a forced shutdown when the battery ran out, my laptop (DELL INSPIRON 1720 with one hard drive, originally with VISTA but now only running with Ubuntu : for the last 6 months without much bother) is no longer able to load up Ubuntu and the original error message I got was GRUB Stage 1.5, number 17.

I've tried 'grub>find /boot/grub/stage1' and got 'Error 15 : File not found'.

I've tried 'find /boot/grub/stage1' and got 'No such file or directory'.

'sudo fdisk -l' gives me :

'Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       30010       30401     3148708+   c  W95 FAT32 (LBA)
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order'

I've tried to get the menu.lst but am only getting a blank page.

I can't find a GRUB directory in my BOOT directory and am having access problems when I try to copy another version into that BOOT directory.

I've tried the SUPER GRUB DISK, and tried most of the options, and then got Error 21.

I wanted to burn a copy of the Alternative Live CD (which seems to give a 'repair' option), but can't eject the Live CD I already have running in there.

And now I'm here, having got as far as I can while still sane. 

I think the problem is to do with not being able to find the Master Boot Record but I can't work out what I can do to solve that. 
I also can't see LINUX shown in any of the devices shown above, apart from the 'swap/Solaris' bit. That doesn't seem right, having looked at other examples previously.

Can anyone point me in the right direction please, and I will provide any further info required.

Thanks in advance.

PS I don't mind if I have to reinstall everything again but I did have some photos and music that I would like to take copies of first. How can I tell if they are still on my hard drive somewhere, because I certainly can't find them while running the Live CD ?
Thanks again.

---

### Post by bcnaat on 2008-09-18
I've got a similar problem. I did find how to get to my things on the drive (mount my linux 'drive' while using the liveCD, but like you, can't remove the liveCD to burn anything.

As far as the first part of your post, I received the same error message 17 until I did mount my linux 'drive'. Still haven't had any luck in repairing grub though. It can find stage1, stage2 but for some reason it can't find the menu.lst even though its there when I do the setup part in grub.

---

### Post by Rayaz on 2008-09-18
You could  download puppy linux from [www.puppylinux.org](www.puppylinux.org) and boot from a CD or USB flash drive. That would allow you to backup your files.

---

### Post by caljohnsmith on 2008-09-18
> **Finny33 said:**
> 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       [COLOR="Red"]30010       30401[/COLOR]     3148708+   c  [COLOR="Red"]W95 FAT32 (LBA)[/COLOR]
/dev/sda2           [COLOR="Red"]29646       30401[/COLOR]     6072570    5  Extended
/dev/sda5           [COLOR="Red"]29646       30401[/COLOR]     6072538+  82  Linux swap / Solaris
```

From your fdisk output above, it looks like your partition table is really munged. Note that the extended partition sda2 overlaps the primary partition sda1. And note also the huge amount of unused space: 1-29645 cylinders, so according to fdisk, you are using less than 5% of your HDD space. Also, I doubt your linux partition, which would most likely be sda1, is really a FAT32 file system. Did you format it that way? 

I would highly recommend that you run testdisk on your HDD and see if it can rebuild your partition table correctly. If you have your Live CD, and if you can use the internet from the Live CD, just do:
```
sudo apt-get install testdisk
sudo testdisk
```
You may need to enable all your repositories in System > Prefs > Software Sources in order to download testdisk. After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen also.

---

### Post by Finny33 on 2008-09-19
> **caljohnsmith said:**
> Also, I doubt your linux partition, which would most likely be sda1, is really a FAT32 file system. Did you format it that way? 

Not that I know of ! I haven't really touched any of that stuff since I got the laptop earlier this year, and the only major change has been the installation of Ubuntu - although that did get rid of my VISTA and everything else on my hard disk. Maybe that made some sort of change that I wasn't aware of : or, at least, that I didn't realise I had agreed to ! I just assumed it would have been NTFS ?

> **caljohnsmith said:**
> I would highly recommend that you run testdisk on your HDD and see if it can rebuild your partition table correctly. 

I will certainly try this when I get home in a few hours so hopefully it will all work and I can post the results later. Thanks for the advice so far.

I will also try and download a copy of PUPPYLINUX (as recommended by Rayaz - Thanks) for possible future need.

---

### Post by Finny33 on 2008-09-19
> **caljohnsmith said:**
> After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. 

I did have screenshots of this and the following but lost them when I closed down and restarted to check whether my problem had been solved just by using the 'testdisk'. No such luck but more typing for me. This is what I got after doing the above :


Disk /dev/sda -250 GB / 232 GiB - CHS 30401 255 63
Current partition structure :

    Partition        Start     End     Size in Sectors

1 * FAT32 LBA  30009 1 1 30400 254 63  6297417 [MEDIADIRECT]
2 E extended   29645 0 1 30400 254 63  12145140
Space conflict between the following two partitions
2 E extended   29645 0 1 30400 254 63  12145140
1 * FAT32 LBA  30009 1 1 30400 254 63  6297417 [MEDIADIRECT]
5 L Linux Swap 29645 1 1 30400 254 63  12145077

> **caljohnsmith said:**
> Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen also. 


Disk /dev/sda -250 GB / 232 GiB - CHS 30402 255 63

  Partition        Start       End     Size in Sectors

D Linux          0 1 1  29644  254 63  476246862
D HPFS-NTFS      6 0 1  30008  254 63  481998195
D Linux Swap 29645 1 1  30400  254 63  12145077
D FAT32 LBA  30009 1 1  30400  254 63  6297417 [MEDIADIRECT]



Hope all this makes sense and brings me nearer to a solution.
Thanks in advance again.

---

### Post by caljohnsmith on 2008-09-19
Before we do anything to your partition table, Finny33, do you remember at all what partitions you had? Based on what you said in your original post, I'm guessing you only now have two partitions: one for the main Ubuntu install, and one for swap space. In other words, you don't have any NTFS or FAT32 partitions on your drive any more, correct?

---

### Post by Finny33 on 2008-09-20
> **caljohnsmith said:**
> Before we do anything to your partition table, Finny33, do you remember at all what partitions you had? Based on what you said in your original post, I'm guessing you only now have two partitions: one for the main Ubuntu install, and one for swap space. In other words, you don't have any NTFS or FAT32 partitions on your drive any more, correct?

I must admit that I don't know. I vaguely recollect there being 3 partitions at one stage, but whether that was under Vista or Ubuntu, I can't remember. GParted, running under the Live CD, shows just one but maybe that's just a default ? I will restart now and check the BIOS settings to see whether that tells me anything.
Thanks for your continuing help.

---

### Post by Finny33 on 2008-09-20
I have not been able to find out any more information so I hope my last reply will allow a move on to the next stage mentioned : working on the partition table.
I wonder, though : does it look as though I have lost everything I had on my hard drive previously ? Is there any way I can check ?

---

### Post by caljohnsmith on 2008-09-20
In your original post you mentioned:
> **Finny33 said:**
> ...one hard drive, originally with VISTA but now only running with Ubuntu
So I'm assuming that you only have Ubuntu on your HDD, correct? If that is true, then go ahead and run testdisk again, but this time when you go through the screens and get to:
```
[COLOR="Red"]D[/COLOR] Linux 0 1 1 29644 254 63 476246862
[COLOR="Red"]D[/COLOR] HPFS-NTFS 6 0 1 30008 254 63 481998195
[COLOR="Red"]D[/COLOR] Linux Swap 29645 1 1 30400 254 63 12145077
[COLOR="Red"]D[/COLOR] FAT32 LBA 30009 1 1 30400 254 63 6297417 [MEDIADIRECT]
```
Then select the first "Linux" partition above, and press "p" to show a directory listing of its root directory. If it shows your Ubuntu root directory OK, then use the left/right arrow keys to change its partition type from "D" (deleted) to "P" for primary. Then select the Linux swap line, and change its partition type to either "P" primary or "L" logical (it will only let you choose one of those I think based on what it was before). Leave the NTFS and FAT32 partitions as "D" or deleted, then "enter" to continue, and finally "write" to write the new partition table. 

Reboot, see if by chance Grub is working on start up, and if not, boot your Live CD and do the following:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), which in your case should be (hd0,0). If it does, then use that:
```

grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Reboot, and see if Grub works now. Let me know how it goes.

---

### Post by Finny33 on 2008-09-21
> **caljohnsmith said:**
> Reboot, and see if Grub works now. Let me know how it goes.

Fantastic ! I now have everything back as it was. Thank you very much.
I'm not entirely sure how, or what was going on with the instructions you gave (especially with regard to recovering the 'deleted' partitions) but am very grateful. I will have to try and work my way through the stages, to see if I can work out what was happening.

The only niggle now is that it is very noticeable how much better the graphics, text sizes, etc. were while I was using the Live CD, as compared to how they are now running under my NVIDAI (GeForce 8600M GT) graphics card. I wasn't too happy with how it looked previously, but got used to it.
The current screen resolution is 1280x800 and when I try to increase it to 1280x1024 the text gets a lot bigger and I can only view a quarter of the screen at a time.
Also, when I log on the laptop, the name and password boxes are only barely visible at the bottom right of the screen, as if the resolution has been turned to 1280x1024 (as above). When I get to the desktop, the resolution reverts back to 1280x800.
The Hardware Drivers screen shows the graphics card enabled and in use but the resolution, etc. suggest otherwise.

Any ideas ? Don't worry if you haven't, because this probably isn't the right forum : I will try a search to see if others have had the same problem.

Thanks again for helping me recover from the previous disaster ! :KS

---

### Post by unutbu on 2008-09-21
Finny33, I'm glad to read you are booting again.
To fix the resolution problem, perhaps take a look at
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

It has a fix for the login window problem in the section entitled "GDM uses a different Resolution than my Desktop"

It also contains instructions on how to fix most resolution problems that occur from within your GNOME session.

---

### Post by caljohnsmith on 2008-09-21
You're welcome, I'm glad you are at least past your Grub problems. About your Video concerns, are you using the Nvidia restricted driver for your card (and is it enabled in System > Admin/Prefs > Restricted Drivers)? If not, that might be a good place to start. Other than that, I'm not too experienced troubleshooting video problems, but I would definitely follow Unutbu's advice. And if that doesn't solve it, I think your best bet will be to start a new thread with that as the topic. Anyway, cheers and have fun. :)

---

### Post by lewisskinner on 2008-09-21
> **caljohnsmith said:**
> 
I would highly recommend that you run testdisk on your HDD and see if it can rebuild your partition table correctly. If you have your Live CD, and if you can use the internet from the Live CD, just do:
```
sudo apt-get install testdisk
sudo testdisk
```
You may need to enable all your repositories in System > Prefs > Software Sources in order to download testdisk. After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen also.

Hey, might this work for my problem as well?
[http://ubuntuforums.org/showthread.php?t=925877](http://ubuntuforums.org/showthread.php?t=925877)

---

### Post by caljohnsmith on 2008-09-21
> **lewisskinner said:**
> Hey, might this work for my problem as well?
[http://ubuntuforums.org/showthread.php?t=925877](http://ubuntuforums.org/showthread.php?t=925877)
It certainly can't hurt to check your partition table with testdisk to make sure everything is OK. If you want help with it, then follow the directions you quoted and post the output, and also post:
```
sudo fdisk -l
```

---

### Post by lewisskinner on 2008-09-21
thanks, tried it, continued on the [thread I quoted](http://ubuntuforums.org/showthread.php?t=925877)

---

### Post by Finny33 on 2008-09-22
> **unutbu said:**
> Finny33, I'm glad to read you are booting again.
To fix the resolution problem, perhaps take a look at
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

It has a fix for the login window problem in the section entitled "GDM uses a different Resolution than my Desktop"

It also contains instructions on how to fix most resolution problems that occur from within your GNOME session.

I have had a quick look there and it does seem to be somewhere I might be able to solve that particular problem. Thanks for the link. I have only been using Ubuntu for a few months and haven't really had a chance to check out all the 'help' and 'how-to' pages available here. Now I know, I will be looking at as many as possible !


> **caljohnsmith said:**
> And if that doesn't solve it, I think your best bet will be to start a new thread with that as the topic. Anyway, cheers and have fun.

Will do ! Thanks again for all your help.

---

