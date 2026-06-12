---
title: "Ubuntu 10.10, no option to not install grub"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2011-03-28
After all of my putzing around to get my tri-boot linux box up and running, the boot drive decided to die on me, so I am re-installing things again. I installed 9.10, and then upgraded to grub2. This went without issue. I am now in the process of installing 10.10. I have the partitions set up as follows,

sda1 primary 8GB swap
sda5 logical 10gb / for 9.10
sda6 logical 20gb /home for 9.10

with grub2 installed on the mbr of sda. I then added

sda7 logical 10gb / for 10.10
sda8 logical 20gb /home for 10.10

This seems like the best config for a multiboot setup.

I was not going to install grub with 10.10, but just boot back into 9.10 and run update-grub. The only options are to install grub on sda, or on one of the logical parts. There is no option in the menu to not install grub.

So what should I do now?

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Hedgehog1 on 2011-03-28
In practical terms, your best results will be to use the GRUB from the most current Ubuntu install.  If you remove 10.10, you can re-install grub from your 9.10 release and get back to where you were before (do the BEFORE you remove the 10.10 partitions).

I believe that the 10.10 grub is the same level as your updated grub in your 9.10 install.

***The Hedge***

:KS

---

### Post by LMHmedchem on 2011-03-28
> **Hedgehog1 said:**
> In practical terms, your best results will be to use the GRUB from the most current Ubuntu install.  If you remove 10.10, you can re-install grub from your 9.10 release and get back to where you were before (do the BEFORE you remove the 10.10 partitions).

I believe that the 10.10 grub is the same level as your updated grub in your 9.10 install.

***The Hedge***

:KSI have already installed 10.10 over my 9.10 install. I just don't have all day to mess around with this.

I don't know if I have ended up with 2 installs the the mbr of sda or not. I also don't know how to check that. I just deleted the 9.10 partitions, created new ones for 10.10, and installed. I pointed to sda for the install location of grub2.

I will install 9.10 later when I need it. Hopefully the 9.10 installer has the option to not install grub. It is very strange that Ubuntu doesn't have the option to not install grub when the preferred method for multi-boot environments, advocated by this forum, is to install grub with the first OS, and then never install it again.

Perhaps there is an assumption that Ubuntu will always be the first OS installed, which I would more or less agree with, but that doesn't account for installing multiple Ub distros if they don't have the option to skip the grub install.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-28
## EDIT THIS CODE IS WRONG IT IS JUST## Edited wrong code this is now correct: Very Sorry:
```
sudo grub-install /dev/sda
```for installing grub while in a install.
 
Having grub2 in multiple installs has no effect at all on the mbr, you can only have one grub
installed in mbr at a time and it uses that config-file and menu entry. 
While in install of choice just:
 
# Cannot do this with (grub) grub-legacy and grub2 (grub-pc) installed together do not play
well together.
*So do not worry about installing grub2 in multiple Operating Systems it matters not.
#So far as I know the ubiguity installer does not have an option to not install grub.
#Anaconda used by fedora, redhat, OpenSuse and others does have a box to check to not
install grub. They use grub-legacy still so if you install one of them DO NOT install grub. Go to
install you are using in mbr and sudo update-grub and will put in config file and as a menuentry

---

### Post by LMHmedchem on 2011-03-28
> **garvinrick4 said:**
> Having grub2 in multiple installs has no effect at all on the mbr, you can only have one grub
installed in mbr at a time and it uses that config-file and menu entry. 
While in install of choice just:
```
sudo grub-install /dev/sdxy
```with x being letter of drive a,b,c,d ect. ect. ect.
and y being number assaigned such as 1, 2,3,4,5 ect. ect. ect.
To find that:
```
sudo fdisk -l
``` (lower case L)

# Cannot do this with (grub) grub-legacy and grub2 (grub-pc) installed together do not play
well together.
*So do not worry about installing grub2 in multiple Operating Systems it matters not.
#So far as I know the ubiguity installer does not have an option to not install grub.
#Anaconda used by fedora, redhat, OpenSuse and others does have a box to check to not
install grub. They use grub-legacy still so if you install one of them DO NOT install grub. Go to
install you are using in mbr and sudo update-grub and will put in config file and as a menuentrySo if I were to install a new OS and point to sda mbr as the install location for grub2,  the installer would see that grub2 was already there and just add to what is already in the menu?

It is such a bore to be doing all of this again after last week, but at least I can try this out on a fresh partition setup and see how it goes.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-28
> **LMHmedchem said:**
> So if I were to install a new OS and point to sda mbr as the install location for grub2, the installer would see that grub2 was already there and just add to what is already in the menu?
 
It is such a bore to be doing all of this again after last week, but at least I can try this out on a fresh partition setup and see how it goes.
 
[COLOR=navy]**LMHmedchem**[/COLOR]
I am sorry the code is:
```
 
sudo grub-install /dev/sda

```
NEVER,NEVER put grub in sda1 or sda2 or sda5 always in sda or sdb or sdc whichever drive you are using.
 
When ever you install grub to mbr it overwrites the one that is already there. The OS-prober go's out and
finds other installs and adds them to menu entry and config files when you update-grub
```
sudo update-grub
```

---

### Post by LMHmedchem on 2011-03-28
My current partition table looks like,

```

[FONT=Courier New]/dev/sda1      linux-swap
/dev/sda2      extended
   /dev/sda5   ext4          /     (Ubuntu 10.10)
   /dev/sda6   ext4          /home (Ubuntu 10.10)[/FONT]
/unalloc

```

I am in Ubuntu gparted and am trying to add two additional partions for the next OS. I would like to make them logical partitions. If I select the unpartitioned space, it will only let me create a primary partition. How can I create more logical partitions for my next OS. The installer DVD will also only create logical partitions, so that is no help.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-28
open a terminal and give the command
```
sudo fdisk -l
``` (lower case L)
and copy and paste it to this thread;

---

### Post by LMHmedchem on 2011-03-28
here it is,

```

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   82  Linux swap / Solaris
/dev/sda2             974        4621    29295617    5  Extended
/dev/sda5             974        2189     9764864   83  Linux
/dev/sda6            2189        4621    19529728   83  Linux

```[COLOR=Navy][B]

LMHmedchem[/B][/COLOR]

---

### Post by garvinrick4 on 2011-03-28
You would like a logical partition inside of sda2 the extended partition. Right now the whole
extended partition is being used.
You cannot work on a partition or increase the size of the extended partition or any partition while it is in use.
In gparted will have keys next to it (meaning locked).
Use a live Cd (the install cd using Try Ubuntu).
You do have 2 primary partitions left on drive, you are using 2 and max is 4.

---

### Post by LMHmedchem on 2011-03-28
> **garvinrick4 said:**
> You would like a logical partition inside of sda2 the extended partition. Right now the whole
extended partition is being used.
You cannot work on a partition or increase the size of the extended partition while it is in use.
In gparted will have keys next to it (meaning locked).
Use a live Cd (the install cd using Try Ubuntu).
You do have 2 primary partitions left on drive, you are using 2 and max is 4.So using the live CD, should I add partitions and declare them as logical, or increase the size of the extended partition, and then add logical partitions to it?

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-28
logical partitions can only exist inside of extended partition. Think of extended partition as
a house for the logicals. Linux can survive in logical or Primary partitions. If you can increase
the size of extended and make a new logical partition inside that is OK. You have the option
of making a primary partition in unallocated space also, it is up to you.

---

### Post by LMHmedchem on 2011-03-28
The live CD/gparted worked fine for creating the new partitions. I just resized the extended partition to include the rest of the drive and added logical partitions.

I am now installing Cent again and I will let you know how it goes.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-28
CentOS uses grub-legacy (grub not to be installed). 
sudo update-grub
in ubuntu after install will put it in config and as menuentry.
[http://wiki.centos.org/](http://wiki.centos.org/)
A cousin of Redhat, fedora and such.

---

### Post by LMHmedchem on 2011-03-28
> **garvinrick4 said:**
> CentOS uses grub-legacy (grub not to be installed). 
sudo update-grub
in ubuntu after install will put it in config and as menuentry.
[http://wiki.centos.org/](http://wiki.centos.org/)
A cousin of Redhat, fedora and such.Hopefully it will work this time and the menu items created by os-prober will be correct without having to manually insert the conf files. I was reading that you can manually insert a menu entry by adding a script to grub.d. Maybe I will try that if it doesn't work this time.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by LMHmedchem on 2011-03-28
Well once again, running update-grub produced a menu entry lacking an initrd line, and newly installed OS will not boot.

I was reading about grub2 and saw that there was a method for manually making manu entries.
[http://ubuntuguide.net/manually-addingremoving-entries-to-grub-2-menu](http://ubuntuguide.net/manually-addingremoving-entries-to-grub-2-menu)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I think I will try this instead of sticking a grub.conf in /boot/grub of the Cent install like I did last time, unless someone thinks that is a bad idea.

**[COLOR=Navy]LMHmedchem[/COLOR]**

---

### Post by LMHmedchem on 2011-03-28
Well I was able to create a custom menu entry for the OS that wouldn't boot. I did it by adding a file to /etc/grub.d called 40_custom which contained the correct menu entry and doing update-grub. I added custom to the name of the new entry.

This creates a menu entry that was able to boot cent. Unfortunately, the inoperative menu entry still exists and I am not sure how to remove it. It seems like it is a better idea to add a properly configured grub.conf file to /boot/grub of the OS that won't boot. OS-prober will find it and add it to the menu. This will avoid the menu entry that doesn't work.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-28
This seems like a CentOS thing. I am sure you have been on a CentoS forum. drs305 had mentioned in a previous thread to get into root in a Live CD using chroot and use mkinitramfs command to produce one.
Using Ubuntu live CD and CentOs sda# and give it a go. Use the code man mkinitramfs for manual.I did, if dr305 is around maybe he will chime in.
Think I got it right. The line that starts with mkinitramfs

```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```
```
mkinitramfs -k -o /boot/initrd.img-2.6.32-30-generic
```Use your own kernel above
```
exit
```
```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt


```

---

### Post by oldfred on 2011-03-29
You can turn the os-porber off. If you need it after another new install just turn it back on again for a while.

I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by LMHmedchem on 2011-03-29
Thanks garvinrick4 and oldfred. I am going to have to take a few days off from the boot stuff to get some apps working. I can boot in at the moment, so I will deal with cleaning up the menu later. I need to get gcc 3.4 and g77 installed and working on 10.10, which seems pretty non-trivial.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

