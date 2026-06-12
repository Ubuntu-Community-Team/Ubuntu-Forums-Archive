---
title: "Installed Ubuntu, but now Im getting JUST a black screen!!"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by sanelx09 on 2006-11-26
Hello.

I have installed ubuntu this morning, having a lot of trouble with the partitioning. So, I researched it and found out what it was. I did the manual partition and I left the main hard drive at around 40 gigs, out of a 80 total, and an "ext3" at about 35 gigs. Then, I kept receiving errors about not having swap space, so I went back and made a "linux-swap" partition, and I didnt receive the error anymore. 

It finished installing, I rebooted and took the cd out, and once the laptop turned back on, it showed a complete black screen saying only "GRUB.." at the top. (Actually Im not 100% it says GRUB at the top, I just know it begins with a G, but Im pretty confident it said GRUB)

I waited around 30 mintues and nothing happend, I rebooted again and waited again and nothing happened. Now, Im running on the live-cd, just so I could post this thread, and beg you guys for help!

I bought this laptop last year and it has a Intel Centrino 1.7ghz processor, 512mb ram, and a 80 gig hard drive. So, I dont think the spec's are the problem.


Please let me know how I can fix this! I really want to run on ubuntu, but if it wont work, I need to have me windows xp working again!

Thank you in advance.

---

### Post by taurus on 2006-11-26
At the GRUB screen, press <Esc> to see the GRUB menu.  Then, highlight a kernel, usually the first one, and hit enter to boot it up?  

Now, see what happens?

---

### Post by sanelx09 on 2006-11-26
Thanks for the quick response taurus, but your suggested solution did not work.

I start up the computer and I get a completely black screen, and on the top left corner, in gray letter its says "GRUB" and thats it.

I tried pressing "ESC" a few times but nothing happened. Any button I press is useless, after a while I just start hearing beeping noises after I press each button.

I looked over the partition, and saw that the NTFS partition had the "boot" flag, maybe this could be the problem? Should I remove that flag and place it on the ext3 partition which has the linux installed on it (I am guessing).

If there is no solution, please tell me how I can go back to my old OS, windows XP, from the Live-CD if possible.

Thanks.

---

### Post by taurus on 2006-11-26
I need to see your /boot/grub/menu.lst so you have to boot it from a LiveCD, mount the partition where / is (unless you have a separate partition for /boot), and paste the output of your /boot/grub/menu.lst here.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
(assuming that your linux partition, /, is on /dev/hda2...)
cat /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by sanelx09 on 2006-11-26
If I did it correctly, this is what it output..

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=3d093911-815e-40f7-a6d3-326a48b0c8fb ro
# kopt_2_6=root=/dev/hda2 ro

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1




I pasted what was in the "code" that you sent, except for the parenthesis.

---

### Post by taurus on 2006-11-26
Yip, that's what I want to see.  A couple things regarding that file.  I would remove the # sign in front of "hiddenmenu" so you can see the menu and I always like to see which process starts when the kernel boots so if there is a problem, I would know which one causes it...  Therefore, you also need to modify the first entry so it would look something like

```

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro vga=773
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

You can edit that file with

Applications -> Accessories -> Terminal
```
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
Also, I need to see the layout of your harddrives.

```
sudo fdisk -l
```

---

### Post by sanelx09 on 2006-11-26
Ok, I updated the menu.lst, and checked to make sure it was updated and it was.

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5716    45913738+   7  HPFS/NTFS
/dev/hda2            5717        9398    29575665   83  Linux
/dev/hda3            9399        9729     2658757+  82  Linux swap / Solaris


And there is the disk information.
Do you want me to reboot now, or wait until further instructions?

By the way, Im from Jacksonville, FL too :)

---

### Post by taurus on 2006-11-26
Unmount your harddrive first (although the LiveCD will unmount it when you reboot) just to be sure.

```
sudo umount /mnt/ubuntu
```
Now, reboot and don't forget to remove the LiveCD.  This time, you will see a GRUB menu and you have 10 seconds to use the arrow keys to move up or down, depending on what you want to boot.

What part of Jax anyway?  ;)

---

### Post by sanelx09 on 2006-11-26
> ubuntu@ubuntu:~$ sudo umount /mnt/ubuntu
umount: /mnt/ubuntu: device is busy
umount: /mnt/ubuntu: device is busy


The unmounting didn't work using the code.. do you want me to go ahead and reboot, or try to unmount it another way?

I live very close the to the Mandarin High School area.

---

### Post by taurus on 2006-11-26
Oh, you have to get out of that directory first before you can unmount it.

```
cd 
sudo umount /mnt/ubuntu
```
Down in the Mandarin area, eh!  I live near UNF...

---

### Post by sanelx09 on 2006-11-26
> ubuntu@ubuntu:~$ cd 
ubuntu@ubuntu:~$ sudo umount /mnt/ubuntu
umount: /mnt/ubuntu: device is busy
umount: /mnt/ubuntu: device is busy


Same error :(

Near UNF, really? I used to live right on kernan before I moved here.

---

### Post by taurus on 2006-11-26
You already saved the new chances in /boot/grub/meun.lst right (on your harddrive)!  Then just reboot...

---

### Post by sanelx09 on 2006-11-26
Hello again Taurus, I tried rebooting and I still have the exact same black screen with the "GRUB" text on the top left.

What do you mean "on your harddrive"? When I edited menu.lst, I just clicked "Save" up top, and it saved.
I Checked the menu.lst again using the code you provided me, I compared it, and it was still as I left it when I updated menu.lst.

Now whats the problem?

---

### Post by taurus on 2006-11-26
Look at the menu.lst on your harddrive again to make sure you have actually saved the chances.

(from the LiveCD again...)
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
more /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by sanelx09 on 2006-11-26
> ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
mkdir: cannot create directory `/mnt/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


and for the menu.lst> ubuntu@ubuntu:~$ more /mnt/ubuntu/boot/grub/menu.lst
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
# kopt=root=UUID=3d093911-815e-40f7-a6d3-326a48b0c8fb ro
# kopt_2_6=root=/dev/hda2 ro

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro vga=773
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1



The menu.lst looks how I updated it.
Look at the first quote, is there errors in there?

---

### Post by taurus on 2006-11-26
Actually, it's /dev/hda2 because /dev/hda1 is your XP!!!  :oops:

---

### Post by sanelx09 on 2006-11-26
Oh, duh lol.

But, what do I do now?

---

### Post by taurus on 2006-11-26
```
sudo umount /mnt/ubuntu
sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
more /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by sanelx09 on 2006-11-26
> ubuntu@ubuntu:~$ sudo umount /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
ubuntu@ubuntu:~$ more /mnt/ubuntu/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entr
y
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or you
r
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default ent
ry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editin
g
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
# kopt=root=UUID=3d093911-815e-40f7-a6d3-326a48b0c8fb ro
# kopt_2_6=root=/dev/hda2 ro

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro vga=773
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


Now what, Reboot?

By the way, did I screw up my XP now?

---

### Post by taurus on 2006-11-26
No, your XP is still in /dev/hda1, waiting for you to boot it.  What if you reinstall GRUB to MBR again.

```
sudo grub-install /dev/hda
```
Then reboot.

---

### Post by sanelx09 on 2006-11-26
ughhh.

> ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.


---

### Post by taurus on 2006-11-26
How about 

```
sudo grub
```
That would drop you into grub command line prompt,

```

grub> root (hd0,1)
grub> setup (hd0)
grub> edit

```
Tell me if you run into a problem after you enter which command from above!

---

### Post by sanelx09 on 2006-11-26
> grub>
      setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stag
e2 /boot/grub/menu.lst"... succeeded
Done.


and then the problem .. 

> grub>
      edit

Error 27: Unrecognized command


---

### Post by taurus on 2006-11-26
Oh dear, I really need to get some sleep.  It should be quit.  ](*,)

---

### Post by sanelx09 on 2006-11-26
I really appreciate your efforts in helping me install this OS :)

So, now I reboot? 

Thanks for the quick responses too :D

---

### Post by taurus on 2006-11-26
Reboot and keep your fingers crossed (and probably your toes too)!!!

---

### Post by sanelx09 on 2006-11-26
Somebody shoot me.

Same problem. :@

As much as I would like ubuntu, I dont think it likes me back :(

Any other suggestions? If not, how can I remove ubuntu and just start off in my regular xp?

Again, thanks for your help.

---

### Post by taurus on 2006-11-26
At this point, you just need to remove the GRUB.  Do you have XP CD?  You can boot from it and remove GRUB.  Then, it will boot into XP for you.  From there, you can remove both /dev/hda2 & /dev/hda3 or you can use the LiveCD to remove those partitions as well.  Otherwise, I just have to drive down there and figure out what is going on myself (or you bring your computer up here)!!!

---

### Post by sanelx09 on 2006-11-26
lol, yeah I think that is the best idea. 
No, I do not have the XP CD. On the LiveCd, Do I just go to the System>Admin>Gnome Partition editor, and erase all the partitions except the first one (NTFS)?

---

### Post by taurus on 2006-11-26
Yip.

---

### Post by sanelx09 on 2006-11-26
Ok, deleted, and resized everything. Hopefully now my XP will work with its regular settings. 

Would you recommend trying to re-install ubuntu?
If so, can you tell me how I should partition my 80 Gig hard drive, giving about 30gb for Ubuntu. Partitioning was what I was most confused on. 

Thanks.

---

### Post by taurus on 2006-11-26
I would use the GParted LiveCD to resize the 80GB, leaving 30GB free at the end of the harddrive!  Then, I would tell the Ubuntu installer to use the whole 30GB harddrive and in which case, the installer would divide that into two more partitions, one for / and one for swap...  

If you're really interested in running Ubuntu on your machine and not sure how to install it or get it to work, PM me and maybe you can bring your computer to my work place on weekend and I can show you how to do it in person...

---

### Post by sanelx09 on 2006-11-26
check your PMB please.

---

