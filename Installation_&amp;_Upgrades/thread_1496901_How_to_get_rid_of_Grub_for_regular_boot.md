---
title: "How to get rid of Grub for regular boot?"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by freesparks on 2010-05-29
Hello all,

    I have a minor problem.  Upon getting ahead of myself after having successfully installed Ubuntu 10.04 on an external USB hardrive.  I thought it would be appropriate to get the jump on another Linux derivative-Debian.  Unaware of how unfriendly Debian's installation is in comparison to Ubuntu's, I took the same goal in trying to install Debian on a different external USB harddrive.  However, upon doing this, not only am I no longer able to just boot into Windows upon powering my laptop if the external USB drive that I have Debian installed on, but now instead I have to have the USB drive attached to my laptop in order for me to be able to choose whether or not I want to boot into Debian, or Windows XP.  In another words, if the external USB harddrive that I have Debian installed on is not connected, I get an error from Grub, the system doesn't start like before.  Based on what I am learning, Grub seemed to have taken over as primary in terms of the boot sequence.  And, regardless whether or not I go into the bios and specify that I want to boot from IDE DVD blah blah, instead of my external USB harddrive, I am not able to boot into Windows XP by just letting the system run.-------AGAIN-I have to have the external USB harddrive that I installed Debian on attached in order for it to let me specify that I want to boot into Windows XP.  My question at this point is how to I get rid of the Grub?  I desperately don't want to interefere with my Windows installation which is installed, on the laptops internal harddrive.  I simply want to get rid of Grub so I can boot normally without having to have the external USB harddrive connected.  Any help on this would be greatly appreciated.  And, no I did not back up my system, nor did I clone the external harddrive so I can't revert to how my system was prior to all of this. Again, any help would be greatly appreciated.

Best Regards,

freesparks

---

### Post by freesparks on 2010-05-29
I guess what's interesting is, in the Debian install there is no advanced prompt that lets you specify where exactly to install GRUB, so with that being said, instead of installing GRUB on /dev/sdb or /dev/sdb1--, this is the part of the install that always confuses me, this allowed the installer to install GRUB whereever the most logical place on the internal harddrive is.  Where as before, when I would install Ubuntu on an external harddrive, there was a portion of the installation where you were able to specify where the boot loader was to be installed i.e. for example, hd(0), /dev/sdb, or /dev/sdb1, etc.  Again, any help on this would be greatly appreciated.  I consider this a good mistake because I am still able to boot into Debian and boot into Windows XP.  However, in order to do this, I have to have the USB exernal harddrive installed that I have Debian 5.04 installed on.

Best Regards,

freesparks

---

### Post by bildr on 2010-05-29
boot from livecd and reinstall grub to sda

---

### Post by freesparks on 2010-05-29
Hello bildr,

    Would you mind expounding on how to go about doing this, I know how to reboot into the livecd, but what do I do once the CD is loaded, and how do I skip all those prompts before i get to the portion of specifying where to install GRUB??  Thank you so much for the quick reply, just need some detail.  I just don't want to do anything that would compromise my Windows XP partition, which is located on sda.

Best Regards,

freesparks

---

### Post by confused57 on 2010-05-29
> I desperately don't want to interefere with my Windows installation which is installed, on the laptops external harddrive.
Did you mean the laptop's internal harddrive?  If so, you might want to take a look at this tutorial for Ubuntu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

If you want to continue using Debian on the external drive, you could install grub to the mbr of the drive:
```
su
grub
find /boot/grub/stage1
root (hdx,y)<---substitute x,y from the results of the previous command, then
setup (hdx)
quit
```
This should set up grub on the external drive's mbr.  Then if you still have Ubuntu on the other external drive, you could boot into it & run the part of the tutorial for installing lilo to the laptop's (internal?) drive.

Also, if you're running Windows 7 or Vista & don't have an installation disc, you might want to download a Rescue Disk:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
You might want do this, before doing anything else I've mentioned previously.

An even better idea, might be to download a copy of Super Grub Disk:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

Added:  Just saw your post that you have Windows XP, I would recommend Super Grub Disk to repair your internal(?) drive's mbr.

---

### Post by freesparks on 2010-05-29
Yes, so sorry, I did mean internal harddrive.  Just typing faster than I am thinking.  i am going to give your commands a try now.... Thank you so much, I will let you know how i fair out..  This is an awesome learning exercise.

Best Regards,

freesparks

---

### Post by bildr on 2010-05-29
wait disregard the previous post

you did install grub to sda, it can't find the grub conf without the usb plugged in.

either shrink your windows partition so you can put the grub config on a little partition at the back, or use windows recovery console to fdisk /fixmbr /fixboot

then you would need to install grub to the USB mbr

---

### Post by freesparks on 2010-05-29
Hello bildr,

I prefer to use the windows recovery console to fdisk /fixmbr /fixboot.  Would you be so kind to explain to me step by step how to do this?  Just nervous cause Windows as you may know is very temperamental, and I don't want to screw it up.

Best Regards,

freesparks

---

### Post by confused57 on 2010-05-29
bildr's suggestion would be the best choice & I think this is what he was referring to:
[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

You'd need an XP installation cd, not a recovery disk.  If you don't have a installation disk, Super Grub Disk would be your next best option.

---

### Post by freesparks on 2010-05-29
Hello confused57,

   I cant thank you and bildr enough for the steady replies.  I just am reading now about Super Grub Disk.  I think I'm just gonna wait it out until I get my Windows XP install disk back.  Not that I don't trust Super Grub Disk.  I'm just really nervous about this overall and don't want to screw up the system.  I've got so much crap on it as it is.  Any explanations with pitfalls to avoid and somewhat detail instructions would be more than appreciated.  You guys have helped me more than enough already.

Best Regards,

freesparks

---

### Post by confused57 on 2010-05-29
Glad to help, I can understand your apprehension concerning Windows, I had the same concerns when I first started using Ubuntu & not wanting to affect Windows.  Read some more on Super Grub Disk, but use what you're more comfortable with.

The biggest pitfall that you would definitely want to watch out for when repairing your mbr is NOT to install to a partition(e.g. /dev/sdb1), but to the mbr(e.g. /dev/sdb).  As long as you don't place a partition number after the drive designation, you should be OK.

Here's the pertinent section for repairing Window's mbr, using SGD:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#boot_windows](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#boot_windows)

---

### Post by freesparks on 2010-05-30
Very strange, I booted with an XP disc that I had, typed r to initialize the repair process.  Then i got the C:/\whatever prompt, typed
fixmbr

, and got no response from the system.

Rebooted from Grub to check on XP and if it would still boot, and it did.  

It did not ask me to logon during the install process, it just went straight to the C:/ prompt with blinking cursor!!

The only commands that the repair disc prompt reacted to were exit, and help,,..Nothing else..

---

### Post by darkod on 2010-05-30
Did you manage to get XP bootloader back on the int disk MBR or not?

There is also command to do it from ubuntu, so you can repair it that way too.

---

### Post by freesparks on 2010-05-30
Hello darko, 

  Can you explain to me how to do it from Debian?  The repair disk option as I stated above your post, is not responding to my command !!

Best Regards,

freesparks

---

### Post by darkod on 2010-05-30
Not sure for Debian, and I don't want to speculate with commands, but I know from ubuntu. You can use it from either a hdd installation of ubuntu, or the cd booted in live mode.

Depending on which disk you want to put a generic MBR, lets say it's /dev/sda (if not change in the second command accordingly):

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warning it will give. It's better to run this from live mode, even if you can boot into your hdd ubuntu.

That will install generic MBR on disk /dev/sda calling the boot flag for boot. As long as your windows boot files are OK, windows should boot fine.

---

### Post by confused57 on 2010-05-30
freesparks,
   You're in good hands with Darko, but I wanted to mention if you want to try reinstalling Debian after you get your Window's mbr repaired, I think the Debian installer is similar to the Ubuntu alternate install cd.  I think it was when I installed Debian etch a few years ago and near or at the end of the installation, it asks if you want to install grub to the mbr.  Here you need to select "No", then the installer will direct you to a new screen where you would type in "/dev/sdb"(without quotes) to install grub to the 2nd drive's mbr.  The other instructions I gave you from one of my previous posts may work.

If you use my previous instructions & it works, when the Debian grub screen appears, press "e", change the root from (hd1,0) to (hd0,0), press "Enter",  then press "b" to boot. Then you can make changes permanent in your /boot/grub/menu.lst.

---

### Post by freesparks on 2010-05-30
hello confused57,
 
  That is exactly it, I have not gotten the MBR on the Windows internal hard drive to work.  I booted from the Windows XP Professional CD, it loaded and the option came up to where I specifiy that I want to repair the disk by hitting r, I hit r on the keyboard, it loads the black screen prompt which lists C:/ with the blinking cursor, I type fixmbr and hit enter and nothing happens, I then proceed to type help to see a list of the commands and that works, and I see FIXMBR as one f the commands that I can use.  The only this that the Windows XP Repair Disk Console seems to respond to are HELP, and EXIT.  Nothing else seems to work.  My question now is where to  enter the commands when I want to fix the MBR in Windows by using the Ubuntu/ Debian cd booted in live mode? And in what order should I execute them in the Debian live mode since I cant use Ubuntu and the Windows XP Repair Console is not responding to my fixmbr command.

 
Best Regards,
 
freesparks

---

### Post by freesparks on 2010-05-30
Hello all,
 
    In other words, I just want to know if I can boot in live mode using my Debian CD, or do I just press e when the Grub prompt launches at boot, and execute these commands:  instead of 
 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
 
I type instead:
 
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
 
--I replace sda with sdb since I want to install Grub on the USB external harddrive and not on the USB internal harddrive, since I want XP to have priority to boot first.  But I still havent fixed the MBR on Windows XP!!
 
Best Regards,
 
freesparks

---

### Post by darkod on 2010-05-30
Hold on, those commands are to install generic MBR on your internal disk, as you wanted. You just use the lilo bootloader but only to install the generic MBR, not the full bootloader. This is because your XP cd didn't work.

Those commands will not install grub/grub2 to the usb hdd if you use /dev/sdb. The commands to reinstall grub2 are different.

Besides, are you using XP + Debian, or XP + Debian + Ubuntu?

---

### Post by confused57 on 2010-05-31
Do you have an Ubuntu 10.04 live cd or still have 10.04 installed on your other external drive, in order to run the commands darkod suggested?

I think Debian 5.04 Lenny uses grub2, so what I mentioned previously wouldn't work. You would have to run:
```
su
grub-install /dev/sdb
```
This would install grub to the mbr of the Debian external drive...to determine the designation of your external drive:
```
sudo fdisk -lu
```

Have you read anymore on what Super Grub Disk is capable of?  It can be an indispensible tool for anyone with Windows or Linux boot problems.

---

### Post by freesparks on 2010-05-31
OK,  Yes I still have access to the Ubuntu 10.04 CD!!

   I have Ubuntu 10.04 installed on its own USB external harddrive,  I also have Debian installed on its own USB external harddrive.  When I have the Ubuntu installed via USB to the laptop unless I go in the laptops bios to specify that I want the USB external harddrive to boot from I get the GRUB2 error asking for the Debian USB external harddrive to be attached to the laptop.  All I want to do is restore how I had my system prior to where, no matter what, XP would boot first unless I went in the laptops bios and specified the USB external harddrive to boot first.  All I need to know now is after I boot from the Ubuntu 10.04 CD, what do I do and what is the best thing to do first?  Since Window XP's recovery console's command line isn't responding to my fixmbr command, where does that leave me other than Super Grub Disk.  Also, this is what I get when i just have only the USB external harddrive with Ubuntu 10.04 installed on it attached to the laptop via USB, and i run from ubuntu's terminal:
```
sudo fdisk -lu
```

I then get this:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   221841584   110920761    7  HPFS/NTFS

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a37e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     1953791      975872   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2         1955838   466794495   232419329    5  Extended
/dev/sdb3       466800705   975386474   254292885   83  Linux
/dev/sdb5         1955840   119140351    58592256   83  Linux
/dev/sdb6       119142400   236326911    58592256   83  Linux
/dev/sdb7       236328960   275388415    19529728   83  Linux
/dev/sdb8       275390464   353513471    39061504   83  Linux
/dev/sdb9       353515520   402341887    24413184   83  Linux
/dev/sdb10      402343936   431638527    14647296   83  Linux
/dev/sdb11      431640576   451170303     9764864   83  Linux
/dev/sdb12      451172352   466794495     7811072   82  Linux swap / Solaris

```

So, in short, I just want to get rid of Debian's Grub and have it boot like my Ubuntu USB external harddrive booted, prior to me installing Debian and not specifying that i wanted it-Debian-installed on /dev/sdb, so that it-debian- would not interfere with the way that Windows XP's MBR would boot first and not Debian..

Thank you so much guys for all the help.  I am learning tons!!

Best Regards,

freesparks

---

### Post by darkod on 2010-05-31
OK, lets split the process in two stages. If I understand correctly, you want Debian's Grub2 gone from the int hdd so it doesn't give you grub error when the ext hdd is dicsonnected. And after that the second task would be to install Debian's grub2 to the MBR of its ext hdd otherwise you can't boot it.

So, like I previously said, to get rid of grub2 on the int hdd MBR, it's best to have both xt hdds disconnected, boot with the ubuntu cd in live mode and in terminal:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give you.

Reboot without the cd and the ext hdds still disconnected and you should see your XP booting. If it doesn't there is also something wrong with the XP boot files. Lets hope not.

Once you have sorted out your int hdd MBR, discuss with confused the exact commands you will need to run for Debian to install its grub2 to its ext hdd MBR. I don't know them, and they are slightly different from ubuntu.

You do have Debian cd to boot in live mode right? If not, hold on with the above because you might need to run the steps in opposite order, first to install debian's grub2 to its ext hdd, and then to restore the int hdd MBR.

---

### Post by confused57 on 2010-05-31
If you don't want to set up Debian similar to how you have Ubuntu on your external drive, you can go ahead & run the lilo commands darkod suggested.  If you do, then you'd need to install grub to the external drive's mbr before you run the commands.

I believe the commands to do this in Debian are pretty much the same as Ubuntu, but instead of sudo, you'll need to use "su" to gain root permissions. Boot into Debian on your external drive & see if Debian recognizes the drives the same as Ubuntu:
```
su
fdisk -lu
```
If the external drive is /dev/sdb, to install grub to it's drive:
```
su
grub-install /dev/sdb
```
Again, be extra cautious not to add a partition number to the drive designation when running the above command.
If there's no errors, see if it will boot the same as your Ubuntu drive.

Then as darkod suggested, disconnect your external drives, boot from the Ubuntu live cd, and run the lilo commands to restore booting into XP.

You might want to wait to see if darkod thinks this would be the best approach.

---

### Post by darkod on 2010-05-31
Yes, that was my thought too.

If you delete grub2 from the MBR with my lilo commands first, the computer will boot directly XP (we hope) and there is no easy way to add Debian grub2 to the ext hdd.

A better and easier approach is this:

- boot with the Debian ext hdd connected and do the commands to add Debian grub2 to the ext hdd MBR, as confused pointed out.
- try to boot but select to boot from the ext hdd, not the int hdd, because at this point they will boot the same so you can't make a diffeence. select to boot from ext hdd to see if the setup of Debian grub2 on it worked fine
- disconnect debian ext hdd and run the lilo commands to restore generic mbr on the int hdd

---

### Post by oldfred on 2010-05-31
I think confused57 post #5 had essentially the same instructions from meierfra.'s page:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by freesparks on 2010-05-31
Hello darkod and confused57,

    This may be something that's a walk in the park for you guys, but i can't begin to thank you guys it work beautifully and to the T.  In other words you guys rock, and most importantly I LEARNED.  Thank you so much, thank you, much gratitude.  It's really those small things like when to disconnect the drive and when to reboot with live CD that i needed help with and once done, it all makes sense because it's purely logical when you sit and give it some thought.  THIS IS TRULY LEGENDARY TECH SUPPORT//  I thank you guys,  and long live UNIX, LINUX, etc.  I'm definitely hooked!!1

Best Regards,

freesparks

---

### Post by confused57 on 2010-05-31
Good job, great that everything worked out OK, always nice to hear a success story.  I do remember how it was over 4 years ago when I first started using Ubuntu, hence my username, so I do understand your hesitancy in doing anything without fully understanding what you needed to do. I know you'll enjoy & appreciate using Ubuntu and Linux as much as I.  This forum is pretty amazing, too, friendly & knowledgable members willing to assist when they can.

---

### Post by freesparks on 2010-06-01
Hello confused57,

  Well, the machine boots just find in terms of booting with XP and Ubuntu 10.04, however I can't say the same for Debian.  I even reinstalled Debian 5.04 and installed Grub on /dev/sdb and rebooted and got this error:

```
Booting 'Debian GNU/Linux, kernel 2.6.26-2-686
root (hd1, 0)
Filesystem type unknown, partition type 0x7
kernel       /boot/vmlinuz-2.6.26-2-686 root=
                /dev/sdb1 ro quiet
Error 17: Cannot mount selected partition
Press any key to continue....._____
```

I just want to know if you know what I could be doing wrong, because as you said, I said no to the default Grub install on the Master Boot Record and went in and specified that I wanted it installed on:
```

 /dev/sdb
```

Just weird that it didn't work.  Anyway, as usual thank you for all you help and apologies in advance for posting what I consider to be a Debian inquiry on a Ubuntu forum.

Best Regards,

freesparks

---

### Post by oldfred on 2010-06-01
Partition type 7 is NTFS. Is it looking at sda1 even though all your setting seem to say sdb1?

You could post boot info script again and someone may be able to see something.

---

### Post by freesparks on 2010-06-01
Hello oldfred,

   I'm a little confused on what you mean by:
> 
You could post boot info script again 


Does this entail booting in live mode again, and running a specific script/command?
Thank you for the quick reply!!

Best Regards,

freesparks

---

### Post by oldfred on 2010-06-02
Sorry mixed up threads - I thought you had posted this once. It hsows your entire install.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.


You can run it from Ubuntu or the Ubuntu liveCD. Or many other linux liveCDs.

---

### Post by confused57 on 2010-06-02
> **freesparks said:**
> Hello confused57,

  Well, the machine boots just find in terms of booting with XP and Ubuntu 10.04, however I can't say the same for Debian.  I even reinstalled Debian 5.04 and installed Grub on /dev/sdb and rebooted and got this error:

```
Booting 'Debian GNU/Linux, kernel 2.6.26-2-686
root (hd1, 0)
Filesystem type unknown, partition type 0x7
kernel       /boot/vmlinuz-2.6.26-2-686 root=
                /dev/sdb1 ro quiet
Error 17: Cannot mount selected partition
Press any key to continue....._____
```

I just want to know if you know what I could be doing wrong, because as you said, I said no to the default Grub install on the Master Boot Record and went in and specified that I wanted it installed on:
```

 /dev/sdb
```

Just weird that it didn't work.  Anyway, as usual thank you for all you help and apologies in advance for posting what I consider to be a Debian inquiry on a Ubuntu forum.

Best Regards,

freesparks
Hi freesparks,
It looks like Debian uses (hd1,0), instead of UUID for where to find root.  Try booting into Debian, make sure the boot entry title you're trying to boot is highlighted, press "e" to edit, then change (hd1,0) to (hd0,0), then ctrl+x to boot.
I'm not sure if you need to press "Enter" between changing the root designation and pressing ctrl+x...I don't think you do.

This is a temporary change if it works, but you can make it permanent, oldfred or darkod could explain this using grub2(I'm still learning grub2, I've always used legacy-grub).

---

### Post by freesparks on 2010-06-02
Hello confused57,

   Changing (hd1, 0) to (hd0, 0) worked liked a charm.  Debian booted right up with no errors.  However, what did you mean when you said that this would only be temporary?  Do you meant that I will have to do this each time I want to boot?:

> Debian 5.0.4( lenny)
Kernel Linux 2.6.26-2-686
Gnome 2.22.3

Anyway, thank you for the pricesless resource.  It is more than appreciated.

Best Regards,

freesparks

---

### Post by oldfred on 2010-06-02
When you manually edit boot entries as you boot, it is a one time change.

You will need to copy the current entry into 40_custom,edit it, and run sudo update-grub. You also want to turn off osprober so you do not keep getting the incorrect entry. (turn it on temporarily if you ever change operating systems and want it to find the new system)

Copy from:
gedit /boot/grub/grub.cfg
Copy to & edit:
gksudo gedit /etc/grub.d/40_custom
sudo update-grub



Other changes you may want to consider:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
gksudo gedit /etc/default/grub
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by confused57 on 2010-06-02
> **freesparks said:**
> Hello confused57,

   Changing (hd1, 0) to (hd0, 0) worked liked a charm.  Debian booted right up with no errors.  However, what did you mean when you said that this would only be temporary?  Do you meant that I will have to do this each time I want to boot?:



Anyway, thank you for the pricesless resource.  It is more than appreciated.

Best Regards,

freesparks

oldfred has give you a thorough explanation & resources for editing grub2 to make the changes permanent, but in case you're using legacy-grub:

First run:
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list.
if this file is blank, you're probably using grub2.  Also you could cd to /boot/grub & see what files are there:
```
cd /boot/grub
ls
```
If the first command showed a complete menu.lst, first back it up:
```
su
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Then edit the file to show the correct boot partition:
```
su
gedit /boot/grub/menu.lst
```
Change the root designation to (hd0,0), and you'll also need to find the line with:
```
#groot=(hd1,0)
```
change it to:
```
#groot=(hd0,0)
```
This line sets the root designation when update-grub is run.

---

### Post by freesparks on 2010-06-02
Hello oldfred,

  Which current entry will I need to copy?  I am not seeing those directories you are talking about when I run:

```
gedit /boot/grub/grub.cfg
```

Nor when I run:
```

gksudo gedit /etc/grub.d/40_custom
```

I looked in my file system and did not find grub.cfg, nor did I find 40-custom.

Are those files generated upon launching some sort of script in the terminal, or must they be manually created?

Thank you for all the help!!

Best Regards,

freesparks

---

### Post by oldfred on 2010-06-02
Then I am wrong & confused57 is correct. You must have old grub (0.97).

Since you installed Debian last are you using Debian's boot loader and it must still be grub legacy.

You do not have to post boot script but because I have several (now older) versions of Ubuntu in different drives with different boot loaders, I use script regularly so I know what is where and save a copy of configuration just in case. I find script useful just to understand system.

---

### Post by confused57 on 2010-06-02
> **oldfred said:**
> Then I am wrong & confused57 is correct. You must have old grub (0.97).

Since you installed Debian last are you using Debian's boot loader and it must still be grub legacy.

You do not have to post boot script but because I have several (now older) versions of Ubuntu in different drives with different boot loaders, I use script regularly so I know what is where and save a copy of configuration just in case. I find script useful just to understand system.

I wasn't sure which grub version Debian Lenny used, even after doing a Google search; but it seems Lenny may offer a choice of which grub to install & possibly defaults to legacy-grub.
Your grub2 info will be extremely useful for freesparks with Ubuntu 10.04.

---

### Post by freesparks on 2010-06-02
Hello confused 57,
 
Thank you for pointing out which Grub version I have. I guess my question now is whether or not it's worth it to update to Grub 2, what are the advantages and disadvantages, etc? My other question is also, in your experience, which Linux version would be worth learning. All of them have the same concept, but different quirks, mostly in terms of updating, etc, and firmware issues like downloading recent drivers for wireless connections. I mean the core is all Unix, but which one in a real world environment would be beneficial to really learn in depth. For example, at work, it seems everybody leans toward Red Hat. I chose Ubuntu because it seems very mainstream. As far as Debian, I read in one of the books I'm using it is very stable, whatever that means; they all seem pretty stable, even MAC OSX which I read is based on BSD Linux. Please feel free to answer at your leisure, these are experiences and things that no book can really teach you. And, one thing I can say about open-source, GNU software is it being prone to an experienced collective. Anyway, thanks to you and oldfred, you guys have given me some amazing resources, to keep me busy for the next months.
 
Best Regards,
 
freesparks

---

### Post by oldfred on 2010-06-02
Grub2 is the future as grub legacy has not been maintained for years and each distribution made minor fixes but still called it 0.97. New systems have lots of new requirements which grub2 will meet. But if grub legacy  works, there is no pressing need to upgrade at the current time. Grub2 has a much better osprober that finds many more systems than old grub did. We usually had to manually add most entries even many windows stanzas to get windows to dual boot.

Their are still some issues with grub2 and they have made major improvements just from 1.96 to 1.98. One issue grub2 does not control is windows software writing into the MBR can corrupting grub2 because it is slightly larger than the windows boot loader (or old grub). The MBR is reserved for booting but some windows software does not follow standards.

Minor points. Linux is not Unix. It was developed totally separately to be a work alike but not based on any Unix code. BSD is Unix (not linux) as parts came from Unix and parts of the original were incorporated into Unix.

---

### Post by confused57 on 2010-06-03
> **freesparks said:**
> Hello confused 57,
 
Thank you for pointing out which Grub version I have. I guess my question now is whether or not it's worth it to update to Grub 2, what are the advantages and disadvantages, etc? My other question is also, in your experience, which Linux version would be worth learning. All of them have the same concept, but different quirks, mostly in terms of updating, etc, and firmware issues like downloading recent drivers for wireless connections. I mean the core is all Unix, but which one in a real world environment would be beneficial to really learn in depth. For example, at work, it seems everybody leans toward Red Hat. I chose Ubuntu because it seems very mainstream. As far as Debian, I read in one of the books I'm using it is very stable, whatever that means; they all seem pretty stable, even MAC OSX which I read is based on BSD Linux. Please feel free to answer at your leisure, these are experiences and things that no book can really teach you. And, one thing I can say about open-source, GNU software is it being prone to an experienced collective. Anyway, thanks to you and oldfred, you guys have given me some amazing resources, to keep me busy for the next months.
 
Best Regards,
 
freesparks

I would recommend sticking with legacy-grub on Debian, you might have problems with upgrading, and you do have grub2 on your Ubuntu installation.  I'm biased towards legacy-grub, since I'm most familiar with it, but I'm beginning to see the benefits of grub2.

As far as a stable distro, I would recommend sticking with Ubuntu for everyday usage, until you're totally comfortable with it for most, if not all, of your computing needs.  You'll learn the most when you have problems or want to install & configure various programs. The forum has an extensive knowledge base of users who can help and most of the time a quick search will find an answer.

If you ask in the Community Cafe which was the best distro to learn linux, you'd get a wide range of suggestions...Gentoo, Arch, Slackware, Linux From Scratch, etc.  I've tried all of these to some extent, but always found myself returning to Ubuntu, mainly for the reasons I've already mentioned.

As far as learning Linux, I'd mainly suggest read, read, read(take notes) as much as your time permits and try out some other distros.  Here's 2 sites I'd recommend first:
Herman's site:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Aysui's site:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Also, a list of links, some of which are broken now, that I posted way back when:
[http://ubuntuforums.org/showthread.php?t=172365](http://ubuntuforums.org/showthread.php?t=172365)

If you want to try out some other distros, you might want to set up an extra partition or 2 on your drive with Ubuntu, which you could use for as the main bootloader to boot the other distros.  First, I'd recommend you learn as much as you can about grub2 and how to restore grub to the mbr, using the Ubuntu live cd.  Oldfred or darkod have already given you several resources for this.  Any time I planned on trying a new distro, I'd do some reading on the documentation & forums so I'd have an idea of how to proceed.

If you want to try a kde distro, I've found PCLinuxOS quite user friendly. It's based on Mandriva and uses rpm instead of deb packaging.

It's been quite a while since I've "messed" with any other distros and I've rambled on enough with my musings, but this should give you a start.  Once you've become more familiar with Linux, you'll find your preferred distro & what you expect from it for your own personal use.  

Good luck and have fun!!!

---

