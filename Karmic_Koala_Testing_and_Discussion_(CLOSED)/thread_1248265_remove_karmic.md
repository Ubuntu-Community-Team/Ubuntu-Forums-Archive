---
title: "remove karmic"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FreezWay on 2009-08-24
I installed karmic, ran into a lot of bugs ( =( ) and want to remove it. I installed it in another partition, so 9.04 is still there (what im using.) but how do i remove 9.10?

---

### Post by raymondh on 2009-08-24
> **FreezWay said:**
> I installed karmic, ran into a lot of bugs ( =( ) and want to remove it. I installed it in another partition, so 9.04 is still there (what im using.) but how do i remove 9.10?

You can use the liveCD and access gparted.  Manually delete the Karmic partition and then (if you wish), extend the jaunty to take up the empty space.

Afterwards, you'll have to edit the /boot/grub/menu.lst and comment out/delete the Karmic entry ... so that GRUB does not give you the option to boot into a deleted (karmic) partition.  Remember to save.

---

### Post by stlsaint on 2009-08-24
+1 Ray <> -2 Microsoft Windows

---

### Post by FreezWay on 2009-08-28
ermm, is there a way to do this w/o the cd. I can't figure out how to do it there and my computers disk drive sucks, so cd botting is slow.

---

### Post by FreezWay on 2009-08-31
can any1 help me here... also i want good'ol grub 1 back... im having issues running an updated kernal (i have intel integrated graphics =P) b/c i cannot select it.

EDIT: i got gparted... what should i delete.

here is the screeny:

[http://i412.photobucket.com/albums/pp208/FreezWay_Productions/Screenshot-1.png](http://i412.photobucket.com/albums/pp208/FreezWay_Productions/Screenshot-1.png)

---

### Post by zvacet on 2009-08-31
Delete extended partition ( I suppose there is Karmic).You can shrink you sda1 (to 10-15GB) and nmake separate home partition.Don´t forget in make swap partition.

---

### Post by stlsaint on 2009-08-31
> **FreezWay said:**
> can any1 help me here... also i want good'ol grub 1 back... im having issues running an updated kernal (i have intel integrated graphics =P) b/c i cannot select it.

EDIT: i got gparted... what should i delete.

here is the screeny:

[http://i412.photobucket.com/albums/pp208/FreezWay_Productions/Screenshot-1.png](http://i412.photobucket.com/albums/pp208/FreezWay_Productions/Screenshot-1.png)


how much space did you give karmic? which ever partition you gave to karmic is the one you want to format!

---

### Post by raymondh on 2009-08-31
> **FreezWay said:**
> can any1 help me here... also i want good'ol grub 1 back... im having issues running an updated kernal (i have intel integrated graphics =P) b/c i cannot select it.

EDIT: i got gparted... what should i delete.

here is the screeny:

[http://i412.photobucket.com/albums/pp208/FreezWay_Productions/Screenshot-1.png](http://i412.photobucket.com/albums/pp208/FreezWay_Productions/Screenshot-1.png)

Assuming Karmic is in sda6:

Make sure the partitions are unmounted. Gparted from a liveCD or a standalone CD ought to unmount automatically.  But just 2-check.  Rt. click on each partition and if given the option to unmount, do so.  For swap, select swapoff.

- Back-up
- Delete sda6, swap (both) and then the extended.  I would make a goal to delete the extended.  Both swaps are inside the extended hence my suggestion to delete both.
- Enlarge/resize sda1 to take up the newly, freed up space
- Use gparted to make a swap.
- Edit your /boot/grub/menu.lst to reflect the new change (e.g. no more Karmic

If Karmic is in sda1:

- Back up
- Delete sda1
- Highlight the extended and resize/enlarge
- delete 1 swap
- highlight sda6 and resize/enlarge to take up unallocated space
- edit menu.lst to reflect change

If you want to create a separate /home. post back as it will require a different tutorial.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Regarding GRUB legacy, you might want to consider re-installing grub from the liveCD to bring back "old grub" (as you say)

**sudo grub**
**find /boot/grub/stage1**  [COLOR="Red"](this will bring out an output like (hd0,1) or something we'll call X,Y.  Note it.[/COLOR]
**root (hdX,Y)**  [COLOR="Red"](what it outputs)[/COLOR]
**setup (hd0)**  [COLOR="Red"]to put it in the MBR of the 1st disk[/COLOR]
**quit**

Back-up.

---

### Post by FreezWay on 2009-08-31
ok i got rid of karmic and even figured out which swap was which. anyhoo... i cant resize sd1... it has a little lock symbol by it.

---

### Post by raymondh on 2009-08-31
> **FreezWay said:**
> ok i got rid of karmic and even figured out which swap was which. anyhoo... i cant resize sd1... it has a little lock symbol by it.

Can you right click on it and unmount (among the options)?  Also, swapoff for swap.  BTW, you are using gparted from the liveCD, right?

---

### Post by FreezWay on 2009-08-31
no, i am using regular gparted. i figured out which swap was which so i only removed karmic's. i can unmount the current filesystem... not sure if i should.

---

### Post by raymondh on 2009-08-31
> **FreezWay said:**
> no, i am using regular gparted. i figured out which swap was which so i only removed karmic's. i can unmount the current filesystem... not sure if i should.

When you say "regular gparted", you mean a standalone gparted disk ... not gparted from an Ubuntu install (say in sda1), right?  

If you are in ubuntu now (say sda1) and accessed gparted from it, you cannot resize sda1 because it is mounted (locked).

If you are using a liveCD (whether it be Ubuntu or a gparted live), then sda1 should be unmounted automatically (but it's good to double-check hence the right click).  You also want to swapoff. Sda1 should be unmounted before you are allowed to resize it.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Back-up your files.

---

### Post by FreezWay on 2009-08-31
ok i just have my main 9.04 partition... but grub is spitting me errors. how do i boot and fix this. posting from friends computer.

---

### Post by raymondh on 2009-08-31
What are the GRUB errors?

---

### Post by FreezWay on 2009-08-31
here is what my terminal i get looks like:

[FONT=Courier New]GRUB loading
Welcome to GRUB! (highlighted)

Entering rescue mode...
error: no such partition
grub rescue>(blinking cursor to type with)

[FONT=Arial]so basiccally i have grub's CLI. how do i boot and how do i make it so i dont get this in the future?[/FONT]
[/FONT]

---

### Post by raymondh on 2009-08-31
> **FreezWay said:**
> here is what my terminal i get looks like:

[FONT=Courier New]GRUB loading
Welcome to GRUB! (highlighted)

Entering rescue mode...
error: no such partition
grub rescue>(blinking cursor to type with)

[FONT=Arial]so basiccally i have grub's CLI. how do i boot and how do i make it so i dont get this in the future?[/FONT]
[/FONT]

When you removed karmic, did you try to reinstall "old" grub (as you wanted)?  Try to reinstall GRUB from the liveCD.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by FreezWay on 2009-09-01
ok i fixed everything thx to all! back and running once again.

edit: oh and ray... +1

---

### Post by raymondh on 2009-09-01
+1 on you as well.

Congratulations and happy ubuntu-ing.

---

