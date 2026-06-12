---
title: "Grub how to change default grub root device"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by tcdrewiv on 2008-08-18
I have 2 drives

(hd0,2)   /dev/sda1   /media/disk/boot/grub/menu.lst

and

(hd1,0)  /dev/sdb1   /boot/grub/menu.lst


I would like grub to read the menu.lst on sdb1 rather than sda1.  I've tried changing the boot order of the drives in the bios but grub loads the menu.lst on sda1 each time.

I believe I need to change the groot from (hd0,2) to (hd1.0)?

Would  sudo grub
            grub> root (hd1,0)
            grub> setup (hd1)

be a solution or could I simply rename the unwanted menu.lst and grub will eventually find the correct one?

---

### Post by cdtech on 2008-08-18
> **tcdrewiv said:**
> 
Would  sudo grub
            grub> root (hd1,0)
            grub> setup (hd1)

be a solution

You would have to install GRUB to the MBR of the primary drive. You have the right idea. The way you show above would work, this will install the GRUB bootloader to the MBR of "sda" and point to the "/boot/grub/menu.lst" on "sdb".

**Update:**
Don't forget to update the menu.lst to point to the correct images....

---

### Post by tcdrewiv on 2008-08-18
After doing the grub>root (hd1,0)
                grub>setup (hd1)
rebooted.....

The incorrect menu.lst from (hda0,2) still appears.  I also tried switching the boot order of the drives in the BIOS but nothing changed.

The new kernel images are placed in (hd1,0) so in the past I have just edited the /media/disk/boot/grub/menu.lst when they have been updated.  

It would be nice to have grub pull up the correct menu.lst (that is automatically updated when a new kernel image is downloaded) from (hd1.0).

I also tried cd /media/disk/boot/grub
             sudo grub
             grub> root (hd1,0)
  Error 21: Selected disk does not exist


Any suggestions?

---

### Post by Herman on 2008-08-18
First set your boot order in your BIOS the way you will like it to remain.

Try using the 'find' command in GRUB.
```
find /boot/grub/menu.lst
```That should tell you which hard drives and partitions contain a /boot/grub/menu.lst file.

Now you want to see which is the right one to install to MBR? Okay,
```
cat (hd0,2)/boot/grub/menu.lst
```Press your tab key to scroll down the list.
Is this the GRUB you want with the menu.lst file you want to install to MBR in your first hard disk?
If yes, then 
```
root (hd0,2)
``````
setup (hd0)
``````
quit
```If that was not the GRUB you wanted to install to your first hard disk,
```
cat (hd1,0)/boot/grub/menu.lst
``` Use your tab key again to scroll down the file and see if that's the menu.lst for the GRUB menu you want.
Is this the GRUB you want with the menu.lst file you want to install to MBR in your first hard disk?
If that one is really the one you want installed to MBR in your first hard disk, then
```
root (hd1,0)
``````
setup (hd0)
``````
quit
```

---

### Post by Herman on 2008-08-18
> After doing the grub>root (hd1,0)
                grub> [COLOR=Red]**setup (hd1)**[/COLOR]
rebooted.....

The incorrect menu.lst from (hda0,2) still appears. I also tried switching the boot order of the drives in the BIOS but nothing changed.You installed GRUB to MBR in hard disk 2, but the BIOS won't automatically look at hard disk 2 unless you use your F12 key at boot time for a BIOS boot menu. Normally the BIOS will only look at hard disk 1, which is (hd0).

Another way you can do things, (this is the way I like), is to install an operating system's GRUB in hard disk 1's MBR to (hd0), and install an operating system's GRUB to MBR in each subsequent hard disk or flash memory or whatever.
Then I add a boot entry in the main /boot/grub/menu.lst file from the first hard disk to go to the MBR in the second hard disk,
```
title     second hard disk
root    (hd1)
chainloader +1
```When I'm booting, I start in the first hrd disk, and if I select to go to the second hard disk, that brings up the GRUB menu in the second hard disk. From there I can go to the third hard disk and so on.
Or, I could just have a list of all my hard disks in my first hard disk's MBR and jump right to the one I want. :)

So in other words, your 
```
grub> **[COLOR=Sienna]setup (hd1)[/COLOR]**

```might be right after all, if you add an entry from your hard disk 1's /boor/grub/menu.lst file to chainload the MBR in your second hard disk. :)

---

### Post by tcdrewiv on 2008-08-18
Thanks for the above solution. Works as intended. It certainly is easier than having to edit the menu.lst file after each kernel upgrade.

---

