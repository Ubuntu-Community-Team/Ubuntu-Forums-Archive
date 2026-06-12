---
title: "[SOLVED] Failed to boot back to windows XP after full fresh installation of Ubuntu 8."
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by SheikhAmanAlam on 2008-08-31
Hello people.
i recently got an idea to move to Ubuntu 8.04.1.

ordered a free CD, and installed a full Ubuntu on a partition which was left intentionally for these purposes.
first i formated that partition with ext3, then installed Ubuntu.

Now, the problem is, whenever iam booting my system iam not getting any option to boot to windows, however, system boots to ubuntu so calmly, and everythng runs fine, but its very important fr me to have windows XP as well.

i guess this problem is because ubuntu has loaded grub, and now MBR is disturbed and is not displaying windows option.

please suggest what to do, i tries GAG, but its a bigger ****, its not even booting to ubuntu. i was better without it, atleast was able to boot to ubuntu.

remmeber, what i want is to have BOTH OS.
"whenever i boot, i get a short message for a while "Loading.." then normal Linux messages"
but no option to boot to windows.

what to do??
i need to have windows to play games and o develop applications fr my windows clients.
pls suggest any way.
iam having Hitachi SATA hard disk, have been a user of Windows since brth.
please help

---

### Post by TenPlus1 on 2008-08-31
I'm surprised that you formatted your spare partition to Ext3 before installing ubuntu (since it does it for you)...  What program did you use to actually do this ?

---

### Post by SheikhAmanAlam on 2008-08-31
actually, i first boot using the live CD and got the desktop.
user was "Live session user".
well, after that, i double clicked the install icon on the desktop to get things done.
it asked me some questions like language and locations, later it came to the partition stuff.
it was partition manager which was there to ask me which partition i wish to install on.
when it was selected on guided, it had then selected the wrong partition (it was using the longest free space available, which i didnt want to share).
as i had another 10gb partition reserved for ubuntu, i selected manual option, then i was presented with a table of partitions.
i had to select sda6, as it was the desired partition. as i pressed next, it said that i have to select at least one partition, so i selected that partition by ticking it to get formatted to ext3.i also put "/" to it.
then everythng went fine. lastly i got the message to restart the computer.
when i did restart, i got ubuntu pretty fine.
bt lost windows.

one more problem is here now, i was using GAG, and it wasnt working, so when i removed it, then my system says "no boot partition found"
GAG says if this error occurs then i should "use FDISK or nay other similar command". and system never boots.

whats this??
i may seem like a dumb stupid, bt thats bcz i have no time to experiment and i also have sensitive data on my disk.
plus i also have some project deadlines.
thats why iam nervous.

iam currently using the Live CD to message u, as my system is not booting.

---

### Post by Elric27 on 2008-08-31
try inserting the windows install cd. Let it load and press R when convenient. Enter the recovery mode and write "fixboot". That should do

---

### Post by SheikhAmanAlam on 2008-08-31
okay,
then what wud that do??
will i have to reinstall the whole XP again??
losing my data and configs??
and if i do this also, then i will lose ubuntu right??
or i'll have to reinstall ubuntu ryt??
do tell about fixboot..
will there be any problems using it?? any known issues??

---

### Post by Elric27 on 2008-08-31
No need to reinstall anything. The most likely thing to happen uf you type fuxboot, is that win will say that the mbr is corrupt (wrong, doesn't recognize ext3) and fix the boot, boot.ini

---

### Post by SheikhAmanAlam on 2008-08-31
thnks it did work and iam now able to boot to windows.
but same problem, now it dsnt give me any option to boot to linux.
directly boots to windows.

---

### Post by SheikhAmanAlam on 2008-09-01
1.)
 some people are suggesting that LILO is far more better than GRUB if its abt having windows also.
is it true??

2.)
cant i make an entry of ubuntu into boot.ini file of windows??
if yes, then what the entry should be??
i have ubuntu 8.04.1 on sda6, that is drive I.

3.)
when i had used fixboot, it made my boot.ini disappear, i had to save it again.why??

4.)
why GAG is not working in my case, means when i finished installing ubuntu, i switched to GAG to configure it, but it didnt boot nay of the OS, instead it just showed a blank black screen with a blinking cursir at the top most left corner

---

### Post by caljohnsmith on 2008-09-01
> **SheikhAmanAlam said:**
> 1.)
 some people are suggesting that LILO is far more better than GRUB if its abt having windows also.
is it true??

2.)
cant i make an entry of ubuntu into boot.ini file of windows??
if yes, then what the entry should be??
i have ubuntu 8.04.1 on sda6, that is drive I.

3.)
when i had used fixboot, it made my boot.ini disappear, i had to save it again.why??

4.)
why GAG is not working in my case, means when i finished installing ubuntu, i switched to GAG to configure it, but it didnt boot nay of the OS, instead it just showed a blank black screen with a blinking cursir at the top most left corner
Did you run "fixmbr" from the Windows CD? That is what will overwrite GRub in the master boot record (MBR) and boot you directly into Windows. "fixboot" only fixes the boot sector of the Windows partition; it does not touch the MBR, nor does it touch boot.ini. 

Grub in my opinion is much better than LILO or GAG in almost all situations. I would recommend reinstalling Grub, and then you can configure your Grub's /boot/grub/menu.lst easily to boot Windows and Ubuntu. Just do the following from the Ubuntu Live CD, in a terminal (Applications > Accessories > Terminal): 
```
sudo grub
grub> find /boot/grub/stage2
[COLOR="Blue"][should find your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Next post your menu.lst if you need help modifying it to boot Windows and Ubuntu, so first do:
```
sudo fdisk -lu
```
Find your Ubuntu partition as /dev/sdaX, should be type "linux" under the "system" category, use that:
```
sudo mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst

```

---

### Post by SheikhAmanAlam on 2008-09-02
> Did you run "fixmbr" from the Windows CD? That is what will overwrite GRub in the master boot record (MBR) and boot you directly into Windows. "fixboot" only fixes the boot sector of the Windows partition; it does not touch the MBR, nor does it touch boot.ini.

brother, i had used fixmbr couple of times before but some bad things happened which later made me reinstall my windows which was rather painful. so i had a fear using it again, so i used fixboot this time, and got things back.

im going to try the things u have told, and will tell u whether it works or not.

take care

---

### Post by caljohnsmith on 2008-09-02
> **SheikhAmanAlam said:**
> brother, i had used fixmbr couple of times before but some bad things happened which later made me reinstall my windows which was rather painful. so i had a fear using it again, so i used fixboot this time, and got things back.

im going to try the things u have told, and will tell u whether it works or not.

take care
I think you might have misunderstood me; I wasn't suggesting you run "fixmbr", because that will install the Win XP MBR and then you won't be able to boot Ubuntu any more. I think the easiest solution to your problem is just reinstall Grub to the MBR using the steps I gave starting with "sudo grub", and then we can easily help you add an entry in your Grub's menu.lst so you can boot Windows.

---

### Post by SheikhAmanAlam on 2008-09-03
my menu.lst as u had said-
> 
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
# kopt=root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



now brother, wt to do

---

### Post by SheikhAmanAlam on 2008-09-03
yup
i have done that, and now iam only booting to ubuntu.
iam waiting fr u to tell me the entry of windows which has to be added into menu.lst

---

### Post by SheikhAmanAlam on 2008-09-04
brother iam waiting for ur reply

pls tell the entries that are to be added in the menu.lst

---

### Post by caljohnsmith on 2008-09-04
OK, pull up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst &
```
And at the very bottom, add the following:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
That will probably work, but if it doesn't, then post the output of:
```
sudo fdisk -lu
```

---

### Post by SheikhAmanAlam on 2008-09-04
yaaaaay!!!:guitar:
everythng is fine now
iam able to boot in both, windows and ubuntu.

thanks to u brother.
thanks a lot.

one more optional question, is there anyway to mount all the NTFS drives automatically when the system starts up??

---

### Post by caljohnsmith on 2008-09-04
> **SheikhAmanAlam said:**
> yaaaaay!!!:guitar:
everythng is fine now
iam able to boot in both, windows and ubuntu.

thanks to u brother.
thanks a lot.

one more optional question, is there anyway to mount all the NTFS drives automatically when the system starts up??
You're welcome, and I'm glad you can use either Windows or Ubuntu now. :) To have your Windows (NTFS) partition mount on start up, you could do:
```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab &
```
Then add the following line:
```
/dev/sda1 /media/windows ntfs defaults,uid=0,gid=46,auto,rw,nouser,umask=007 0 1
```
You can use the same technique as above to mount any other NTFS partitions on start up.

---

### Post by SheikhAmanAlam on 2008-09-05
yup brother

i made some experiments based on your directives, and am successful to mount all my ntfs drives at startup.
thanks to u dear brother.

now, can i push sound output level to much higher level than this?
i have tried alsamixer and have turned all volumes to full, bt sound output is still very low as compared to windowws performance.
is there any other package or OD update avaailable for this??

and as iam a developer, so i need to know where i can download Java API for linux (i dnt think its same for windows and linux cz SDk is an exe file in windiws which is not supported here).

---

### Post by SheikhAmanAlam on 2008-09-06
plus, one more problem is there.
whenever i boot to windows after booting to ubuntu, i get wrong time in windows.
means, i get the time set to the unit when i had switched to ubuntu (i guess), but its not correct always, and i always have to update it with time servers.
why is it happening??
and is there any solution to this??

---

### Post by caljohnsmith on 2008-09-06
About your sound problem, if you open up your volume controls, the two volumes you should be concerned with are the "PCM volume" and of course the master/main volume. Check to make sure those are not turned down, and if that doesn't give you enough volume, then I'm not sure what your problem might be at this point. I would recommend starting a new thread in the "media" category of the forums so you can get everyone's input.

And about the time problem in Windows, I've noticed the same thing on my computer, but I've never searched for a fix. I just right-click my Windows clock, select "change time/date", and then click on the tab where Windows automatically updates the clock. But if you want a true fix for the problem, you could search the forums or post a new thread maybe in the "general" section. Anyway, good luck and hope you can find solutions to your problems. :)

---

### Post by SheikhAmanAlam on 2008-09-06
> **caljohnsmith said:**
> About your sound problem, if you open up your volume controls, the two volumes you should be concerned with are the "PCM volume" and of course the master/main volume. Check to make sure those are not turned down, and if that doesn't give you enough volume, then I'm not sure what your problem might be at this point. I would recommend starting a new thread in the "media" category of the forums so you can get everyone's input.

And about the time problem in Windows, I've noticed the same thing on my computer, but I've never searched for a fix. I just right-click my Windows clock, select "change time/date", and then click on the tab where Windows automatically updates the clock. But if you want a true fix for the problem, you could search the forums or post a new thread maybe in the "general" section. Anyway, good luck and hope you can find solutions to your problems. :)

okay, i'll search other areas of threads, and will also let u know if something fruitfull comes to me.

thanks a lot for all ur valuable help dear.
how to mark this thread as solved??

---

### Post by caljohnsmith on 2008-09-06
Just click the "thread tools" at the top of the postings, and select "solved". :)

---

