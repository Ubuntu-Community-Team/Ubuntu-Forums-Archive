---
title: "dual boot ubuntu/vista major problem"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by ferrety on 2008-11-01
Hey all,

I just installed Ubuntu 8.04 on my Dell Inspiron 1720 and can no longer access my Vista install.  I could use some serious help - I've researched this topic online, read countless threads, but have yet to find a problem that exactly matches mine nor a solution that works.

My set up:  two drives, both 320 gig sata.

I had Vista already installed on the first drive - completely up to date as of today, Nov. 11 2008.  That drive is in 2 partitions, Vista on one, apps and data on the other.  I can still see the second partition on that drive in Ubuntu under 'places' and can mount it and see my files.  I don't see, or at least, don't think I can see, the first partition that has/had Vista on it - so can't even attempt to mount it (any ideas?).

During the installation of Ubuntu, I followed the directions on apcmag.com, 
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

One major issue I saw was that the 'migration assistant' was left blank during my install, but I thought that might just be because I was using two different drives, not a single partition.

The first install, I clicked on the 'advanced' settings and selected the Vista Boot Loader (or something like that) option.  This may have been my downfall?  At that point, trying to boot to Vista would simply return me right back to Grub.   I tried a few new grub options based on forum reading and nothing could boot to Vista.  

I finally decided to reinstall Ubuntu, hoping (dreaming) that perhaps a reinstall would reinstall Grub a slightly different way and fix the issue. This time around, however, the install didn't even properly see the two partitions on my first drive (though I'm fairly certain they are still there?) so Grub doesn't have any vista entries.

So now i'm stuck with a super fresh install of Ubuntu, but no way to boot into Vista.

I can't seem to 'recover' my Vista install, either.  When I use my Vista install cd, it does not recognize my drive and prompts me to install my driver CD so it can recognize my hardrive.  I put my dell driver cd in, and it doesn't seem able to find the proper driver... which is strange, since I think it's on there.

the relevant (i think) part of my /boot/grub/ menu.lst is currently:

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0d174e9a-29ae-4313-82a7-1d99fad3d2c7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0d174e9a-29ae-4313-82a7-1d99fad3d2c7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


though I used to have some options in there for vista, but none seemed to work.  i'm more than willing to try options any of you may suggest.

i'm very curious as to whether or not the initial Vista partition is even accessible at this point, but am not savvy enough to figure this out.

I am very much a newbie, and any knowledge I seem to have above is only dangerous knowledge, and based on my forum reading.  So please, if you do have suggestions, step by step instructions would be helpful since I don't really know what I'm doing.

---

### Post by ferrety on 2008-11-01
some basic updates...

i followed the directions here:
[http://ubuntuforums.org/showthread.php?t=675667](http://ubuntuforums.org/showthread.php?t=675667)

it hasn't solved the issue, but I can now provide even more fun info.

In Gparted, I can see two partitions on my vista drive. There is also a mystery 1 meg unallocated, but i don't know if that matters.

the data partition, which i can access through ubuntu, is /dev/sda2

the vista partition is listed as the correct size (about 41 gigs), but has a yellow triangle with an exclamation point in it.  this exclamation point, or whatever is causing it, might be the issue here?

it is listed as /dev/sda1
it has the 'boot' flag set
it is correctly listed as ntsf, with a green box and the aforementioned yellow triangle with ! point.
it's size is correctly listed, but both unused and used space are both listed as '---'


i tried editing my device.map as per the other thread - it used to read:

(hd0)	/dev/sda
(hd1)	/dev/sdb

but I edited it to read

(hd1)	/dev/sdb
(hd0,0)	/dev/sda1
(hd0,1)	/dev/sda2

trying to get it to recognize the other partition.  this doesn't  seem to have worked, so i might have done something wrong.

my menu.lst now reads as
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0d174e9a-29ae-4313-82a7-1d99fad3d2c7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0d174e9a-29ae-4313-82a7-1d99fad3d2c7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry added to get Vista to work
title Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

.....................

and now? it seems to skip the bootloader entirely, flashing me some sort of error message and then booting directly into ubuntu.

help, please, i'm drowning.

---

### Post by caljohnsmith on 2008-11-01
How about opening a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
Also, can you set your BIOS to boot from your Ubuntu drive? Right now you have Grub installed to the MBR (Master Boot Record) of your Vista drive. It would be more ideal to boot from the Ubuntu drive and add Vista to your Grub menu.

---

### Post by ferrety on 2008-11-01
results of sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x62ef356c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    86038527    43018240    7  HPFS/NTFS
/dev/sda2        86038528   625139711   269550592    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000db201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   602341109   301170523+  83  Linux
/dev/sdb2       602341110   625137344    11398117+   5  Extended
/dev/sdb5       602341173   625137344    11398086   82  Linux swap / Solaris


************
>Also, can you set your BIOS to boot from your Ubuntu drive? Right now >you have Grub installed to the MBR (Master Boot Record) of your Vista >drive. It would be more ideal to boot from the Ubuntu drive and add >Vista to your Grub menu.

I'm wondering if I somehow caused it to install the MBR to the vista drive, and caused all this headache?

I know how to get to the BIOS, and I think I could manage changing it to boot from my Ubuntu drive... but wouldn't i need to create some sort of boot record on that drive first?  Or will Ubuntu know what to do?  Are you asking me to just change it in bios and see what happens, or is there a step i should do first?

---

### Post by caljohnsmith on 2008-11-01
> **ferrety said:**
> 
I'm wondering if I somehow caused it to install the MBR to the vista drive, and caused all this headache?

You don't have to blame yourself, because it's not at all your fault :); Ubuntu by default will install Grub to the MBR of (hd0), otherwise known as /dev/sda, which in most cases will be your internal HDD. They do this so you can simply reboot after the installation, and Voila, you should get the Grub menu. The big disadvantage of this though is that your HDDs are now dependent on each other for booting, so if anything happens to either of them (including simply removing the Ubuntu drive), you most likely won't be able to boot at all. It is more ideal if you can set your BIOS to boot the Ubuntu drive on start up, we can install Grub to the MBR of your Ubuntu drive, and then you can boot both Windows/Ubuntu from your Ubuntu drive; the advantage is your drives will be independent, so if you remove your Ubuntu drive, or if anything happens to your Ubuntu drive (or Ubuntu), you will still be able to boot Vista. Of course you will need to reinstall a Windows MBR to your Vista drive though to make it bootable for Vista again. 

Because some BIOSes will refuse to boot a drive that doesn't have at least one partition marked as bootable, please do the following to mark your Ubuntu partition bootable on your sdb drive:
```
sudo fdisk /dev/sdb
```
Press "a", then "1" for the partition, then "w" to write the change.

Next, do the following to install Grub to the MBR of your Ubuntu drive:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Also, you'll need to modify your Grub's menu.lst, so do:
```
gksudo gedit /boot/grub/menu.lst
```
And change all the Ubuntu entries to use (hd0,0) instead of (hd1,0), similar to:
```
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root [COLOR="Red"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=0d174e9a-29ae-4313-82a7-1d99fad3d2c7 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet
```
Also change the line that says "# groot=(hd1,0)" to be:
```
# groot=(hd0,0)
```
And at the end, change your Vista entry to:
```
title	   Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
That should work to boot Vista, but it sounds like you may have some issues with Vista. So when you try and boot Vista from your Grub menu, let me know exactly what happens, and we can work from there. Or let me know if you run into any problems. :)

---

### Post by ferrety on 2008-11-01
first off, thanks so much for your help.  i'll be responding to this post 'as i go'....


> **caljohnsmith said:**
> ...Of course you will need to reinstall a Windows MBR to your Vista drive though to make it bootable for Vista again. 


All of this makes sense.  You are definitely correct, it would be nice to be able to boot to either in case of drive failure.


> **caljohnsmith said:**
> 
Because some BIOSes will refuse to boot a drive that doesn't have at least one partition marked as bootable, please do the following to mark your Ubuntu partition bootable on your sdb drive:
```
sudo fdisk /dev/sdb
```
Press "a", then "1" for the partition, then "w" to write the change.


Results:
The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): a
Partition number (1-5): 1

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.


So I think this worked, but requires a Reboot. I'm not sure if I should be rebooting now, or when everything is done.  I think I'll try doing the rest of the steps first.  Crossing my fingers that this is the right decision.

> **caljohnsmith said:**
> 
Next, do the following to install Grub to the MBR of your Ubuntu drive:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```


This seems to work flawlessly.
grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit

> **caljohnsmith said:**
> 
Also, you'll need to modify your Grub's menu.lst, so do:
```
gksudo gedit /boot/grub/menu.lst
```
And change all the Ubuntu entries to use (hd0,0) instead of (hd1,0), similar to:
```
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root [COLOR="Red"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=0d174e9a-29ae-4313-82a7-1d99fad3d2c7 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet
```
Also change the line that says "# groot=(hd1,0)" to be:
```
# groot=(hd0,0)
```
And at the end, change your Vista entry to:
```
title	   Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```


ok, all changes made.  
cutting and pasting relevant parts for completionist's sake, to make sure i didn't make typos

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

and then, later:

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0d174e9a-29ae-4313-82a7-1d99fad3d2c7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0d174e9a-29ae-4313-82a7-1d99fad3d2c7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry added to get Vista to work
title Windows Vista
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

> **caljohnsmith said:**
> 
That should work to boot Vista, but it sounds like you may have some issues with Vista. So when you try and boot Vista from your Grub menu, let me know exactly what happens, and we can work from there. Or let me know if you run into any problems. :)

Ok.  About to reboot.  Will post back in a few minutes when I have results.  

Thanks again!!

---

### Post by ferrety on 2008-11-01
ok, barely made it back.

so... after making the changes above, and rebooting:

First I see 
'Grub 1.5
Grub Loading please wait'

on the screen.

Then I get

Error 17: Can not mount selected partition
Press any key to continue

When I press a key, It goes to grub

If i select Windows Vista I get:

Error 13: Invalid or Unsupported Executable Format
Press any key to continue

this takes me back to Grub
If i select any of the Ubuntu options, I get
Error 17: Can not mount selected partition

So, at this point, I can't do anything.  I remember you mentioning changing the boot drive in BIOS so I restart.

I hit F2, get into Bios.  I have an Dell Inspiron 1720, BIOS revision A09 if that helps.

And... I can't figure out where I can change the boot drive.  I've looked everywhere, but, hey, I could have missed it.  I did find a boot order option, but it was setting the order of floppy drive, cd, and internal drive... but didn't seem to have any way to indicate which internal drive.  I may be missing something here.  

EDIT: I just fixed this. I was blind - I just had to basically activate the second drive as a possible boot option, and then could 'move' it above the first internal drive. I am now booting directly to second hard drive (Ubuntu) but it never gives me a grub menu, boots directly into ubuntu, and thus no way to test Vista.
END EDIT

Anyway, at this point, I exit out of BIOS, and this time I hit F12 which allows me to indicate what to boot from on the fly.  This DOES have the option (thankfully) to boot from the second internal drive, so I do so, and here I am.

Sorry I don't have better news to report... but at least I was able to get back here to report, grin.

---

### Post by caljohnsmith on 2008-11-01
That's great news you can boot the Ubuntu drive now. The reason why you don't see a Grub menu on start up is most likely because you have the "hiddenmenu" line your menu.lst uncommented. So first pull up the menu.lst again:
```
gksudo gedit /boot/grub/menu.lst
```
Then find the "hiddenmenu" line near the beginning and change it to:
```
#hiddenmenu
```
Reboot, and you should see the Grub menu now. :)

---

### Post by ferrety on 2008-11-01
> **caljohnsmith said:**
> That's great news you can boot the Ubuntu drive now. The reason why you don't see a Grub menu on start up is most likely because you have the "hiddenmenu" line your menu.lst uncommented. So first pull up the menu.lst again:
```
gksudo gedit /boot/grub/menu.lst
```
Then find the "hiddenmenu" line near the beginning and change it to:
```
#hiddenmenu
```
Reboot, and you should see the Grub menu now. :)

(sorry for the slight delay, needed to grab a bite)

OK, now seeing the menu!  and i'm glad everything seems to be moving forward - thanks again.

But when I select Windows Vista I get:

Starting Up..
GRUB Loading Stage 2..

and then it hangs indefinitely.  had to reboot.

---

### Post by caljohnsmith on 2008-11-01
OK, now that you can boot the Ubuntu drive, you can replace Grub in the MBR of your Vista drive with a Windows MBR. To do that:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
[QUOTE=ferrety]OK, now seeing the menu! and i'm glad everything seems to be moving forward - thanks again.

But when I select Windows Vista I get:

Starting Up..
GRUB Loading Stage 2..

and then it hangs indefinitely. had to reboot.[/QUOTE]
So does it hang with that Grub loading message when booting Vista from the Grub menu, or when you boot the Vista drive directly on start up?

---

### Post by ferrety on 2008-11-01
> **caljohnsmith said:**
> OK, now that you can boot the Ubuntu drive, you can replace Grub in the MBR of your Vista drive with a Windows MBR. To do that:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```


done... but nothing seems to have changed.  it still hangs if i boot to vista from ubuntu drive, and i still get error messages per message #7 in this thread if i boot from the vista drive.

> **caljohnsmith said:**
> So does it hang with that Grub loading message when booting Vista from the Grub menu, or when you boot the Vista drive directly on start up?

It hangs booting from the grub menu of my Ubuntu Drive.

---

### Post by caljohnsmith on 2008-11-01
OK, you may need to repair the boot sector of the Vista partition, because it sounds like Grub at one point may have been accidentally installed to the Vista partition boot sector. To fix the boot sector, boot up your Vista Install CD, go to the command line, and do:
```
bootrec /fixboot
```
Also, it is always a good idea to run a chkdsk on the partition to make sure the file system is in good shape, and also to find bad sectors:
```
chkdsk /r
```
Run the chkdsk as many times as it takes until it reports no errors. Also, in case you don't have a Vista Install CD that came with your computer, you can instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). 

After doing the above steps, reboot, and let me know what happens when you select Vista from the Grub menu.

EDIT: Actually, are you getting the Grub error 13 when you boot Vista from the Grub menu? If so, how about also posting:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L. It may be you will get an error from that first command.

---

### Post by ferrety on 2008-11-01
> **caljohnsmith said:**
> 
EDIT: Actually, are you getting the Grub error 13 when you boot Vista from the Grub menu? If so, how about also posting:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L. It may be you will get an error from that first command.

after i do this, i'll go back and use my recovery disk as per the other part of you message and will report back.

yes, i get error 13 from the grub menu when i boot from the vista drive.

here are the results:

sudo mount /dev/sda1 /mnt

returns:
mount: you must specify the filesystem type

ls -l /mnt

returns:
total 0


back soon after using recovery disc.

---

### Post by ferrety on 2008-11-01
> **caljohnsmith said:**
> OK, you may need to repair the boot sector of the Vista partition, because it sounds like Grub at one point may have been accidentally installed to the Vista partition boot sector. To fix the boot sector, boot up your Vista Install CD, go to the command line, and do:
```
bootrec /fixboot
```
Also, it is always a good idea to run a chkdsk on the partition to make sure the file system is in good shape, and also to find bad sectors:
```
chkdsk /r
```
Run the chkdsk as many times as it takes until it reports no errors. Also, in case you don't have a Vista Install CD that came with your computer, you can instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). 

After doing the above steps, reboot, and let me know what happens when you select Vista from the Grub menu.



ok, not having too much luck with this.  

when i first get to the main screen and select 'recovery', it gives me a list of 'vista' drives, and none are listed.  there is a message that if none are listed, i need to install drivers.  so i insert my driver cd, and i'm pretty sure i'm loading up the right drivers, but nothing shows up in the list anyway

i ultimately just selected 'next', which brings me to a menu and select command prompt.  

worth noting - while i can change to drive D: and see my data partition and folders and files, when i try to switch to drive c: (the first partition on that drive, vista) i get the following message:

the volume does not contain a recognized file system.  please make sure that all required file system drivers are loaded and that the volume is not corrupted.

as another side note, i went back to ubuntu and gparted says that both partitions are ntsf, though i still can't seem to mount the first partition in ubuntu (though i can mount/view the data partition).

anyway, bootrec /fixboot initially gave me a 'success' type message, but it didn't fix anything.  i'm also concerned the drive was set wrong or something (it was defaulted to x:) because when i tried chkdsk immediately aftwards i got an error about it being write protected... which makes me wonder if i ran bootrec /fixboot on the cd/dvd drive or something.  that's when i tried changing to the c: drive and got the error message above.

soo... i'm confused.  both ubuntu and even the vista recovery install disc recognize my data partition, but none seem to recognize my vista partition.

confused.  i don't even know if i successfully ran bootrec as requested or not.

---

### Post by caljohnsmith on 2008-11-01
What you say unfortunately doesn't surprise me, because when you tried to mount sda1 with that command I gave, the mount command didn't recognize sda1 as a valid NTFS partition or it would have mounted it OK. Before getting too worried though, how about first trying the following from Ubuntu to repair Vista's boot sector:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows Vista partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, then do:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt
```
If that returns an error, then try:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt -o force
```
If either of the commands work, then please post:
```
ls -l /mnt
```
And if that shows your Vista root directory, go ahead and reboot and try Vista again from the Grub menu.

---

### Post by ferrety on 2008-11-01
strange issue.

I've successfully installed testdisk, however, when I run it if I select /dev/sda it looks like it's crashing out of testdisk to the command prompt.

If I select /dev/sdb I get the next option as you mention, though since that's not the right drive I quit out of terminal.  I've tried several times, and I get crashed out to command prompt every time. 

Kind of scary that an app made for drive problems crashes out due to some sort of drive problem... any ideas?

Also, thanks. again. do you accept presents?

---

### Post by caljohnsmith on 2008-11-01
> **ferrety said:**
> strange issue.

I've successfully installed testdisk, however, when I run it if I select /dev/sda it looks like it's crashing out of testdisk to the command prompt.

If I select /dev/sdb I get the next option as you mention, though since that's not the right drive I quit out of terminal.  I've tried several times, and I get crashed out to command prompt every time. 

Kind of scary that an app made for drive problems crashes out due to some sort of drive problem... any ideas?
Yikes, that's not a good sign. I think it would be good to run some HDD diagnostic tests on sda (if they will even be able to test sda), because you might have a hardware issue at this point. You can download and use the [Ultimate Boot CD]("http://www.ultimatebootcd.com"), because that has lots of great HDD diagnostic programs for testing your HDD's health. 

Also, was Vista working perfectly OK up until the moment you tried to install Ubuntu? Have you had any other problems with Vista? Any other clues you can give that might have led to your unfortunate circumstances would help to diagnose the problem. 
> **ferrety said:**
> 
Also, thanks. again. do you accept presents?
You're most welcome, I try to help out when I can. About a present, I assume you are saying that tongue-in-cheek; but thank you so much for the offer, it really isn't necessary. :)

I have to leave now and won't be around until tomorrow morning some time, so we can pick up then. Until then, good luck and let me know what the HDD tests results are. :)

---

### Post by ferrety on 2008-11-02
> **caljohnsmith said:**
> Yikes, that's not a good sign. I think it would be good to run some HDD diagnostic tests on sda (if they will even be able to test sda), because you might have a hardware issue at this point. You can download and use the [Ultimate Boot CD]("http://www.ultimatebootcd.com"), because that has lots of great HDD diagnostic programs for testing your HDD's health.

burning the cd now (second attempt, the first iso i dl'd was corrupt).  I'll run some tests that seem applicable, but if there are any specific ones i should run let me know.
 
> **caljohnsmith said:**
> 
Also, was Vista working perfectly OK up until the moment you tried to install Ubuntu? Have you had any other problems with Vista? Any other clues you can give that might have led to your unfortunate circumstances would help to diagnose the problem. 


Yep, Vista was working just fine.  I actually did a clean install about a month ago (with a lot of after-install tweaking) in preparation for getting a second drive and having a dual boot install.  No problems whatsoever, until I installed Ubuntu.

I can't imagine Ubuntu caused a hardware issue, and... it's just seems too coincidental for a hardware issue to crop up during the Ubuntu install.  My completely uneducated guess is that the boot record got corrupted or something? I don't know.  Hopefully the Universal Boot CD will shed some light.    

> **caljohnsmith said:**
> 
You're most welcome, I try to help out when I can. About a present, I assume you are saying that tongue-in-cheek; but thank you so much for the offer, it really isn't necessary. :)


Nah, I was serious. Your help is very much appreciated.  If you PM me your address, I'll send you something.

This entire... episode has been completely fraught with nightmarish level problems.  I spent over 20 hours on the phone with Dell trying to get the right parts to install my second hard drive (needed a dell specfic caddy and an interposer), but a) nobody knew what i was talking about, and b) when i finally got sent the parts, they were for a desktop computer.  Trying to tell Dell they had the wrong parts in the system for a secondary drive for a 1720 was... futile. They still insist an interposer that's obviously for a 3.5 drive will fit a 2.5 drive. I finally ordered the caddy for the primary slot, and bent the metal so it fit in the secondary slot and ordered an interposer for a different system that has a 2.5" drive and got the correct one.  I'm ranting now, but honestly, i'm giving the simplified version and leaving out 20+ hours of hang ups, permanent holds, and circular transfers between ordering, tech support, and customer care.  They even tried to charge me $60 to have their tech support explain to me how to install a 3.5" interposer on a 2.5" drive. Morons.

The point is - your help is an oasis.  Seriously. 


> **caljohnsmith said:**
> 
I have to leave now and won't be around until tomorrow morning some time, so we can pick up then. Until then, good luck and let me know what the HDD tests results are. :)

Will do. CD done burning now...

---

### Post by ferrety on 2008-11-02
Ok, I'm honestly at a loss as to what to do with the Universal Boot CD.  I've launced into a couple different diagnostic programs, but couldn't seem to get them up and running.  Any specific ones you'd like me to run?

EDIT TO ADD:
would a corrupt boot sector affect the first partition on the drive in anyway?
i ask because I just booted (yet again) into window recovery. when i click on repair, it doesn't recognize any vista drives and asks to install drivers.  I inserted my driver cd, but then realized i could explore the file system.  I was able to go up to computer, and could see the various partitions -- my data partition was clearly visible, with used/unused space, etc.  The C: drive, however, was showing but didn't have this information.  When I tried to click into it to see if i could see files, it told me i would need to format the partition.

So.. it may be that this entire partition is now corrupt in some way. Would this be a result of the boot sector? Or is it a separate issue?  

also worth noting - at some point, if we (as in  you) deem this an impossible recovery, i could always reinstall vista.  i'm not really looking forward to that, but as my wife pointed out, i've already spent tons of time trying to avoid that, so i might as well spend it doing it.

---

### Post by caljohnsmith on 2008-11-02
[QUOTE=ferrety]This entire... episode has been completely fraught with nightmarish level problems. I spent over 20 hours on the phone with Dell trying to get the right parts to install my second hard drive (needed a dell specfic caddy and an interposer), but a) nobody knew what i was talking about, and b) when i finally got sent the parts, they were for a desktop computer. Trying to tell Dell they had the wrong parts in the system for a secondary drive for a 1720 was... futile. They still insist an interposer that's obviously for a 3.5 drive will fit a 2.5 drive. I finally ordered the caddy for the primary slot, and bent the metal so it fit in the secondary slot and ordered an interposer for a different system that has a 2.5" drive and got the correct one. I'm ranting now, but honestly, i'm giving the simplified version and leaving out 20+ hours of hang ups, permanent holds, and circular transfers between ordering, tech support, and customer care. They even tried to charge me $60 to have their tech support explain to me how to install a 3.5" interposer on a 2.5" drive. Morons.[/QUOTE]
I can totally understand your frustration with your tech support fiasco, because I've run into the same circus myself when dealing with tech support sometimes. :roll:
[QUOTE=ferrety]
The first install, I clicked on the 'advanced' settings and selected the Vista Boot Loader (or something like that) option. This may have been my downfall? At that point, trying to boot to Vista would simply return me right back to Grub. I tried a few new grub options based on forum reading and nothing could boot to Vista.[/QUOTE]
You mentioned what's above in your original post. If booting Vista from the Grub menu returned you to the Grub menu, that's usually a classic symptom of accidentally installing Grub to the boot sector of the Vista partition; thus when Grub goes to boot Vista, Grub just boots itself again and reloads its boot menu. That is usually easily fixable by doing what you previously tried to do (with no success):
```
bootrec /fixboot
```
But since your Vista partition is not even recognized nor mountable at this point, it seems you have more serious problems. 

One last thing I would try is to boot your Ubuntu Live CD, and try running testdisk from there. It might be it won't crash, and you'll maybe be able to fix the Vista boot sector. If that doesn't work, I would still go ahead and run a HDD diagnostic test on your HDD just to make sure that your HDD's health is not the issue; since your data partition on that drive seems to be fine, it's not likely you have a hardware problem, but it wouldn't hurt to check at this point. From the Ultimate Boot CD, just select "Hard Disk Tests", then "Diagnostic Tools", and pick one of the programs that matches the manufacturer of your HDD if possible. 

If the HDD test doesn't turn up anything, then I think your wife is right; I think reinstalling Vista is about the only realistic option left. Let me know how it goes. :)

---

### Post by meierfra. on 2008-11-02
> **caljohnsmith]After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows Vista partition, choose "boot", then choose "Rebuild BS" said:**
> 

"Rebuild BS" won't be able to recover your boot sector. It only changes a few numbers associated to the file system. 

Instead  of (or in addition to) "Rebuild BS" choose "Backup BS".

[QUOTE=caljohnsmith] One last thing  I would try is to boot your Ubuntu Live CD, and try running testdisk from there. 
testdisk is also on Ultimate Boot CD:
Start->Programs->Disk Tools->Partition->Testdisk

---

### Post by ferrety on 2008-11-02
> **meierfra. said:**
> 
testdisk is also on Ultimate Boot CD:
Start->Programs->Disk Tools->Partition->Testdisk

It's actually worth noting that I discovered Testdisk on the Universal Boot CD last night... and I had nearly the same issue.  This time, it would let me select the drive, but as soon as I tried to do any test (I think the option was 'Analyse', Testdisk would crash to a (useless) command prompt.

So whatever problem I do have seems very capable at crashing Testdisk. 

I'll try running Testdisk from the Ubuntu cd and report back.

I'm simply stumped at what could possibly have happened here, and how a partition I didn't even install Ubuntu on could have been corrupted.

> **caljohnsmith said:**
> 
But since your Vista partition is not even recognized nor mountable at this point, it seems you have more serious problems. 

One last thing I would try is to boot your Ubuntu Live CD, and try running testdisk from there...

If the HDD test doesn't turn up anything, then I think your wife is right; I think reinstalling Vista is about the only realistic option left. Let me know how it goes. :)


Your Grub explanation makes sense.

The first Ubuntu install I could definitely 'see' the vista partition.  The second one... couldn't.

Do I need to do anything special if i get to the point of installing Vista, now that i have Ubuntu on this drive?

---

### Post by caljohnsmith on 2008-11-02
Did you have any better luck running testdisk from the Live CD? I would guess not. Could your Vista HDD maybe have a loose cable or something? Can you reseat its cable connections? That might help. Also, just to check, let's see if you can mount the data partition OK:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt
```
Let me know if that lists the contents of your sda2 root directory.

---

### Post by ferrety on 2008-11-02
> **caljohnsmith said:**
> 
One last thing I would try is to boot your Ubuntu Live CD, and try running testdisk from there. It might be it won't crash, and you'll maybe be able to fix the Vista boot sector. 

I'm currently running from CD.  How do I run Testdisk from here?

Trying to apt-get it results in errors (likely due to me running from CD) but I can't see to find it already installed in any of the menus.

The program 'testdisk' is currently not installed.  You can install it by typing:
sudo apt-get install testdisk
You will have to enable the component called 'universe'
bash: testdisk: command not found

ubuntu@ubuntu:~$ sudo apt-get install testdisk
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by caljohnsmith on 2008-11-02
You need an internet connection to download and use testdisk from the Live CD, and also you will need to enable all your repositories in System > Admin > Software Sources (or just enabling the Universe repository should be enough). That error you got when using apt-get is because most likely there is some other package management program open, like Synaptic or something. If you don't have internet when using the Live CD, then don't worry about it, I really doubt running testdisk from the Live CD will be any different. How about trying the steps from post #23 and letting me know the results.

---

### Post by ferrety on 2008-11-02
> **caljohnsmith said:**
> You need an internet connection to download and use testdisk from the Live CD, and also you will need to enable all your repositories in System > Admin > Software Sources (or just enabling the Universe repository should be enough). That error you got when using apt-get is because most likely there is some other package management program open, like Synaptic or something. If you don't have internet when using the Live CD, then don't worry about it, I really doubt running testdisk from the Live CD will be any different. How about trying the steps from post #23 and letting me know the results.

I do have internet, but i rebooted into regular Ubuntu to run the tests you asked.

and, now, I'm getting the following error message when trying to mount the second partition.  it's worth noting i HAVE mounted it several times during these posts (directly from the Places menu).  I must have left it in use somehow before shutting down?  Wouldn't shutdown automatically unmount mounted drives?  

Well, I'm sure this one is an easy fix - as mentioned, I've definitely perused this second partition from Ubuntu yesterday.

Should I run the force option detailed below?

******

Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /mnt ntfs-3g force 0 0

---

### Post by caljohnsmith on 2008-11-02
You could run the force option with mount, but I think I would actually recommend using a program called "ntfsfix" on it to clean it up and make it mountable:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
```
Then try mounting the sda2 partition again. If that doesn't work then go ahead and try the force option:
```
mount -t ntfs-3g /dev/sda2 /mnt -o force
```

---

### Post by ferrety on 2008-11-02
> **caljohnsmith said:**
> You could run the force option with mount, but I think I would actually recommend using a program called "ntfsfix" on it to clean it up and make it mountable:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
```
Then try mounting the sda2 partition again. If that doesn't work then go ahead and try the force option:
```
mount -t ntfs-3g /dev/sda2 /mnt -o force
```

that fixed it, i was able to mount, and ls correctly shows my folders for the second partition.

this may be a goofy idea, but would running ntfsfix on the first partition make any sense?

---

### Post by caljohnsmith on 2008-11-02
> **ferrety said:**
> that fixed it, i was able to mount, and ls correctly shows my folders for the second partition.

this may be a goofy idea, but would running ntfsfix on the first partition make any sense?
You can always try, but I'm almost positive it will just give you an error. :) Ntfsfix won't fix a corrupted partition; it just does a little basic "housekeeping" with the NTFS file system, mainly to clean up Windows partitions that were "uncleanly shutdown". 

It really sounds like your sda1 partition is basically beyond repair at this point. Since we don't know for sure how it got that way, I still think it would be prudent to at least run a HDD diagnostic test on your HDD to make sure that's not the issue. You can do it from Ubuntu in the command line if you want:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And let me know the results.

---

### Post by ferrety on 2008-11-02
> **caljohnsmith said:**
> ...And let me know the results.

CONTENTS OF THE 'BEFORE' FILE:

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3200BEKT-22F3T0
Serial Number:    WD-WXE708PX5513
Firmware Version: 11.01A11
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Nov  2 10:23:41 2008 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (8400) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 100) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   177   176   021    Pre-fail  Always       -       2116
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       113
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       181
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       89
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       16
193 Load_Cycle_Count        0x0032   198   198   000    Old_age   Always       -       6500
194 Temperature_Celsius     0x0022   108   102   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.



CONTENTS OF THE 'AFTER' FILE:

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3200BEKT-22F3T0
Serial Number:    WD-WXE708PX5513
Firmware Version: 11.01A11
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Nov  2 11:56:32 2008 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (8400) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 100) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   177   176   021    Pre-fail  Always       -       2116
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       113
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       183
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       89
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       16
193 Load_Cycle_Count        0x0032   198   198   000    Old_age   Always       -       6504
194 Temperature_Celsius     0x0022   101   100   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       183         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.



> **caljohnsmith said:**
> Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And let me know the results.


sudo smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

---

### Post by caljohnsmith on 2008-11-02
At least that's great news about the HDD test results; everything looks really good from what I can see. Maybe meierfra might have some other ideas of what you could do to fix the Vista partition, but if he doesn't, I think a reinstall is about the only option left. After the reinstallation, it might be a good precaution to run testdisk on the drive again and make sure testdisk doesn't crash or find any problems with the partition table; that would be at least a little insurance against future problems. Anyway, good luck and let me know how it goes. :)

---

### Post by meierfra. on 2008-11-02
Let's see whether "bootsec" can fix your Vista's boot sector:

Boot to the Vista CD commandline.

Type

```
diskpart
```

and then

```
list volume
```

This will list all the partitions and their drive letters.  Take  note of the drive letter of your Vista partition and of  your CDrom drive.

type 

```
exit
```

to exit  "diskpart". Then

```
X:\boot\bootsect.exe  /nt60  Y:
```

here  X needs to be replaced the drive letter of your CDrom drive and
Y by the drive letter of your Vista partition.

---

### Post by ferrety on 2008-11-02
meierfra. --- thanks for the reply, but sadly I had already begun the Vista reinstall before you posted. 

> **caljohnsmith said:**
> At least that's great news about the HDD test results; everything looks really good from what I can see. Maybe meierfra might have some other ideas of what you could do to fix the Vista partition, but if he doesn't, I think a reinstall is about the only option left. After the reinstallation, it might be a good precaution to run testdisk on the drive again and make sure testdisk doesn't crash or find any problems with the partition table; that would be at least a little insurance against future problems. Anyway, good luck and let me know how it goes. :)

I have reinstalled successfully.  I'll have to re-tweak, and reinstall all my applications, but as of now I can successfully dual boot.  Yea!  Thanks SO much for all your time and energy, it's appreciated.

I do have a question while I have your attention, that is mildly related to this whole problem.  If proper etiquette here dictates I should start a new thread, I can do that - it's just that the issues in this thread influence my options.

The issue - since this episode seems to be of the infinite headache variety, I just discovered that in about a weeks time I'm going to need to swap my 320 gig Ubuntu drive for an 80 gig drive.   

I'm not going to be doing a whole lot in Ubuntu this week, so a clean install isn't the end of the world, but i'm currently scared to death a clean install will cause the same problem to repeat itself (that is, somehow damaging my Vista drive partition)

Is there an easy way for me to avoid this?  Can I somehow create an image of the data on my 320 gig and copy it to the 80gig (even if this requires temporarily switching out my Vista drive)?

Or should I just do the clean install and consider this time around a freak incident?

EDIT: or possibly take the vista drive out while installing on the 80 gig, then fixing menu.lst aferwards?  Though I fear I'd render something unbootable if i did this.

---

### Post by caljohnsmith on 2008-11-02
> **ferrety said:**
> 
The issue - since this episode seems to be of the infinite headache variety, I just discovered that in about a weeks time I'm going to need to swap my 320 gig Ubuntu drive for an 80 gig drive.   

I'm not going to be doing a whole lot in Ubuntu this week, so a clean install isn't the end of the world, but i'm currently scared to death a clean install will cause the same problem to repeat itself (that is, somehow damaging my Vista drive partition)

Is there an easy way for me to avoid this?  Can I somehow create an image of the data on my 320 gig and copy it to the 80gig (even if this requires temporarily switching out my Vista drive)?

Or should I just do the clean install and consider this time around a freak incident?

EDIT: or possibly take the vista drive out while installing on the 80 gig, then fixing menu.lst aferwards?  Though I fear I'd render something unbootable if i did this.
Personally I wouldn't be afraid to do a reinstall of Ubuntu if I were you, because I really do think that whatever happened to Vista was entirely out of the ordinary and shouldn't happen again if you are careful. If you do a reinstall, just make sure to click the "advanced" button near the end of the installation process and tell Grub to install to /dev/sdb or whichever is the new drive; just don't select /dev/sda or (hd0), or any partitions either, and you should be just fine. Removing the Vista drive of course would be the ultimate insurance to prevent anything from happening during a reinstall of Ubuntu, but I don't think it is really necessary. 

Since your Ubuntu partition on the 320 GB disk can't be simply cloned over to your new drive since the new drive is only 80 GB, if you first create a partition on the new drive for Ubuntu, it is possible to copy over the entire Ubuntu file system instead. If you do that you have to modify some Ubuntu system files to actually get it all working, but I've used that method myself successfully so I know it works. If you haven't done a lot of tweaking/customizing in Ubuntu though, a clean install might be the better solution. Good luck and let me know how it goes. :)

---

