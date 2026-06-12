---
title: "Unsure how to remove Ubuntu"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by tjhans on 2012-01-07
I installed ubuntu 11.10 a while back along side windows 7 using the instructions from the ubuntu site found here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I used it for a while, and enjoyed it (mainly the faster cold boot and just getting to say i'm an ubuntu user and getting weird looks), but with time i gradually got tired of it and have now decided that for now I'm best off with just windows 7 rather than dealing with the complications of having 2 os's on one computer (more than one computer would be a different story).

The problem is I don't really know how to get rid of it with out putting my windows install at risk.  If anyone knows the safest way to take it off i would be very thankful.

---

### Post by Basher101 on 2012-01-07
first of, do you have a windows installation CD or recovery CD? if you have neither you must create a recovery CD with the windows tools in System Settings -> Backup & Restore and there on the left you click the second option. You will need to insert an empty CD-R in your drive and then you can create it following the instructions on screen.
----------------------------------------------------

After you made a recovery CD you click start, rightclick on Computer and choose the tab "manage". On the window that pops up you choose Diskmanagement. Now you should see your partitions on all hard drives.Select the drive where ubuntu is installed and simply rightclick and delete the partitions that have no name (at the top they will be no name) also no filesystem will be displayed (see screenshot)

note that you may have a swap partition. It should be equal or a bit larger than your RAM, it will also have no name. Simply delete those without a name. After you deleted them, rightlick on the partition that you shrunk before installing ubuntu to use that free space again (or make another partition for storage, its up to you).
-----------------------------------------------------

Now Ubuntu has been deleted, but there are still some remains of Grub. To get rid of those, pop in the Recovery CD you made, boot from it and choose "startup repair" when a window appears. Wait until it is done and reboot. 


Uninstall successful


regards

---

### Post by tjhans on 2012-01-07
Thank you for replying so quickly.

Okay, I have the recovery disk that was packaged with my computer, but when i look at my disk partitions, there are a ton with no names.  I am not sure how many were there before I installed ubuntu, but one at least I am sure is supposed to be there.  Here is a shot of the partition manager.  I am pretty sure I gave 100GB to ubuntu, but none are that size.

ps, is there not a tool for uninstalling ubuntu, like maybe using the install disk?

---

### Post by Basher101 on 2012-01-07
a question...did you try to install ubuntu a few times? Every time you use the automatic install it will always create a swap partition. You have 3 swap parititons (all that are 4 GB big). Those 3 and the 81 GB partition are your Ubuntu partitions. You can safeley remove all of them, except the 17 GB partition that says [COLOR="Red"]recovery partition[/COLOR]

p.s. Since your ubuntu partitions come after C: and before D: you can either enlarge your C: by those 100 GB again, or make another 100 GB partition. I would recommend the enlarging tho.

regards

---

### Post by tjhans on 2012-01-07
that makes sense, I did a re-install twice (tinkered with things and didn't know how to fix them) so that could be where the extra partitions came from.  I can't try it out right now, but ill report back soon on how it goes.

---

### Post by Basher101 on 2012-01-07
you should train custom installations in a Virtualbox so you can avoid making installs that create swap partitions over and over...

otherwise i have helped a guy that had absoluteley no idea of partitioning via remote control...he told me what he wanted, i did it and helped him until the part where you have to enter your username..

so if you want a small tutorial, just start a Virtualbox, boot up ubuntu in there and PM me.

---

### Post by darkod on 2012-01-07
1. Be VERY CAREFUL if using recovery CDs. That term has different meanings. Usually they may be designed to restore your computer to factory state, which means deleting ALL partitions, ALL data, ALL programs and configuring the computer as it was when you received it.

You don't want that to happen. You only want to install windows bootloader to the MBR.

If you only have CDs to restore to factory state, there is an option to install a MBR with linux tools.

2. The screenshot from Disk Management is not worth much because it can't fully understand linux partitions. It's better to boot ubuntu and take a look in Gparted (install it if necessary).

In fact, I think it's best to do the following:

A. Install windows bootloader on the MBR with windows dvd (but only if that doesn't delete everything) or linux tools.
B. Make sure windows boots fine.
C. Boot your computer with the ubuntu cd (always keep one at hand) into live mode, open Gparted and delete the ubuntu partitions.
D. Boot windows and create one ntfs partition from the unpartitioned space so you can use it.

---

### Post by ottosykora on 2012-01-08
@darkod

how it comes that he has apparently more then 4 prim partitions on the first drive, or this is at least what I did understand from the screenshot.

Is this an efi install or what?

---

### Post by darkod on 2012-01-08
> **ottosykora said:**
> @darkod

how it comes that he has apparently more then 4 prim partitions on the first drive, or this is at least what I did understand from the screenshot.

Is this an efi install or what?

No, it's because it can't successfully recognize linux partitions. They are logical. It can see the size and layout, but not the type I guess. That's why Disk Management is not a good tool to display linux partitions and can get you confused.

---

### Post by tjhans on 2012-01-22
So a small update on my progress, I was looking at what the Samsung Recovery Solution 5 had to offer (hold F4 while booting and you get a recovery environment).  I forgot that the samsung recovery solution does not get along with grub...if i open it, it makes my computer unable to boot from the hard drive, it just shows the Samsung splash, then a black screen, then restarts (one reason i want to get rid of grub).  I tried to use the windows recovery disk.  in the repair options it had a specific part for fixing problems that prevent booting, but it didnt find any problems to fix, so i booted on the ubuntu live disk and saved all the stuff i needed from the ubuntu partition and reinstalled ubuntu (yay! one more swap partition!).  moral of the story, i guess my recovery disk wont help with the MBR problem, any suggestions on a different tool?

ps, i rebooted with the recovery disk after grub was fixed and it still could not find any boot related problems...

---

### Post by reeegiii on 2012-01-22
[http://www.youtube.com/watch?v=Z6I6xv8BNoc](http://www.youtube.com/watch?v=Z6I6xv8BNoc)

Watch this video and read the most liked comment. I uninstalled Ubuntu yesterday successfully.

---

### Post by darkod on 2012-01-22
> **tjhans said:**
> So a small update on my progress, I was looking at what the Samsung Recovery Solution 5 had to offer (hold F4 while booting and you get a recovery environment).  I forgot that the samsung recovery solution does not get along with grub...if i open it, it makes my computer unable to boot from the hard drive, it just shows the Samsung splash, then a black screen, then restarts (one reason i want to get rid of grub).  I tried to use the windows recovery disk.  in the repair options it had a specific part for fixing problems that prevent booting, but it didnt find any problems to fix, so i booted on the ubuntu live disk and saved all the stuff i needed from the ubuntu partition and reinstalled ubuntu (yay! one more swap partition!).  moral of the story, i guess my recovery disk wont help with the MBR problem, any suggestions on a different tool?

ps, i rebooted with the recovery disk after grub was fixed and it still could not find any boot related problems...

It's not grub's fault that it can't boot after you start the recovery option even if you don't go trough with it. It seems most recovery solutions immediately make changes to the MBR of the disk even if you don't complete the whole recovery process. Basically it deletes grub.

There is a very easy way to restore grub if it gets deleted, you don't have to install ubuntu again. You are just creating a more and more complicated layout on your disk by repeating installs.

So, before you get in even bigger trouble, stop reinstalling ubuntu all the time, and tell us this:
1. Do you want to delete all ubuntu partitions with all the data on them? Do you need to save any of the data?

2. Boot the ubuntu you installed latest, or boot with the cd in live mode, and post the output of
sudo fdisk -l (small L)

After that we can proceed with the removal of ubuntu.

---

### Post by tjhans on 2012-01-22
1. there is nothing on the ubuntu partion i  need, i can freely delete/overwrite it.

2. this is the output from sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6a2585c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   694179990   346986571+   7  HPFS/NTFS/exFAT
/dev/sda3       694181886   940775423   123296769    f  W95 Ext'd (LBA)
/dev/sda4       940775424   976769023    17996800   27  Hidden NTFS WinRE
/dev/sda5       889401344   940775423    25687040    7  HPFS/NTFS/exFAT
/dev/sda6       881432576   889391103     3979264   82  Linux swap / Solaris
/dev/sda7       873463808   881422335     3979264   82  Linux swap / Solaris
/dev/sda8       865495040   873453567     3979264   82  Linux swap / Solaris
/dev/sda9       694181888   857524223    81671168   83  Linux
/dev/sda10      857526272   865484799     3979264   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by darkod on 2012-01-22
Without a windows cd there is an easy way to install a generic mbr from live mode. Boot with the ubuntu cd in live mode and do:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

It will give you a warning about lilo config files, ignore it and continue. That's normal.
When you reboot the computer should load win7 directly, without any grub boot menu. Tell us if this happens.

---

### Post by tjhans on 2012-01-23
ok, I finally get it fixed, thank you everyone for your help.  The way I did it was actually guided by an Ubuntu user I met at school.  Pretty much it went like this, I rebooted and after selecting windows 7 from the grub options, tapped F8 to get the windows boot options.  The top option was something like repair this computer.  This gave me an interface that looked the same as what you get if you boot from a win 7 disk.  after telling it my language and stuff i was able to open a command prompt.  i used "bootrec.exe /fixmbr" and "bootrec.exe /fixboot" and rebooted the computer and it went straight to windows 7.  then from there you just use the disk manager to delete the ubuntu partion (after deleting the main one, the swaps disappeared with it) and stuff.  I think he got the instructions here:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Thanks again to everybody who helped.

---

