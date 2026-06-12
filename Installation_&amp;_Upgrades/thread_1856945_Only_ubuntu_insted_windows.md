---
title: "Only ubuntu insted windows"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by drofart on 2011-10-09
Hi all.
      I have a dell with windows 7 & ubuntu 11.04 . Now i want to remove windows completely not a little dust should remain & use both os' s space for a fresh installation of ubuntu. 

If possible in safe way i want to make new partition table , like a new hard disk( as close as) .
  Waiting for a response ,
 thank you.

---

### Post by WasMeHere on 2011-10-09
At first, think a while about what you want and consider the alternatives you will get from this thread!

Backup your drive or at least your private files!

I suggest you edit the partition table with *gparted* from a live CD or USB drive. It is easy to remove windows completely: delete the windows partition(s)!

Either keep your partition with Ubuntu if you are satisfied with the size and performance, or wipe the whole disk removing all partitions!

- If you keep your partition with Ubuntu, you can make a data partition of the previous Windows partition. If you have only linux, I suggest that you use the *ext3* file system (while it is a good idea to have *ext4* for the system partition).

Run ```
sudo update-grub
``` to get a fresh grub menu!

- Check that you have enough space in the swap partition, larger than the RAM!

Have fun
Olle

---

### Post by drofart on 2011-10-09
> **Olle Wiklund said:**
> At first, think a while about what you want and consider the alternatives you will get from this thread!

Backup your drive or at least your private files!

I suggest you edit the partition table with *gparted* from a live CD or USB drive. It is easy to remove windows completely: delete the windows partition(s)!

Either keep your partition with Ubuntu if you are satisfied with the size and performance, or wipe the whole disk removing all partitions!

- If you keep your partition with Ubuntu, you can make a data partition of the previous Windows partition. If you have only linux, I suggest that you use the *ext3* file system (while it is a good idea to have *ext4* for the system partition).

Run ```
sudo update-grub
``` to get a fresh grub menu!

- Check that you have enough space in the swap partition, larger than the RAM!

Have fun
Olle

Thank you, but i am unable to download gparted through sourceforge ,, Is their any other source for download?

---

### Post by drofart on 2011-10-09
>  If you keep your partition with Ubuntu, you can make a data partition of the previous Windows partition. 


Can u please explain a little more .

Thank you [COLOR="White"]dear[/COLOR]

---

### Post by WasMeHere on 2011-10-10
> **drofart said:**
> 
Thank you, but i am unable to download gparted through sourceforge[/SIZE] ,,[SIZE=3] Is their any other source for download?
Sorry for the delay...
Gparted is on the Ubuntu live disk (from which you can install Ubuntu), so you need not download it :-)

---

### Post by WasMeHere on 2011-10-10
> **drofart said:**
> Can u please explain a little more .

Thank you [COLOR="White"]dear[/COLOR]

What I mean is that many people have several partitions on their hard disks, not one big partition with operating system and data (plus a small swap partition, which is more or less automatically installed by linux). For example, on my 'work-horse computer, I have Ubuntu 10.04 LTS on one partition, a swap partition, a bleeding-edge Ubuntu on another partition, a bleeding edge Linux Mint on another partition, and multimedia files (photo, video, music) on a data partition.

This can be convenient and improves the possibility to have suitable backup for the different kinds of data.

---

### Post by harry_r_s on 2011-10-10
There's one more way to do that!
1. Backup your files.
2. Uninstall Ubuntu.
3. Manage partitions as you want to have (optional)
4. Again install ubuntu 11.04 but this time choose the option to    replace windows!
If you didn't managed partitions in win then do that while you are installing ubutu!
.
I guess this helped you.

---

### Post by hansdown on 2011-10-10
One more way, is to do a fresh install, and choose,

```
use entire disk
```

---

### Post by drofart on 2011-10-10
[SIZE=2][[/SIZE][SIZE=2]QUOTE=Olle Wiklund;11326840]Sorry for the delay...
Gparted is on the Ubuntu live disk (from which you can install Ubuntu), so you need not download it :-)[/QUOTE]
  Thank u .
           Should not say the first latter :) ok u mean that advance option during installation, ok got it.

> **Olle Wiklund said:**
> What I mean is that many people have several partitions on their hard  disks, not one big partition with operating system and data (plus a  small swap partition, which is more or less automatically installed by  linux). For example, on my 'work-horse computer, I have Ubuntu 10.04 LTS  on one partition, a swap partition, a bleeding-edge Ubuntu on another  partition, a bleeding edge Linux Mint on another partition, and  multimedia files (photo, video, music) on a data partition.

This can be convenient and improves the possibility to have suitable backup for the different kinds of data
   Thanks Again
> **harry_r_s said:**
> 
[/SIZE][SIZE=2] 				[/SIZE][SIZE=2][IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG] 				**Re: Only ubuntu insted windows**[/SIZE] 			
[SIZE=2] 			[/SIZE][SIZE=2] 			 		   		 		 		[/SIZE][SIZE=2]There's one more way to do that!
1. Backup your files.
2. Uninstall Ubuntu.
3. Manage partitions as you want to have (optional)
4. Again install ubuntu 11.04 but this time choose the option to    replace windows!
If you didn't managed partitions in win then do that while you are installing ubutu!
.
I guess this helped you.
 Thank u 
> **hansdown said:**
> 
[/SIZE][SIZE=2] 				 				[/SIZE][SIZE=2]**Re: Only ubuntu insted windows** 			[/SIZE]
[SIZE=2] 			[/SIZE][SIZE=2] 			 		   		 		 		[/SIZE][SIZE=2]One more way, is to do a fresh install, and choose,

[/SIZE]  	[SIZE=2]Code:[/SIZE]
 	[SIZE=2]use entire disk[/SIZE] 

[SIZE=2][/SIZE]
thank u dear that's it.

---

### Post by WasMeHere on 2011-10-10
> **drofart said:**
> [SIZE=2][[/SIZE][SIZE=2][QUOTE=Olle Wiklund;11326840]Sorry for the delay...
Gparted is on the Ubuntu live disk (from which you can install Ubuntu), so you need not download it :-)
  Thank u .
           Should not say the first latter :) ok u mean that advance option during installation, ok got it.[/QUOTE]
Well, you can use *advance option during installation* but I think it is better to run gparted as is in the live environment from the menu
System -- Administration -- Gparted (in Gnome shell)
or simply ```
sudo gparted
``` from a terminal window.

---

### Post by SunshineGoldwing on 2011-10-10
Well, I guess that you now got everything you need, so I suppose that you don't need more help. But if you do: just ask! ;)

---

### Post by hansdown on 2011-10-10
Glad you fixed it, drofart.

---

