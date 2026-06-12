---
title: "Install dual-boot w/XP"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by leaded on 2006-06-01
I've searched the web a little bit and this forum too and haven't found an answer to my question. How do I set up Dapper to dual-boot with an existing Windows install? My lack of an answer leads me to believe that the Dapper install will detect the Windows partition and install Grub and configure it appropriately. Is there any reason for me to be wrong here?

I saw that there's an install option of "Resize partitions automatically" or something similar, but I'm going to be using GParted first and then Install; if I choose a Manual disk configuration during install, will it still detect my Windows partition?

How does this affect the "Diagnostic" partition that came with my Vaio?

Thanks in advance!
-Alan

---

### Post by michaeljb2005 on 2006-06-01
[QUOTE=leaded]I've searched the web a little bit and this forum too and haven't found an answer to my question. How do I set up Dapper to dual-boot with an existing Windows install? My lack of an answer leads me to believe that the Dapper install will detect the Windows partition and install Grub and configure it appropriately. Is there any reason for me to be wrong here?

I saw that there's an install option of "Resize partitions automatically" or something similar, but I'm going to be using GParted first and then Install; if I choose a Manual disk configuration during install, will it still detect my Windows partition?

How does this affect the "Diagnostic" partition that came with my Vaio?

Thanks in advance!
-Alan[/QUOTE]

When I tried to dual boot on my dell, with a diagnostic utility on a seperate partition at the beginning of the disk it did not list my XP partition at all in grub and I had to add it manually (which isn't hard, there's a guide for it somewhere around here).  But when I tried to add it manually it didn't work correctly because of the diagnostic partition at the beginning of the disk.  In the end I believe it didn't work because the windows partition was unbootable after gparted did it's dirty work.  It would, however, amusingly enough boot to the diagnostic utility, go fig.

---

### Post by leaded on 2006-06-01
So using the desktop CD's GParted is going to kill my XP partition?!?

---

### Post by Zdravko on 2006-06-01
No, I managed it to work flawlessly with XP. Now I have a dualboot system Dapper-WinXp. It just works!

---

### Post by leaded on 2006-06-01
HELP!!!!

I just set up GParted (LiveCD) to resize NTFS/Windows and create some logical partitions for windows and everything froze! What should I do!?

---

### Post by michaeljb2005 on 2006-06-01
[QUOTE=leaded]HELP!!!!

I just set up GParted (LiveCD) to resize NTFS/Windows and create some logical partitions for windows and everything froze! What should I do!?[/QUOTE]

Restore your MBR for windows xp and see if xp will boot, if not then you have two options.  Chances are not all the data on your original partition were lost.  If you desperately need something off there create a seperate partition for ubuntu then install.  Make sure in the setup you have it mount the drive containing windows (or whatever's left) and try to get the data off there after rebooting into ubuntu.  If you don't need any data on there then delete all partitions on there and install ubuntu and just use that.  If you want windows on there (and don't need any data from the drive) then delete all partitions and create two new ones, one for windows, one for ubuntu.  Don't install ubuntu yet, just use the partitioner.  Then reinstall windows on the first partition.  After that install ubuntu on the other and make sure to add windows to grub manually if it doesn't do it automatically.

---

### Post by jurij20 on 2006-06-01
I'm an Ubuntu newbie, but I've learned that it's important to defrag your XP partition (several times) before installing your dual boot with Ubuntu. Have you done so ? I´ve found this link very helpful on this subject: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  Forgive my ignorance if you already have followed these steps before installing Dapper.

---

### Post by Herman on 2006-06-01
1) Three Linux keyboard sequences for dealing with a frozen machine are here in) this Wikipedia link:  [Raising Skinney Elephants  I s Utterly Boring]("http://en.wikipedia.org/wiki/Raising_Skinny_Elephants_Is_Utterly_Boring"). 
> HELP!!!!
I just set up GParted (LiveCD) to resize NTFS/Windows and create some logical partitions for windows and everything froze! What should I do!? These are not quite the same as CTRL + ALT + DEL, which also work when used prior to booting. Normally a freeze-up of GParted Livecd should have no effect on the rest of your computer. Just re-boot and try again.
Regards, Herman. :D

> I've searched the web a little bit and this forum too and haven't found an 2) answer to my question. How do I set up Dapper to dual-boot with an existing Windows install? My lack of an answer leads me to believe that the Dapper install will detect the Windows partition and install Grub and configure it appropriately. Is there any reason for me to be wrong here?
 My old /hermanzone website is for 'Breezy Badger', it is out of date and obsolete now, GParted should be able to defrag Windows, but the older installer didn't have that functionality. Thanks anyway, jurij20, for recommending my site though. 
[LEFT][COLOR=Black][COLOR=#3333ff]**For help with Dapper Drake 6.06 install from the new Dapper Live/Install CD, I recommend Aysiu's website, [http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php") and in particular, this page, [http://www.psychocats.net/ubuntu/windowstoubuntu.html]("http://www.psychocats.net/ubuntu/windowstoubuntu.html")**[/COLOR]
[/COLOR] Regards, Herman. :grin:
[/LEFT]

---

### Post by AEngineer on 2006-06-01
I have a similar question.  I carefully prepared partitions after my windows partition on my harddrive - \ swap and \home - and apparently installed KUbuntu with no problems.  There was no message or dialog box about GRUB, just a request to reboot.  When I did so I came up in Windows with no options to choose KUbuntu.

Can anyone point me to advice on how to get it dual-booting?

Jim M.

[QUOTE=leaded]I've searched the web a little bit and this forum too and haven't found an answer to my question. How do I set up Dapper to dual-boot with an existing Windows install? My lack of an answer leads me to believe that the Dapper install will detect the Windows partition and install Grub and configure it appropriately. Is there any reason for me to be wrong here?
[/QUOTE]

---

### Post by snoops on 2006-06-01
Hi AEngineer.. Seems a few people are having that issue - I setup this little thread [http://ubuntuforums.org/showthread.php?t=186232](http://ubuntuforums.org/showthread.php?t=186232) 

Do you have a sata drive?

---

### Post by leaded on 2006-06-01
I did a hard reboot of the machine and XP booted. It wanted to do a disk scan or whatever so it must've at least resized the NTFS partition. I didn't have time to check it because I was late for my train.

I used Hiren's Boot CD to copy the HD->Image file on a USB drive with Ghost, so I have a backup. HBCD also has PartitionMagic on it or something similar, so if GParted freezes again I'll try PM. (I know HBCD probably isn't legal but we have site licenses for Ghost and PM, so it just saves me from locating the CDs in the Software closet!)

snoops; I'm trying it with a laptop, but it could be SATA inside. I have some free time again at work tomorrow so I'll try again and report back. Oh, and it might not've helped that I had RC1 and not the final disk. I'll try with final tomorrow :)

---

### Post by Herman on 2006-06-01
> I have a similar question. I carefully prepared partitions after my windows partition on my harddrive - \ swap and \home - and apparently installed KUbuntu with no problems. There was no message or dialog box about GRUB, just a request to reboot. When I did so I came up in Windows with no options to choose KUbuntu.
Can anyone point me to advice on how to get it dual-booting? Well GRUB is a very intelligent bootloader as well we a boot (loader) manager. Normally, it automatically configures itself, unlike some other bootloaders.

However, in a small minority of instances, it needs some help from the user.
Unlike any other bootloader, GRUB features a command line, and can be used to search for and boot any Linux kernel. Click [HERE ]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")to find out how.
When you are using GRUB's command line to boot with, record your commands, and once Ubuntu is booted, you can edit your /boot/grub/menu.lst file with the same correct commands you used for the command line.

Booting Windows from GRUB's command line is also mentioned further down that link. Windows is the more common operating system for GRUB not to be able to find automatically. It is a wise precaution to make yourself a [GAG Boot Manager]("http://gag.sourceforge.net/") CD or floppy disk before a Linux install. [Here's my webpage about using GAG]("http://users.bigpond.net.au/hermanzone/p12.htm").
GAG helps take a lot of the stress away from a Linux install when people might really need their Windows system to always be bootable, until any initial temporary GRUB problems can be corrected, normally by manually editing /boot/grub/menu.lst
Regards, Herman :D

EDIT: If you mean you aren't even getting a GRUB menu on boot-up (Grub has completely failed to install) you should be able to install GRUB by one of these older out-of-date methods.You should still be able to use an old 'Breezy' install CD for this, or any Ubuntu Live CD should work if you choose one of the 'LiveCD' methods to re-insall GRUB.[Re-installing GRUB ]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29")   |     [  Swiss2K thread]("http://www.ubuntuforums.org/showthread.php?t=114332")    |     [Arnieboy thread]("http://ubuntuforums.org/showthread.php?t=76652")   [vnbuddy2002 thread]("http://www.ubuntuforums.org/showthread.php?t=24113")

---

### Post by confused57 on 2006-06-01
[QUOTE=Herman]1) 

 My old /hermanzone website is for 'Breezy Badger', it is out of date and obsolete now, GParted should be able to defrag Windows, but the older installer didn't have that functionality. Thanks anyway, jurij20, for recommending my site though. 
[/QUOTE]

Wouldn't your site still be appropriate using the "text installer" on the alternate Dapper CD?

---

### Post by Herman on 2006-06-01
>  Wouldn't your site still be appropriate using the "text installer" on the alternate Dapper CD? If the alternate Dapper CD's text installer is very similar to the 'Breezy' installer it might be okay. I'll download one shortly and test it out. I have a new job that means I have had just enough time to work, eat and sleep lately, so I'm a little behind on the latest events here. 
This weekend I might be able to get more up to date, and if it is needed, I will try to get my website updated as much as I can too. 
I'm not certian yet whether there will be differences that might mislead people and cause them some trouble if I recommended my website for Dapper installs too soon. I need some time to check and make sure it's all suitable.
likely it will need to be updated one page at a time.
Have you tried out the text based installer already, confused57? And do you think the installer is reasonably similar to Breezy, or dis-similar?
Regards, Herman

---

### Post by catlett on 2006-06-01
[QUOTE=Herman]If the alternate Dapper CD's text installer is very similar to the 'Breezy' installer it might be okay. I'll download one shortly and test it out. I have a new job that means I have had just enough time to work, eat and sleep lately, so I'm a little behind on the latest events here. 
This weekend I might be able to get more up to date, and if it is needed, I will try to get my website updated as much as I can too. 
I'm not certian yet whether there will be differences that might mislead people and cause them some trouble if I recommended my website for Dapper installs too soon. I need some time to check and make sure it's all suitable.
likely it will need to be updated one page at a time.
Have you tried out the text based installer already, confused57? And do you think the installer is reasonably similar to Breezy, or dis-similar?
Regards, Herman[/QUOTE]
Your site will always be in my signature. It is the bible. Just to add, when I installed the beta 6.04 it had a text installer just like the Breezy i.e. compatable with your how to. I hope you will update. If you don't have much time maybe just keep it a guide for text install in dapper and leave the live cd gui to Aysiu.
P.S. I hate the espresso installer. No options at all. Terrible. There are all these issues with grub because it doesn't prompt you to let you choose where to install it or to let you overview it's other os detection.
Glad to see you around. I was a greenie when you were active and ruled the how tos with your site:-D .

---

### Post by Herman on 2006-06-01
Thanks, catlett. Don't worry, I won't delete the site, but some of the most important parts of it might be out of date for a while.
It might be okay for a rough guide for those who have some experience already, but I would hate to see any new users who might be installing Ubuntu for the first time rely on it too much and possibly get into any kind of difficulties.
>  maybe just keep it a guide for text install in dapper and leave the live cd gui to Aysiu. Yes, that's a good idea, it's probably what I will do, Aysiu has done an excellent job on presenting the new caffiene installer. 

I'll download b2e9120f06d70cc076c1852c6c04654e ubuntu-6.06-alternate-i386.iso shortly and start experimenting with it, and see what needs to be done. :D
Regards, Herman

---

### Post by Christopher on 2006-06-02
Not sure if this is the correct place, but im going to install the NEW Dapper 6.06. The question i have is this, When i installed XP i made 2 partitions 1 for Ubuntu v5.10 and 1 for XP. Now do i just boot to my Dapper 6.06 CD and delete v5.10 and then install it onto that partition? Or will that mess up my boot file and not be able to access XP at all?  Thank you for your time.

---

### Post by Zdravko on 2006-06-02
[Christopher]("http://ubuntuforums.org/member.php?u=78619"), I got it working - dual boot : Ubuntu 6.06 and WinXP. While installing Dapper just use the partition application -  you will have to delete the 5.10. partitions, and then reformat them. The interface may seem a little confusing though.

---

### Post by Christopher on 2006-06-02
[QUOTE=Zdravko][Christopher]("http://ubuntuforums.org/member.php?u=78619"), I got it working - dual boot : Ubuntu 6.06 and WinXP. While installing Dapper just use the partition application -  you will have to delete the 5.10. partitions, and then reformat them. The interface may seem a little confusing though.[/QUOTE]

Ok so this wont mess up my XP partition then, by this i mean not allowing me to boot into at least windows?

---

### Post by catlett on 2006-06-02
A new grub will be installed that will let you to boot into XP. The old one will be written over.

---

### Post by Christopher on 2006-06-02
[QUOTE=catlett]A new grub will be installed that will let you to boot into XP. The old one will be written over.[/QUOTE]

Very nice, thank you for the quick reply.;)

---

### Post by leaded on 2006-06-04
Are there any workarounds for SATA issues? My laptop cannot get through the installation process on the LiveCD without freezing at some point, and I think the HD is SATA, but I'm not sure. Should I try the Alternate CD? Can I get the same end result of having Gnome and thelike by using the Alternate CD vs the regular Live CD?

---

### Post by leaded on 2006-06-06
Back to the XP thing, I got Ubuntu to install using the Alternate CD and it prompted me about adding Windows to Grub. I also chose to install Grub to the MBR. After I did that, Windows wouldn't boot without giving me an error shortly after showing the XP Logo. I'm assuming that Grub should *not* be installed to the MBR, right?

---

### Post by rcarring on 2006-06-07
Just a word of caution, placing non-dos logical drives in an extended partition may lead to problems.

Since you can have four primary partitions on a hard disk, I would tentatively suggest that the swap and fat32 partitions are made primary.

1 == win xp
2 == linux root and boot
3 == swap
4 == fat32 drive

A further suggestion:

1 == win xp
2 == fat32 data
3 == linux root
4 == swap

Win Xp should see four partitions, two of which it will see as ext3 and ext5 respectively.

At the point that the fsdriver to r/w to ntfs is working well enough to be trusted then the fat32 partition can be converted to ntfs.

In addition should Linux become corrupt it can be deleted and reinstalled.

One final pointer which i don't think anyone has picked up on, you can MOVE Documents & Settings for your user profile to another drive, so you could move it to the fat32 partition and thus be able to see/read /use said files under Linux.

---

### Post by catlett on 2006-06-08
[QUOTE=leaded]Back to the XP thing, I got Ubuntu to install using the Alternate CD and it prompted me about adding Windows to Grub. I also chose to install Grub to the MBR. After I did that, Windows wouldn't boot without giving me an error shortly after showing the XP Logo. I'm assuming that Grub should *not* be installed to the MBR, right?[/QUOTE]
grub installs to the mbr with no problem. that shouldn't effect you xp boot. it is in the first 512bytes of the drive (or something like that) and that's it, The info that is being used to boot your xp isn't in the grub area.grub passes the boot process to that windows area that completes the boot.
Do you have your windows partition mountged? If so can you see all the windows folders in the files? If they are there than windows is there.
You can restore your xp mbr and then reinstall ubuntu. Next install choose to put grub on a floppy (you can only get this option with the alternate install cd)
This way XP will boot when you start your computer normally. If you want Ubuntu, put the floppy in and start your computer. It will boot to the floppy and grubs menu will come up.
To get your windows mbr back get your windows install disk or your recovery disk from your computer maker. When you boot to the cd you will be given the option to boot to a recovery mode (usually by entering "R") When you get to a command prompt enter ```
fixmbr
``` This will rewrite the mbr with windows' boot loader. 
It is easier to run the install again than to explain how to install grub to a floppy before you change the mbr with "fixmbr". Since you have just installed, re-install.
About the partitions, you only have to worry aboput your primary partitions NOT exceeding 4. As long as windows is on a primary partition and you have under 4 primary partitions total, XP and grub can boot without a problem as well as any linux distro you have.

P.S. If the windows files aren't there or you can't boot once you change the mbr post. I reread the post and it says you have a backup. You mat have to reformat and install your windows backup and then reinstall dapper. Not a big deal but post so we can help you set up your drive.

---

