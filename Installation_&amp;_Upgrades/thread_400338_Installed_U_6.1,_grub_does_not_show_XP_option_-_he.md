---
title: "Installed U 6.1, grub does not show XP option - help!"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by jaguiler on 2007-04-03
Hi everyone,

I am new to Linux - not new to computers.  

I installed Ubuntu 6.1 with the alternate CD.  I first installed (fresh) a copy of Windows XP Pro, then I booted with the alternate CD.  My XP partition is 16 gb, my Linux part is 10gb, and I have a 4 gb nonpartitioned.

When I reboot from Ubuntu - I do not get a choice for Windows XP - argghh !
How do I get configure Grub to have a choice for my XP install ?

Thanks in advance for the help !!

PS - the live installs do not work on my machine - so booting the Live Cd and using Grub may not work as a solution!!

Thank you all !!

---

### Post by thelinuxguy on 2007-04-03
Boot into Ubuntu
Edit /boot/grub/menu.lst and add this entry at the end
```

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

You will have to replace (hd0,0) by the disk and partition number of your Windows install.
((hd0,0) is the first partition on the first drive)

EDIT: More information here - [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by jaguiler on 2007-04-03
I was able to edit the menu.lst - I added the lines....

I mad HD0,1 for my first partition -  when I selected it - nothing happened... it stayed on the "starting" screen

is there a way to see all my partitions ?


----

ok now I set it to HD0,4 - and when I choose Windows - I get a quick flash that says, invalid boot.ini unable to detect Ntxxxx(something)

any ideas ?

---

### Post by bulldog on 2007-04-03
Try ```
sudo fdisk -l
```to see your partitions and what's on it.
I get the impression your windows isn't on the first partition of any hdd.
Post the outcome of the fdisk command and we'll have a look.

---

### Post by jaguiler on 2007-04-03
OK - here are the results....
> 
john@Laptop1-Ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        2601        3648     8418060   83  Linux
/dev/hda2             511        2600    16787925    f  W95 Ext'd (LBA)
/dev/hda5             511        2550    16386268+   7  HPFS/NTFS
/dev/hda6            2551        2600      401593+  82  Linux swap / Solaris

Partition table entries are not in disk order
john@Laptop1-Ubuntu:~$ 

I believe this is my XP partition

/dev/hda5             511        2550    16386268+   7  HPFS/NTFS

it is kind of odd that partition 2 and 5 start on the same area.... 511

any ideas ?

---

### Post by egrus on 2007-04-03
hey, try (hd0,4) as grub starts counting at 0.

by the way, hda2 and hda5 starting at the same block number is ok, as hda2 designates the extended partition which contains hda5 and 6 if i'm not mistaken

---

### Post by bulldog on 2007-04-03
> **jaguiler said:**
> OK - here are the results....


I believe this is my XP partition

/dev/hda5             511        2550    16386268+   7  HPFS/NTFS

it is kind of odd that partition 2 and 5 start on the same area.... 511

any ideas ?

I think you're in trouble,as far as I know,windows should be on a primary partition,preferable the first one.
You have windows on a logical partition.

I've heard from people they have windows running in this kind of configuration,but never seen any proof of it.
You can try to modify the boot.ini [windows] file,to point to the right partition.

---

### Post by jaguiler on 2007-04-03
ok - how do I get to my boot.ini file now ?

I had NT4 loaded on this pc - and from there I installed XP.... - I figured this would be an issue...

any other way to save it ?

---

### Post by thelinuxguy on 2007-04-03
> **jaguiler said:**
> ok - how do I get to my boot.ini file now ?
I had NT4 loaded on this pc - and from there I installed XP.... - I figured this would be an issue...
any other way to save it ?

You could log onto the Recovery console from an XP boot disk and edit your boot.ini file. But I am not very sure that the boot disk will not overwrite your MBR and grub even when you don't invoke FIXMBR.

So my suggestion is: 
install a package that can write to an NTFS partition
mount /dev/hda5
```

mkdir windowsc
sudo mount /dev/hda5 windowsc

```
edit boot.ini

I use ntfs-3g for the purpose and a good HOWTO is located here: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

You may skip changing the fstab enties at this point and first see whether editing boot.ini works.

---

