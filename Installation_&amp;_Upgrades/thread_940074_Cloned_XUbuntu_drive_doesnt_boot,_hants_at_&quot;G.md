---
title: "Cloned XUbuntu drive doesnt boot, hants at &quot;GRUB &quot; with blinking cursor"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by seidleroni on 2008-10-06
I have an XUbuntu HD which I got "just right" with all the settings I need, and I want to clone it onto another hard drive which is exactly the same (same manufacturer, model #, size, etc...)  However, once I cloned it (using Macrium Reflect) and then restored image onto the 2nd hard drive (which wasnt blank), I get the problem where it clones just fine, but when I try to boot off the disk, it gives me "GRUB  " and then the cursor, but doesnt let me type anything in.  

Any ideas?  I'm more than happy to try another cloning s/w (which is hopefully free) if that would be better.  A s/w that I can clone the drive in Windows XP would be great.

Thanks,
Seidleroni

---

### Post by upchucky on 2008-10-06
a restored image does not write the boot sector, you need to set up grub to see the new drive and then write the boot sector.

search for supergrub advanced, if this is a single os boot setup supergrub should get it right atomatically.

if you have peculiar settings then there is a readme for supergrub, and lots of posts here about repairing a boot sector

---

### Post by caljohnsmith on 2008-10-06
Cloning a whole drive is extremely easy with the "dd" command in linux, so you could do it from a Live CD. For instance, if your input drive is sda and target drive is sdb, you could use:
```
sudo dd if=/dev/sda of=/dev/sdb bs=10M conv=notrunc
```

But it sounds like Macrium may have cloned your drive fine and that you might have a BIOS issue with booting that cloned drive. Have you had any other OSes on that drive and were able to boot them? 

You could try reinstalling Grub to the MBR (Master Boot Record) of your cloned drive and see if that helps (but I think a BIOS issue is more likely at this point):
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know if that makes any difference.

---

### Post by seidleroni on 2008-10-07
I reloaded a clone copy of Windows XPe on the hard drive (which couldnt load XUbuntu) and it the computer booted into XPe with no problem, so I dont think the fault is with the hard drive.  I dont understand why windows XPe can boot up, but Linux cannot.  

Also, I have no method to connect two different hard drives to one PC at the same time (these drives are mini IDE drives on a Panel PC) and only one can go on at a time.  I have a USB to IDE converter that I"ve been using to create/reload the images.

Also, when I have loaded on XUbuntu and connected it to the PC, the hard drive that I want IS listed on the "boot options" selection in the BIOS, so I dont know why it cannot boot into it.

---

### Post by seidleroni on 2008-10-07
I reloaded a clone copy of Windows XPe on the hard drive (which couldnt load XUbuntu) and it the computer booted into XPe with no problem, so I dont think the fault is with the hard drive.  I dont understand why windows XPe can boot up, but Linux cannot.  

Also, I have no method to connect two different hard drives to one PC at the same time (these drives are mini IDE drives on a Panel PC) and only one can go on at a time.  I have a USB to IDE converter that I"ve been using to create/reload the images.

Also, when I have loaded on XUbuntu and connected it to the PC, the hard drive that I want IS listed on the "boot options" selection in the BIOS, so I dont know why it cannot boot into it.

---

