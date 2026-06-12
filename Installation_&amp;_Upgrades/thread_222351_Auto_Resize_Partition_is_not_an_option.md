---
title: "Auto Resize Partition is not an option"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by smectic on 2006-07-24
;) 
hi all, 
I am new to the Linux scene, and I am trying to install Ubuntu 6.06 from the CD I downloaded and burned. I want to have dual boot as I am running Win XP here too. I have two HD, and I thought of leaving the Slave HD just for Ubuntu. 

I formatted the drive from Windows first, to erase it. Then from Ubuntu installation I chose "Erase entire Disk" partition option, selecting the slave drive.
Everything went ok, but when it finished installing it asked for a reboot, after which it came out with an error about, "wrong drive" or something like that. And it just wouldn boot. It also deleted the win XP boot option. :confused: 
I formatted both drives again (very painful, after backing up the Master HD), reinstall win XP, and did the same process again. It spitted the same error again. :mad: 
I reformatted, redid the partitions from winXP recovery console, reinstalled winXP, etc. This time I tried with the suggested "autoresize partition" option, I was about to do it with the master slave, and I hesitated and cancel the installation. I tried again with the autoresize HD on the slave drive, but the option was gone!! ](*,) 
I cancelled, restarted, ran chkdsk. I just can't make it to show the autoresize drive option on the partitioner...

I have been reformatting and installing for three days, I would appreciate some help, as I really do not want to format the drives again just to realize the installation is not working.

(luckily I am doing this with my home desktop, not the one I have t work with everyday)

I will appreciate any suggestion

smectic

---

### Post by confused57 on 2006-07-24
Since you have 2 hard drives, here's an option to consider:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I have 2 computers set up this way.

---

### Post by smectic on 2006-07-24
thank's a lot
will try now and post the results

:)

---

### Post by smectic on 2006-07-25
I have been following the advice on different threads.
Unfortunately, none fits my case. So I've been adapting the process to my case:
I have a Master HD C:, where I want my Win XP installed,
and a Slave HD D: where I want Ubuntu Installed.

Following one of the threads, I took out the C drive, (where win XP was just installed and running), setup the slave drive as master and installed Ubuntu. Everything went perfect, I rebooted and installed all updates (kinda long process considering there were 130+ updates for UBUUNTU 6.06 Desktop available). I then reconnected the primary drive and set that as master and the Ubuntu one as slave.
rebooted, and error, wrong disk.
I took of the Ubuntu drive, trying to boot as initially, just from my Windows drive, ... wrong, wouldn't boot.
I repaired windows installation with the WinXP CD, (this is already my 5th reinstall of winxp during this process, really tired of doing so). Reboot, and windows boot OK.
Now I reconnected the Ubuntu drive and can't get to boot it.
According to one Herman's advice, I downloaded GAG, the software that would redirect to each particular booting file on each drive. I boot from GAG CD, it found and installed both OS, Win Xp from HD 1, and Ubuntu from the HD 2.
When I boot win XP it is OK, but when booting Ubuntu it gives an error about booting system missing, or smth like that.

I am using the Ubuntu 6.06 desktop Live CD, and I think I would have to try reinstalling grub on my D: drive and then pointing at it with GAG, but I don't have an option for installing just GRUB when using the LIVE CD. 
I just don't want to reinstall all over again to realize that when Ubuntu is installed it messes up the booting sequence.

please, please..... HELP.
Hasn't anybody seen or done an installation of Ubuntu on a slave drive with Windows XP on a master drive with dual boot?


desperate and tired, after working until 4:30 on this 4th reinstall yesterday night.

smectic](*,)

---

### Post by confused57 on 2006-07-25
Can you boot both drives separately when connected as the Master drive?  If you can, I believe you can set up a dualboot using Ubuntu as the master drive and Windows as slave, as described in the link I suggested.
There's no problems with Ubuntu as master, as I mentioned I have 2 computers set up this way.  Is the slave drive enabled in your bios, I ask because I had this problem installing to a Dell?
If the answer to the 1st question in this reply is yes, connect Ubuntu as master, and Windows as slave...boot into Ubuntu and post the output of:

```
cat /etc/fstab
```
and
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by smectic on 2006-07-25
ok, Iam back and trying to finally succeed with this installation.

yes, I checked, if I set up each of the HD as masters, and disconnect the other, they boot OK in each OS. 
I am following your advice and connected the Ubuntu drive as Master and the WinXP as slave.

It boots into Ubuntu, and the outcome of the first line is

/////////////////////////////////////////////////////////////////////
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/////////////////////////////////////////////////////////////////////

and from the second line of code:

/////////////////////////////////////////////////////////////////////
Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4661    37439451   83  Linux
/dev/hda2            4662        4863     1622565    5  Extended
/dev/hda5            4662        4863     1622533+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19456   156280288+   7  HPFS/NTFS
////////////////////////////////////////////////////////////////////

should I proceed? is this what was expected?
If my win xp HD is the slave, will this affect the letter asigned for it C: or D: ?

thx

---

### Post by confused57 on 2006-07-25
Yes, everything looks good...read back over this link:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

With Ubuntu as master and Windows as slave, set it up as described in the thread.  If you have any questions about the instructions, I'll try to help you any way that I can.  My system set up like this automatically boots into Windows, but I can choose Ubuntu from the grub menu at bootup.

---

### Post by smectic on 2006-07-25
Thanks a lot confused57,
it all worked out.
=D> =D> =D> =D>

WindowsXP HD is slave now and Ubuntu is in the master drive, I did the tweaking in the menu.lst file, and it all worked perfectly.
Indeed, it worked better than expected, I got to keep my WINXP OS in C:, and Ubuntu in D:, and when booting it gives the option of dual boot, and then loads windos by default, something I needed as I do a lot of remote work connecting from to the office or from my laptop to any of these, etc, and many times I have to reboot remotely, and I needed it to start Windows automatically or I would be locked out.
the dualboot is working just fine.

Thanks for the patience and the help.
=D> =D> =D> =D>

smectic

---

### Post by confused57 on 2006-07-25
I'm glad it worked out, it was one of the few areas I have personal experience with...I knew you'd really like the setup, grub isn't installed to your Windows mbr(which is what I prefer).  Enjoy your dualbooting.
Thanks for letting me know it worked.

---

