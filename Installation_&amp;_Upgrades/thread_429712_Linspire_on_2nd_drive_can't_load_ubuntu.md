---
title: "Linspire on 2nd drive can't load ubuntu"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by bill1492 on 2007-05-01
I loaded Linspire on 2nd hard drive and although the Linspire menu shows Ubuntu it won't load Ubuntu.I have Ubuntu 6.06 with upgrades installed. The Ubuntu menu had Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernel 2.6.15-23-386  regular and reccovery modes aswell as Ubuntu, memtest86+ 
If I remove 2nd drive and reinstall Ubuntu 6.06 will iI be able to keep all data and upgrades. [email]billn6bct@netzero.net[/email] 650 726-3630

---

### Post by bulldog on 2007-05-01
Hi,
Did you put actual a new hdd in your computer **after you installed ubuntu?**

And no,if you do a reinstall,your settings are lost,but if you have made a separate /home partition when you installed Ubuntu,your personal data  is save,but your installed applications are not.

---

### Post by bill1492 on 2007-05-06
Yes I installed a 2nd hard drive after I installed ubuntu on the first . Then I installed Linspire on the 2nd drive which gave me a menu with Linspire as first choise and Ubuntu 6.06 LTS as the last choise.When I couse it the screen shows GRUB loading stage1.5 :aftwerwords nothing happens. 
Bill:lolflag:

---

### Post by confused57 on 2007-05-06
> **bill1492 said:**
> Yes I installed a 2nd hard drive after I installed ubuntu on the first . Then I installed Linspire on the 2nd drive which gave me a menu with Linspire as first choise and Ubuntu 6.06 LTS as the last choise.When I couse it the screen shows GRUB loading stage1.5 :aftwerwords nothing happens. 
Bill:lolflag:
You might want to boot up the Ubuntu live cd, open a terminal, post the output of:
```
sudo grub
find /boot/grub/stage1
```

then enter "quit", without the quotes, to exit the grub prompt.
This may show us what we need to know...you might also want to boot into Linspire, and post the output of:
```
cat /boot/grub/menu.lst
```
or possibly:
```
cat /boot/grub/grub.conf
```
I don't which Linspire uses.

---

### Post by bill1492 on 2007-05-07
Ok the result of    sudo grub
                             find /boot/stage1
was                      (hd0,0)
and                      (hd1,0)



hda1/boot/grub/menu.1lst  is:# menu.lst - See: grub(8), info grub, update-grub(8)
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
default		3

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
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by confused57 on 2007-05-07
It looks like you're booting first to your Ubuntu drive with grub on your hda mbr...root (hd0,0), and your Linspire root partition is root (hd1,0).
What you can do is use the Ubuntu live cd to install Linspire's grub to the root partition:
```
sudo grub
find /boot/grub/stage1
```
your results should be as before:
root (hd0,0)
root (hd1,0)
to install Linspire's grub to it's root partition:
```
root (hd1,0)
setup (hd1,0)
quit
```

Then you should be able to add an entry to your Ubuntu menu.lst to boot Linspire, using chainloading:
```
title   Linspire
rootnoverify (hd1,0)
chainloader +1
```

Rather than doing the above, you might be able to boot your Linspire root partition, using configfile:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
in fact, you might want to try the configfile method first...which would be easier if it works.

---

### Post by bill1492 on 2007-05-10
I followed directions :
sudo grub
find /boot/grub/stasge1
resulte
root (hd0,0)
root (hd1,0)
then I gave command
root (hd1,o)
result filesystem type is reinserts, pattition type 0x83
hten
setup (hd1,0)
with the result
checking if "/boot/grub/stage1" exist ...yes
checking if "/boot/grub/stage2" exists...yes
checking if "/boot/grub/reinserts_stage1_5" exists...yes
running "embeded/boot/grub/reinserts_stage1_5 (hd1,0) 18sectors are
embeded.
succeded
running "install/boot/grub/stage1 (hd1,0) (hd1,0)+1p/boot/grub
/stage2/boot/grub/memu.lst....succeded
then 
quit

Idid all this but when I reboot the computer I still have the same Linspire Menu. Should I have done root (hd0,0) , setup (hd0,0) instead?
My Ubuntu is on the first drive (hd0,0) and Linspire is on the secound (hd1,0). I also failed to mention that when booting up the computer says that it is booting from a CD .

I also got an Email from nam [email]ascertia@hotmail.com[/email] 
It has been awhile since I installed Ubuntu, however when you go through the install upgrade feature you should keep updates. If not then you will have to re-write your boot loader.

IS this true?
Bill

---

### Post by confused57 on 2007-05-10
If you're booting first to your Ubuntu drive, it looks like Linspire installed it's grub to the Ubuntu drive's  mbr...so what you need to do is:
```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

This should install Ubuntu's grub IPL to the Ubuntu drive mbr and you should get Ubuntu's grub boot menu...since you've already installed Linspire's grub to it's root partition, then all you should have to do is add the chainloader entry to Ubuntu's /boot/grub/menu.lst to boot Linspire.

---

### Post by fred0843 on 2007-05-10
What Version of Linspire are you using?

---

### Post by bill1492 on 2007-05-12
I did it and now Istill get Linspire menu but now when I slect  Ubuntu ,it now boots ok. My question now would be if I remove the Linspire drive from this computer, will I have to go thru this proceedure over again?
     The other questio asked was what  Linspire I am using . It is Linspire 5.05 ,now with suite 6.06 installed

Thanls much Bill

---

