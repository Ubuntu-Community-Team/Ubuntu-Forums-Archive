---
title: "Fresh install GRUB problem - please help!"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by cab6fh on 2010-12-23
I previously had a machine that dual booted Windows 7 and Ubuntu 10.10 32 bit.  I recently attempted to wipe out the 32 bit Ubuntu and install 64 bit Ubuntu.

Here what I did:
-I booted from the LiveCD, and had no problems
-I formatted /sda3 using gparted.  I checked that Ubuntu resided on /sda3 via the command "sudo fdisk -l".  This worked fine.
-I then clicked the "install ubuntu" option on the desktop, and chose the largest chunk of free space.
-About 15% through the install, I was told the CD could not be read from due to a potential scratch or issue.  I then tried to revert back to the Os running from the LiveCD, and things went crazy.  I had trouble shutting down the machine and did a hard reset.

Now, whenever I boot I am greeted with the following message:
Windows Deployment Services: PXE boot aborted
error: no such partition
grub rescue>

At the grub rescue prompt when I ls, i see:
(hd0) (hd0,4) (hd0,2) (hd0,1)


I can still boot the LiveCD.  I tried that again and tried to again format sda3 using gparted but had no luck fixing the issue.  When booting from the LiveCD I am also told by gparted that "sda1 does not coincide with a cylinder boundary" or something of that nature...


Does anyone know how to fix this?

I will be extremely grateful if anyone can help me out!  For now I'm going to burn another LiveCD and see what I can do...I'm a grad student and I need to get this running by 9am... :(


Thanks so much!
~Colin

---

### Post by Rubi1200 on 2010-12-23
Hi and welcome to the forums :)

From the LiveCD, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here please.

Thanks.

---

### Post by T.J. on 2010-12-23
Hi Colin! 

If you mean that you need Windows repaired as soon as possible so that it will boot, and you can work on your classes - insert your Windows DVD and boot.  You will be presented with the option to install Windows but also "Repair your computer".

Pick Repair, and then select the repair prompt from the menu.

Type in "bootrec /fixmbr".  If it succeeds, reboot the machine and Windows should come up normally.  If it doesn't work it won't do any real harm, except that you might have to reinstall Ubuntu - which from the sound of your post is likely anyway.

---

### Post by cab6fh on 2010-12-23
> **Rubi1200 said:**
> Hi and welcome to the forums :)

From the LiveCD, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here please.

Thanks.

Here is what I get after running the boot info script:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   614,402,047   614,195,200   7 HPFS/NTFS
/dev/sda3         614,404,094 1,242,527,743   628,123,650   5 Extended
Empty Partition
/dev/sda4       1,242,527,744 1,250,263,039     7,735,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1EEA81ACEA8180AF                       ntfs       System Reserved               
/dev/sda2        045C9EB95C9EA4C8                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        85331f7a-87cc-401d-964b-4aa91bf2511a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)



Does this give you any ideas?

Thank you so much!

---

### Post by garvinrick4 on 2010-12-23
#Put your windows 7 boot manager back in with recovery disk:
see below.
#You have an extended partition with no  logical partitions inside right now
for linux. You have a swap in sda4 you do not need.
#grub is looking for files that are not there linux install gone.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by garvinrick4 on 2010-12-23
If you want to reinstall linux use live cd and take a screen shot of gparted and 
post here using paper clip attachment in Message box. A user will be around
to help you make a partition for you and get rid of swap you do not need in sda4
with gparted. You know just clean up your drive and get installs correct.

If you do not have windows recovery disk.
Put in live cd and open a terminal and get internet connection:
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
Will say error ignore we just want mbr portion

---

### Post by Rubi1200 on 2010-12-23
As the previous poster mentioned, if you need this up and running for school you need to restore the Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I am not sure what went wrong, but you have no Ubuntu installed and GRUB is on sda3, which is marked as an extended partition.

I recommend you get Windows back up and running and deal with the Ubuntu issues later.

Downloading and burning a new CD will also help based on your previous comments.

When you do so, reformat sda3 and the swap partition and start afresh.

Good luck!

---

### Post by cab6fh on 2010-12-23
> **T.J. said:**
> Hi Colin! 

If you mean that you need Windows repaired as soon as possible so that it will boot, and you can work on your classes - insert your Windows DVD and boot.  You will be presented with the option to install Windows but also "Repair your computer".

Pick Repair, and then select the repair prompt from the menu.

Type in "bootrec /fixmbr".  If it succeeds, reboot the machine and Windows should come up normally.  If it doesn't work it won't do any real harm, except that you might have to reinstall Ubuntu - which from the sound of your post is likely anyway.


The issue is that I need Ubuntu 64 bit installed by tomorrow; but I still need to keep my Windows install intact.  I could not run this code on my previous Ubuntu install because I need a 64 bit address space for various reasons that I will not bore everyone with here...also, I don't have the original Windows install disk since this install was done by school staff...Thanks for your help though; I sincerely appreciate it and I think the confusion was due to a lack of detail given by me.



I just tried this:


sudo apt-get install lilo
and
sudo lilo -M /dev/sda mbr


I'm going to reboot and see what changes and I will get back.

Thanks to everyone for their help!  I find it  ironic that there is better customer support for a free OS compared to an OS that was paid for... ;)

---

### Post by cab6fh on 2010-12-23
> **garvinrick4 said:**
> 
If you do not have windows recovery disk.
Put in live cd and open a terminal and get internet connection:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Will say error ignore we just want mbr portion


Awesome!  Windows is back in action; therefore half the battle is complete.  Looks like I'm about to go back for round two with installing Ubuntu-64.  I'm burning a new CD now (My old one was all scratched up, and started this problem). 

How can I fix up my partitions in gparted so that I don't run into more issues while installing?  I'm about to post a screenshot of my gparted

Thanks,
Colin Braley

---

### Post by garvinrick4 on 2010-12-23
> **cab6fh said:**
> The issue is that I need Ubuntu 64 bit installed by tomorrow; but I still need to keep my Windows install intact.  I could not run this code on my previous Ubuntu install because I need a 64 bit address space for various reasons that I will not bore everyone with here...also, I don't have the original Windows install disk since this install was done by school staff...Thanks for your help though; I sincerely appreciate it and I think the confusion was due to a lack of detail given by me.



I just tried this:


sudo apt-get install lilo
and
sudo lilo -M /dev/sda mdr


I'm going to reboot and see what changes and I will get back.

Thanks to everyone for their help!  I find it  ironic that there is better customer support for a free OS compared to an OS that was paid for... ;)
That is:
```
sudo lilo -M /dev/sda mbr
```
YOU Have a typo

---

### Post by cab6fh on 2010-12-23
> **garvinrick4 said:**
> That is:
```
sudo lilo -M /dev/sda mbr
```YOU Have a typo
Sorry about that; I typed it correctly when entering it on the command line.

When I quoted you I eliminated the code tags in the quote for the sake of keeping the post on one screen and then accidentally typed mdr...sorry about that.

~Colin Braley

---

### Post by garvinrick4 on 2010-12-23
#Boot off of ubuntu cd and go into live cd (try ubuntu).
#open gparted:
#take a screenshot and post it here with paper clip in message box.
#Will then make partitions to install ubuntu into:
#Not that hard to do just need to do it once and you will get the idea.
#With screenshot of gparted also need to know how much Ram you have.
```
free
```

---

### Post by wilee-nilee on 2010-12-23
So when you have the cd burned and booted to the live enviroment, take a screen shot of gparted in menu-system-admin-gparted,and post it.

You can use the menu-accessories-Take Screen shot if it woks for you. This will probably get enough information for help.

You guys have this I have it subscribed in case anybody disappears.

---

### Post by T.J. on 2010-12-23
> **cab6fh said:**
>   I could not run this code on my previous Ubuntu install because I need a 64 bit address space for various reasons that I will not bore everyone with here...

Oh goodness!  Sounds like comp sci. ;)

  
> 
also, I don't have the original Windows install disk since this install was done by school staff...


Yikes! :o I'll keep that in mind before I make any wild suggestions.  I'd retry installing Ubuntu very carefully to avoid damaging the Windows partition. I agree with Rubi1200, if the install failed, it probably didn't write the data properly.  Reformatting the Linux partition and reinstalling is probably the fastest route to end your boot problems.

> 
Thanks to everyone for their help!  I find it  ironic that there is better customer support for a free OS compared to an OS that was paid for... ;)


You're very welcome!

---

### Post by cab6fh on 2010-12-23
> **garvinrick4 said:**
> #Boot off of ubuntu cd and go into live cd (try ubuntu).
#open gparted:
#take a screenshot and post it here with paper clip in message box.
#Will then make partitions to install ubuntu into:
#Not that hard to do just need to do it once and you will get the idea.
#With screenshot of gparted also need to know how much Ram you have.
```
free
```


Here is the screenshot with all the relevant information.  Looks like I only have 4GB of RAM anyway, so 64 bit isn't going to matter in that department.  However, I did want/need 64 bit Ubuntu installed eventually for other reasons.



Thanks,
Colin Braley

---

### Post by garvinrick4 on 2010-12-23
#You have plenty of Ram do not need swap.
#Now we are in gparted and we can right click on swap and delete:
#We right click on sda3 extended and resize to take up free space left by swap. ( no big deal just small bit)
#We can right click on sda3 and make new partition as logical to the size you want in ext4 for ubuntu install.
#We can right click on free space left over and make new logical partition in NTFS ,size for
partition to use both in Windows and Linux for Data. Linux can read both ntfs and ext4
and windows can read ntfs but not ext4. This partition will show up as a F of G drive in
Windows and a sda# in linux and is nice to have.
#You have to hit the green apply arrow to make things happen in gparted.
Now the ext4 partition is the one we will use to install your 64 bit ubuntu.
The ntfs partition you do not have to touch again will just be for data.
Write down the ext4 number so you remember it.
Now give me another screen shot of gparted.

## Do not touch sda1 or sda2 they are boot partition and windows OS

---

### Post by cab6fh on 2010-12-23
Thanks so much for your help this is a lifesaver.

Looks like I have to wait over an hour for gparted to move some stuff on disk around...
Attached is a screenshot of gparted's current status:

Once this operations finished I will change a few more things and get my partitions to look as follows:

```

/dev/sda1 ntfs ... (windows)
/dev/sda2 ntfs ... (windows)
/dev/sda3 extended
    /dev/sda4 ext4 (ubuntu will go here)
    /dev/sda5 ntfs  (data for windows and ubuntu)

```

Then I'll run the Ubuntu installer and install to sda4
Does that look right?  

Thanks again!

~Colin

---

### Post by garvinrick4 on 2010-12-23
Nope sda3 is extended partition just to house logical partitions for linux.
should be nothing in sda5 to move, have not installed anything.
#sda5 will be first logical partition for ubuntu install in ext4
#sda6 will be in logical ntfs for data between Windows and linux in ntfs

#inside of extended partition the partitions start with sda5
#sda4 is a primary number not in extended partition you will not have one.
#primarys are sda1 thru sda4 and extended counts as primary get 4 primarys.
#With nothing to move making two logical partitions in extended and deleting 
swap in sda4 should have took about 20 seconds.

---

### Post by garvinrick4 on 2010-12-23
#sda3 one big extended partition ( houses both sda5 and sda6 inside of called logical partitions)
#sda5 will take up large part inside sda3 as logical in ext4 now in ext2 no big deal to change anytime.
#shrink sda5 to make room for sda6 for data partition.
#If you do not care about data partition between windows and linux just use sda5
## Do not touch sda1 or sda2 it will ruin windows you have no disk.
gparted will assign sda numbers in proper order.

## looks like you have your install should have been ext4 instead of ext2 cannot change without reformatting
so up to you. See sda6 will be in that 10 gig spot in middle of drive in NTFS. Easier and quicker way to do it
but you are getting it done. First go at gparted get to understand a little better in time. Have ext2 (older) ext3 (old) ext4 (new)
Always put grub in sda never sda1 or sda5 always sda that is where mbr (master boot record) resides. sda
You have a boot partition sda1 so if ever going to install grub by running code have to have sda1 and sda5 mounted to install grub by code.
Good luck in your class and have a Merry Christmas.

---

### Post by cab6fh on 2010-12-23
So I finally your gparted suggestion done, and my current gparted setup looks fine :)

However, when I try to install I can choose either:
-Install alongside other OS 
(I don't think this is what I want since it looks like it would wipe my swap partition)
or
-Specify Partitions Manually (advanced)

When I enter "Specify Partitions Manually" I am supposed to choose where to put the bootloader.  However, I am unsure which option to choose.  Anyone have any ideas?  I attached a screenshot to help.

I've been trying to figure out some of this stuff by reading about disk-layout, grub, lilo and things but I still find it all quite confusing...

Thanks again for your help(esp. garvinrick4) and happy holidays,
Colin Braley

---

### Post by wilee-nilee on 2010-12-23
Bootloader goes to sda that is where the MBR is do you understand how to install to that single partition=sda5 in the custom menu?

---

### Post by cab6fh on 2010-12-23
> **wilee-nilee said:**
> Bootloader goes to sda that is where the MBR is do you understand how to install to that single partition=sda5 in the custom menu?

No, I don't think I do.  

When I choose /dev/sda ATA WDC ... (640.1 GB)
for "Device for boot loader installation"

I get the error message:
"No root file system is defined.  Please correct this from the partitioning menu."
I don't know what that means. 

To recap,  all I want to do is:
-leave /dev/sda1 and /dev/sda2 alone, since they are for windows
-install ubuntu 64 bit on /dev/sda5
-leave /dev/sda6 alone as ntfs swap space for windows and linux


Thanks,
Colin Braley

---

### Post by wilee-nilee on 2010-12-23
You just setting the bootloader to sda with the drop down you show. In custom; to install the actual os to sda5 hit the check box it opens a popup, make it a exstention 4 as it is then in the open box below in that popup put a / click save on that popup. You can just install from there you may see a wrning that it will overwrite sda5 that is okay.

So lets recap the bootloader is this.
[ATTACH]179238[/ATTACH]

The Ubuntu OS goes to sda5 with it marked with a / in the popup when you click the sda5 box then change=make it a ext4 add the / then install.

---

### Post by cab6fh on 2010-12-23
> **wilee-nilee said:**
> You just setting the bootloader to sda with the drop down you show. In custom; to install the actual os to sda5 hit the check box it opens a popup, make it a exstention 4 as it is then in the open box below in that popup put a / click save on that popup. You can just install from there you may see a wrning that it will overwrite sda5 that is okay.

So lets recap the bootloader is this.
[ATTACH]179238[/ATTACH]

The Ubuntu OS goes to sda5 with it marked with a / in the popup when you click the sda5 box then change=make it a ext4 add the / then install.


Awesome!  It appears I just needed to check that box.  My install is nearly done; everything seems to be going smoothly.

This forum is awesome; and you all are awesome for being so helpful.

Happy holidays,
Colin

---

### Post by wilee-nilee on 2010-12-23
> **cab6fh said:**
> Awesome!  It appears I just needed to check that box.  My install is nearly done; everything seems to be going smoothly.

This forum is awesome; and you all are awesome for being so helpful.

Happy holidays,
Colin

Once you do custom installs you will probably just do them that way, more control and your able to confirm where grub goes and such.;)

---

