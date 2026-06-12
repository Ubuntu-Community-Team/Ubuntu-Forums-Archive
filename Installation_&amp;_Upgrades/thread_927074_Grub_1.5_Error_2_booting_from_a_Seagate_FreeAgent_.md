---
title: "Grub 1.5 Error 2 booting from a Seagate FreeAgent external usb disk"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by spink007 on 2008-09-22
I have loaded Ubuntu 8.04.1 (Hardy Heron) onto my new Seagate FreeAgent external disk. I have put, I think, a grub loader on this disk. I have set the bios for booting from the external disk, I think, but when I try to boot, I get an error message from Grub 1.5 of "Error 2". The grub config file (menu.1st) has (hd0,0) (mapped to /dev/sda1 in the mapping file) as the root and the right file for the kernel, or so it seems. Everything else appears right in the menu.1st file. Also, when I try to use grub from the grub shell and I put the same parameters in, the grub shell terminates back to bash (this is all running on the LiveCD) without rebooting. I can see the ext3 filesystem and read and write to it from the LiveCD, and the grub shell can mount it, I think, as I can cat /etc/fstab from the grub shell.
Still no joy when I try to reboot from this external disk, only the Error 2 message from Grub stage 1.5.

Any idea what I can do?

---

### Post by caljohnsmith on 2008-09-22
How about posting the output of:
```
sudo fdisk -lu
```
And post the full contents of your /boot/grub/menu.lst from the Ubuntu partition (note it is LST, it does not use a one). If you need help with that, let me know.

Also, to make sure that Grub in the master boot record (MBR) is pointing to your Ubuntu partition for its system files, please do the following:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you need more details/info.

---

### Post by spink007 on 2008-09-22
> **caljohnsmith said:**
> How about posting the output of:
```
sudo fdisk -lu
```
And post the full contents of your /boot/grub/menu.lst from the Ubuntu partition (note it is LST, it does not use a one). If you need help with that, let me know.

 sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c1c04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   958566419   479283178+  83  Linux
/dev/sda2       958566420   976768064     9100822+   5  Extended
/dev/sda5       958566483   976768064     9100791   82  Linux swap / Solaris

ubuntu@ubuntu:/media/disk/boot/grub$ cat menu.lst 
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=8f21ddd0-0c40-4806-a717-512a86d5c3cc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# howmany=all

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8f21ddd0-0c40-4806-a717-512a86d5c3cc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8f21ddd0-0c40-4806-a717-512a86d5c3cc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




Also, to make sure that Grub in the master boot record (MBR) is pointing to your Ubuntu partition for its system files, please do the following:
```
sudo grub
grub> find /boot/grub/stage1
```

grub> find /boot/grub/stage1
 (hd0,0)
After I did this and got the return value (hd0,0), it would no longer
allow me to set the root as below (it now says Selected disk does not exist--error 21) .  In fact,  when I did the find again as above,
it now tells me File Not Found.


That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```

I'm afraid I can't do this now.  the root command says that Selected Disk does not exist !!!

Let me know how it goes or if you need more details/info.

Thanks, Any help will be appreciated.

Steve

---

### Post by caljohnsmith on 2008-09-22
[QUOTE=spink007]grub> find /boot/grub/stage1
(hd0,0)
After I did this and got the return value (hd0,0), it would no longer
allow me to set the root as below (it now says Selected disk does not exist--error 21) . In fact, when I did the find again as above,
it now tells me File Not Found.[/QUOTE]
That kind of inconsistent behavior you describe is certainly not a good sign; how old is your HDD? I would highly recommend you run some disk checks on it. Do you have a HDD diagnostics CD that came with your HDD? If you don't, you could download the "[Ultimate Boot CD]("http://www.ultimatebootcd.com")" and use that, because it has lots of HDD diagnostic tools on it. Let me know how it goes or if you need further details/info.

P.S. Also make sure you have the HDD connected securely and that the cables are in good shape.

---

### Post by spink007 on 2008-09-22
> **caljohnsmith said:**
> That kind of inconsistent behavior you describe is certainly not a good sign; how old is your HDD? I would highly recommend you run some disk checks on it. Do you have a HDD diagnostics CD that came with your HDD? If you don't, you could download the "[Ultimate Boot CD]("http://www.ultimatebootcd.com")" and use that, because it has lots of HDD diagnostic tools on it. Let me know how it goes or if you need further details/info.

P.S. Also make sure you have the HDD connected securely and that the cables are in good shape.

Sorry about my last post.  I sent it off too hastily.  I was running the grub shell as an ordinary user not as root (I forgot to do "sudo grub".  When I did "sudo grub", I succeeded with the root (hd0,0) command after succeeding witht he find command again, and then I did the setup on hd0 and that reported that all was in order.  I then did quit in grub.  I setup the bios for the external usb hard disk to boot, and I rebooted.  

Unfortunately, this time there was nothing, not even the Error  message 2 from Grub 1.5, just a blank screen with the cursor blinking in the right hand corner.

Any ideas?  (Again, sorry to mislead you with my last reply.  There was no inconsistent behavior from the disk, it was me who was inconsistent.)

Thanks again,

Steve

---

### Post by unutbu on 2008-09-22
spink007, I have an idea but am sufficiently unsure that I'd like to hear if caljohnsmith agrees before we go down this path:

Some older BIOSes make assumptions about the maximum number of Cylinders, Heads and Sectors a drive can have. There are other difficulties too, but they all amount to the BIOS being unable to read files that are very deep into a large hard drive. I think this might be the problem you are seeing. (See [http://www.pcguide.com/ref/hdd/bios/size-i.htm](http://www.pcguide.com/ref/hdd/bios/size-i.htm) for info on Hard Disk Size Barriers).

One way around this problem is to use GParted to create a small 10MB grub partition at the beginning of your hard drive. Then copy the files in /boot/grub into this grub partition.
These are the files GRUB uses to complete its stage of the boot process. GRUB uses the BIOS to access these files. Once control is handed off to these files, Linux will be able to see your entire 500GB drive. 

So I suggest you boot from the LiveCD, click System>Administration>Partition Editor,
and resize /dev/sda1 (the Linux partition) so that there is about 10MB of free space at the very beginning of the drive. Then create a new partition in this space. It will probably be called /dev/sda3.

We can give you instructions on how to set up the grub partition after you create the partition and post the new output of
```

sudo fdisk -l

```
(To see an example of how it goes, see [http://ubuntuforums.org/showpost.php?p=5746969&postcount=85](http://ubuntuforums.org/showpost.php?p=5746969&postcount=85)).

---

### Post by caljohnsmith on 2008-09-22
[QUOTE=spink007]Sorry about my last post. I sent it off too hastily. I was running the grub shell as an ordinary user not as root (I forgot to do "sudo grub". When I did "sudo grub", I succeeded with the root (hd0,0) command after succeeding witht he find command again, and then I did the setup on hd0 and that reported that all was in order. I then did quit in grub. I setup the bios for the external usb hard disk to boot, and I rebooted.

[COLOR="Red"]Unfortunately, this time there was nothing, not even the Error message 2 from Grub 1.5, just a blank screen with the cursor blinking in the right hand corner[/COLOR].[/QUOTE]
Actually, Unutbu, I'm concerned about the fact that Grub didn't even report an error this time, but instead just left spink007 with a blank screen and a blinking cursor. I think that might point to maybe a bad partition table, dying HDD, maybe incorrect HDD setup in BIOS, or something along those lines. If it were an issue of the Grub files (menu.lst, stage2, etc) being out of reach of BIOS, then I believe he should have gotten a Grub error 18 or something like that at least. Does this sound reasonable to you?

---

### Post by spink007 on 2008-09-22
> **unutbu said:**
> spink007, I have an idea but am sufficiently unsure that I'd like to hear if caljohnsmith agrees before we go down this path:

Some older BIOSes make assumptions about the maximum number of Cylinders, Heads and Sectors a drive can have. There are other difficulties too, but they all amount to the BIOS being unable to read files that are very deep into a large hard drive. I think this might be the problem you are seeing. (See [http://www.pcguide.com/ref/hdd/bios/size-i.htm](http://www.pcguide.com/ref/hdd/bios/size-i.htm) for info on Hard Disk Size Barriers).

One way around this problem is to use GParted to create a small 10MB grub partition at the beginning of your hard drive. Then copy the files in /boot/grub into this grub partition.
These are the files GRUB uses to complete its stage of the boot process. GRUB uses the BIOS to access these files. Once control is handed off to these files, Linux will be able to see your entire 500GB drive. 

So I suggest you boot from the LiveCD, click System>Administration>Partition Editor,
and resize /dev/sda1 (the Linux partition) so that there is about 10MB of free space at the very beginning of the drive. Then create a new partition in this space. It will probably be called /dev/sda3.

We can give you instructions on how to set up the grub partition after you create the partition and post the new output of
```

sudo fdisk -l

```
(To see an example of how it goes, see [http://ubuntuforums.org/showpost.php?p=5746969&postcount=85](http://ubuntuforums.org/showpost.php?p=5746969&postcount=85)).

Thanks for this.  I think this is an interesting strategy and I don't have a lot to lose, so I started by trying to bring up gparted, but even when I type "sudo gparted" from the terminal window, I get a message from libparted 1.71 that it can't open up /dev/scd0 read-write and is only opening it up read-only.  The graphical window that then comes up bears this out as the "resize/move" option is grey-ed out.  Is there something I can do to get around this?

Thanks again,

Steve

---

### Post by spink007 on 2008-09-22
> **caljohnsmith said:**
> Actually, Unutbu, I'm concerned about the fact that Grub didn't even report an error this time, but instead just left spink007 with a blank screen and a blinking cursor. I think that might point to maybe a bad partition table, dying HDD, maybe incorrect HDD setup in BIOS, or something along those lines. If it were an issue of the Grub files (menu.lst, stage2, etc) being out of reach of BIOS, then I believe he should have gotten a Grub error 18 or something like that at least. Does this sound reasonable to you?

Thanks.  The one thing in this list I could fix, is an incorrect HDD setup in the BIOS.  I thought I had it right, but perhaps I haven't.  I now have the Seagate FreeAgent External Disk Drive as the first boot device in the boot priority list.  Is there something else that needs to be done?

Steve

---

### Post by caljohnsmith on 2008-09-22
> **spink007 said:**
> Thanks.  The one thing in this list I could fix, is an incorrect HDD setup in the BIOS.  I thought I had it right, but perhaps I haven't.  I now have the Seagate FreeAgent External Disk Drive as the first boot device in the boot priority list.  Is there something else that needs to be done?

Steve
As far as your Ubuntu HDD BIOS settings are concerned, do you have the HDD set as "auto", "LBA", "CHS", or something else in BIOS? And how old is that HDD? Based on your computer's symptoms, I would still recommend that we check your HDD and partition table at this point. You certainly have nothing to lose by doing so, and we might find the root of your problem. And Unutbu's point may also be entirely valid, but at this point we can't know for sure until we can get Grub working to the extent where it will at least give us errors. :)

So can you download the Ultimate Boot CD I mentioned earlier, or do you have a CD that came with your HDD with diagnostic tools? Also, I think we should check your partition table, so boot your Live CD, open a terminal and first do:
```
sudo fdisk -l
```
Please post that output (it uses units different than the previous time you posted with the "-lu" option and will save me doing the math for all your partitions). Then enable all your repositories in System > Prefs > Software Sources in order to download testdisk:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by meierfra. on 2008-09-22
> I now have the Seagate FreeAgent External Disk Drive as the first boot device in the boot priority list

Are you still getting the "blinking cursor" at boot up? Or is it error 2 again.


Your "fdisk" only shows one hard drive. Did you disconnect your internal drive? 


I'm not sure whether this applies in your case, but you might check out this post:
[http://ubuntuforums.org/showthread.php?t=151682]("http://ubuntuforums.org/showthread.php?t=151682")

How old is your computer?


Edit: Hadn't  seen caljohnssmith last post, when I posted this
2nd Edit: Don't worry about the link I posted yet. First post the testdisk result caljohnsmith requested.

---

### Post by unutbu on 2008-09-23
caljohnsmith, yes, I agree getting feedback from GRUB in the form of a GRUB Error would be a good thing before going down the path I suggested. 

spink007, I'm not sure what to do about the "can't open up /dev/scd0 read-write" error.
/dev/scd0 is the CD/DVD drive. GParted should have tried to read /dev/sda, your Linux hard drive instead. 

caljohnsmith and meierfra both have more knowledge and experience resolving GRUB problems than I do, so I'd recommend trying what they suggest first.

---

### Post by spink007 on 2008-09-23
> **meierfra. said:**
> Are you still getting the "blinking cursor" at boot up? Or is it error 2 again.

Still blinking cursor.


Your "fdisk" only shows one hard drive. Did you disconnect your internal drive? 

No.  The internal drive is still connected, and I can still boot from it (FreeBSD 7.0) if I change the bios to make it the first boot device.


I'm not sure whether this applies in your case, but you might check out this post:
[http://ubuntuforums.org/showthread.php?t=151682]("http://ubuntuforums.org/showthread.php?t=151682")

How old is your computer?

Just bought it a few weeks ago:  Asus P5Q De Luxe, Q9450, 500 GB Sata (Samsung, I think), runs FreeBSD 7.0 just fine.


Edit: Hadn't  seen caljohnssmith last post, when I posted this
2nd Edit: Don't worry about the link I posted yet. First post the testdisk result caljohnsmith requested.

Thank you for your help. I will run caljohnssmith's recommeded test disk and post the results asap.

Steve

---

### Post by spink007 on 2008-09-23
> **unutbu said:**
> caljohnsmith, yes, I agree getting feedback from GRUB in the form of a GRUB Error would be a good thing before going down the path I suggested. 

spink007, I'm not sure what to do about the "can't open up /dev/scd0 read-write" error.
/dev/scd0 is the CD/DVD drive. GParted should have tried to read /dev/sda, your Linux hard drive instead. 
.

Thanks.  This is odd, but may have something to do with the problem of not being able to boot from this USB disk.  The complaint from the gpated library is that it is "unable to open /dev/scd0 read-write (read-only filesystem)...."Unable to open /dev/scd0 - unrecognized disk label."  

In fact, gparted does seem to open this disk read-only, it is in fact mounted /dev/sda1 on /media/disk and I can write to the disk anyway, so the OS can read-write to this disk.  

I'm not sure what the message about the "unrecognized disk label" means.  Do you think this is perhaps the problem?

Thanks again,

Steve

---

### Post by spink007 on 2008-09-23
> **caljohnsmith said:**
> As far as your Ubuntu HDD BIOS settings are concerned, do you have the HDD set as "auto", "LBA", "CHS", or something else in BIOS? 

The HDD is set to "auto".

And how old is that HDD? 

Just a couple of weeks old.

Based on your computer's symptoms, I would still recommend that we check your HDD and partition table at this point. You certainly have nothing to lose by doing so, and we might find the root of your problem. And Unutbu's point may also be entirely valid, but at this point we can't know for sure until we can get Grub working to the extent where it will at least give us errors. :)

So can you download the Ultimate Boot CD I mentioned earlier, or do you have a CD that came with your HDD with diagnostic tools? Also, I think we should check your partition table, so boot your Live CD, open a terminal and first do:
```
sudo fdisk -l
```
Please post that output (it uses units different than the previous time you posted with the "-lu" option and will save me doing the math for all your partitions). 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1c04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59668   479283178+  83  Linux
/dev/sda2           59669       60801     9100822+   5  Extended
/dev/sda5           59669       60801     9100791   82  Linux swap / Solaris


Then enable all your repositories in System > Prefs > Software Sources in order to download testdisk:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

I didn't see any errors, but here is the complete output from the testdisk (1st screen):

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1 59667 254 63  958566357
 2 E extended             59668   0  1 60800 254 63   18201645
 5 L Linux Swap           59668   1  1 60800 254 63   18201582











*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

And then I chose [Proceed] and I got the following output (2nd screen):

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1 59667 254 63  958566357
L Linux Swap           59668   1  1 60800 254 63   18201582











Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock Recover, 490 GB / 457 GiB


I hope that tells you something about the problem. (Is it odd that it didn't find the internal hard disk?)

Thanks once again,

Steve

---

### Post by caljohnsmith on 2008-09-23
It looks like your partition table for your new HDD is OK, Steve. But it is not a good sign that fdisk does not see your internal HDD for one thing. And since your HDD is so new, it is highly unlikely you have a problem related to a dying HDD. So I think the most likely culprit at this point is how you have your HDD set up in BIOS, and that might also be why your internal HDD is not being recognized either. What is on your internal HDD? Can you presently boot from it? Has it been working up until now? 

I would check out that thread that meierfra linked to; they give some good ideas in that thread of how you might set your BIOS to make your HDD work. You mentioned the HDD is set as "auto", so I would try other settings. For instance, you could change the "auto" to LBA, or if there is some place to turn off "DMA", try that. I've even read where people set their HDD to "RAID" to get it to work properly, even though they didn't have a RAID setup at all. So bottom line, try experimenting with your BIOS settings, reboot each time, and see what happens; you want to at least get to a point where Grub loads or tries to load and returns an error, so that you're not left with a blank screen and blinking cursor. :)

---

### Post by spink007 on 2008-09-23
> **caljohnsmith said:**
> It looks like your partition table for your new HDD is OK, Steve. But it is not a good sign that fdisk does not see your internal HDD for one thing. And since your HDD is so new, it is highly unlikely you have a problem related to a dying HDD. So I think the most likely culprit at this point is how you have your HDD set up in BIOS, and that might also be why your internal HDD is not being recognized either. What is on your internal HDD? Can you presently boot from it? Has it been working up until now? 


I would check out that thread that meierfra linked to; they give some good ideas in that thread of how you might set your BIOS to make your HDD work. You mentioned the HDD is set as "auto", so I would try other settings. For instance, you could change the "auto" to LBA, or if there is some place to turn off "DMA", try that. I've even read where people set their HDD to "RAID" to get it to work properly, even though they didn't have a RAID setup at all. So bottom line, try experimenting with your BIOS settings, reboot each time, and see what happens; you want to at least get to a point where Grub loads or tries to load and returns an error, so that you're not left with a blank screen and blinking cursor. :)

Thanks.  My internal hard drive looks just fine when I boot up FreeBSD 7.0 which is the OS that I have on it. I have no problems with it.  One thing I noticed is that I can't see the external drive when FreeBSD is booted (from the hard drive), and I can't see the internal drive when Linux is booted (from the LiveCD). 

I have been trying to change the parameters, with no luck, but I will look again and see if there are more I can change.  

Thanks for your help.  If you have any other ideas, please let me know.

Steve

---

