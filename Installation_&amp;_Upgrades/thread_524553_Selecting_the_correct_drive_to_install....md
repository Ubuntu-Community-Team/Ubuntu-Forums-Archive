---
title: "Selecting the correct drive to install..."
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2007-08-13
In working to install feisty, I have been getting Error 21 time and again, though I have confirmed the drive DOES exist and the files ARE installed. After going rounds in the forums (to no avail despite the valiant effort) I finally had to appeal to the folks at JMicron, the makers of the IDE controller on my motherboard. I have gotten this advice from the support technician, but am not sure how to go about it. 

The email I received states: 

> Dear Sir:

 

Please select “/dev/sda” to install the boot loader.

You will see both “/dev/sda” and “/dev/hdx” in the menu.

 

This MB’s BIOS seems to have some problems to install Linux.

Please try it, thanks!

I do not see such options in any menu upon trying to install feisty. 

I turn again to the forums, amazed that no one else has encountered this issue, but more importantly, looking for guidance as to how to accomplish this feat. How do I confirm the install on the correct drive as advised by JMicron?

---

### Post by tgalati4 on 2007-08-13
Download and create a Super Grub Floppy.  It boots off of the floppy, detects your /boot/grub/menu.lst and generally gets around BIOS weirdness.  Once you are booted into your distro, you can make changes to improve your boot detection.

You may need to use MAP statements to fix your boot problem.

Post:

/boot/grub/menu.lst

and 

/boot/grub/device.map

---

### Post by sp0nge on 2007-08-13
One problem there is that the machine in question does NOT have a floppy drive. When I was building the machine, I said to me self "Self", I said, " what are the chances that you'll actually need (let alone want) a floppy drive on this machine?" I opted for only the optical super drive instead. 

The next issue is that I've been dealing with this for about a week now, and have been directed in other posts to create this SGD, which I've continually tried and failed. I have burned both the Super Grub stand alone, and the SGD_GPARTED_SYSTEM_RESCUE disk. Both have failed miserably. I will be visiting a friend today on who's machine I will attempt to burn both, but since I have attempted both 3 times now (and I know I'm doing it correctly, because I successfully burned the feisty ISO) I don't see much changing. 

When I try to post the results of the files you request, I find the don't exist now. Once I open /boot, there are only the following:

abi-2.6.20-15-generic
config-2.6.20-15.generic
initrd.img-2.6.20-15-generic.bak
memtest86+.bin
System.map-2.6.20-15-generic
vmlinuz-2.6.20-15-generic


This was not the case before. I had access to the grub folder, but for some reason, now it is not there.

---

### Post by sp0nge on 2007-08-13
Well, in hopes something might change, I'm attempting the install once more. 

I'll be heading to a buddy's house shortly to try to both the ISO for sgd and for the sgd_gparted_system_rescue disk. I don't expect much change, but with 20 views and only 1 reply, I suppose I'm on my own. 

This is the first time I've found the forums unable to help, quite surprising if I might say. 

This install is about half done, I'll look to post more info as it comes along.

---

### Post by sp0nge on 2007-08-13
One step at a time, we're progressing. Hopefully someone is out there to help where I fall short. As requested earlier, I can now access /boot/grub/menu.lst and /boot/grub/device.map:

menu.lst:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=67944f0b-501e-4766-99c6-b97bc33d092f ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=67944f0b-501e-4766-99c6-b97bc33d092f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=67944f0b-501e-4766-99c6-b97bc33d092f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


and 


device.map:
```
(hd0)	/dev/sda
```

---

### Post by merlinus on 2007-08-13
You might comment out the hiddenmenu line near the top of menu.lst so the grub menu will appear upon bootup.

Otherwise, this looks good to me.

-merlin

---

### Post by sp0nge on 2007-08-13
Upon your suggestion, merlin, I attempted to comment out the hiddenmenu line and am told I do not have sufficient permissions when I try to save it. I've attempted to gain root by using the password I used upon the install and get authentication failure. How can I make this suggested change?

---

### Post by merlinus on 2007-08-13
```

gksudo gedit /boot/grub/menu.lst

```

-merlin

---

### Post by sp0nge on 2007-08-13
```
** (gedit:9031): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

** (gedit:9031): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

```

---

### Post by merlinus on 2007-08-13
Strange.  Did you use a lowercase L in menu.lst?

You could also use a text editor:

```

sudo nano /boot/grub/menu.lst

```

-merlin

---

### Post by sp0nge on 2007-08-13
I am using lower case letters. 

Upon using both gedit AND nano, I open a blank file. Nothing on it. No data. But I can navigate through Places -> Home Folder -> disk -> boot -> grub -> menu.lst and get the results posted earlier. This is making my brain hurt!! :confused:

---

### Post by sp0nge on 2007-08-13
New developments from JMicron, at least they're trying to help. 

> Dear Sir:

 

Could you show me the dmesg log in OS installation?

I think it can help us to clarify this issue.

 

Thanks~

 

Best Regards,
Ethan Hsiao


How/where can I find this log?

---

### Post by merlinus on 2007-08-13
Seems as though you are booting from the live cd?  If so, you can perhaps edit it with this:

```

gksudo gedit /disk/boot/grub/menu.lst

```

To get the log:

```

dmesg

```

-merlin

---

### Post by sp0nge on 2007-08-13
```
gksudo gedit /disk/boot/grub/menu.lst
```

Opens a blank file.

---

### Post by merlinus on 2007-08-13
So where is your ubuntu installation located, and how can you access its files and folders in Places/Computer?

-merlin

---

### Post by sp0nge on 2007-08-13
Well, it LOOKS like the installation was put on the hard drive correctly. From what I'm understanding from this guy with JMicron, as well as everything I've read thorough this meltdown, the problem is the controller is having trouble communicating with GRUB.

Upon looking at Places>Computer I have 3 options: External CD-RW/DVD RW, 227.1GB Volume: disk, and File System. Upon poking into the 227.1BG Volume: disk (the one that LOOKS like it should be my HDD), I have the usual folders that I would expect to see, namely /boot in this situation. 

Places>Computer>227.1GB Volume:disk>boot>grub>menu.lst

---

### Post by merlinus on 2007-08-13
If you right-click on menu.lst, is there an option to open it as Administrator?

-merlin

---

### Post by sp0nge on 2007-08-13
No. I can open with Text Editor, or open with Other Application, but nothing about admin.

---

### Post by merlinus on 2007-08-13
Open it with the text editor, click Save As, and look at the path (e.g. boot/grub).  Maybe that way you can figure out how to open it using gksudo gedit.

Also, in Places/Computer, do you have an entry for File System?

-merlin

---

### Post by sp0nge on 2007-08-13
The path looks to be correct, /boot/grub/menu.lst

Again, when trying to open it with gedit, it is an empty file. 

Yes. In Places>Computer, there is a place for File System. Upon looking in there, I see the folders that I would expect, but when I open the /boot folder, there are only generic files, no /grub or any other folder.

---

### Post by bwtranch on 2007-08-13
You need to become root, not just sudo

sudo su

---

### Post by sp0nge on 2007-08-13
Well, that answers one question, I've gained root access, but still find an empty "new" file when I try to open /boot/grub/menu.lst

---

### Post by sp0nge on 2007-08-13
Now that I've gained root, and since I'm getting an empty file when I try

```
gksudo gedit /disk/boot/grub/menu.lst
```

I started navigating through the system in the terminal, thinking that if I can SEE menu,lst, I will be able to open it. 

```
root@ubuntu:/# ls
bin   cdrom  etc   initrd      lib    mnt  proc  root  srv  tmp  var
boot  dev    home  initrd.img  media  opt  rofs  sbin  sys  usr  vmlinuz
root@ubuntu:/# cd /boot
root@ubuntu:/boot# ls
abi-2.6.20-15-generic             memtest86+.bin
config-2.6.20-15-generic          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-15-generic

```

How can it be that I can navigate to the file graphically, but not through the terminal?!

---

### Post by sp0nge on 2007-08-13
Well. Ethan has offered me more advice,,,

> Dear Sir:

 

The logs are looked OK.

 

Can you try to install in the other modes?

 

Please try to change JMB361 controller’s BIOS setting to RAID or AHCI mode.

 

Best Regards,
Ethan Hsiao

I'll make this adjustment, and see what happens next.

---

### Post by merlinus on 2007-08-13
You can open gedit as root (gksudo gedit), and try to navigate to menu.lst using File/Open.

But it does seem that although it exists, there is no content.

Have you tried to reinstall grub?

-merlin

---

### Post by sp0nge on 2007-08-13
When trying to open the file as suggested, there is no option to get into the needed folders.  I can access HOME and INSTALL only. 


I have not tried to re-install GRUB, can you direct me as to how to accomplish this?

---

### Post by merlinus on 2007-08-13
```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute results from find for (hdx,x).

-merlin

---

### Post by sp0nge on 2007-08-14
I believe you had me do this in one of the first posts when I encountered this issue. Just before quit, returned:

```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

```

---

### Post by merlinus on 2007-08-14
Now see if there is any content in /boot/grub.menu.lst.

-merlin

---

