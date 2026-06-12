---
title: "Using grub to recover"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by apche93 on 2008-07-11
Hi,

I just installed Ubuntu.

Here are my partitions:
[IMG]http://i260.photobucket.com/albums/ii30/apche93/Screenshot-1.png[/IMG]

/dev/sda1 is my Recovery partition for Windows Vista.  I want to know if there is any way to restore it to /dev/sda3

Some add'l info:
when i start Grub, i have the option of starting the ubuntu, ubuntu (in recovery mode), memtest, or the RECOVERY partition.

When i run the recovery partition and try to restore the C: drive, it says that the C: drive is missing.  Sooo, is there a way to somehow install vista thru the use of ubuntu?

I just want to get my vista partition back so that i can once again happily dual boot.

PLEASE HELP.

---

### Post by Herman on 2008-07-11
:) Hello apche93,
That appears to be quite a pickle you have gotten yourself into there.
It looks to me like whatever partitioner you used has taken the liberty of changing your partition numbers.
Was your Windows partition number /dev/sda2 originally?
 I don't think you'll be able to convince your recovery program to re-install Windows in a different partition number than it was designed for, which would normally be /dev/sda2, and I am guessing that's supposed to be 'Drive C:', and not /dev/sda3.

There's no easy way to change partition numbers that I know of yet. Some partition editors seem to be able to do it quite effortlessly, but I don't know of a program for reversing the changes.

The only way I know how to do that is to delete a partition to make a partition number vacant, then copy another partition and paste it somewhere so it'll be allocated the partition number of the deleted partition.

In other words, I think the only way would be to use either a  [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") or else Gnome Partition Editor in your Ubuntu Live CD to do some heavy duty work on your partitions. (You will need somewhere to back up all of your data first).
I would begin by deleting your Ubuntu partition, and the swap area and the extended partition they're in.
You could make a Partimage backup of your Ubuntu partition first if you'd rather restore it instead of re-installing it, GParted LiveCD features Partimage or you can install Partimage temporarily in your Ubuntu Live CD. ('sudo apt-get install partimage').
Aysiu has a good how-to on Partimage here, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage").

Once those partitions have been deleted, the partition number 2 will be vacant, so all you need to do is copy and paste partition number 3 somewhere and it'll be automatically allocated the number 2.
The catch here is you can only paste a partition into an area of free space which is larger than the partition you copied. That means you'd need to resize (shrink) partition 3 and move it to the left until you have enough free space there behind partition 1 first. Depending on how full it is, you may need to delete some files in order to be able to resize it small enough.
When you're ready, copy partition number 3 (which I assume is your Windows), and paste it into the free space after partition number 1, and it should receive the partition number of 2 like it's supposed to have.

You'll then probably want to delete partition number 3 and do the same thing with partition number 4, to make it have the partition number of 3.

Finally, you can re-install Ubuntu or restore it from your Partimage backup. You'll be able to create a new extended partition, (number 4), with an ext3 partition in it and a swap area, (numbers 5 and 6). You will need to edit your /etc/fstab file, edit your /boot/grub/menu.lst files with the different partition numbers, and re-install GRUB. 
These two links should help, but please feel free to ask more questions if you need more help, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD"), and [About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with").

---

### Post by apche93 on 2008-07-11
hi,

but the thing is, I used Gparted to delete ALL my other partitions but the Recovery one (I: in windows).  So wouldnt that mean that it would have lost the drive letter.  But, yes, the last time i had ubuntu installed with vista, sda2 WAS my vista partition, and i had an sda3 as ubuntu, sda4 was extended- sda5 (swap) & sda6(a common parition where i could keep my files)

---

### Post by Rallg on 2008-07-11
A possibility: I recall that in my previous laptop (with XP), the "Windows Genuine" validation apparently measured the starting point of the Windows partition, among other things. I found this out when I moved the partition. Although it still booted, it complained that my copy was not genuine (a phone call to MS solved the problem).

Looking at your list of partitions, it appears that you moved the starting point of Windows. Is that so? Perhaps the Recovery partition expects the partition reserved for Windows to be in a specific place on the hard drive. If it is not there, then "C: is missing." There is not much chance that you would be able to re-arrange the partitions exactly as they were.

It appears that your Windows operating system may still be OK; you haven't lost Windows and don't need to restore anything. More likely than not, Windows is in sda3 which is known to Grub as (hd0,2) in this case. Note: I'm not sure if that still applies when the partitions are out of numerical order, as you have it. But if so, then it would be (hd0,n) for some other n.

Try this: Within Ubuntu, edit your Grub menu.lst file so that it has another entry. To edit the menu.lst file, call up a Terminal (Ubuntu Start - Accessories - Terminal) and type:

gksudo gedit /boot/grub/menu.lst

Then edit the file by adding the following to the menu choices:

title		Vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1

Save the change, re-boot, and try to boot to the newly added Grub choice. did that work?

There are other possibilities. But I wouldn't attempt using the Recovery partition unless all other possibilities have been exhausted.

---

### Post by apche93 on 2008-07-11
This is my /boot/grub/menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd0,5)/boot/grub/splashimages/boot_splash.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6baef251-3102-41f7-8321-b25dad76f6bb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6baef251-3102-41f7-8321-b25dad76f6bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6baef251-3102-41f7-8321-b25dad76f6bb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6baef251-3102-41f7-8321-b25dad76f6bb ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6baef251-3102-41f7-8321-b25dad76f6bb ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (Recovery)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title Vista
root (hd0,2)
savedefault
makeactive
chainloader +1
```


Okay, i rebooted and selected the Vista option, then it said that there was no boot manager and i needed to restart.  But Grub is not broken.

---

### Post by Rallg on 2008-07-11
No boot manager at (hd0,2) ? Well then, try (hd0,n) for various n from 1 to 5.

You don't have to manually edit the menu.lst file. Instead, when you get to the Grub menu, you can select the Vista choice, then edit the boot commands directly within Grub. You would edit (hd0,2) to some other value, and try it. If Grub doesn't like your change, try again with a different value. it won't hurt.

If you can get it to work, then you will need to manually edit the Grub menu.lst file, for the correct value. (When you change the Grub command line from within Grub, the change is temporary.)

Now, to reassure yourself that Windows is still there, boot to Ubuntu (from hard drive or live CD). Go to the mounted volume where Windows ought to be, and look at the files contained within it. Do you see what you would expect to see (Windows file structure)? If the files are there, then you can get to them one way or another.

Unless you have over-written your Windows files (and I don't think you did), you can expect eventual success.

---

### Post by apche93 on 2008-07-11
> **Rallg said:**
> No boot manager at (hd0,2) ? Well then, try (hd0,n) for various n from 1 to 5.

You don't have to manually edit the menu.lst file. Instead, when you get to the Grub menu, you can select the Vista choice, then edit the boot commands directly within Grub. You would edit (hd0,2) to some other value, and try it. If Grub doesn't like your change, try again with a different value. it won't hurt.

If you can get it to work, then you will need to manually edit the Grub menu.lst file, for the correct value. (When you change the Grub command line from within Grub, the change is temporary.)

Now, to reassure yourself that Windows is still there, boot to Ubuntu (from hard drive or live CD). Go to the mounted volume where Windows ought to be, and look at the files contained within it. Do you see what you would expect to see (Windows file structure)? If the files are there, then you can get to them one way or another.

Unless you have over-written your Windows files (and I don't think you did), you can expect eventual success.

Um, I definitely deleted my windows files, and everything on my hd except the recovery partition.  I thought that i could just do a clean install!  And i know what ur trying to get at, but do you think that i should just follow the other ppl's advice and reassign the partition numbers (move my extended down, and my sda3 up).  That may actually work.

---

### Post by Herman on 2008-07-11
> A possibility: I recall that in my previous laptop (with XP), the "Windows Genuine" validation apparently measured the starting point of the Windows partition, among other things. I found this out when I moved the partition. Although it still booted, it complained that my copy was not genuine (a phone call to MS solved the problem).:-k Hmmm, interesting. Windows comes with lots of booby traps doesn't it?
I have worked on a few Acer computers and they all seem to be different with regards to their 'Recovery' CDs or partitions. Some Acers I've worked on need three partitions, partition number 1 for the 'recovery' partition, number two for the 'C:/' drive, and a third ('D:/ partition' for the Acer eRecovery program to store files in.  
I found out it's not a good idea to wipe the 'D:/' drive in some Acer computers to install Ubuntu in, Windows will slow to a crawl unless the eRecovery progam is disabled. When a new 'D:/ drive' (partition 3 with a fat32 file system) is created it's possible to re-enable eRecovery and everything will be okay again. 
If Ubuntu is installed it can be in logical partitions, but then it's possible to install Partimage in Ubuntu and make a Partimage backup of the Windows drive. Most people like hving a Partimage backup better than running the recovery program because that way you can restore everything back to an earlier state but with all the added software and settings all in place.  
That brings us back to one of the questions in the original post,
  > Sooo, is there a way to somehow install vista thru the use of ubuntu?Yes, there is if you made a Partimage backup first. 
I have use Partimage backups to restore Windows in people's computers after viruses have destroyed Windows and it's great! :) 
Aysiu, one of the Ubuntu Web Forum moderators, has a nice how-to on Partimage, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage").
When you make a backup with Partimage, it's wise to record the partition size and the partition number too. A partition backup can only be restored to a partition at least as large as the original one or greater. The partition number isn't vital, but it does make things easier if you can restore to the same partition number. 
If you can't restore to the same partition number you will need to edit some files to get the thing to boot and run properly. If it's XP you need to edit boot.ini, if it's Ubuntu you need to edit menu.lst and /etc/fstab.
I don't know very much about Vista.
Booby traps and validation issues would be quite a hazard when working with proprietary operating systems and their software. I didn't know the location of the start of the partition was important in some computers, thanks for that info, Rallg. Is that a new booby trap that will apply to all Windows systems or all Vista installations I wonder? 

apche93, if those ntfs partitions are empty, you might be able to save a lot of time by just deleting your /dev/sda4 and copy your Ubuntu to the middle of that free space somewhere, then make a new extended at the end of the drive and copy Ubuntu and paste it into that. 
Then you can create a new /dev/sda2 and a new /dev/sda3 if those are only empty. Or copy and paste them if they're not.
The main thing to understand is that by copying and pasting your partitions, you are able to change the partition numbers.  I wish there was an easier way, but I don't know of any.
.... unless... TestDisk! 
Hmmm...:idea: We might be able to do it (easily change partition numbers) with TestDisk but I'd have to try that out first and see for myself before I could say for sure.
For now I still think you'll have to copy and paste with a partition editor to fix your partition numbers.

I have also read some reports where a few people claim that we need to use Vista's partition manager for making partitions in a disc with Vista in it. Allegedly there's something different about Vista's partitioning rules. I don't know if that's true or not.
Good reason to switch completely to Linux if it is. There are too many booby traps in proprietaty operating systems, they're becoming unsafe for their users.

---

### Post by Rallg on 2008-07-11
Ah, you wiped Windows, leaving only the recovery? I misunderstood you. In that case, you might as well try re-numbering the partitions, as others have suggested. Might work using Recovery.

Do you remember the original partition configuration? I would guess that everything following Recovery was used for Windows. In that case, it would probably be best to completely remove your present sda2 and higher, leaving only sda1 followed by a large chunk of unallocated space. Then, re-format the unallocated space as a primary partition (not extended) in ntfs format.

You will notice that your present sda1 has a small gap of unallocated space between it and the following extended partition. On your original disk, that gap might not have been there. It could be an artifact of having ntfs followed by non-ntfs in your present configuration.

If getting rid of everything but sda1, then making a new sda2 and filling it with ntfs, does not help: It is possible (only as a last resort) that it MIGHT help to try moving the front of the new sda2, so that the gap disappears.

If the Recovery appears to work, but the recovered Windows does not boot (BIOS gives an error message, no operating system), then you may need to launch GParted from the live CD, and put the boot flag on your new partition.

Herman: I do not know if the start point of the Windows partition is measured in all XP or all Vista. Maybe not. It's my understanding that Windows measures several factors; in my case, I had also changed the size of RAM.

I strongly advise Vista users to first use Vista's own partition manager to shrink the size of the Windows partition, so you can then put Ubuntu into the freed area. Once you have the freed area, you can do whatever you wish with Gparted. Although it might not be "necessary" to do it that way, it sure cannot hurt!

---

### Post by apche93 on 2008-07-11
[IMG]http://i260.photobucket.com/albums/ii30/apche93/Screenshot-3.png[/IMG]

OKay guys,

In live cd, i rearranged the partitions, as shown above.

When i booted the recovery partition, it still said the same message that C: was missing or had low disk space.

Also, with my Windows Xp cd, It said that it couldnt find any hd, and it suggested me to turn on the hd.  

I know that i am in the biggest pickle ever!

---

### Post by apche93 on 2008-07-11
Is there any way that i can use my recovery partition to install vista home premium thru vista?

Could i perhaps install it on a virtual hardisk and somehow transfer those settings over to my newly updated /dev/sda2 ?

Im thinking that is the only certain way to do it.  And even if vista somehow fails to boot, it will automatically go into recovery mode, and from there i will have a C: drive into which i could fix my computer again.

Would that work?

---

### Post by Herman on 2008-07-11
Maybe you should look for exact instructions at your computer manufacturer's website about how to run the recovery partition for your particular make and model of computer.

Even different models and years within the same brand can vary a great deal in the way to run the recovery. Some don't like it if the partitions are already made, they just want a blank hard disk, others need certain files in the 'D:\' partition for some reason.
Maybe you need to create the partitions with Vista's own partition manager for some reason.
Since you don't have a Vista installation CD you can't use Vista from the command line I suppose, to do anything like that. It is possible to get your own [Windows Vista Recovery Disc Download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") from Neosmart.net, thanks lswest for the link. Thanks for the download to Computer Guru, of NeoSmart Technologies (the developer of [EasyBCD]("http://neosmart.net/dl.php?id=1")).
I'm not sure, but if there's a partition editor in that disk you might be able to use that to make your partition table acceptable to Windows Vista. Likely it will delete Ubuntu.

---

### Post by apche93 on 2008-07-12
> **Herman said:**
> 
I'm not sure, but if there's a partition editor in that disk you might be able to use that to make your partition table acceptable to Windows Vista. Likely it will delete Ubuntu.

Hmm,

Do you think that if i copy the contents of the .iso to a flash drive, and then set my bios to boot from my flash drive it can boot into it?  Or is there something else i need to do to make the flash drive bootable?

Also, ive recognized in Gparted that my Recovery partition has a "boot" flag.  What is teh purpose of this?  Like what would happen if i change that flag?

Thankyou everyone for your time and help..Ubuntu forums is really great. I just want to get this sorted out!

---

### Post by Herman on 2008-07-12
> Do you think that if i copy the contents of the .iso to a flash drive, and then set my bios to boot from my flash drive it can boot into it? Or is there something else i need to do to make the flash drive bootable? I don't know. I never mess around with proprietary software.
> Also, ive recognized in Gparted that my Recovery partition has a "boot" flag. What is teh purpose of this? Like what would happen if i change that flag?The boot flag is needed by some versions of Windows and by some BIOSes to 'set the partition as active' and enable Windows to boot. It's a small code in the partition table in the MBR. When we boot with GRUB, the 'makeactive' command is used to make sure the boot flag is set on whichever Windows partition is being booted. It's also possible to set the boot flag with a partition editor. It's only needed by some BIOSes and some Windows systems. Linux boots just as well without it and many computers these days can boot Windows okay withou it too. It was important in DOS, Win95 to 2000 I think, and some XP. I'm not sure if it's needed with Vista. Maybe. Probably it's best to leave it there just to make sure.
Some computers will give the error message, "Error loading operating system" if there's no boot flag in the partition table.

---

### Post by apche93 on 2008-07-12
> **Herman said:**
> 
Some computers will give the error message, "Error loading operating system" if there's no boot flag in the partition table.

Actually, when i tried to install ubuntu right after my vista crashed with the virus, the ubuntu installation said that grub couldnt install.  So, when i restarted, it said that it couldnt load the operating system.  Just some clues...Does that have anythng to do with my problem..


ALSO, you said that if i used that vista recovery cd, that my ubuntu would likely go away. Is this for sure or is it just maybe?

---

### Post by Herman on 2008-07-12
> Actually, when i tried to install ubuntu right after my vista crashed with the virus, the ubuntu installation said that grub couldnt install. So, when i restarted, it said that it couldnt load the operating system. Just some clues...Does that have anythng to do with my problem..It might. 
Normally the main reason GRUB might not be able to install would be if there's some kind of MBR write protection feature turned on in your BIOS. Apart from that, it might only be caused by a problem of some in your Ubuntu installation CD. There was a problem with GRUB for a while in Hardy Heron beta, but you would be using the latest Hardy Heron 'Desktop' Live CD.
> ALSO, you said that if i used that vista recovery cd, that my ubuntu would likely go away. Is this for sure or is it just maybe?     Just maybe, I don't know for sure. It seems like all Windows installation or recovery CDs and all restore partitions are different too. Some will wipe everything off your hard disk completely, others will just wipe the Windows 'C:\' drive.

---

