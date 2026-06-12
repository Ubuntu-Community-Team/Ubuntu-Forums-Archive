---
title: "Tricky Dual Boot Issue"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by edvinpul on 2008-06-04
Hello Ladies and Gents, here's what I think is a tricky one (or maybe my ignorance makes it tricky)

I used to have a dual boot system that worked.  I decided I would install my 'golden' linux system on a single disk with my other systems on other hard disks. I created the following 4 partition on my new drive (on first SATA port)
sda1 /boot
sda2 /
sda3 swap
sda4 /home

I thought this was good!  My XP install (which i need for work) used to be on the first SATA port but I moved it to the third.  Ubuntu recognizes it as sdc1.  I have added (hd2,0) with the chainloader to grub and but it does not work.  When I use the XP fixmbr it writes over grub.  I tried to reinstall XP but it doesn't recognize the partition on (hd0,0) and wants to erase it which will screw up Ubuntu

Any suggestions?

---

### Post by logos34 on 2008-06-05
You need to [add mapping]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")--windows won't boot unless you trick it into thinking it's the boot drive.

In your case:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

If that doesn't fix things, try moving the hard disk to sata port 2 and edit the entry just like in the link

---

### Post by edvinpul on 2008-06-05
Ok, great.  I will try that tonight.  Thanks for the help.

---

### Post by edvinpul on 2008-06-06
So I added what was suggested to the menu.lst file and I've gotten a little closer.  When I select the windows operating system (via grub) I get "NTLDR is missing"

If I try to use the XP repair "fixmbr" or "fixboot" it erases my grub (which is on hd0,0)  if I use the install feature, which tries to fix the windows partition, it says I have to reformat hd0,0...i guess to reinstall the MBR.

So should I be trying to get the NTLDR on my windows partition?

---

### Post by logos34 on 2008-06-06
The thing with windows is it refuses to install unless the target installation disk is first in the Bios hard drive boot order.  (hd0)  

Try setting it first in the boot order, then run **fixboot** or reinstall.  Now set the linux drive back as boot disk and [restore grub using the live cd]("http://ubuntuforums.org/showthread.php?t=224351"). 

If that still does not work, you might also need to edit /boot/grub/device.map to match new arrangement

---

### Post by edvinpul on 2008-06-06
Do you think if I were to place the hd with the XP install as the first device, repair the install, then return my Ubuntu install back as the first device it would work (with the drive mapping of course)?  Or would I end up with two drives with the 'boot' flag set and mess up the boot process for both?

---

### Post by logos34 on 2008-06-06
> **edvinpul said:**
> Do you think if I were to place the hd with the XP install as the first device, repair the install, then return my Ubuntu install back as the first device it would work (with the drive mapping of course)?

That's what I just suggested you try.

> Or would I end up with two drives with the 'boot' flag set and mess up the boot process for both?

XP won't change grub settings/flags--whatever you do to the windows drive (whether fixboot or reinstallation) will only affect that drive, not the linux drive/mbr, where grub is


EDIT: actually what I mean is that windows won't change or overwrite grub if the latter is on another drive, but it will I think add a boot flag to windows in the DOS partition table.  But that's not usually a problem since windows is the only that seems to care about the flags anyway

---

### Post by edvinpul on 2008-06-06
Yes your right!  You did suggest that. I tried it, with the fixmbr and fixboot and it still said NTLDR missing.  

I thought there was an option on the XP CD to repair the current installation on disk, so i thought I would try that, however it seemed to have erased everything. I was strumming away on my guitar while i was trying it so maybe I selected the wrong option.  

Never the less, I got the dual boot working again!  Thanks for the help.

---

### Post by anglicus on 2008-06-06
Lots of information here. Worked for me;
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by logos34 on 2008-06-06
> **edvinpul said:**
> I tried it, with the fixmbr and fixboot and it still said NTLDR missing.  

I thought there was an option on the XP CD to repair the current installation on disk, so i thought I would try that, however it seemed to have erased everything. I was strumming away on my guitar while i was trying it so maybe I selected the wrong option.  

Never the less, I got the dual boot working again!  Thanks for the help.

Well, glad you managed to get it to boot again...hopefully you didn't lose anything important.  (If you did you could try PhotoRec or TestDisk).  XP 'repair' is supposed to do just that, no wipe it! odd

---

### Post by edvinpul on 2008-06-06
Yeah, everything is gone.  I needed to access installed software - so I was lucky in that sense - no lost data.  
Thanks for the help though, at least I learned something new!

Thanks again

---

