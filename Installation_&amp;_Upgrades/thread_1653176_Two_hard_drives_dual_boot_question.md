---
title: "Two hard drives dual boot question"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by robby631 on 2010-12-26
[SIZE=2]I had Ubuntu installed on a 500 gig SATA drive on my computer. I wanted to install Windows 7 as well. Knowing that Windows would wipe out the MBR[/SIZE], [SIZE=2]I decided to install it on a separate 250 gig SATA drive. Being extra cautious (ALL my stuff is on that Ubuntu drive!) I disconnected the 500 gig drive so that there was no chance the Windows installation would damage my Ubuntu install. Windows installed just fine.


Now, the question is, given this situation (2 operating systems installed completly independent of each other at different times), what is the best way to dual boot them? I would like Windows to still boot itself from it's own boot loader, and not add Ubuntu to it's boot menu. I would like the choices to show up in GRUB. Most advice I find on this subject pertains to installing one or another OS whith an existing one already present.


Rob:)[/SIZE]

---

### Post by oldfred on 2010-12-26
Welcome to the forums.

Yours is the best way to do it and you will want to keep each drive independently bootable.

Not sure if you have reconnected so windows is sda or sdb. When you install each system with the other drive disconnected each system has configured itself to be drive 0 (in windows ) or hd0/sda in grub/Ubuntu.

I would reconnect drives such that windows is the first drive in BIOS or sda in Ubuntu. Grub/Ubuntu uses both drive and then a search by UUID, so it will still boot as it will find the correct partition by UUID. Windows may need reconfiguration if it has changed from drive 0 to drive 1, so keeping it as drive 0 is better.

Windows will not boot Ubuntu without third party boot loaders but to get grub to find windows and let you boot it.

```
sudo update-grub
```Then in BIOS set the Ubuntu drive  as the first to boot. From grub's menu you should be able to boot Ubuntu or windows and if for any reason Ubuntu drive is not working you can in BIOS or with one time boot key directly boot the windows drive.

---

### Post by dino99 on 2010-12-26
welcome,

mainly you have to decide which bootloader you want to use to build a boot menu. ubuntu comes with grub2 (grub-pc) which is able to chainload all the OS found on your system.

[http://www.thefreecountry.com/utilities/multi-boot-managers.shtml](http://www.thefreecountry.com/utilities/multi-boot-managers.shtml)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by robby631 on 2010-12-26
[SIZE=2]Thanks for the quick replies! I went with grub2 as the bootloader, set the Ubuntu drive as the first drive in the BIOS, ran sudo update-grub, and it worked fine. I also commented out a lot of old kernel entries in the grub file, so now there is only Ubunu, Memtest, and Windows 7 to choose from. I guess I should remove the old kernels and then do another update. But, for now, I have to work on my heating system which just konked out now during the worst snowstorm for years here in the Northeast USA. I like working on computers much better.[/SIZE]

---

### Post by oldfred on 2010-12-26
If you commented out the lines in grub.cfg like you would have done with grub legacy, then on the next update everything is back. Grub2's entire file is like the area in grub legacy called automagic that got rewritten on every update. You set parameters in grub or the executables that do the updating.

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

Lots of info here:
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

### Post by gpix13 on 2011-01-14
Alright so I am looking to install Windows 7 and Ubuntu on separate hard drives (just like what is in this thread), but if I do this and want to get rid of Ubuntu or change distributions, how would i go about this? Windows 7 is my main OS and main HDD, i once made the mistake of formatting ubuntus drive while on Windows side and I couldnt boot back to windows.

Thanks

---

### Post by oldfred on 2011-01-14
As long as you keep both drives separate you will not have issues. You do need to keep track of which boot loader is in which drive. I think it is better that windows is drive 0 or sda.

Your issue before was that you did not reinstall a windows boot loader to the windows drive before uninstalling the Ubuntu partition. 

Just always have available a windows repair cd and an Ubuntu liveCD and you can easily reinstall boot loaders:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Some examples of installs and issues:
Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

---

### Post by gpix13 on 2011-01-14
Alright so if I do this and windows drive is not drive 0 or sda, how would I go about changing that?

---

### Post by gpix13 on 2011-01-14
Alright so if I do this and windows drive is not drive 0 or sda, how would I go about changing that?

---

### Post by oldfred on 2011-01-14
On my computer it is by SATA port number, but it may be by BIOS settings. If you have mixed IDE & SATA, you may not have control.

---

### Post by scooper77515 on 2011-01-14
My first post!:popcorn: But been poking around as a guest for a week.

Been doing Ubuntu and Zorin for about a week with several computers. 

Did exactly what this guy did yesterday, XP originally installed on 500G hd, then added second 500G hd for Ubuntu. Ate up my MBR and grub. Couldn't get into windows anymore, where all my stuff is. 

Got that fixed "grub rescue" and then followed the advice on this thread to get my boot menu back. Works GREAT!

Thanks!!!

---

