---
title: "Lucid Lynx: Need help restoring Grub2 (dual boot)"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by t36 on 2010-04-30
Hi,

I'm having a serious problem. After upgrading to 10.04 from 9.10 Win7 wouldn't startup any more. So I tried this HowTo:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

to restore Grub2. But now each time I boot up I get this two lines:

error file not found
grub rescue>

I have NO idea what to do. Can some help me, please?

I added the output of sudo fdisk -l below, if it's any help

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3a9f839

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        7760    62226432    7  HPFS/NTFS
/dev/sda3            7760      121595   914380800    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa059d385

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       21487   172594296   83  Linux
/dev/sdb2          119371      121601    17920507+   5  Extended
/dev/sdb3           21488      119370   786245197+  83  Linux
/dev/sdb5          119371      121601    17920476   82  Linux swap / Solaris

---

### Post by Octanen on 2010-04-30
After im done upgrading to 10.04 (running in background) since the installation bugged out for me and many others apparently... ill let you know, since next step when im done is dual boot install W7... 

Anyways ill let you know how it goes... 

Since its gonna be my first time doing it, but this guide seemed to help alot on the way;

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

But im no rookie in all that stuff so should be fine, heard from a Linux hardcore user friend of mine that it should work properly... so dunno if its the same way you did.

As said before ill let you know if this worked out for me, but keep in mind i got a clean HDD to do it on with only Ubuntu installed for now.

Regards :)

---

### Post by schnelle on 2010-04-30
Start live session from CD or usb flash drive and then folow this guide under "Reinstalling GRUB 2 from LiveCD " section:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by schnelle on 2010-04-30
If this ```
/dev/sdb3
``` is your root partition you should type:

sudo mount /dev/sdb3 /mnt

sudo grub-install --root-directory=/mnt /dev/sdb

sudo umount /mnt

Then reboot.


I don't know what is your root partition. Maybe it is sdb1. If you don't choose right partition you won't restore grub.

---

### Post by t36 on 2010-04-30
Hi,

My root partition is sdb1, sdb3 is my home partition. Doing this I have restored the Grub2 menu so now at least I don't have to use the LiveCD to write these posts :).

But one problem still remains, for some reason when I select to boot in Win7 nothing happens.

Anyone has idea how to solve this?

Thanks in advance,

t36

---

### Post by schnelle on 2010-04-30
Open Terminal and type ```
sudo update-grub
``` .

Then try to boot into win7.

---

### Post by t36 on 2010-04-30
I tried running update-grub,to no avail.

---

### Post by VMC on 2010-04-30
> **t36 said:**
> Hi,

My root partition is sdb1, sdb3 is my home partition. Doing this I have restored the Grub2 menu so now at least I don't have to use the LiveCD to write these posts :).

But one problem still remains, for some reason when I select to boot in Win7 nothing happens.

Anyone has idea how to solve this?

Thanks in advance,

t36

Two things I would suggest. One read this on the [boundary error]("http://www.linuxquestions.org/questions/linux-newbie-8/partition-1-does-not-end-on-cylinder-boundary-282563/").
The second thing is to run and output the *RESULTS.txt* file of *[COLOR="Blue"]boot_info_script[/COLOR]*[see my blue link].

Windows 7 usually has two partitions, one for recovery where the boot info is, the other for all the Windows files.

---

### Post by t36 on 2010-04-30
Hi,

To be honest, I don't really understand the link, but I attached the output of the bash script to this post. I hope this will give more information about what's wrong.

---

### Post by wilee-nilee on 2010-04-30
> **t36 said:**
> Hi,

To be honest, I don't really understand the link, but I attached the output of the bash script to this post. I hope this will give more information about what's wrong.

Repost that on the thread in code tags, otherwise it has to be downloaded to be read. This is fixable just wait for a little help. I see some problems but I am hesitant to suggest when there are others who can give you some definitive answers.

---

### Post by VMC on 2010-04-30
> **t36 said:**
> Hi,

To be honest, I don't really understand the link, but I attached the output of the bash script to this post. I hope this will give more information about what's wrong.

You have installed grub2 on both MBR's of sda and sdb. Do you know if your BIOS is set to boot off of sda (normal) or sdb.

The Windows 7 menu entry looks correct:
```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 36461ef7461eb797
	chainloader +1
```

But you have this problem:
```
There is a problem with Windows boot
Grub 2 is installed in the boot sector of sda1 and 
looks at sector 274815 of the same hard drive for 
**core.img**, but core.img can not be found at this location
```

You can try to reinstall Windows boot recovery onto sda MBR using fixmbr command. If you can get Windows 7 to boot up, then its easy to re-install grub2. The key is the above core.img error.

Edit: Try this [solution]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") for re-installing Windows 7 boot info.

---

### Post by Hashmere on 2010-05-01
> **VMC said:**
> 
Edit: Try this [solution]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") for re-installing Windows 7 boot info.

Thank you so much! I've been browsing these forums for awhile looking for a solution and this did the trick!

My Problem: I was dual booting with 9.10 and W7, each on their own respective hard drive. I did the upgrade of 9.10, rather than the fresh install and when it came to the question regarding grub, I chose to keep the current version. After 10.04 was finished installing, when I tried to boot into W7 I got a black screen with a flashing white cursor and was unable to boot into windows 7.

If anyone has a problem that resembles mine, try the trick VMC suggested

---

### Post by gungrog on 2010-05-01
> If anyone has a problem that resembles mine, try the trick VMC suggested

Seconded! Worked a treat for me with Lucid/XP boot issue. :)

---

### Post by t36 on 2010-05-01
Thanks, the testdisk solution fixed my problem! 

I think this may have been caused when during installation of lucid I was asked select where to install Grub.
For future reference, what should I choose?

Thanks a lot!

t36

---

### Post by chezzo on 2010-05-01
Just thought I should share my experience in this matter - all fixed now but it's been a painful couple of days!

Just as a reference, my hard drive is laid out as follows-
sda1: Sony Vaio recovery partition
sda2: Windows "System Reserved" partition
sda3: Main Windows 7 partition
sda4: Extended partition containing...
sda5: Linux partition
sda6: Swap
sda7: Large NTFS partition for sharing docs etc between Windows and Linux

It all started, as I think a lot of people's problems did, when I ticked the wrong box in the Grub dialog during 10.04 update. Instead of installing it to sda, I installed it to sda5, meaning that when I booted I just got an error message. I used the instructions [here]("https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found") and [here]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") to properly install GRUB, but this is also where I made my second big mistake. At some point, sda2 had been set as the boot partition, so I thought it would be a good idea to install Grub there too - so after running dpkg-reconfigure grub-pc, as well as selecting sda, I also ticked sda2. Bad move.

Booting now gave me a Grub screen with all the Linux options, properly working, and then "Windows Vista on sda1" and "Windows 7 on sda2", with selecting the Windows 7 option just restarting the PC. I became convinced that the reason I could not get Windows to boot was because Grub was not recognising sda3. I used a Windows recovery CD to try to fix the Windows boot, but all the command line instructions given, for example [here]("http://ubuntuforums.org/showpost.php?p=9159551&postcount=16"), resulted in error messages, and running the automatic boot fixer (and then update-grub) did nothing except change the name of sda1 in Grub from Windows Vista to Windows 7.

I tried running testdisk, but still thinking that the problem was in sda3 I selected it and found no BackupBS option. I then tried the Boot Info script, which included the following output:

```
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 19467240 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD /grub/core.img

```

Realisation finally dawned. I ran testdisk again but for sda2, used the BackupBS option, and now selecting sda2 from the Grub menu boots into Windows. Problem (finally) solved! A huge thank you to everyone posting on this matter, couldn't have done it without you! :D

---

### Post by chezzo on 2010-05-01
> **t36 said:**
> Thanks, the testdisk solution fixed my problem! 

I think this may have been caused when during installation of lucid I was asked select where to install Grub.
For future reference, what should I choose?

Thanks a lot!

t36

I think it depends, but assuming it's installed to your Master Boot Record, you should pick sda (or whatever your drive is called) *without* any numbers after it.

---

### Post by VMC on 2010-05-01
> **chezzo said:**
> I think it depends, but assuming it's installed to your Master Boot Record, you should pick sda (or whatever your drive is called) *without* any numbers after it.

True, if you use sdX it would install grub on the MBR of that hard drive. If you used "numbers"[sda1, for example], it would instill grub on that hard drives partition number 1.

sda,sdb,etc = MBR
sda1,sdb1,etc = partition

---

### Post by ssican on 2010-05-01
**DUAL BOOT WITH TWO HARD DRIVES** -
To remember that, it is necessary TO CHANGE THE HARD DISK BOOT PRIORITY in the BIOS.
In the BIOS , on ADVANCED BIOS FEATURES to put
1)- First Boot Device - CD-ROM
2)- Second Boot Device - Hard Disk with Ubuntu
3)- Third Boot Device -Hard Disk with Windows 7

For IDE Hard Disk, see this example:
[http://www.ehomeupgrade.com/2006/06/02/how-to-dual-boot-ubuntu-606-dapper-linux-desktop-along-side-windows-xp/](http://www.ehomeupgrade.com/2006/06/02/how-to-dual-boot-ubuntu-606-dapper-linux-desktop-along-side-windows-xp/)

For more information about BIOS , see the BIOS Page:
[http://members.iinet.net.au/~herman546/p1.html#Changing_the_hard_Disk_Boot_Priority](http://members.iinet.net.au/~herman546/p1.html#Changing_the_hard_Disk_Boot_Priority)

EDIT 1
For Install GRUB2 on the Hard Disk with Ubuntu, in the installation of Ubuntu, on the step 8 of 9, press the button ADVANCED and to choose -**sda**-
**sda** - it is now the hard disk that first boot. Choosing **sda**, you to choose to install GRUB2 on the MBR of the Disk that first boot; the Hard Disk with Ubuntu. 

EDIT 2
Before to start the installation of Ubuntu, check the name of the Hard Disk(if it is **sda**) on SYSTEM > ADMINISTRATION > GParted

---

### Post by adm1968 on 2010-05-01
[FONT="Georgia"]I have followed all the instructions provided to use testdisk

  First   screen:  Select "No Log" and press enter.
  Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
  Third   screen:  "intel"
  Fourth  screen:  "advanced",
  Fifth   screen:  Select the Windows system partition  and choose "boot"
  Sixth   screen:  "BackupBS"
  Seventh screen:  type "Y" to confirm

However, on the sixth screen, no option is given to me to "BackupBS". The only option available is "Rebuild BS", which I have selected, then updating grub, and rebooting, to no avail (my MBR is not corrupt, I have double checked).

Win 7 remains unavailable

Any help greatly appreciated! [/FONT]

---

### Post by chezzo on 2010-05-01
If it's the same problem I had, try testdisk on your "System Reserved" partition, instead of your main Windows partition - it's usually a small partition immediately in front of the Windows one.

---

### Post by ssican on 2010-05-01
For Adm1968

**How to Restore Windows 7 Bootloader**:

[http://ubuntuforums.org/showthread.php?p=6391959#post6391959](http://ubuntuforums.org/showthread.php?p=6391959#post6391959)

---

### Post by drmikegreen on 2010-05-01
I have what I suspect is the same problem as many in this thread: After upgrading to Lucid Lynx, I can no longer boot into Windows 7. When I try to do so the system hangs.

I suspect the problem could have been caused by my response to the screen which asked where to install Grub, which came up during the upgrade process. The instructions there left me with the impression that checking all of the boxes was better than checking none. And I had no idea which was the correct one. When I checked all, however, the installation process coughed and came back with only one (or possibly two) boxes checked. So I went with that. I suspect now that I would have been better off not checking any boxes, but must find a way to correct the situation. I have searched and tried several. There is, however, a significant possibility that I will just dig myself into a deeper hole by doing the wrong thing.

Based on what I read in this thread I tried sudo fdisk -l (I'm pretty weak on command line stuff). The result was a message which included the following:
"   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary. ..."

So I now (think I) know that the location of boot is /dev/sda1. And I suspect that is where I should have told the install procedure to put Grub. (I didn't know about the command sudo fdisk -l before. And I'm not even sure that Grub should be in the directory which this command indicates is boot.)

Also, I don't know what -- if anything -- to do about the message "Partition 1 does not end on cylinder boundary."

I would very, very much appreciate some simple instructions on how to get out of this hole -- instructions which don't assume a great depth of knowledge about things at the system level. I will try my best to understand whatever help is given. I would, however, just like to have a quick fix :)

And I would recommend, if the right parties are listening, that the screen which asks where to put Grub be improved greatly to take into consideration that folk upgrading may not know how to respond -- or even understand much about what is said there.

Thanks in advance for any and all help.

Cheers!

Mike Green

---

### Post by drmikegreen on 2010-05-01
Well, I have resolved this now, thanks to the instructions at [http://ubuntuforums.org/showthread.php?p=6391959#post6391959](http://ubuntuforums.org/showthread.php?p=6391959#post6391959).

It was not, however, at all without difficulty. I had to do the instructions in rather the reverse order in the end. See my posts #s209-211 in response to that thread ([http://ubuntuforums.org/showthread.php?p=6391959#post6391959](http://ubuntuforums.org/showthread.php?p=6391959#post6391959)), if you think you might be assisted by a somewhat blow-by-blow account of my (mis-)adventures.

Cheers!

Mike Green

---

### Post by adm1968 on 2010-05-02
> **ssican said:**
> For Adm1968

**How to Restore Windows 7 Bootloader**:

[http://ubuntuforums.org/showthread.php?p=6391959#post6391959](http://ubuntuforums.org/showthread.php?p=6391959#post6391959)

[FONT="Georgia"][SIZE="2"]Thanks for your feedback
However, I am not clear about the method. If I follow it, will I not install the Windows bootloader over GRUB?[/SIZE][/FONT]

---

### Post by ssican on 2010-05-04
For Adm1968,

Yes, you will Install the windows bootloader over GRUB.

Another option it is Reinstall GRUB2

Code:
sudo update-grub

---

