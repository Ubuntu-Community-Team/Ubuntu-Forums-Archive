---
title: "Problem with GRUB and dual boot"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by Spacedementia87 on 2007-09-01
Right, so i had windows XP installed on my IDE1 master HDD. I am guessing it is hd0 for grub.

Now i have 3 other hard drives on my PC.  2 just for data and the 3rd (SATA) I want to install Ubuntu 7.04 on.

So i did so, going through the set up as normal.
On reboot it told me there was error 22 when loading GRUB.

A little bit of research told me that i needed to install GRUB on the same disk as my linux installation.

So tried installing again and got to the dick partitioning bit.

Put 20gig aside for linux, 256MB aside for the swap a few hundred for the /boot and the rest on a separate partition for more data.

the partition screen said the /boot was sdb partition 3.

So when it got to the final screen, i clicked advanced and put (hd3,3) for the GRUB installation.

It installed fine.

Then i get the same error 22 when booting up.

How do I fix this?

---

### Post by ssican on 2007-09-01
For GRUB ERROR 22, see  [http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

For INSTALL LINUX(UBUNTU) and XP in DUAL BOOT on TWO HARD DRIVES (distinct,different hard drives), see  [http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+twohardrives](http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+twohardrives)

---

### Post by logos34 on 2007-09-01
Please post /boot/grub/**menu.lst** and /boot/grub/**device.map**, along with output of 

**sudo fdisk -l** (lowercase L)

This will help clarify matters since you have so many drives.

From the info you've provided, if you had wanted to write grub to the bootsector of the /boot partition (**sdb3**) then you should have entered '(hd3,**2**)' -- assuming, that is, /dev/sdb = 'hd3'.  But you also need to go into the BIOS and change the hard disk boot order so your ubuntu sata drive is FIRST...Sounds like you're still booting to grub on windows disk.  

Grub does not need to be installed on the linux drive.

---

### Post by Spacedementia87 on 2007-09-02
Ok i am quite confused now.

Completely new to all this linux business.

> Please post /boot/grub/menu.lst and /boot/grub/device.map, along with output of

sudo fdisk -l (lowercase L)

How would I do this?

And in my BIOS there is only one Hard Drive option in the boot list.
And if i do the manual boot thing it says that the 2nd SATA drive is not a bootable drive which confused me.

> Grub does not need to be installed on the linux drive.

So why didn't the first install work?

I will go upstairs and have a fiddle with it now and see what I can do.

---

### Post by logos34 on 2007-09-02
Boot the ubuntu live cd, 

applications>acessories>terminal, then type

sudo fdisk -l

Grub (i.e. stage1) installs by default to the Master boot record of the first Bios hard disk (hd0), which in multidisk systems like your own is obviously not necessarily the same disk that has the linux installation.


> **Spacedementia87 said:**
> And in my BIOS there is only one Hard Drive option in the boot list.
And if i do the manual boot thing it says that the 2nd SATA drive is not a bootable drive which confused me.

Apparently that's one of your data drives without a bootable system partition.

---

### Post by Spacedementia87 on 2007-09-02
Ok, using the ubuntu cd i can get onto the live version and get those files, but i can't get onto the actual installation.  It seems to boot in VGA mode which just displays as as epeleptic fit inducing load of flashing lines.

But my 2nd SATA drive is where i have told grub to install.  And looking at the file system it is on there but it won't boot from it

I no got rid of the separate boot partition and decided to have GRUB on the same as the root partition.

---

### Post by Spacedementia87 on 2007-09-02
Ok this is what i managed to get off the system:

[device.map]("http://james.hope87.googlepages.com/DEVICE.MAP")

[menu.lst]("http://james.hope87.googlepages.com/menu.lst")

[sudofdisk-1]("http://james.hope87.googlepages.com/sudofdisk-l")


2 other smaller problems are that i cannot connect to my wireless network.

When I try it asks for the authentication key, so i put in the WEP key i have and it still doesn't work.
The light on my card isn't on.


I also cannot see my mouse pointer no matter which one i select!

Both of these may be alright when running of my HDD.

---

### Post by logos34 on 2007-09-02
,

---

### Post by Spacedementia87 on 2007-09-02
> **logos34 said:**
> ,

hmm?

---

### Post by logos34 on 2007-09-02
Here's what I'd do:

Use the live cd to reinstall grub to hd0 ('setup (hd0)'), the windows drive mbr.  But first run a [filesystem check]("http://users.bigpond.net.au/hermanzone/p15.htm#22") on your linux root:

**sudo e2fsck -f -y -v /dev/sdb3**  (or just 'sudo fsck /dev/sdb3')

Then check your Bios to make sure that the windows drive (/dev/hda) is first in the **hard disk boot order** (not to be confused with the 'device' boot order which lists all your storage drives).  All 4 hard disks should be listed in that submenu.

If that doesn't work you could try reinstalling grub to the root partition '(hd3,2)' or to the MBR '(hd3)' and switch the bios order so /dev/sdb boots first.  But if you do that you'll have to change the 'root' lines in menu.lst beforehand to read '(hd0,2)'

---

### Post by Spacedementia87 on 2007-09-02
Is there any way to make it just reinstall grub and not affect my linux installation.

Just because it takes a long time other wise!

---

### Post by Spacedementia87 on 2007-09-02
oh and i have managed to fix the display problem, now just trying to fix the networking and mouse pointer problem

---

### Post by logos34 on 2007-09-02
> **Spacedementia87 said:**
> Is there any way to make it just reinstall grub and not affect my linux installation.

Just because it takes a long time other wise!

to reinstall grub to hd0 you don't have to change anything.  But if that doesn't work you'll have to try something else, such as reinstalling grub on the linux drive.  However that means setting the Bios hard disk order to boot the linux drive first, which means you will have to edit menu.lst so that grub stage1 (on the mbr or bootsector of root) knows where to find /boot/grub/menu.lst...the minute you change it to first place in the boot order it becomes (hd0), and if you leave the root lines in menu.lst the same grub will look for it in vain at (hd3,2) instead of (hd0,2), the new location.

If all else fails just reinstall.  Maybe some corrupted files caused a problem with grub.

---

### Post by Spacedementia87 on 2007-09-02
but how do you just reinstall grub?

It won't let me past the partitioning screen unless i choose to format the root drive.

---

### Post by Spacedementia87 on 2007-09-02
i can't see where i should type in this 'Setup (hd0)'

tried in the terminal and things, just don't get it

---

### Post by Spacedementia87 on 2007-09-02
actually no managed it.

Still gewt the error 22 though

---

### Post by Spacedementia87 on 2007-09-02
well it said suceeded after the setup but on inspection it didn't do anything.

no boot folder or grub files on hd0

---

### Post by Spacedementia87 on 2007-09-02
I'm going to reinstall linux now, putting (hd0) in the advanced box.

This is what i did first time round so i am guessing it still won't work.

No idea what the problem could be.  If i can't get it sorted soon then i'm going to uninstall linux and go back to XP.  seriously can't be woth this hassle.  My friend told me it was easy.  The only problem then would be to get the regular windows MBR back working

---

### Post by Spacedementia87 on 2007-09-02
Ok, right the reinstall didn't work.

I have now used the XP disc to fixmbr and so i can boot windows again.

Now how can i do the install to get ubuntu working on a different HDD?

Do i now have to reinstall it all?  If so, how?  What settings, nothing i have done before has worked.

Can i just reinstall GRUB?  How can i get the GRUB prompt now that i have fixed my MBR?

---

### Post by confused57 on 2007-09-02
If your bios is capable of booting first to your Ubuntu drive(/dev/sdb), you could try using the live cd to install grub to the Ubuntu drive's mbr...open a terminal:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd3,2)", then you would enter:
```
root (hd3,2)
setup (hd3)
quit
```

The above was taken from this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then boot first to your Ubuntu drive, if you get a grub menu, highlight your Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd3,2) to (hd0,2), press "enter", then "b" to boot...this is temporary if it works, but it can be made permanent.

---

### Post by Spacedementia87 on 2007-09-02
ok, sounds good, i'll give that a go.

But how can i install grub to that drive without reinstalling ubuntu?

I can't think of a way to get to a working terminal window now i have repaired my windows MBR

---

### Post by Spacedementia87 on 2007-09-02
actually ignore that, i may be ok.

Could have just been being stupid, i'll report back in a few mins

---

### Post by Spacedementia87 on 2007-09-02
Ok, amazing thank you.  That is almost completely working now!

Problem only being that now it won't boot windows off the GRUB list.  I had to change my Boot Drive order to get here!

I changed menu.lst and put the root for the windows XP as (hd1,0) as that drive would be the second in boot order, but after pressing return it just shows:

Starting Up...

and doesn't do anything.  I tried every one ((hd2,0) etc..) and the only one that was different was (hd0,0) that complained about being invalid.

---

### Post by confused57 on 2007-09-02
> **Spacedementia87 said:**
> Ok, amazing thank you.  That is almost completely working now!

Problem only being that now it won't boot windows off the GRUB list.  I had to change my Boot Drive order to get here!

I changed menu.lst and put the root for the windows XP as (hd1,0) as that drive would be the second in boot order, but after pressing return it just shows:

Starting Up...

and doesn't do anything.  I tried every one ((hd2,0) etc..) and the only one that was different was (hd0,0) that complained about being invalid.

Since you changed your menu.lst, I assume you were able to make the changes permanent...to boot your Window's drive, you may need map commands:
```
title Windows Xp
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Also, be sure to change the line with #groot to reflect (hd0,2):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

If Windows still won't boot, you might need to change your device.map:
```
gksudo gedit /boot/grub/device.map
```
you'll need to make your Ubuntu drive (hd0) and your Windows drive (hd1), i.e.
```
(hd0) /dev/sdb
(hd1) /dev/hda
```

---

### Post by logos34 on 2007-09-02
> **Spacedementia87 said:**
> Ok, amazing thank you.  That is almost completely working now!

Problem only being that now it won't boot windows off the GRUB list.  I had to change my Boot Drive order to get here!

I changed menu.lst and put the root for the windows XP as (hd1,0) as that drive would be the second in boot order, but after pressing return it just shows:

Starting Up...

and doesn't do anything.  I tried every one ((hd2,0) etc..) and the only one that was different was (hd0,0) that complained about being invalid.


Sorry for leaving you in the lurch, Spacedementia87, I had to step away from the computer for what I thought would only be a little while...turned out to be most of the day!  I thought you might be able to take it from there, but forgot you didn't know how to install grub from live cd (you did it only in the install process).  Anyway, glad Confused57 was around...you're in good hands with him.

Follow the directions in his last post and that should get grub to boot XP.  You need to do what's called a 'virtual swap' by changing the drive mapping because Windows is on a non-first hard disk.  Device.map needs to be edited to reflect the new bios hard disk boot order.  More on that here:

[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

---

### Post by Spacedementia87 on 2007-09-03
It's ok, thanks a lot guys, i think that should solve my problem.  I'll give it a go right now.

Then it's just the internet and the mouse pointer to sort.

You have been a great help thanks! :)

---

### Post by Spacedementia87 on 2007-09-03
Ok i am afriad that didn't work.

I changed the device.map file and it still won't boot windows.  I will get the files and put them up here for you now.  Just need to reboot into ubuntu first.

---

### Post by Spacedementia87 on 2007-09-03
Device.map
```
(hd0)	/dev/sdb
(hd1)	/dev/hda
(hd2)	/dev/hdb
(hd3)	/dev/sda

```

menu.lst
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
timeout		60

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
# kopt=root=UUID=57bad360-a383-44de-9bf8-7eceb20b811c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=0x318

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu 7.04 Feisty Fawn
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=57bad360-a383-44de-9bf8-7eceb20b811c ro quiet splash vga=0x318
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu 7.04 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=57bad360-a383-44de-9bf8-7eceb20b811c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1

```

I got rid of the map commands because i changed the device.map file.

---

### Post by Spacedementia87 on 2007-09-03
Oh also, how does one write files to anywhere but the "user area"?

I can't save things onto the file system or any of my pre-existing data drives.  Says i don't have permission.

---

### Post by confused57 on 2007-09-03
You definitely need the map commands to boot Windows on a different hard drive...do you have your bios hard drive boot order set to: Ubuntu drive(/dev/sdb) first, then Windows drive(/dev/hda) second?

If you do & Windows still won't boot with the Windows entry I gave you previously, then you might try "root (hd2,0)" or "root (hd3,0)", for example:
```
title Windows Xp
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

Since your other hard drives are ntfs, you'll need to install the ntfs-3g program to write to ntfs partitions...I personally haven't used ntfs-3g, but I think you can install it from Synaptic.

You should probably enable the multiverse & universe repositories in your sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list
```
then take out the # in front of anything that looks like website...this explains it pretty well:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

You may want to see which partitions are being mounted in your /etc/fstab:
```
gedit /etc/fstab
```

There is much debate among forum users as to using automatix2 to install programs:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

I routinely use automatix to install movie players, codecs, etc and I haven't had any problems with it, but there are reports of it breaking some users systems.  I think it is capable of installing & configuring ntfs-3g also.  You might want to do a search for automatix, which makes installing extra programs much easier, & read some of the debates over using automatix to decide if you want to use it.  You'll eventually want to learn how to install programs manually through Synaptic.

---

### Post by Spacedementia87 on 2007-09-03
> **confused57 said:**
> You definitely need the map commands to boot Windows on a different hard drive...do you have your bios hard drive boot order set to: Ubuntu drive(/dev/sdb) first, then Windows drive(/dev/hda) second?

If you do & Windows still won't boot with the Windows entry I gave you previously, then you might try "root (hd2,0)" or "root (hd3,0)", for example:
```
title Windows Xp
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```


Ok i'll give it another go with the map commands, but last time it just said that the partition was missing or something.

> Since your other hard drives are ntfs, you'll need to install the ntfs-3g program to write to ntfs partitions...I personally haven't used ntfs-3g, but I think you can install it from Synaptic.

Guess that involes an internet connection.  Can't get mine working.  No idea what is wrong and i am getting no help in the internet connection forum.

---

### Post by confused57 on 2007-09-03
If you still can't Windows to boot trying (hd2,0), (hd3,0), or (hd4,0), making sure to include mapping lines, try changing your device.map just to show your Ubuntu drive:
```
(hd0)	/dev/sdb
#(hd1)	/dev/hda
#(hd2)	/dev/hdb
#(hd3)	/dev/sda
```

What brand of nic are you using and how do you connect to the internet(cable, dsl)?  You might want to post the output of:
```
lspci
```

Added:  Try clicking on the Network Manager icon in the upper right section of the top panel, select "Manual Configuration"...see if it shows something like eth0 & if it is recognized and active.  If it does show eth0, try deselecting it by removing the check mark in the box, then reselect it by "rechecking" the box...this will reconfigure your internet connect, if possible.

---

### Post by Spacedementia87 on 2007-09-03
I have got the wondows boot working now.  Thank you very much.

I am using a linksys wireless card connecting to a router with a DSL connection.
The card is reported to work "of of the box"

And it has drivers and everything but just won't connect to the network.  It tires every so often (shoing the blue thing circling in the top corner) but never manages.

---

### Post by confused57 on 2007-09-03
> **Spacedementia87 said:**
> I have got the wondows boot working now.  Thank you very much.

I am using a linksys wireless card connecting to a router with a DSL connection.
The card is reported to work "of of the box"

And it has drivers and everything but just won't connect to the network.  It tires every so often (shoing the blue thing circling in the top corner) but never manages.

Glad you were able to get Windows booting from grub.  I'm sorry but I can't help you with wireless...the only thing I can suggest is searching forum threads & howto's for getting wireless configured.  There are probably many users on the forum who can help you with wireless, but they haven't seen your thread yet.

You might try downloading & burning Gutsy Tribe 5 & try the live cd...may not work any better than Feisty, but may be worth trying.

---

### Post by logos34 on 2007-09-03
> **Spacedementia87 said:**
> I have got the wondows boot working now.  Thank you very much.

Just for future reference, what fixed it?  Using (hd2,0), or (hd3,0) or did you comment out the device.map lines?

---

