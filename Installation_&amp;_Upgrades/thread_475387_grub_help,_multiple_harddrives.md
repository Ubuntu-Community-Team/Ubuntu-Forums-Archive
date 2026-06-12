---
title: "grub help, multiple harddrives"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Sqwishy on 2007-06-16
ok i'm making this breif.
we have 3 harddrives
hda
- ntfs partition with important system files like boot.ini that boots windows on hdd5
hdb
- ntfs partition with lots of ... junk/data/warez
hdc doesnt exist
hdd
- ext3 with ubuntus intalled
- linux-swap
- ext2 with grub
- ntfs with all the windows files that windows boots from

It's a werid setup. I've never installed grub on a compy with multiple harddrives
I'm thinking it's suppsot obe on hda cause booting is not working
I odn't think theres antyhing else to say? I really need help!

---

### Post by bulldog on 2007-06-16
The best thing to do is to install GRUB on your ubuntu hdd.
Make this hdd your master boot device and it should work.

But if you want to take a different approach,you have to boot from the hdd which has the GRUB menu in the MBR.

---

### Post by Sqwishy on 2007-06-16
> **bulldog said:**
> But if you want to take a different approach,you have to boot from the hdd which has the GRUB menu in the MBR. I can't do the first one, and I don't really understand what that means. MBR is master boot record, that has somethign to do with the BIOS and where it finds it's boot loader i'm guessing. And it does taht on the first HD right? So i need to isntall grub on the first harddrive.
I'm going to try that...

---

### Post by waggygee on 2007-06-16
> **Sqwishy said:**
> ok i'm making this breif.
we have 3 harddrives
hda
- ntfs partition with important system files like boot.ini that boots windows on hdd5
hdb
- ntfs partition with lots of ... junk/data/warez
hdc doesnt exist
hdd
- ext3 with ubuntus intalled
- linux-swap
- ext2 with grub
- ntfs with all the windows files that windows boots from

It's a werid setup. I've never installed grub on a compy with multiple harddrives
I'm thinking it's suppsot obe on hda cause booting is not working
I odn't think theres antyhing else to say? I really need help!

I reinstalled my Ubuntu last night and I am experiencing what I think is an identical problem (Ubuntu boots but Windows XP does not appear on Grub). I did things the same way I did on my previous setup and it ran smoothly

---

### Post by bulldog on 2007-06-16
> **waggygee said:**
> I reinstalled my Ubuntu last night and I am experiencing what I think is an identical problem (Ubuntu boots but Windows XP does not appear on Grub). I did things the same way I did on my previous setup and it ran smoothly

You can easily edit the menu.lst,and put  windows manually.
Something like this [I have windows on the second hdd,so you have to map your hdd's]
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	(hd1,0)+1

```

---

### Post by bulldog on 2007-06-16
> **Sqwishy said:**
> I can't do the first one, and I don't really understand what that means. MBR is master boot record, that has somethign to do with the BIOS and where it finds it's boot loader i'm guessing. And it does taht on the first HD right? So i need to isntall grub on the first harddrive.
I'm going to try that...

You can in most BIOS programs change the boot device order.
Set the ubuntu hdd as master boot device [the first one to boot from] and install GRUB on this hdd.
You can reinstall GRUB with the live cd very easily.
]Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Setup hd0 means it will be installed on the first hdd,you can change this in the hd which is indicated by the find command,like (hd2).

---

### Post by waggygee on 2007-06-16
> **bulldog said:**
> You can easily edit the menu.lst,and put  windows manually.
Something like this [I have windows on the second hdd,so you have to map your hdd's]
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	(hd1,0)+1

```

This worked for me! Thanks!

---

### Post by Sqwishy on 2007-06-16
> **bulldog said:**
> You can in most BIOS programs change the boot device order....
Yeah i probobly could of done that, i just reinstalled the whole thing using the samepartions except for boot, which i used /boot on the 1st hd instead of the 2nd and its' allgood. 
If none of that made any sense, Its because i should be asleep right now. But It works, by putting the boot partition on the first harddrive.
Good night. Aand thanksyou

---

