---
title: "Dual Boot XP/Ubuntu Single Hard Drive"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by tetsuo316 on 2006-08-27
Hello All,

First, in my defense, I will say that I've read over many posts on these forums that cover dual booting, but none seem to deal with my situation. If there is one that does, please point me in that direction. I'd really be very much obliged. I'm *very* new to linux.

Situation: I have a single SATA hard drive in my computer that currently has Windows XP installed on the first partition and Ubuntu installed on the second. However, after finishing the Ubuntu install, I am no longer able to boot into XP. I can of course, delete the Ubuntu partition and then access XP fine, but that's not really the point, now is it?

The tutorials I've seen on the internet both involve installing Ubuntu without GRUB - something that seems impossible to do with Dapper. Is it possible?

I saw in other posts that the following information might help, so I'm including it here: 

cat /boot/grub/menu.lst returned this:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

cat /etc/fstab returned this: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda6       /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

sudo fdisk -l returned this:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

I would greatly appreciate any assistance.

---

### Post by Herman on 2006-08-27
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
[COLOR=Red] root[/COLOR]            (hd0,0)
savedefault
makeactive
chainloader     +1
``` Hello, tetsuo316, it wouldn't do any harm to try altering your Windows entry in your menu.lst for 'root' to 'rootnoverify', since your filesystem in Windows is NTFS. Try that and see if it helps or not.
Are you getting any error messages, or can you describe what happens when you try to boot Windows?
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
[COLOR=Sienna] rootnoverify[/COLOR]            (hd0,0)
savedefault
makeactive
chainloader     +1
```4
>  sudo fdisk -l returned this:

```
 Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```  Is that really all sudo fdisk returns? Surely something has gone wrong with uploading the information to the forums, there must be more to it than that. Thanks for including all the other relevant information. It does make helping you a lot easier.  :D
Regards, Herman

---

### Post by tetsuo316 on 2006-08-27
Hi Herman, thanks for the help.

1) When just using 'root' in the menu.lst file, this is what I see upon attempting to boot XP:

Booting 'Microsoft Windows XP Professional'

root (hd0,0)
     filesystem type unknown partition type 0x7
savedefault
makeactive
chainloader +1

If I change menu.lst to 'rootnoverify,' the filesystem type unknown message goeas away, but the rest of the text is displayed and the cursor '_' just sits there blinking at me stubbornly.

2) Sorry, yes. fdisk -l returns this:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18240   146512768+   7  HPFS/NTFS
/dev/sda2           18241       35844   141404130   83  Linux
/dev/sda3           35845       36481     5116702+   f  W95 Ext'd (LBA)
/dev/sda5           35845       36354     4096543+  82  Linux swap / Solaris
/dev/sda6           36355       36481     1020096    c  W95 FAT32 (LBA)

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36481   293033601    7  HPFS/NTFS

Thanks again for the help.

---

### Post by Herman on 2006-08-27
tetsuo316, I can't see  any problem, this is odd.
>  I can of course, delete the Ubuntu partition and then access XP fine, but that's not really the point, now is it? You don't need to delete the partition, but more testing is in order to try to find out what the problem could be.
What happens when you overwrite the bootloader code for Grub in your MBR with the code to make the MBR point to Windows bootloader again? (If you haven't tried that already). You can overwrite Grub's Stage1 in your MBR with Windows stage1 with one of the methods explained on this page, [Click Here.]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
Or, if it's easier, what happens when you try booting Windows with some other bootloader from a floppy disk or a CD?

---

### Post by tetsuo316 on 2006-08-27
So if I install the Windows bootloader over GRUB, how can I boot back into Ubuntu? Is there a line I can add to the boot.ini file?

I'm a bit hesitant to take the steps outlined on your page until I know that I can 'undo' that change.

Thanks!

---

### Post by DarkDead on 2006-08-27
Hi, I have just the same problem as tetsuo.
> **tetsuo316 said:**
> If I change menu.lst to 'rootnoverify,' the filesystem type unknown message goeas away, but the rest of the text is displayed and the cursor '_' just sits there blinking at me stubbornly.

**fdisk -l**
Disco /dev/hda: 20.4 GB, 20491075584 bytes
16 cabeças, 63 setores/trilha, 39704 cilindros
Unidades = cilindros de 1008 * 512 = 516096 bytes

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hda1 * 1 23440 11813728+ 7 HPFS ou NTFS
A partição 1 não termina no limite do cilindro.
/dev/hda2 23445 38394 7534485 83 Linux
A partição 2 não termina no limite do cilindro.
/dev/hda3 38394 39701 658665 82 Linux swap / Solaris
A partição 3 não termina no limite do cilindro.

Disco /dev/hdb: 15.3 GB, 15382241280 bytes
255 cabeças, 63 setores/trilha, 1870 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hdb1 * 1 1870 15020743+ 7 HPFS ou NTFS

**grub menu.lst**
[...]
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1

title Ubuntu, kernel 2.6.15-26-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
boot

title Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.15-26-386
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

I need to use rootnoverify for the same reason as tetsuo, probably because I used Partition Magic to resize an ntfs partition that occupied all disk in order to install Ubuntu. And as I read somewhere Grub root command doesn't work with nfts partitions formatted by other than Windows Xp (or it's installation cd).

I read about people who resolved this problem by changing their disks type to LBA in the BIOS, don't ask me why (this might help you tetsuo). But I can only use NORMAL, with LBA or LARGE Grub doesn't boot (it gives me error 17). Both Windows and Ubuntu were installed using the LBA format, I changed to NORMAL after their installation.

Any idea about what I can do?

[QUOTE=tetsuo316]So if I install the Windows bootloader over GRUB, how can I boot back into Ubuntu? Is there a line I can add to the boot.ini file?

I'm a bit hesitant to take the steps outlined on your page until I know that I can 'undo' that change.[/QUOTE]

To boot Ubuntu with Windows bootloader this might help: [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3").

You can always make an grub boot floppy:
[http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy")
[http://www.linuxjournal.com/article/4622]("http://www.linuxjournal.com/article/4622")

---

### Post by confused57 on 2006-08-27
You might want to make a grub boot floppy first:
[http://www.ubuntuforums.org/showthread.php?t=224345&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=224345&highlight=floppy)

Yes, after you restore the Windows mbr you can reinstall grub:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

Edit: DarkDead beat me to it.

---

### Post by Herman on 2006-08-27
tetsuo316, If you aren't comfortable with changing your what bootloader is in your MBR, you don't have to. 
The main thing I was wanting to find out is whether  there is 
1) A problem with your Grub Bootloader that I missed, and some other bootloader, or Grub from a floppy disk or CD can boot your Windows okay
2) The problem is something to do with Windows, and no bootloader can load it.

So it doesn't really matter if you want to leave your MBR as it is now, just try some other way to boot Windows for me and see what happens.
Making a grub floppy disk might be a good idea, as the other posters suggested. 
You could also make yourself a GAG Boot Manager floppy disk or CD, GAG will usually boot Windows without any trouble, and you can use it from the floppy disk or CD, you don't have to install it to MBR (unless you want to). [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")
Also, Super Grub DIsk can work from CD, floppy disk or USB as well. [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

>  root (hd0,0)
     filesystem type unknown partition type 0x7
savedefault
makeactive
chainloader +1

If I change menu.lst to 'rootnoverify,' the filesystem type unknown message goeas away, but the rest of the text is displayed and the cursor '_' just sits there blinking at me stubbornly. I would think, (but I'm not sure, I'll find out), that Grub would always regard an NTFS filesystem as an unknown type. I'll test that shortly. Since there is no error message, and your monitor is mostly blank and not much happens at all, it seems to me as if Grub is not finding your Windows boot sector (the first sector or your Windows partition. The command 'chainloader +1' should make sure Grub looks at the first sector of that partition for the boot sector. 

I see that your Windows partition has not been 'hidden' , or that would have shown up in your sudo fdisk -l output.

Maybe it's just Windows being 'finnicky'. You know I had a problem booting a Windows installation yesterday, I was just doing it for testing purposes and it was doing nothing at all, like yours. The problem was in Windows boot.ini file. I was just getting a blank monitor with no error message, and had to do a hard reboot. I don't think your problem will be the same as mine though. I was aware of changes I had made to the boot,ini file. You probably haven't changed yours. Your Windows is still partition number1, so it should be okay. I made my Windows to be a different partition number on purpose to see what would happen and learn how to make it boot that way, for an experiment. Anyhow, in my computer Windows still wouldn't boot even after I fixed the boot.ini file.  I ended up pressing the f8 key for alternative start-up menu, then I changed my mind and selected 'boot Windows normally', and guess what, it booted right up. This was after  whole afternoon of fiddling around with it. Now, why would Windows need to be told I want to boot it normally, I ask ? Anyway, I guess nothing was really wrong with it all afternoon, it was just being 'finnicky'. :D
So maybe, if you can boot it some other way, you might be lucky it'll fix itself.
Or else, maybe we'll have to work for it and conduct more tests to see if we can discover the exact problem and then fix it, that's the normal way.
Regards, Herman :D

---

### Post by tetsuo316 on 2006-08-27
So I overwrote the MBR using the Windows XP install disc and the fixmbr command. After that (as one would expect), the comp boots right into Windows XP without presenting any option to boot into Ubuntu.

I'm fine with using the boot.ini to choose between Windows and Ubuntu, provided it can be done. From what I can tell from other posts, I need to create a Ubuntu.bin file on the Fat32 partition, boot into XP, move that .bin file to C://, and then add a line to the boot.ini file that specifies Ubunu.bin="Ubuntu".

That about right? Is there an easier way?

Thanks!

---

### Post by Herman on 2006-08-27
> So I overwrote the MBR using the Windows XP install disc and the fixmbr command. After that (as one would expect), the comp boots right into Windows XP without presenting any option to boot into Ubuntu. Okay, good, so we proved that Windows is still bootable alright. Good! :D

>  I'm fine with using the boot.ini to choose between Windows and Ubuntu, provided it can be done. From what I can tell from other posts, I need to create a Ubuntu.bin file on the Fat32 partition, boot into XP, move that .bin file to C://, and then add a line to the boot.ini file that specifies Ubunu.bin="Ubuntu".

That about right? Is there an easier way? Well, normally that's the hard way. The easiest and best way is to just follow confused57's and catlett's method for re-installing Grub and give Grub another try.
Really, once you get Grub working, (which is normally easy in most instances) Grub is a far more interesting and useful bootloader than any other in the world. You will really be missing something if you can't have Grub. [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

I'm glad you got Windows booting, I just converted one of my Windows installs to NTFS while you were doing that. Yesterday I added a second hard disk to my PC as well, so I can simulate people's booting problems and test out possible solutions for people. 
As it happened, without even trying, I experienced your problem too for a little while, but mine has booted okay now. I couln't seem to boot it from Grub's command line, but oddly enough, with the other (FAT32) Windows install still 'hidden', it booted up from the other Windows install's entry in my menu.lst in my main Ubuntu install!:D  I still think it's just Windows being stubborn and difficult for no good reason.:confused: 

Anyhow, I have to go for now, I'll be back in twelve or so hours probably. (It's Monday morning here).
Bye for now, Herman :D
EDIT, DarkDead, I am hoping something will help your here that has already been mentioned. If not, I'll be back, or , in the meantime, maybe someone else will help, I didn't mean to be rude and ignore you, it's just that I'm out of time for now. Regards, Herman

---

### Post by tetsuo316 on 2006-08-27
So I thought I'd give the whole ubuntu.bin thing a try and this is what happened.

First, I started the install CD and from terminal ran the following commands:

sudo mkdir /mnt/osshare

mount -t msdos /dev/sda6 /mnt/osshare

dd if=/dev/sda2 of=/mnt/osshare/ubuntu.bin bs=512 count=1

Then, I booted into Windows and copied the ubuntu.bin file to C:\. Using the System control panel, I added the following line to the boot.ini file:

C:\ubuntu.bin="Ubuntu Linux"

After doing that, I could see both options when booting up, and I could boot into XP, but the comp would hang every time I selected the ubuntu option. It would just freeze while displaying the boot options.

Since that didn't work, I thought I'd try GRUB again since Herman seemed to have so much success with it. I followed [these]("http://www.ubuntuforums.org/showthread.php?t=224351") instructions for restoring GRUB, and now I'm back to the same place I was before - GRUB shows both OSes, but I just get a blinky cursor when I select the XP OS.

Any ideas?

---

### Post by confused57 on 2006-08-27
I don't know what going on with booting Ubuntu, but I can give you a suggestion if you want to try.
First, make a GAG boot floppy and a Super Grub Disk, or at least the GAG floppy.
Restore your Windows mbr, as you did before, to enable booting of Windows.
Reinstall grub, using the live cd, however you might want to try **setup (hd0,1)** as described in catlett's "howto"...this will install grub on the root partition of Ubuntu.
Then, the GAG boot floppy "should" be able to boot Ubuntu.

It may or may not work, but it shouldn't hurt anything.  At least you'll be able to boot into Windows and play around with the GAG & Super Grub Disk until Herman is able to reply.

---

### Post by DougS on 2006-08-27
Help, I'm in a worse state...

Tried to install Kubuntu from known good disc, went OK, restart...
Grub Error 17!

Not a Linux expert so found advice to use Windows CD FIXMBR and did that...

No success, so every time I do that it says disc has unknown type of boot record (or similar)
So doesn't look as though MBR is being fixed?

Thought about boot sector being protected, but no option in BIOS to do that.

Now just get: Error loading operating sysytem

Stranger still, can mount, and view all partitions including the Windows one with Puppy live CD so it looks as though the partitions are there.

I don't relish the thought of reinstalling all Windows but as the disc is now unuseable at any realistic level for me, I would appreciate some advice.

Needless to say my faith in Kubuntu is, for the moment shattered (even though I'd tried it on another machine in a similar dual boot way)

---

### Post by confused57 on 2006-08-27
> **DougS said:**
> Help, I'm in a worse state...

Tried to install Kubuntu from known good disc, went OK, restart...
Grub Error 17!

Not a Linux expert so found advice to use Windows CD FIXMBR and did that...

No success, so every time I do that it says disc has unknown type of boot record (or similar)
So doesn't look as though MBR is being fixed?

Thought about boot sector being protected, but no option in BIOS to do that.

Now just get: Error loading operating sysytem

Stranger still, can mount, and view all partitions including the Windows one with Puppy live CD so it looks as though the partitions are there.

I don't relish the thought of reinstalling all Windows but as the disc is now unuseable at any realistic level for me, I would appreciate some advice.

Needless to say my faith in Kubuntu is, for the moment shattered (even though I'd tried it on another machine in a similar dual boot way)
What version of Windows is on this computer...I think fixmbr only works with XP & 2000(I've seen it suggested to also enter the **fixboot** command, as well as , fixmbr???)?  There's another method if you have 98 or ME:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by tetsuo316 on 2006-08-27
> **Confused57 said:**
> I don't know what going on with booting Ubuntu, but I can give you a suggestion if you want to try.
First, make a GAG boot floppy and a Super Grub Disk, or at least the GAG floppy.
Restore your Windows mbr, as you did before, to enable booting of Windows.
Reinstall grub, using the live cd, however you might want to try setup (hd0,1) as described in catlett's "howto"...this will install grub on the root partition of Ubuntu.
Then, the GAG boot floppy "should" be able to boot Ubuntu.

It may or may not work, but it shouldn't hurt anything. At least you'll be able to boot into Windows and play around with the GAG & Super Grub Disk until Herman is able to reply.

The problem is that this comp doesn't exactly have a floppy drive...

---

### Post by confused57 on 2006-08-27
> **tetsuo316 said:**
> The problem is that this comp doesn't exactly have a floppy drive...

The GAG boot loader can be put on a CD:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

The Super Grub Disk is also for a CD.

Add:  The above link is from Herman's website...he knows Linux much better than I, might be best to wait until he gets back.  I don't want to give you any inaccurate information.

---

### Post by tetsuo316 on 2006-08-27
Thanks, Confused57. Awaiting Herman's return.

Herman, whenever you're ready to bless me with your genius... :D

---

### Post by tetsuo316 on 2006-08-28
btw...

Having Ubuntu AMD64 installed shouldn't make a difference, right? The boot sector is completely independent of that, correct?

---

### Post by Herman on 2006-08-28
> I don't know what going on with booting Ubuntu, but I can give you a suggestion if you want to try.
First, make a GAG boot floppy and a Super Grub Disk, or at least the GAG floppy.
Restore your Windows mbr, as you did before, to enable booting of Windows.
Reinstall grub, using the live cd, however you might want to try **setup (hd0,1)** as described in catlett's "howto"...this will install grub on the root partition of Ubuntu.
Then, the GAG boot floppy "should" be able to boot Ubuntu.

It may or may not work, but it shouldn't hurt anything. At least you'll be able to boot into Windows and play around with the GAG & Super Grub Disk until Herman is able to reply. I agree with confused57. Installing Lilo or Grub to the first sector of your Ubuntu partition is a great idea, it gives you a second method for booting Ubuntu, and should work and won't hurt anything. I do it all the time.
You should try booting Windows with Grub from a CD (Super Grub Disk) to test whether Grub in general has some problem with booting your Windows install, (I doubt that very much, because this problem is relatively rare), or if it's just your installed Grub. (I think maybe). If that's true then there must be a way to fix it.
GAG Boot Manager is probably the most expedient work-around for your problems at the moment. GAG Boot Manager works great from a floppy disk, but since you don't have a floppy disk drive, you can try it out from a CD instead. The only problem with GAG on a CD is that you can set it up but you can't 'save the changes' to a CD, (the CD won't remember your settings for next time like a floppy disk can). However, if you test GAG and see if you like it and make sure GAG will boot both operating systems for you. Then you might even want to install GAG to MBR instead.  That way you will be able to set up GAG and it will remember your settings. I have recommended GAG to two people now who have had AMD64, and they both said it works fine on thier systems.
You'll still have Grub installed in your Ubuntu system, we can fiddle around and try to troubleshoot that later on if you still feel like it, lets see if GAG or Super Grub can boot it first and that might help us pinpoint where the problem is.
Regards, Herman :D

---

### Post by Herman on 2006-08-28
> I need to use rootnoverify for the same reason as tetsuo, probably because I used Partition Magic to resize an ntfs partition that occupied all disk in order to install Ubuntu. And as I read somewhere Grub root command doesn't work with nfts partitions formatted by other than Windows Xp (or it's installation cd).
I read about people who resolved this problem by changing their disks type to LBA in the BIOS, don't ask me why (this might help you tetsuo). But I can only use NORMAL, with LBA or LARGE Grub doesn't boot (it gives me error 17). Both Windows and Ubuntu were installed using the LBA format, I changed to NORMAL after their installation.
Any idea about what I can do? ```
fdisk -l
Disco /dev/hda: 20.4 GB, 20491075584 bytes
16 cabeças, 63 setores/trilha, 39704 cilindros
Unidades = cilindros de 1008 * 512 = 516096 bytes

Dispositivo......     Boot......       Início......       Fim......       Blocos......       Id......       Sistema
/dev/hda1..............          *..........            1     ......23440......     11813728+......       7......      HPFS ou NTFS
A partição 1 não termina no limite do cilindro.
/dev/hda2...................                   23445......      38394     ......7534485......       83......      Linux
A partição 2 não termina no limite do cilindro.
/dev/hda3...................                   38394      ......39701      ......658665......       82......      Linux swap / Solaris
A partição 3 não termina no limite do cilindro.

Disco /dev/hdb: 15.3 GB, 15382241280 bytes
255 cabeças, 63 setores/trilha, 1870 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Dispositivo......      Boot......       Início......       Fim......       Blocos......       Id......       Sistema
/dev/hdb1..............           *            ......1      ......1870......     15020743+......       7......       HPFS ou NTFS
```DarkDead, does ' A partição 3 não termina no limite do cilindro.' mean your partitions are not starting and ending on cylinder boundaries?

If it does, I think you should probably use a Live CD to mount your partitions with and first rescue all your important files if you have not already made a back up of all of them.

Then download for yourself a GParted LiveCD .iso and burn it to a CD-RW or a CD-R disk. [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php")
I think maybe the best thing to do would be to ask for help in [GParted Web Forums]("http://gparted-forum.surf4.info/"), because you will get the real experts there who can help you better than I can. 

I think that they might ask you to delete your new Ubuntu partitions since if they haven't been used yet they won't have anything important on them and they can be re-installed quite quickly. With those out of the way,  you'll be able to 'move' your Windows partition around and place it again and hopefully GParted will automatically line it up with a cylinder boundary for you. Then you can install Ubuntu again and everything should work okay after that. 
This problem will probably be easy to fix, but I am not certian. Sometimes it is impossible or at least very difficult to undo damage done to the partition table by a bad partitioner and the only way is to delete all your partitions and start all over again with a brand new partition table. That's why you should back up all your data first. But I think it might not be that bad.

That's what I think anyway, Regards, Herman. :D

---

### Post by tetsuo316 on 2006-08-28
Hi Herman and Confused57, thanks for the advice. Unfortunately, at this point, I'm about ready to throw in the towel.

My initial desire to move to linux stemmed from my frustration with all the Windows activation crap I have to go through each time I upgrade my machine, but in the end, at least I can resolve that by making a phone call.

So far, I've spent four or five solid days trying to do three things in Linux:

dual boot successfully
get my wireless card to work
get my bluetooth keyboard and mouse to work

I've tried everything posted on the wiki, the forums and tertiary sources to get the hardware recognized, but to no avail. Seeing as how even if I get the dual boot situation resolved, I'll still be without wireless internet and have to buy a new keyboard and mouse, I think I'd rather just wait until there's a Linux distro that 'just works.' I don't mind fiddling with drivers and installing third party apps, but if my hardware doesn't work, that's not good.

The one thing that linux has going for it is the incredibly active and supportive user base. Herman - you have an entire website (adless, to boot) created solely to assist others with Linux issues. You install other OSes in your spare time in order to replicate total strangers' issues. You are a good person. :D It's users like you who will help linux turn the corner and serve as the complete package that it can be.

*sigh* Maybe 7.X Satiated Salamander or whatever it will be called...

:-({|=

---

### Post by Herman on 2006-08-29
Well, sorry I couldn't solve it for you quickly, ( I hoped it would turn out that way too), and thanks for your patience this far. 
Regards, Herman

---

### Post by Claus7 on 2006-09-08
Hello all,

I do now that this discussion has reached an end, yet as far as I have searched the net, this is the latest discussion, which is covering the boot problem of windows. 
I must point out that I do not have a solution to this problem, even though I have tried many things. The best might be to format the entire disk, yet I have seen that in Suse Linux they have found a solution to this problem. 
First thing first though. One solution that seems to work is to change an IDE option to the BIOS. Some people have found this solution working. Yet, it seems that to the majority of people that doesn't work.One other solution has to do with rootnoverify in grub. Some other solutions have to do with Grub and Gag disks which seem to do nothing to this problem as well. I have tried both. The first refuses to boot and the second freezes (it doesn't allow me even to start the procedure and see what it will happen). Of cource there might be other solutions which haven't solved the matter either (one more is the fxmbr command when someone inserts the windows disk). 

In Suse Linux, as I have said, they have found a solution through some update.They have pointed out also that this problem is a general one. Yet, they say that this works only in a specific edition.*[COLOR="DarkRed"]The reason why I haven't formated my disk yet is because my partitioning and booting were ok until I updated to Dapper Drake around July 2006[/COLOR]*. My computer was working fine at least 3 months. The only difference with the majority of people facing this problem is that my first partition is Linux and the second Windows. Needless to say that the partition of Ubuntu works fine. My question is whether there exists a similar update for Ubuntu as well.

PS : Here I provide all the addresses that someone might find interesting about the subject. I would be very glad if an update of Ubuntu would solve the problem.

[http://www.ubuntuforums.org/archive/index.php/t-186733.html](http://www.ubuntuforums.org/archive/index.php/t-186733.html)
[http://www.ubuntuforums.org/showthread.php?t=193624&highlight=rootnoverify+%28hd0%2C1%29](http://www.ubuntuforums.org/showthread.php?t=193624&highlight=rootnoverify+%28hd0%2C1%29)
[http://ubuntuforums.org/showthread.php?t=244874](http://ubuntuforums.org/showthread.php?t=244874)
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
[http://www.linuxquestions.org/questions/showthread.php?t=205954](http://www.linuxquestions.org/questions/showthread.php?t=205954)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://www.ubuntuforums.org/showthread.php?t=213754&highlight=Filesystem+type+unknown+partition+0x7](http://www.ubuntuforums.org/showthread.php?t=213754&highlight=Filesystem+type+unknown+partition+0x7)

---

### Post by Herman on 2006-09-09
I have not really found a way to solve this problem or problems either, that's why I haven't posted here until now.  There could be many problems with the same symptoms, so diiferent solutions will work for some and not for others. Those links you provided were interesting, thank you for those, it's nice to hear from someone else who is interested in sovling bootint problems.  I spent quite some time combing through them.
The most promising theory (to me) looks like some BIOSes could have something to do with the problem, since some people solved it by setting their BIOS from AUTO to LBA.

  I actually succeeded in reproducing similar symptoms in my computer, but so far that has not yielded any useful information.
One thing I did find useful was making my own Windows XP boot floppy disk, which is quite simple to do and costs nothing, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").

Someone who has a computer that has problems booting both Windows XP with NTFS and Linux might be able to either use,
1) Grub in the MBR for booting Linux and a Windows boot floppy for booting XP, or,
2) Windows bootloader from the MBR to boot Windows and a [Grub floppy disk]("https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28CategoryDocumentation%29") or [CD to boot Ubuntu]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD") with, or [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php").

Those are about the best I can offer so far, they seem like 'bandaid solutions' though, but either of those should work.

Regards, Herman

---

