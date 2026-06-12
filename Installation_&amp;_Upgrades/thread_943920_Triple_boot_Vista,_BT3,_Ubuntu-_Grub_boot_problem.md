---
title: "Triple boot: Vista, BT3, Ubuntu- Grub boot problem"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by Nyoxis on 2008-10-10
Edit: If you're reading this post due to a Grub boot vista problem, I'd suggest looking elsewhere, because my problem was in how I installed Vista, not in Grub.

Hey guys, I hate to be that guy that has a first post asking for help, but having seen the sheer awesomeness this forum's posters I figured you might be able to save me heaps of trouble. :)

I've just installed 3 OS onto my PC, Vista first, Backtrack, then Ubuntu but I'm now having problems loading Vista from Grub. Everytime I try to load it it just reboots my computer, I've done some looking around for similar problems/solutions but I'm reluctant to try out any non-specific advice for fear of undoing my work.

Here's some system info:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f04e582

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7860    63130216+   7  HPFS/NTFS
/dev/sda2            7860       10292    19540242   83  Linux
/dev/sda3           10293       23666   107426655    b  W95 FAT32
/dev/sda4           23667       30401    54098887+   5  Extended
/dev/sda5           23667       30120    51841723+  83  Linux
/dev/sda6           30121       30401     2257101   82  Linux swap / Solaris

Disk /dev/sdb: 123 MB, 123207680 bytes
16 heads, 32 sectors/track, 470 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xfa6f098f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         470      120304    b  W95 FAT32

Disk /dev/sdc: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   623257122   679486963    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(623257121, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(679486962, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   567173161  1190466982   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(567173160, 0, 2)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(1190466981, 0, 3)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?         858         858           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(857, 0, 3)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(857, 0, 2)
Partition 3 does not end on cylinder boundary.
/dev/sdc4               1  1145037824  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(1145037823, 0, 3)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

...And the grub menu:
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
# kopt=root=UUID=63824ffe-3584-46e5-b4b1-ae1d824e827c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash all_generic_ide xforcevesa

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=63824ffe-3584-46e5-b4b1-ae1d824e827c ro quiet splash all_generic_ide xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=63824ffe-3584-46e5-b4b1-ae1d824e827c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		BackTrack3 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 ro vga = 773 
savedefault
boot

```

Thanks. :)

---

### Post by sokopok on 2008-10-10
I don't know if this will work, but I had similar problems a while ago, so you might give it a try: just remove the "savedefault" line from your Windows entry in grub's menu.lst . It doesn't need to be there anyway. I know this seems to have no relation to the problem, but for me it was the only thing that made things work again. Never hurts to try. (You can try it by editing the boot commands from grub itself, so you don't have to edit your actual menu.lst just to check if it works)

---

### Post by Nyoxis on 2008-10-10
> **sokopok said:**
> I don't know if this will work, but I had similar problems a while ago, so you might give it a try: just remove the "savedefault" line from your Windows entry in grub's menu.lst . It doesn't need to be there anyway. I know this seems to have no relation to the problem, but for me it was the only thing that made things work again. Never hurts to try. (You can try it by editing the boot commands from grub itself, so you don't have to edit your actual menu.lst just to check if it works)

Thanks for the response, but unfortunately that didn't work, just rebooted. :(

---

### Post by caljohnsmith on 2008-10-10
Your entry in your Grub's menu.lst for Vista should work assuming Vista is in the first partition of your Vista + Ubuntu drive, so I'm almost positive you have a Windows problem and not a Grub problem at this point. Do you have a Vista Recovery CD? If not, you can download one [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Once you have that, boot it up, and just do the "Vista Repair" option. That will most likely fix your problem, but if not, we can go from there. Let me know how it goes. :)

---

### Post by Nyoxis on 2008-10-10
I tried the repair, it wouldn't do a system restore (no restore points created) and the boot fix finished showing no found problems. I tried vista again but it just restarted, as per norm. :) Thanks for the help.

Update: I had tried the Vista boot CD before this, but failed to see any 'RM Windows Recovery Tool' ([as seen here]("http://www.rm.com/Support/TechnicalArticle.asp?cref=TEC838573")) and because my Visa OS had nothing on it, I'm currently trying a fresh installation on the 60gb partition- I'll let you know how it goes.

---

### Post by Nyoxis on 2008-10-11
Yeah so I reinstalled Vista, it removed the Grub loader, so I reinstalled Ubuntu, and now I'm back to square-one.
Any ideas? :)

---

### Post by caljohnsmith on 2008-10-11
> **Nyoxis said:**
> Yeah so I reinstalled Vista, it removed the Grub loader, so I reinstalled Ubuntu, and now I'm back to square-one.
Any ideas? :)
"Square one": so does that mean you when you start up, you get a Grub menu where you can choose Vista, but booting Vista causes a reboot? Can you successfully boot Ubuntu? Since you changed things around, please post again:
```
sudo fdisk -lu
```
And also post your menu.lst if you can, and we can work from there.

---

### Post by Nyoxis on 2008-10-11
Okay the disk layout:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f04e582

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   126260495    63130216+   7  HPFS/NTFS
/dev/sda2       126260496   165340979    19540242   83  Linux
/dev/sda3   *   165340980   380194289   107426655    b  W95 FAT32
/dev/sda4       380194290   488392064    54098887+   5  Extended
/dev/sda5       380194353   483877799    51841723+  83  Linux
/dev/sda6       483877863   488392064     2257101   82  Linux swap / Solaris

```

And the Grub menu:
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
# kopt=root=UUID=b4118b9b-1043-49be-ba34-1fb6ae037848 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash all_generic_ide xforcevesa

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b4118b9b-1043-49be-ba34-1fb6ae037848 ro quiet splash all_generic_ide xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b4118b9b-1043-49be-ba34-1fb6ae037848 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		BackTrack3 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 ro vga = 773 
savedefault
boot

```

At the moment Ubuntu loads fine, Backtrack3 loads fine and trying to load vista causes the pc to reboot. Thanks again. :)

---

### Post by caljohnsmith on 2008-10-11
So is Vista on sda1 or sda3? I would assume sda1, but then what is sda3? If Vista is in sda1, your Grub menu entry for Vista should be fine. What is the linux partition sda2? Your main Ubuntu install appears to be in sda5. Also, have you ever been able to boot Vista from that HDD and/or that computer? Or is this your first try? 

Something else that is suspicious is that sda3 is marked as the active (bootable) partition, and yet if you ran Vista from your Grub menu prior to posting that fdisk output, I believe that should have made sda1 the active partition since your Grub menu.lst entry for Vista includes the "makeactive" command. I'm assuming you tried to boot Vista from Grub before posting the "fdisk" output?

---

### Post by Nyoxis on 2008-10-11
> **caljohnsmith said:**
> So is Vista on sda1 or sda3? I would assume sda1, but then what is sda3? If Vista is in sda1, your Grub menu entry for Vista should be fine. What is the linux partition sda2? Your main Ubuntu install appears to be in sda5. Also, have you ever been able to boot Vista from that HDD and/or that computer? Or is this your first try? 

Something else that is suspicious is that sda3 is marked as the active (bootable) partition, and yet if you ran Vista from your Grub menu prior to posting that fdisk output, I believe that should have made sda1 the active partition since your Grub menu.lst entry for Vista includes the "makeactive" command. I'm assuming you tried to boot Vista from Grub before posting the "fdisk" output?

Vista is on sda1, Backtrack3 is on sda2, sda3 should be my shared area for swapping files between the operating systems. 
Hmm that's strange about the boot on sda3, I'll go into fdisk and change it to sda1 and retry a Vista boot.
I've had Vista on this pc before and yes, it worked fine.

Before posting the fdisk output I'm not too sure what I was doing, I tried temporarily changing the Grub commands in the boot loader, some of this involved taking out the makeactive line.
So yeah I'll go into fdisk and change the bootable options to sda1 only. Thanks.

Edit: Nothing, changing the boot to exclusively sda1 still results in a reboot when selecting Vista in Grub.

---

### Post by Nyoxis on 2008-10-11
Thought I should add I just noticed, before the system reboots when trying to load Vista it says, "Starting up...", then it reboots. Nothing fancy just normal-text.

---

### Post by caljohnsmith on 2008-10-11
Yes, changing the boot flag from sda3 to sda1 won't make any difference to Grub about booting either partition, I was only pointing that out because it was curious how sda1 didn't have the flag even with "makeactive" in its Grub entry; I didn't mean to imply that changing sda1 to the active partition was going to help, so sorry if I caused confusion. :)

Anyway, because your Grub entry for Vista should be fine, it looks like you have a Vista problem rather than a Grub problem at this point. So you went through the entire "Vista Repair" from the Vista Recovery CD, but Vista still reboots when you try and boot it? If so, boot the Recovery CD again, go to the command line, and do the following:
```
bootrec /fixboot
chkdsk /r
bootrec /rebuildbcd

```
I think the "Vista Repair" option probably did the equivalent of the above commands, so I'm not sure if they will make any difference; it's worth at try, so let me know what happens after using them and booting Vista again.

EDIT: Also, you said in post #6 you reinstalled Vista, and then reinstalled Ubuntu. Before you reinstalled Ubuntu, did Vista work? Could you boot directly into it?

---

### Post by Nyoxis on 2008-10-11
The fixboot completed successfully.
The checkdisk said it was nfst, but "Windows cannot run disk checking on this volume because it is write protected."
The rebuild identified windows.old and asked me if I wanted to add it to the boot somethingorother and I said yes, just to see where it went.
I restarted, tried Vista again, nothing had changed (just reboots, with the aforementioned message).
I'm considering formating my first partition within Ubuntu and reinstalling vista agin on it, then reinstalling Ubuntu (for Grub).

> Also, you said in post #6 you reinstalled Vista, and then reinstalled Ubuntu. Before you reinstalled Ubuntu, did Vista work? Could you boot directly into it?
Yeah, I'm pretty sure I could, not 100% though. Again, thanks for the help. :)

Edit: If it helps, I can access my windows files in Ubuntu...

---

### Post by caljohnsmith on 2008-10-11
So do you have an actual Vista Install CD/DVD? You previously gave a link about having a Vista recovery partition, which you obviously don't have any more. So how are you installing Vista? 

It would be helpful to at least look at your Vista root directory and make sure it looks like you have a normal Vista install, so please post the output of:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one.

---

### Post by Nyoxis on 2008-10-11
> **caljohnsmith said:**
> So do you have an actual Vista Install CD/DVD? You previously gave a link about having a Vista recovery partition, which you obviously don't have any more. So how are you installing Vista? 

It would be helpful to at least look at your Vista root directory and make sure it looks like you have a normal Vista install, so please post the output of:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one.

Unfortunately 
```

sudo mount /dev/sda1 /mnt

```
Didn't work, and :
```

ls -l /mnt

```
Said, "0".

Since I've got my data backed up, I figured instead of fiddling around with lots of settings I would do a completely clean install of everything . This is because the first time I installed the 3 operating systems I encountered lots of problems (which I overcame) and Vista not loading may have been a result of me fiddling with settings I was not too sure with.
So, yeah, I formatted the HDD in BT3-->fdisk and now I'm reinstalling Vista onto my blank HDD with my Vista DVD^^. :)

I appreciate all the help so far, and I should be finished in a few hours (hopefully with no Vista loaidng problems) so I'll keep you updated, and keep a log of how I install incase I encounter any problems. Thanks. :)

---

### Post by Nyoxis on 2008-10-11
I think I might have found the problem...it's rather embarrasing though. :oops:
See, when I begun the task of trying to get 3 OS on my pc, I really didn't know much and I used all the resources I could find to help me along the way, but now going back and retracing all my steps with a fresh start I've found the problem in what I did.

When I was partitioning my drives into the 4 areas, I simply resized my only partition, sda1 - which had Vista installed on, instead of using the Vista shrink space tool. This obviously led to the 'destruction' of Vista, and I realise this now. After installing Backtrack 3 I didn't see Vista in the new bootloader (Lilo, I think) and I presumed this was because it was, simply, inferior to Grub.

So yeah, I've seen the error in my ways and I should, hopefully, have no similar problems in the future. I'm glad I started again, now, because it's allowed me to find my problem and I've learned loads, so much that I plan to write a decent guide on how to do the whole process from a newbie POV. :D

Thanks for all the hard work mate, I'll either start a new, or rekindle this post if I get any more problems, but for now I'll mark as solved. :)

Nyoxis.

---

### Post by caljohnsmith on 2008-10-11
Actually, you shouldn't feel embarrassed at all, because if it weren't for the fact that Vista (unlike any other OS I know of) maintains its own partition table exclusive from the main partition table in the HDD's MBR, you could easily resize Vista with gparted or any other good partition editor. So Vista is really a special case. But anyway, I'm glad you have it all working now, and I'm glad I could help out. Cheers and have fun with your three OSes. :)

---

