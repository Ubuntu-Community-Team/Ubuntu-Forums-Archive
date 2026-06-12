---
title: "Complete linux Noob needs help with windows/linux"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by broken_nephilim on 2007-05-28
And im desperate!

It has been 3 days since I first installed ubuntu, just for the sake of it, i wanted to try it. Well, Im really liking linux! i have ubuntu 7.04 and its just great.

but it couldnt be so easy...it never is :(

i need windows back, just for the little things until i can manage a "only linux" machine.

problem is, i cant install windows back

This past 3 days have been nightmarish, i have tried it all...creating a boot cd for windows xp, messing with slax, trying to format the entire hard disk...im just unable to do this...

tutorials for linux are just HARD on the friendly user :p i have started to use the terminal, but when a procces needs some imput form the human im completely lost

I have a 250gb hard disk, an ubuntu 7.04 disk and a windows XPhome disk

maybe a mighty linuxer can help me?

---

### Post by aysiu on 2007-05-28
You think Linux tutorials are hard? Try using this Microsoft one:
[How to Remove Linux and Install Windows XP](http://support.microsoft.com/kb/314458)

By the way, next time you want to try Ubuntu, you can use a live CD (doesn't affect your hard drive) or set up a dual boot (allows you to still boot into Windows).

P.S. Even though I am being a bit cheeky, that link from Microsoft's website is the one you need in order to reinstall Windows. But it is more difficult to follow than Linux tutorials, unfortunately.

---

### Post by broken_nephilim on 2007-05-28
first of all im really thankful for you to answer me

but, its useless

To remove Linux from your computer and install Windows XP, follow these steps:
1.	Remove the native, swap, and boot partitions used by Linux:
a. 	Start your computer with the Linux Setup floppy disk, type fdisk at the command prompt, and then press ENTER.


I DONT HAVE A FLOPPY DISK UNIT 


XDDDDD

i found that tutorial before

i tried the live version before, then isntalled it. didnt think i would want windows back for some programs

---

### Post by aysiu on 2007-05-28
That's precisely why I take issue with your earlier statement about Linux tutorials. They vary in quality, of course, but by and large they are much better than Windows tutorials.

Instead of using a "Linux Setup floppy disk," you can use the live CD's Gnome Partition Editor tool (I think it's in the System > Administration menu) to delete the Ext3 and swap partitions (there shouldn't be a boot partition, unless you set one up manually).

---

### Post by ryanVickers on 2007-05-28
Ok, format your hardrive using gparted, then make a fat32 partition the size you want windows to be.  then install windows onto it (reformat it as ntfs or something). Then install linux into the empty space.  It will automatically make a menu for duel booting.  Yes, making it all windows then shrinking would be *Slightly* easier, but not worth it; when you shrink it windows gets really slow for some reason :)

so in order:

1. make HD blank

2. make a Fat32 the size you want windows to be

3. put in your windows disk and install it over top of the blank Fat32 - reformat in the process as ntfs

4. put in ubuntu live cd.  Install into empty space (/ and swap needed)

5. then, every boot, you can choose windows or ubuntu!

---

### Post by aysiu on 2007-05-28
If you do decide you want a dual boot, follow this tutorial:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I promise you it'll be easier to follow than Microsoft's lousy tutorial about removing Linux.

---

### Post by hanzomon4 on 2007-05-28
Do you have a windows installation disk? If so setup your system to boot from the cdrom. On my Dell I basically press F2 to get into the BIOS which lets me change the boot order, or I could press F12 and it will ask where I want to boot from.

---

### Post by broken_nephilim on 2007-05-28
well is not working...

I used gnome partition editor,  deleted all and created a fat 32 partition, put my windows CD in for installation and...

the windows CD doesn't boot, Linux tries to boot but says

unable to load GRUB error 22

this saddens me:(

---

### Post by ryanVickers on 2007-05-28
Wierd, it shouldn't need grub if it's loading from the live CD.  at least it's not error 8 (I think it is), that's a doozee! :p
(actually I'm serious)

---

### Post by aysiu on 2007-05-29
You have to set your BIOS to boot from CD.

Are you sure you have a Windows installer CD and not some other kind of Windows-related CD?

You may also want to Google the Windows *fixmbr* command. That may help.

---

### Post by hanzomon4 on 2007-05-29
Yeah if grub is involved you're not booting from the cd. Google your computer brand to see how to go about getting to the bios and setting it to boot from the cd. Also check the disc to make sure it's an installation disk, Dell didn't provide me with one until I called and asked for one.

---

### Post by broken_nephilim on 2007-05-29
well, it is an xp home installation cd, I used it on my sister machine

My bios set up is 

boot from cd1
boot from cd2
boot from hard disk

i even turned off hard disk, but it stills loads grub

maybe its my windows cd, but i dont know how to get another one that does boot:(

thx for all your help

---

### Post by ryanVickers on 2007-05-29
perhaps there is something wrong with the disk.  Try downloading it again, or getting the alternative cd.  The disk comes with grub on it but I didn't think it should need it!  But for booting from cd it's setup right!

---

