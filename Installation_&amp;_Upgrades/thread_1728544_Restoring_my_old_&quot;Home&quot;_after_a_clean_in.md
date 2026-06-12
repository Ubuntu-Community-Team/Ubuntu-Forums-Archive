---
title: "Restoring my old &quot;Home&quot; after a clean install"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by JoeFriday49 on 2011-04-13
Here's where I'm at right now...  Just did a clean install of 10.10 64bit into the old partition /   This was a 20 GB partition where the old install used to live.  When I did the install I didn't touch the existing 10 GB swap partition or the old "Home" partition (The remainder of a 1 TB drive) but I did reformat the old 20 GB partition...  Now I have a folder called 970 GB filesystem that contains all my old stuff, and there is a brand new Home Folder that I assume is coexisting within the 20 GB partition I assigned to install into...  (It only reports 13.8 GB free space)...

I sorta' figured that since I had used the same login and password that everything would just fall into place, but it didn't happen.  Is there any way to incorporate the 970 GB as my new "Home Folder"?

I had always previously just used the entire drive without assigning any partitions and reloading my stuff from a backup drive, so this is my first attempt at holding onto my stuff when reinstalling...

---

### Post by Hedgehog1 on 2011-04-13
You can make an addition to your /etc/fstab file to 'override' the '/home' to use your seperate '/home' partition:

Here is my /etc/fstab file (your UUIDs will be different)
```
# / was on /dev/sda5 during installation
UUID=f2fd03c5-2835-415c-8448-75473daf624a  /                 ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a  none              swap  sw                   0  0  
# /home partition was /dev/sda7
**[COLOR="Red"]UUID=4aebc2c6-5984-47e3-b2ea-7fdfaf23343e  /home             ext4  nodev,nosuid         0  2[/COLOR]**
```

First - figure out the UUID of your new '/home' partition (the -'l' is a lower case 'L'):

```
sudo fdisk -lu
```

Then add your /home line with your UUID to /etc/fstab:

```
gksudo gedit /etc/fstab
```

When you re-boot, your will be using the new partiton for '/home'. :D

This is the 'short list' to making this work.


***The Hedge***

:KS

If you need to stop using a line in /etc/fstab, just put a '#' in front of the line to make it a comment.

---

### Post by JoeFriday49 on 2011-04-14
> **Hedgehog1 said:**
> You can make an addition to your /etc/fstab file to 'override' the '/home' to use your seperate '/home' partition:

If you need to stop using a line in /etc/fstab, just put a '#' in front of the line to make it a comment.

Cool, I'll give that a shot this evening...  Another question...  I don't believe this is the way everyone does new installations.  Is there some way to "make" the new install see the old "home" partition during the install so it just comes up right?

Thanks!

---

### Post by JoeFriday49 on 2011-04-14
Here is the code I get from the first command. It doesn't appear to contain the info you referenced...

joefriday49@A740GM:~$ sudo fdisk -lu
[sudo] password for joefriday49: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1a0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39064547    19531250   83  Linux
/dev/sda2        39065598  1953523711   957229057    5  Extended
/dev/sda5        39065600    58595327     9764864   82  Linux swap / Solaris
/dev/sda6        58597376  1953523711   947463168   83  Linux
joefriday49@A740GM:~$ gksudo gedit /etc/fstab

The next command yields this...  I'm still lost...

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2f842152-e404-4b1a-b3cf-3fbb5d6928fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=47979097-809f-40ef-8ae5-7b1fdd049b51 none            swap    sw              0       0

---

### Post by Hedgehog1 on 2011-04-14
Had a little cut'n'paste error from my cheat sheet.  I gave you the wrong listing command - sorry.


Please run this for a list of the UUIDs:
```
sudo blkid
```

This command will give you an output that looks something like this:

```
marc@MarcsDesktop:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="965E0E865E0E5EFD" TYPE="ntfs" 
/dev/sda2: LABEL="Area51" UUID="EA561004560FCFED" TYPE="ntfs" 
/dev/sda5: LABEL="/" UUID="f2fd03c5-2835-415c-8448-75473daf624a" TYPE="ext4" 
/dev/sda6: UUID="cb0c7226-150e-45ca-ba5c-2e161dc10f6a" TYPE="swap" 
**[COLOR="red"]/dev/sda7: LABEL="myolddata" UUID="aaaaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeee" TYPE="ext4" [/COLOR]**
/dev/sda8: UUID="b838c4e8-1966-4078-bcbf-b5773bcd1e9a" TYPE="ext4" 
```

Figure out the UUID that is the one for your partiton that has the '/home' you want, then add a line for it in the /etc/fstab file:

```
gksudo gedit /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=2f842152-e404-4b1a-b3cf-3fbb5d6928fb / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=47979097-809f-40ef-8ae5-7b1fdd049b51 none swap sw 0 0
[B][COLOR="Red"]# Adding my /home partition:
UUID=aaaaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeee  /home             ext4  nodev,nosuid [/COLOR][/B]
```

Once you save /etc/sftab and reboot, the file system will use the '/home' partition.


As to: "How do you set this up at install (or upgrade) time?", you have to do it manually:

[IMG]http://img51.imageshack.us/img51/337/mbrpariondemo15.png[/IMG]

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]


***The Hedge***

:KS

---

### Post by Vaphell on 2011-04-14
yes, but of course you would want to untick the format checkbox :)

---

### Post by JoeFriday49 on 2011-04-14
YEA!!!...  I'm back!

Worked like a champ, and the tutorial on how to do it right the next time will be a BIG help when the time comes...

---

### Post by JoeFriday49 on 2011-04-14
> **Vaphell said:**
> yes, but of course you would want to untick the format checkbox :)

Yep, looks like that would be a good thing...  ( :

---

### Post by Hedgehog1 on 2011-04-15
> **Vaphell said:**
> yes, but of course you would want to untick the format checkbox :)

[SIZE="3"]VERY TRUE![/SIZE] (but it was the only image I had of that... Gotta make one with the box un-checked...)

***The Hedge***

:KS

---

