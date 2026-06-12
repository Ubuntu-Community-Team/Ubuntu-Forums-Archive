---
title: "installed 8.04 and can not boot windows..."
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by chrisneedshelp on 2008-05-03
I am a first time user, and once getting ubuntu loaded i love it, but i want to dual boot with my XP system as well.

I have two sata hdd's, one for XP and the other for Ubuntu.

XP is first Sata device, Ubuntu is second device.

I understand this is a grub file problem, i have verified that the bios settings are in agreeance with the physical connections on the mobo.

I have tried following instructions on other threads for sudo grub/...stage1 etc...that did not help or change anything.

My problem started b/c when I loaded ubuntu, since the two hdd's are identical, i took the windows drive out of the system to ensure i didn't format over it...

so after figuring out how to id them, i reloaded ubuntu w/ the windows drive in the system, and it boots with error 17, unable to mount selected partition, and gives me option only to load ubuntu, but is unable to do so...

please help!!!!

---

### Post by chrisneedshelp on 2008-05-03
oh, and my menu.lst file is a blank file with nothing at all in it.

my 'sudo fdisk -l' reads as 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xa72d6376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7cad7ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59859   480817386   83  Linux
/dev/sdb2           59860       60801     7566615    5  Extended
/dev/sdb5           59860       60801     7566583+  82  Linux swap / Solaris

---

### Post by chrisneedshelp on 2008-05-03
oops, got menu file, added windows, hd(0,0) and rebooted from live, now for ubuntu partitions i have

error 17: can not mount selected partition

for windows partition I get 

error 13: invalid or unsupported executable format


can not boot machine at all

---

### Post by Herman on 2008-05-03
:) Hello chrisneedshelp,

You need to make sure you use the proper 'syntax' (computer word for 'punctuation and spelling'), when you type things in your /boot/grub/menu.lst file.
Where you have: 'hd(0,0)' in your Windows boot stanza, you should change that to: '(hd0,0)' instead, (without the inverted commas). The location of the brackets could be the cause of your GRUB Error 13 

In the Ubuntu boot stanza, check that the partition number isn't (hd0,0) as well, because the hard drive you have Ubuntu on was the only hard drive when you installed, so it would have been the first hard disk at that time.
Now, it's the second hard disk, so you probably need to change the number there from (hd0,0), to (hd1,0), I am guessing.

---

### Post by chrisneedshelp on 2008-05-03
I had switched the drive connections on the sata ports and enabled Ubuntu load, but still get error trying to load windows

I had the menu list file reading as

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic
root=UUID=2f907e7d-3c51-4693-ab7a-2210c2da754b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic
root=UUID=2f907e7d-3c51-4693-ab7a-2210c2da754b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Microsoft Windows XP Home Edition
root 		(hd0,0)
makeactive
savedefault
chainloader 	+1


I then changed it to(as per your suggestion) 


## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic
root=UUID=2f907e7d-3c51-4693-ab7a-2210c2da754b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic
root=UUID=2f907e7d-3c51-4693-ab7a-2210c2da754b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Microsoft Windows XP Home Edition
root 		(hd1,0)
makeactive
savedefault
chainloader 	+1


and i got the 13 and 17 errors back, unable to boot in ubuntu or windows.  booted live and restored menu.lst file to previous settings.

At this time i am able to boot to ubuntu without errors, however I can not boot to windows, or see the windows hdd from ubuntu, the bios does see both hdd's.  when I load grub at start up, if i choose ubuntu or windows, I get ubuntu loading

I have read in other posts something of a mkdir command?  can this help me at all?

if i hit f11 during post(choose load device) and choose the ubuntu hdd all works like normal turn on, if i choose the windows hdd i get the 13/17 errors again, as though the hd1/hd0 settings for the two hdd's are backward...please tell me I didn't hurt my windows hdd, i have some files on there that i really need:(

---

### Post by Herman on 2008-05-04
:) Okay, decide which hard drive you want to be the first hard drive and once you have made that decision, stick with it, for the time being at least. (At least while I'm trying to help you). :)
If you make the Ubuntu hard drive the first hard drive, you should be able to boot Ubuntu okay, and you can use a pair of 'map' commands to boot Windows with on the second hard drive.
If you make the Windows hard drive the first hard drive, you'll probably need to re-install GRUB and edit your /boot/grub/menu.lst file again.

Now, take a look on your motherboard and plug your first hard drive into the number one port and the number 2 hard drive into the number 2 port.

Then, boot up and go into your BIOS and check the hard disk order in there.
Make sure your first hard drive is listed there as the first and your second hard drive is second, in your BIOS hard disk order.

Then, when you have that straightened out, boot Ubuntu your Ubuntu Live CD and run 'sudo fdisk -lu' again.

This time don't unplug anything or change anything in your BIOS until I have time to help you again with your menu.lst file, if you still need help.

---

### Post by chrisneedshelp on 2008-05-04
done done and done...the 'sudo fdisk -lu' gives back

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7cad7ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   961634834   480817386   83  Linux
/dev/sda2       961634835   976768064     7566615    5  Extended
/dev/sda5       961634898   976768064     7566583+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa72d6376

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976770143   488385040+   7  HPFS/NTFS


and my menu.lst has ubuntu as hd1 and windows as hd0

it seems to me that that may not be what it should, but is the way it seems to work....at least for ubuntu

oh, and thank you so much for your help!

---

### Post by Herman on 2008-05-04
```
## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-15-generic
root         (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root         (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root         (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```:) Okay, good.
So here's what should work, you won't be able to use this example menu.lst because the UUID numbers will be wrong for you, but this is how I think your menu.lst file needs to be edited as far as the (hd0,0) and (hd1,0) and map commands are concerned.
.
If that doesn't work, then reverse your hard disk order in your BIOS and see what happens. :)

---

### Post by chrisneedshelp on 2008-05-04
okay, so i made the chages of hd(0,0) and hd(1,0) and added the map commands...this cause me to get the error 13 on windows attempt and error 17 on ubuntu attempt again...after switching the bios order it will not load windows, but it changed somewhat...instead of giving an error, it says 

starting up....
GRUB loading stage2

and just freezes there...


arg!!!  really hoped that would work...

---

### Post by Herman on 2008-05-04
:) Okay, good!

Sorry it isn't booting yet, but at least it's trying to load stage2.

I think you have some kind of corruption in your GRUB files.
If you have switched your hard drive order in your BIOS now your Ubuntu disk is your second hard disk again, is that right?

So, Ubuntu will be /dev/sdb1 now right?

One thing you can try is booting your Ubuntu Live CD and running 'sudo e2fsck -C0 -p -v -f /dev/sdb1'
```
sudo e2fsck -C0 -p -v -f /dev/sdb1
```
Where: /dev/sdb1 is your Ubuntu partition, if that's not it then pleasse replace that number with whatever is correct

Do you have a Super Grub Disk? If you don't can you download one and burn it to CD or make a Super Grub Floppy or USB or whatever?
Because if the file system check doesn't fix it we'll re-install GRUB, this time including the GRUB files in /boot.

---

### Post by chrisneedshelp on 2008-05-04
ubuntu is currently sda1, so i made that change, ran the code that you supplied, output was 

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -v -f /dev/sda1
                                                                               
  110426 inodes used (0.37%)
     316 non-contiguous inodes (0.3%)
         # of inodes with ind/dind/tind blocks: 4896/37/0
 1537212 blocks used (1.28%)
       0 bad blocks
       1 large file

   82632 regular files
   11803 directories
      69 character device files
      26 block device files
       2 fifos
       0 links
   15876 symbolic links (15100 fast symbolic links)
       9 sockets
--------
  110417 files


rebooting now


i was going to download the super grub disk, i went here:
[http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/usb/](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/usb/)
for a usb download, but idk what of that list i should download, or do i need all of it, or any one of them?


no change at all after reboot

---

### Post by Herman on 2008-05-04
You can use any GRUB, but Super Grub Disk is very good and it's only a very small download and it's free.
It's easier for most people to use the CD, but if you have a floppy disc drive then you can use the floppy version of Super Grub Disc, or, if you want, you can use the USB version. The USB is probably the hardest to make, and not ever computer can boot a USB, but some computers don't have a floppy drive, and maybe the CD/DVD drive is not working, so the USB is good sometimes.

Make whichever one suits you and your computer.

---

### Post by chrisneedshelp on 2008-05-04
okay, so i'm trying to make the cd one, and i actally successfully made it, but have the wrong hd numbers for the cd drive, and i'm not entirely sure what they should be....

---

### Post by Herman on 2008-05-04
Whatever Super Grub Disk you get, boot it and take a look around in it if you want.
There are lots of useful tricks it can do.
Right now we just want to boot Ubuntu with it.
You should be able to boot Windows with it too, any time you want, but the main thing for now is to get into Ubuntu so we can fix your Ubuntu's GRUB.

Look for somewhere that says 'boot Gnu/Linux Directly', I think that's in 'Gnu/Linux' there somewhere, it used to be.

If you can't find it, just press your 'c' key from any menu for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")..

Then type 'find /vmlinuz'
```
find /vmlinuz
```, and GRUB should say, (hd1,0)
If so, type,
```
root (hd1,0)
```Type,
```
kernel /vmlinuz root=/dev/sdb1
``````
initrd /initrd.img
``````
boot
```...and Ubuntu should boot!
If you need help let me know.
Let me know when you get to that stage and I'll tell you what to do next.

---

### Post by Herman on 2008-05-04
> okay, so i'm trying to make the cd one, and i actally successfully made it, but have the wrong hd numbers for the cd drive, and i'm not entirely sure what they should be....:confused: Hey, wait a minute - what?

Is your CD/DVD drive plugged in and jumpered correctly, that can affect booting too you know.

---

### Post by chrisneedshelp on 2008-05-04
yeah, the cd drives are fine, i just don't know how they are read by linux, both my cd drives are ide and jumpered for cable select, windows reads them as e and f

i loaded up to the grub loader and did the commands you listed, it did what you showed it would, still no changes in booting though, boot to ubuntu is good as it has been, boot to windows freezes at 2

oh, and when i did 'find /vmluniz it came back '(hd0,0), so i ran the script with hd0,0 and sda1 vice sdb1

---

### Post by MongooseCage on 2008-05-04
> **chrisneedshelp said:**
> okay, so i made the chages of hd(0,0) and hd(1,0) and added the map commands...this cause me to get the error 13 on windows attempt and error 17 on ubuntu attempt again...after switching the bios order it will not load windows, but it changed somewhat...instead of giving an error, it says 

starting up....
GRUB loading stage2

and just freezes there...


arg!!!  really hoped that would work...


I am a noob, but have you tried Super Grub Disk? Because that should help, I am not able to follow up but I am supposing that you are getting locked up around GRUB. Super Grub Disk seems to work everytime if you need to replace your GRUB  bootloader

---

### Post by chrisneedshelp on 2008-05-04
i have not tried a super grub disk, mainly as i do not no how.  I tried to make one, but i do not know how to designate my cd drive (ie hd0,0 or whatever it sould be) so it's not functional, or at least i don't think it is in my limited knowledge...

---

### Post by Herman on 2008-05-04
> i loaded up to the grub loader and did the commands you listed, it did what you showed it would, still no changes in booting though, boot to ubuntu is good as it has been, boot to windows freezes at 2

oh, and when i did 'find /vmluniz it came back '(hd0,0), so i ran the script with hd0,0 and sda1 vice sdb1 	
:) Alright, so by the sounds of it you have Ubuntu booing okay as (hd0,0) now and you just need to be able to boot Windows, is that right?

And When you try to boot Windows, you're getting 
'starting up....
GRUB loading stage2

and just freezes there...'

If that's right that sounds like you need to run FIXMBR and BIXBOOT on your Windows drive, I don't know how GRUB could have been installed in your Windows hard drive or parition if you had it unplugged when you installed? ...oh well.

---

### Post by chrisneedshelp on 2008-05-04
YES!!!  exactly true

so, how do i do FIXMBR and BIXBOOT?

---

### Post by Herman on 2008-05-04
You put your Windows XP installation CD in and boot your PC and go into the [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), choose to work on Drive C and run FIXMBR and FIXBOOT.

Here's a link to lswest and bodhi.zazen's thread about boot sectors and MBRs, [**HOW-TO restoring XP and Vista Bootloader & Restoring GRUB**]("http://ubuntuforums.org/showthread.php?t=740221")

I'm just guessing you need to do that, because you are having a GRUB problem when you chainload Windows boot sector. I would expect Windows to boot ir give a Windows error. You're getting a GRUB error about not being able to find stage2, so I'm guessing GRUB must be installed in your Windows boot sector. Again, I can't imagine how that could possibly have happened.

---

### Post by Herman on 2008-05-04
Oh yeah, about your Super Grub Disk download, first you might have to extract the .iso from the compressed file if you downloaded a compressed file. to do that,you right-click on it and click 'extract here', and you should see an .iso file appear somewhere..

To burn an .iso file to a CD in Ubuntu you just put a blank CD in your CD drive. 
If the Ubuntu detects your blank CD and opens the CD-writer which offers to make a data disk for you, just ignore it and click off it, (close it), we don't want a data disk. 
Go look for your .Super Grub Disk .iso file you downloaded and right-click on it and click 'burn to disk'.
If your CD is a CD-RW and you have old data on it you want to erase, don't worry about it, just put it in the way it is and Ubuntu will let you know it has something on it in case you want to exchange it for another disc or offer to erase it for you. 
I always burn software discs at the slowest possible speed, which is still fast enough for me.

In a minute or so you should have a Super Grub Disk CD.

If we still have trouble booting Windows or if you don't have a Windows Installation CD, you should be able to use Super Grub Disk to boot your Windows for you, and/or fix it if that's what's needed.

---

### Post by chrisneedshelp on 2008-05-04
so, i had figured out the fixmbr, but being tired i screwed it up and accidently did it to the ubuntu drive...oh yeah, it's hosed now

so then i just took that drive out and did it again on the windows drive...helped, would start to load, but freezes at some driver file...so am doing a chkdsk through the recovery module right now, it's at 45% and going steady...we'll see

for the super grub disc, i was able to do all that and get it on the cd and all, seems to work, get's me to a grub load, but i am unsure what to do with it from there...i hate being a nube:(

this chkdsk is acting funny, went steady to 50%, then jumped to 75%, then back to 50% and acting normal again...hopefully doesn't mean anything...stalling pretty hard at 55%, but going, i fear this will take a while as it is a 500Gb drive...

thinking though, I may be able to rebuild the grub file on ubuntu after(i hope)windows is fixed...what it is doing is when i try to load it says something like error reading operating system, using super disk i could get to the grub file, but unable to do anything to fix it, perhaps due to my inexperiance...

---

### Post by Herman on 2008-05-04
Oh, okay, well, just hang in there. You'll be an expert in no time! :)
Normally getting started with Ubuntu is a lot easier than this, but it seems like you're just having more than your fair share of problems. Don't worry, I can imagine how you feel, I have days like that too sometimes.

If Windows did a FIXMBR on the Ubuntu hard drive's MBR, that's easy to fix by re-installing GRUB. That's easy. We can use Super Grub Disk for that or your Ubuntu CD can do it too. Actually, it's only one part of GRUB that gets copied to the MBR anyway, most of the GRUB files are still inside your Ubuntu partition.

---

### Post by Xylograph on 2008-05-04
I had a similar problem with DSL and Windows 95. WIndows booted fine for weeks, and then I got the unknown format error. 
Its annoying isnt it?

Good luck!

---

### Post by chrisneedshelp on 2008-05-04
what did you do to fix it?

herman, so i ran
fixmbr
fixboot
chkdsk

it finished the check disk, acknowledge at least one problem that was corrected, i try to boot to winows with no change..I get to the windows boot page, asking for normal boot or safe boot, i choose safe boot and it halts rather quickly when trying to load ...\windows\system32\drivers\mup.sys
i haven't a clue if that file has anything to do with it...

---

### Post by chrisneedshelp on 2008-05-04
so, at this time I cannot boot to either windows or ubuntu disks, both fail misurably in ways that had i even a smidge less knowledge of what was going on I might have cried!

but, right now I am booted on the live cd and found something quite interesting!  I can see, and access the files of both windows and ubuntu drives!

there's a good chance i may just put an ntfs format to the ubuntu drive, copy off 'my documents' from windows, reload windows, copy my documents back, then format second drive ext3 and load ubuntu, this time keeping the darn windows hdd in the system!

before I do all that though, what did i do to cause all this?  obviously i likely caused some of it myself trying to fix the first problem.  the first and persistant problem was the mbr/ntldr or something on the windows drive...what did i probly do to cause that?

---

### Post by Herman on 2008-05-04
> herman, so i ran
fixmbr
fixboot
chkdsk

it finished the check disk, acknowledge at least one problem that was corrected, i try to boot to windows with no change..I get to the windows boot page, asking for normal boot or safe boot, i choose safe boot and it halts rather quickly when trying to load ...\windows\system32\drivers\mup.sysI see, this means that you have GRUB configured correctly now for sure, because Windows has started to load. GRUB doesn't actually load Windows itself, it relays the signal to boot to Windows own boot loader at Windows' boot sector. So, if Windows has a problem booting from here it's a Windows related problem and normally should be able to be fixed within Windows itself.

Yes, you can use Ubuntu to rescue all of your Windows files if you would rather re-install Windows. If it was me, I would simply copy all of my files into Ubuntu, you don't need to make an NTFS file system. You can do that if you want to, but it doesn't matter what file system files get stored on, they're just files, but I'll leave that up to you.

> so, at this time I cannot boot to either windows or ubuntu disks, both fail misurably in ways that had i even a smidge less knowledge of what was going on I might have cried!
Oh, something went wrong with your Ubuntu again too?
> before I do all that though, what did i do to cause all this? obviously i likely caused some of it myself trying to fix the first problem. the first and persistant problem was the mbr/ntldr or something on the windows drive...what did i probly do to cause that?   	
I really don't know. It is certianly very unusual for anyone to have this amount of trouble all at once. I suspect there may be some kind of a hardware problem here somewhere behind all of this. It could be something as simple as a loose for dirty connection somewhere, maybe where you plug one of your sata cables in to a hard drive or into the motherboard, or a damaged sata cable, or something like that. I would be inclined to try running the machine on just one hard drive for now and swapping cables and drives to see if they both work reliably one at a time and see if the fault can be isolated.

---

### Post by chrisneedshelp on 2008-05-04
well, for the problems, i first removed my windows drive, and loaded ubuntu, than added my windows drive...i hadn't started a thread for help, i was going off of info from other threads to add my windows hard drive.  had enough problems, so i just put the windows in and reloaded the ubuntu drive, allowing grub to id my ms os, still a problem there though too.  so on and on, i think where i made my for sure mistake was i was installing grub, and i think i may have messed up when i was loading it, and i think i loaded it to my windows disk vice my ubuntu disk...and you know the story from there...nube mistakes and not asking for help sooner:(

i actually remembered i had another hard disk that was already formatted so i put that in as dbc and loaded on live and am copying files.  If i can just repair my windows drive i'd be happy to, but after already doing fixmbr and fixboot, then trying to copy the i386 files but getting access denied, so then try chkdsk, and now having windows freeze during initial load, i think i may be forced to reload it...which with my files off is not so much a problem any more, and with files off i'm more more willing to play with it and learn since there's no longer a risk of data loss.

during ubuntu load, i will be loading from live install, manual load, than entire disk...is there anything I need to know to DO or NOT DO to allow dual boot to work?

what actions would be done differently to allow windows boot to be primary?  i'm still thinking what I want to do for primary boot...

I plan to run 3hdd, one windows, one ubuntu, and one media....as my experiance grows i'll go with multiple partitions for more os's, but right now i'm not so confortable with it

---

### Post by chrisneedshelp on 2008-05-04
oh yes, when I ran fixmbr the first time i wasn't paying attention and applied it to the ubuntu drive:(  so much for working when tired...

---

### Post by halfhaggis on 2008-05-04
My experience with dual-booting has always generated more grief for me when I tried to use multiple disks. 
I've had much fewer issues with just partitioning a single disk, and placing the different operating systems files on it.

Then I used additional disks for storage of media. Removing disks that aren't bootable won't (or at least, really really shouldn't) cause the horrible problems you've experienced (I cringed reading this thread because similar stuff has happened to me in the past).

This was admittedly a few years ago, so dual booting with multiple disks might have become easier, provided all the disks you intend to boot from are present during OS installation (although you might not agree).

---

### Post by Herman on 2008-05-04
> well, for the problems, i first removed my windows drive, and loaded ubuntu, than added my windows drive...i hadn't started a thread for help, i was going off of info from other threads to add my windows hard drive. had enough problems, so i just put the windows in and reloaded the ubuntu drive, allowing grub to id my ms os, still a problem there though too. so on and on, i think where i made my for sure mistake was i was installing grub, and i think i may have messed up when i was loading it, and i think i loaded it to my windows disk vice my ubuntu disk...and you know the story from there...nube mistakes and not asking for help sooner:sad:Yes, some people do recommend unplugging hard drives before installing operating systems. I think mainly Windows users think that's necessary because a Windows installation will try to unload all it's vital boot loader files into an older Windows if it detects one when it's installing.
We used to be able to just set the partition to 'hidden' with GRUB or a partition editor so the new Windows XP install wouldn't detect the existing one, and thus retain its boot loader.
This doesn't work anymore for Wndows Vista, it can detect even 'hidden' partitions, apparently, and will even give up it's boot loader files to an older Windows installation on a different hard disk. Therefore, when installing Windows, it's adviseable to unplug your other hard drives.

Linux operating systems don't have that problem. Well, at least Linux doesn't write to any other operating systems, although it is possible for GRUB to be installed in the wrong hard disk's MBR by mistake in some circumstances. (IDE and SATA drive mixed).
It's a trivial operation to restore the correct IPL to a MBR though, so no permanent harm is done.

I think for sure it's better to leave your hard drives plugged in when installing Ubuntu, mainly because most users probably aren't comfortable with opening up their PC cases and messing with their hardware. 
I normally shouldn't cause this much trouble though, whether you do or don't unplug hard drives.
> i think where i made my for sure mistake was i was installing grub, and i think i may have messed up when i was loading it, and i think i loaded it to my windows disk vice my ubuntu disk...Nope, wouldn't hurt it a bit. I do experiments all the time with installing all kinds of different boot loaders to different hard disk's MBRs and also to the boot sectors of partitions and have been doing so for years now. It hasn't hurt any of my operating systems or hard disks yet, although it may make an operating system temporarily unbootable if an inappropriate boot loader is installed somewhere where it shouldn't be.
I even do things like that on purpose, just to see what happens and learn how to recover from it.
In my experience, we can install GRUB to a MBR or a boot sector and reverse the operation with FIXMBR and FIXBOOT or install some other loader like GAG Boot Manager or LiLo and then go back to GRUB and so on, pretty much forever as long as the hard drive lives for and not hurt anything. (Well, nothing that can't be easily fixed anyway).

---

### Post by Herman on 2008-05-04
> i actually remembered i had another hard disk that was already formatted so i put that in as dbc and loaded on live and am copying files. If i can just repair my windows drive i'd be happy to, but after already doing fixmbr and fixboot, then trying to copy the i386 files but getting access denied, so then try chkdsk, and now having windows freeze during initial load, i think i may be forced to reload it...which with my files off is not so much a problem any more, and with files off i'm more more willing to play with it and learn since there's no longer a risk of data loss.:) Yes, it's always best to make a backup of all your files, or at least your important ones, (and you never know sometimes, which ones will turn out to be important at a later date either).
> during ubuntu load, i will be loading from live install, manual load, than entire disk...is there anything I need to know to DO or NOT DO to allow dual boot to work?No, it's normally as simple as falling out of bed.
> what actions would be done differently to allow windows boot to be primary? i'm still thinking what I want to do for primary boot...I'm not sure exactly what you mean there. Do you mean you want Windows to be in the number 1 hard disk? If so then just install Ubuntu in number2 hard disk and it will install GRUB in number1 hard disk's MBR and offer you the choise of which operating ystem you want to boot, Ubuntu or Windows.
If you don't make a decision within ten seconds, it will choose Ubuntu by default. You can change that by editing your /boot/grub/menu.lst file in Ubuntu. GRUB can be configured and customized in lots of different ways to suit your own wants and needs.
Here's a web page about that, [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") (by me).
> I plan to run 3hdd, one windows, one ubuntu, and one media....as my experiance grows i'll go with multiple partitions for more os's, but right now i'm not so confortable with it We can have as many hard drives and operating systems as we want.
I had seven hard drives in one computer for a while. Most of my computers have between three and five operating systems in them, and most have at least two hard disks.

---

### Post by chrisneedshelp on 2008-05-04
well now that i have my extremelly valuable data being backed up on a seporate disk all together, and I know it's in one piece:D  i'm very happy to have gone through all this cause i've learned a ton,or maybe i did, lol...

the true test to whether i've learned much is when im done backing up and load everything, and can get it working!

do you have any suggestions as to how i might repair my windows disk?  after trying fixmbr and fixboot and it freezing immediately after start of boot, i'm not aware of any other measures that can be taken aside from reload...would redoing fixmbr/fixboot possibly have any further effect?

i've heard of a windows auto recovery that is capable from the xp recovery mode, but it's warned against because it will reset a lot of things...well i'm not worried about that, so i'm willing to try it, but i don't know how to do it...I never saw a prompt for it during all my entries into windows start up and repair sections


while i do have sata and pata, my hdd's are all sata, and only optical drives are pata.

i doubt there was a hardware failure only because I just built this system with all new everything 6mo ago(and the windows load was done last weekend), including hdd's...loose sata connection, while I am careful, is entirely possible

---

### Post by chrisneedshelp on 2008-05-04
I had read something, and i don't remember which thread, about allowing the windows boot manager be in charge vice grub, making windows the os auto loaded without operator action, it is not entirely important, just a curiousity.

also, and this is truly trivial...in the menu.lst file(and then displayed in grub) there are three partitions for ubuntu...generic, something else, and memtest...is it possible to remove those from sight at grub without some sort of negative impact on the system or t/s capabilities?  maybe # infront of those lines?  this way at grub I would only see(at least for now) ubuntu and windows XP...

---

### Post by Herman on 2008-05-04
> My experience with dual-booting has always generated more grief for me when I tried to use multiple disks. 
I've had much fewer issues with just partitioning a single disk, and placing the different operating systems files on it.

Then I used additional disks for storage of media. Removing disks that aren't bootable won't (or at least, really really shouldn't) cause the horrible problems you've experienced (I cringed reading this thread because similar stuff has happened to me in the past).

This was admittedly a few years ago, so dual booting with multiple disks might have become easier, provided all the disks you intend to boot from are present during OS installation (although you might not agree).:) I do agree with that.
It also makes it a lot easier to keep your data organized too.
I have a computer with four operating systems in the first disk and all the data in the second disk, and another operating system in a third hard disk. All the operating systems access the same data disc.
If we don't, then what happens is, a file with the same file name will be copied to more than one operating system. 
Then. as time goes on, the file is updated with fresh information in one operating system, and then opened again in a different OS on another day, and different info is saved in the other system's version of the same file. The result - migraine headache when you try to consolidate your files again or go look for missing information. #-o
It's much better to have only one single copy of each file (except for backup copies), that we're working on, and have it accessible by any operating system we happen to have booted at any one time.

---

### Post by chrisneedshelp on 2008-05-04
while i do understand all of that, and with consideration will likely just use my first drive for os's...is having os's on one disk and shared access to files on a different disk somehow different than having os's on different disks, with shared access to data from from yet another disk?

---

### Post by Herman on 2008-05-04
> do you have any suggestions as to how i might repair my windows disk? after trying fixmbr and fixboot and it freezing immediately after start of boot, i'm not aware of any other measures that can be taken aside from reload...would redoing fixmbr/fixboot possibly have any further effect?FIXMBR, FIXBOOT and CHKDSK should be all you need.
Apart from that, it could be that some entirely unrelated software anomaly has cropped up at this inopportune time, just to cloud the issues you're already having even more. I'm not sure, I can only guess. a freind's computer home for a simple defrag. The partitioning was all wrong, there was one huge partition that was almost empty, while the operating system partition was close to 100% full, and all red in the defrag window. There was no room for files to be moved. So I resized some partitions and defragged, but then it wouldn't boot. So I ran CHDSK, but it still wouldn't boot. I started on Friday afternoon and I tried all weekend to get that darned thing to boot. Anyway, the problem turned out to be something to do with a well know brand of antivirus meddling with some video driver or settings, would you believe? I was able to undo that somehow in safe mode and then get the thing working by late Sunday evening and back plugged in time for Monday morning. Whew! :lolflag:
> i've heard of a windows auto recovery that is capable from the xp recovery mode, but it's warned against because it will reset a lot of things...well i'm not worried about that, so i'm willing to try it, but i don't know how to do it...I never saw a prompt for it during all my entries into windows start up and repair sections
[Windows System Restore]("http://www.microsoft.com/windowsxp/using/helpandsupport/getstarted/ballew_03may19.mspx") is pretty good, if you can press F8 while Windows is booting and try to boot it into the last known good configuration you might be able to get it to boot up for you. I'm not that much of a Windows expert to be honest, I just know enough to try to keep myself out of trouble. I have fixed a few computers that way for friends.
System Restore makes restore points automatically, so that may help once you get Windows to boot so you can use it. I don't know if booting in last known good configuration is related to System Restore or not, it might be.
Apart from that, another CHKDSK might help. I have read of people who say two or three file system checks helped them get Windows to boot. A file system check is always good, and won't hurt, apart from taking time.
> while i do have sata and pata, my hdd's are all sata, and only optical drives are pata.Okay, that's probably what most people have in their PCs.
> i doubt there was a hardware failure only because I just built this system with all new everything 6mo ago(and the windows load was done last weekend), including hdd's...loose sata connection, while I am careful, is entirely possibleIt's easy to have a hardware problem of some kind, I don't necessarily mean a failure, it could be just some little thing that's hard to detect. Something like a wire that's broken off or loose inside of a plug maybe, or a small grain of dust or a strand of hair in between the contacts in the plug hole or some other little thing like that, (just for example, I don't know, of course, it could be almost anything).
> while i do understand all of that, and with consideration will likely just use my first drive for os's...is having os's on one disk and shared access to files on a different disk somehow different than having os's on different disks, with shared access to data from from yet another disk? No, you can do it any way you like, one operating system per disk is fine, and data on another disk. There are all kinds of possible ways to do things. :)

---

### Post by chrisneedshelp on 2008-05-04
okay, so something really cool just happened, and I think I even know how I did it, if not intentionally....

When I loaded XP onto dba, i hadn't initially realized that it was set as d: via bios, so after loading xp it booted, but was showing d: as root, oh well, it worked, load ubuntu, same disk, different partition....

after loading ubuntu and restarting i found that i could not load to it, the grub did not come up, but the windows boot loader did, showing my two xp disks(the new one and the old that won't boot)...so i restarted again, and thought to at least fix the XP c: v. d: problem, did that, and restarted to grub...

so long story short, now when I boot i boot to grub, my options are to the ubuntu partition or to the windows boot manager, i think i'll end up trying to change that so that it's just the windows boot in grub, but for the moment this is interesting!



THANK YOU SO MUCH FOR YOUR HELP!!!!!!

I do have a few small problems, like sound working etc, but I am up on both xp and ubuntu, and quite happy with it!

---

### Post by Herman on 2008-05-04
:) Okay, Cool!  8-)

---

