---
title: "Ubuntu doesnt start from grub after fresh install"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by klaztaz on 2008-02-29
Hi all,

after finally installing Ubuntu for the first time, i restart my PC as it ask me and when i select the windows installation  from the Grub it tells me that NTLR is missing.
When i try to boot Ubuntu it says something like kernel alive and then my computer just restarts.

What am i doing wrong?

I have windows on a SATA and Ubuntu on a normal one.
My primary was the SATA so only windows was loading so i changed it to the master hard drive which had the linux for the Grub to appear. But when I do this, windows doesnt start and Ubuntu just freaks out and restarts my PC.

Can anyone shed some light please?

Thanx in advance

---

### Post by Pumalite on 2008-02-29
Put back drives as they were. Boot Ubuntu Live CD and post:
sudo fdisk -lu

---

### Post by klaztaz on 2008-02-29
i used the alternative CD because the live was not working, it was restarting my pc as well.
should i try the same with the alternative cd?

---

### Post by Pumalite on 2008-02-29
If you get a command line, sure. I don't think you get a Terminal with the Alternate CD.

---

### Post by klaztaz on 2008-02-29
i tried to boot from the first hard drive option while i had the cd loaded which brought me the grub again. But still the same result.
I also tried the F6 other options command and typed in the fdisk -lu but it gave me an error after displaying a lot of lines of code ans telling me some things like cannot mount or boot something like that

what do i do now? Why is it so hard to make an istall :(

---

### Post by Pumalite on 2008-02-29
Get a Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to disk and boot from it.
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst ( from the partition where you installed Ubuntu)

---

### Post by klaztaz on 2008-02-29
im right now in the knoppix desktop and i cannot run the cat ..... command you said. How do i do it? I opened the consle and typed the sudo fdiskisk -lu.
Now what next?

---

### Post by Pumalite on 2008-02-29
sudo fdisk -lu (Enter)
Post here (copy and paste) the output.
Menu.lst is in 'grub' which is in 'boot' which is in the partition in which you installed Ubuntu. This partition is probably mounted somewhere in /media

---

### Post by klaztaz on 2008-03-01
ok ill give it a go tonight again because i almost game up on it for the 4th time hehe.

thanx again for your patience, time and advice.

Ill first have to check if i can surf the web from knoppix.

By the way this knoppix version was pretty nice. I liked the environment.

Anyway ill post the output tonight and hope for the best

---

### Post by Pumalite on 2008-03-01
Ok.

---

### Post by klaztaz on 2008-03-01
hello again Pumalite,

ok i tried everything i know but nothing worked when i tried to enter the web or copy it to another hard disk so i took a photo of it, with my phone :)

---

### Post by Pumalite on 2008-03-01
All I see is you fdisk. I need your menu.lst. I don't like Windows in sdb.

---

### Post by klaztaz on 2008-03-01
yes but how can i get it?
when i type it in the console i get an error telling me that such a file or directory does not exist
.

And what do you mean you donw like windows in sdb? My win istallation is on sda

---

### Post by Pumalite on 2008-03-01
You have your partition mounted. You have to get menu.lst from there.

---

### Post by klaztaz on 2008-03-01
sorry but i am very new to ubuntu. could you provide me some steps to follow?
Correct me if im wrong...

i open the hard drive (with all the linux folders in it such as boot usr var etc..) and from the window i go to options open terminal ( i noticed that way im already navigated in the hard drive because i dont know the command).
Then i type *cat /boot/grub/menu.lst*.
this is what i do but it tells me that there is no folder or directory or i dont have the permissions i think


cat /boot/grub/menu.lst

---

### Post by Pumalite on 2008-03-01
Look in /media and navigate to hda2.
If you are in Knoppix Terminal. you are 'root', so the command might be something like this:
cat /media/hda2/boot/grub/menu.lst

---

### Post by klaztaz on 2008-03-01
Woohooooooooo finally one step closer to Ubuntuuu  hehehe



Here are the results:



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
# kopt=root=UUID=b98db3cf-d230-4d8d-8866-4b9ae3fb7bc9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b98db3cf-d230-4d8d-8866-4b9ae3fb7bc9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b98db3cf-d230-4d8d-8866-4b9ae3fb7bc9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

knoppix@Knoppix:/media/hda2/boot/grub$

---

### Post by Pumalite on 2008-03-01
By the looks of it you should at least be able to boot Ubuntu. Do you?

---

### Post by klaztaz on 2008-03-01
Unfortunatly I cant! Whatever I do, using the grub or booting through the alternative CD, the minute i press the first option to boot which is the Ubuntu, a screen come up saying kernal alive and then usually my computer just restarts or occasionally it just doesnt do anything while my screen diaplays 'no signal' and goes to sleep mode.
Booting windows doesnt work either through the Grub. Is says

starting...
NTLDR is missing
press Ctrl-Alt Del to restart

(something like that)

The only way i can boot in to windows is by changing from the bios to boot from my windows hard drive instead of the one Ubuntu was installed.

---

### Post by Pumalite on 2008-03-01
This means that you installed Grub to the wrong place or while your Windows drive was disconnected:
'The only way i can boot in to windows is by changing from the bios to boot from my windows hard drive instead of the one Ubuntu was installed.'

Which one was it? You cannot have dual boot if Grub is not installed to the MBR.

---

### Post by Pumalite on 2008-03-01
Get Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
And boot either one.

---

### Post by klaztaz on 2008-03-01
My windows drive was not disconected so it has to be that the grub was misplaced.

But how can this be possible? All i did was basically next next next in the installation. And when a message appeard saying that it has detected windows xp on my machine and if i want to install grub to manage them and that it would be safe i pressed yes.

Hoever i just noticed in the picture from the fdisk -lu command, that after a couple of lines it says:
*Partition table entries are not in disk order*

Is that ok?

Apart from this i have no idea whats wrong.
But if you have any suggestions im happy and grateful to follow

---

### Post by Pumalite on 2008-03-01
Maybe Grub installed to hda. You said you had Windows in sda1, so reinstall Grub to that drive:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
(check your fdisk)

---

### Post by klaztaz on 2008-03-01
ok im going back to try this web page using KNOPPIX live cd.

but is it safe for windows if i install the grub to the windows partision?

---

### Post by klaztaz on 2008-03-01
hhhmmm im following the tutorial you gave me from the forums but on the second command 'find /boot/grub/stage1' is says it should return me a location, but instead i get :

Error 15: File not found

This is proving more difficult than i expected

---

### Post by Pumalite on 2008-03-01
Your major problem is a mix of IDE and SATA:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

---

### Post by klaztaz on 2008-03-01
oh no i hope you are not right! otherwise i have to buy another hard drive.
i noticed that using the super grub it says from what i undertood that my linux / partision for the grub is hd(1.1) but in the grub normal window i press e to edit the linux and t reveals that its on hd(0,1). So something is wrong there. Im going to try and change it

---

### Post by Pumalite on 2008-03-01
Good luck.

---

### Post by klaztaz on 2008-03-01
ok when i edit the grub to the hd(1,1) it says again the same.
kernel alive but then it stops and the screen dies.

so the grub is loaded on the wrong hard disk and when you change it it crashes

---

### Post by klaztaz on 2008-03-01
ok i give up,
is there any way of uninstalling th grub? because now i cannot enter my windows.

---

### Post by Pumalite on 2008-03-02
Fix your Windows MBR with your installation CD>Recovery>FIXMBR>FIXBOOT
Or Super Grub.

---

