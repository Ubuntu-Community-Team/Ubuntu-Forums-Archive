---
title: "Problem booting to windows"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by zenthor on 2008-06-03
Greetings to everyone reading this. First of all, i want to let you know that im new to to Linux and Ubuntu, Ive used Windows all my life and im tired of it and i was whilling to switch to Ubuntu. So,  heres the thing:

I have 2 hard disks, one of 60GB and other of 40GB.
I had 3 diferent windows on them, Windows XP SP1 and Windows XP SP2 on diferent partitions on the disk of 40GB, and i had Windows XP SP2 UE on the 60GB. After doing many test on them 3, i decided that i wanted to deleat the SP1, keep UE and SP2, so i deleated the partition of the SP1 in the 40GB disk, and keep part of the disk with the SP2, and the 60GB parted in 3, one with UE, and other 2 for games/music.

So i proceed to install Ubuntu 7.04 FF from a live CD ive got from a teacher, i went all the steps quite ok, but i didnt made a partition for the SWAP (wich now i know i have to), i specifically went manual when partition time came, and then, i made a ext3 partition on the 19GB left i had on the 40GB, I pick "primary" not logical, and "beginning" not end on the options. Then I proceed to the end. My ubuntu was ok, but then i wanted to go into my Windows to finish some homework i had for this morning and i couldnt. I thought i could fix it on my own, and decided to eliminate the ext3 partition, so i deleated it, and on its place, i went "Guided" at the time of partition and Ive picked "use largest continue free disk space" so it automatically do the swap, etc etc, and i try again, and nothing, still my windows not appearing on the GRUB. I throw myself into forums to try to find out whats the problem, eddited a lil my GRUB list and such but no efect, since on the GRUB list, theres no where, where appears a windows. I formated again, and then i went manually again, i made a 2GB partition for the SWAP(i know its a lil too much for my 7XX RAM but i guess theres no problem on adding a lil till 2GB), and installed again the ubuntu on the space left, and nothing still ;(

Now, what im guessing is, that since i was a beginner at the time ive installed my windows, the SP1 was the OS that was already in when i got the computer, so im guessing that who put it there, made the C:/ of the SP1, primary, and the D:/ of it was secondary/logical. So, after that, ive installed the UE on the other disk, i cant recall if i picked to make the UE partition primary or was secondary/logical really, and then i installed the  SP2 on the D:/ of the 40Gb disk, wich im sure was secondary/logical. Now aside this, when i enter the boot menu on my comp, after the POST, before i went Ubuntu, i had as one choice to boot from HardDisk IDE-0 and same -1, but the thing was on the 0, i had the SP1 alone, and on the -1 i had the Sp2, and UE(even if they were on separate disks, they appeared like if was on the same IDE HardDisk), this leads me to think that the partition where i installed the UE was secondary/logical not primary, so i guess it would appear with the SP1.

Anyways, now with ubuntu on, i cant get neither of my 2 other windows on the grub menu, not the UE or the Sp2, there is a solution to this?

If i decide to format lets say the first partition, where my UE is on the 60GB disk, can i move safely the important files i have there to the other partitions of the same disk, and at the time or re installing my windows i re create that partition as primary, will this make any diference? makeing as primary will allow me to boot it from the grub menu? or should i move all the rest of the files of the 40GB disk to the 60GB one, and make 40GB disk only ubuntu and the 60GB windows's? (i would rather not give ubuntu as much space as 40GB, but only half)

Someone please help me, i have to finish my homework for next week (for less points since i didnt today), and i need to use windows for it, i would really really really apreciate it :(


Kind regards,
Esteban Zenteno

---

### Post by pytheas22 on 2008-06-03
In order to give a better understanding of your situation, please do these things:

1. install gparted by opening a terminal (Applications>Accessories menu) and entering the command:
```

sudo apt-get install gparted
```

2. then run gparted by typing in a terminal:
```

sudo gparted
```

and please take a screenshot of the gparted screens for both of your disks (you will need to use the Gparted>Devices menu to switch between your two disks).  You can take a screenshot by pressing the "Print Screen" button of your keyboard (press with Alt to take a shot of only the current window).  Post the screenshots here.

3. Please post the output of this command:
```

cat /boot/grub/menu.lst
```

With this information we should be able to help you.

---

### Post by zenthor on 2008-06-03
im doing this right away, please hold on, and i'll post the SS's
Thanks A LOT for trying to help me :)

---

### Post by zenthor on 2008-06-03
Heres the two screen shoot from the 2 disks with the gparted.
If you can't understand something, cause is on spanish, let me know, I'll translate it for you.

Heres the 3. point code:

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
timeout         3

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
# kopt=root=UUID=1f5e2668-af0d-4ea1-82bb-ced5d9681103 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=1f5e2668-af0d-4ea1-82bb-ced5d9681103 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=1f5e2668-af0d-4ea1-82bb-ced5d9681103 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1f5e2668-af0d-4ea1-82bb-ced5d9681103 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1f5e2668-af0d-4ea1-82bb-ced5d9681103 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by pytheas22 on 2008-06-03
In a terminal, type:
```

sudo gedit /boot/grub/menu.lst
```

and add to the bottom of the file this section:
```

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Now reboot and see if you can boot to either of options for Windows.  If you can get that far, we'll keep working to get all of the Windows partitions back.  If it doesn't work, be sure to write down any error messages.

---

### Post by pytheas22 on 2008-06-03
Another approach to this that you can take is to download from [http://forjamari.linex.org/frs/download.php/942/super_grub_disk_0.9716.iso](http://forjamari.linex.org/frs/download.php/942/super_grub_disk_0.9716.iso) the "Super Grub Boot Disk."  I have never used it, but in principle it will automatically fix your grub menu.  But hopefully the solution above will solve your problem and this won't be necessary.

---

### Post by zenthor on 2008-06-03
Ill do the first thing you said right away, please dont leave, wait until i tell you the results. T_T im desperate

---

### Post by zenthor on 2008-06-04
I did what you said, and it works to me, but just for the record, if I enter the 2th option on my grub menu, it throws me an error, if i enter the first one, its perfect, cause it leads me to the menu where i can pick between my 2 windows that i have left, so i think ill deleat the last entry on the grub menu to fix it right?

Now if you wouldnt mind, how can i give my GRUB menu, more time to pick a OS, i mean, giving me more time to press ESC to get in, and how can I set windows on top of the list, so if i dont press anything, it would automatically get into the windows one on top?

Thanks a lot Pytheas, i'll "thank" you for this too!
You saved my butt

---

### Post by bartos on 2008-06-04
Along the same lines so we don't start a new post. Is there a command or gui way to list how the hard drives are seen so they show up as (0,0) XP or (1,0) Ubuntu? Wouls make it easier to add to grub.

Thanks

---

### Post by pytheas22 on 2008-06-04
I'm glad it worked!

> I did what you said, and it works to me, but just for the record, if I enter the 2th option on my grub menu, it throws me an error, if i enter the first one, its perfect, cause it leads me to the menu where i can pick between my 2 windows that i have left, so i think ill deleat the last entry on the grub menu to fix it right?

I thought that this would probably happen.  I didn't think that the second Windows option would work, but I had you append it to the menu.lst just in case, because I wasn't sure.  You can delete the last grub entry since it doesn't work.
> 
Now if you wouldnt mind, how can i give my GRUB menu, more time to pick a OS, i mean, giving me more time to press ESC to get in, and how can I set windows on top of the list, so if i dont press anything, it would automatically get into the windows one on top?

While I was researching your problem last night I came across a utility [here]("http://ubuntuforums.org/showthread.php?t=228104") that says it will allow you to do this in an easy way.  You can give it a try, but I would recommend that you backup your current working menu.lst first, just in case.  This command would place a backup copy onto your Desktop:
```

cp /boot/grub/menu.lst ~/Desktop/menu.lst.backup
```

You could also email to yourself.  If you don't want to use that script, I could try to figure out how to do it using the command line, but I've never done it so I'm not sure right now.
> 
Is there a command or gui way to list how the hard drives are seen so they show up as (0,0) XP or (1,0) Ubuntu? Wouls make it easier to add to grub.

I don't know of any way to do this in one step (although there probably is a way).  The way I know to do it is to look at your current /boot/grub/menu.lst file and see which partition addresses correspond to which operating systems, and then look at the geometry of your hard drive (using gparted) to figure out where everything is.  If you need help, post screenshots from gparted and your menu.lst file.

---

