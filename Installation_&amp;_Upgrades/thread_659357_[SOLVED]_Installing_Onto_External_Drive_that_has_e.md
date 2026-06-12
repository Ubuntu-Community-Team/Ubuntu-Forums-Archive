---
title: "[SOLVED] Installing Onto External Drive that has extra NTFS Partition"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by SkylineGT-R on 2008-01-05
I wish I didn't have to come here.  It looks like this place gets a lot of questions about external drives and I hate to add to it.  I tried to look for a solution but could not find anything.

Anyway, here's  what I want to do.  I want to install Ubuntu 7.10 onto a 15gb ext3 partition(with no swap) on my external USB hard drive (WD Passport).  And I want the rest of the space to be an NTFS partition.
I have successfully installed ubuntu onto the 15gb ext3.  But whenever the NTFS partition is there ubuntu will not boot. :confused: Ive tried installing it a few times and can't figure out what to do now.  Anyone know what I can do?

Update:
When I hit F12 on the BIOS screen I can select to boot from a USB device.  So I do that and another screen loads and gives me  options to load ubuntu, ubuntu recover, mem86, and windows vista (I guess this screen is GRUB.)  When I try to boot ubuntu or mem86 it gives me *Error 17: Cannot mount selected Partition*.  When I try to boot vista from that list it says loading sometihng like "GRUB stage 2..." and very quickly goes back to the previous screen with ubuntu and mem86 and Vista.

---

### Post by logos34 on 2008-01-05
> **SkylineGT-R said:**
> ...When I try to boot ubuntu or mem86 it gives me *Error 17: Cannot mount selected Partition*.  When I try to boot vista from that list it says loading sometihng like "GRUB stage 2..." and very quickly goes back to the previous screen with ubuntu and mem86 and Vista.

highlight the ubuntu kernel and pres 'e' to edit.   'e' again on the 'root' line...change to (hd0,0) if ubuntu is the first partition, or (hd0,1) if second, etc.  Then 'enter' and 'b' to boot.  If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

(change 'groot' line also)

For windows you need to add[ map commands]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") and possibly edit /boot/grub/device.map.  Post back if you need any add'l help

---

### Post by SkylineGT-R on 2008-01-05
It worked!  But I thought the external drive was hd1 and the internal was hd0.  Hmm....

I probably won't touch the Windows part of it.  I can just boot that without GRUB.

I'm going to reboot to make everything is all after editing that file.

Update:  It boots fine now, thanks.  But I'm still curious about what I said before about the external drive being hd1 and the internal being hd0.

---

### Post by logos34 on 2008-01-06
> **SkylineGT-R said:**
> But I'm still curious about what I said before about the external drive being hd1 and the internal being hd0.

The minute you change the Bios boot order so that the USB drive is first, then it becomes '(hd0)'.  Hence the need to edit menu.lst.  

The only way around it is to disconnect the internal hdd before installing.

---

### Post by SkylineGT-R on 2008-01-06
I see... thanks.

---

### Post by logos34 on 2008-01-06
alrighty.  enjoy. And mark as 'solved' in thread tools menu.

---

### Post by SkylineGT-R on 2008-01-07
Oh decided to fix that Windows part.  All I had to do was change that to hd1,0.  There's still something going on with this though. When I have my power cord plugged in (this is a laptop) it won't boot from the external drive.  It's not a big deal I just thought I'd share that.  It's actually kind of funny.

---

### Post by logos34 on 2008-01-07
> **SkylineGT-R said:**
> Oh decided to fix that Windows part.  All I had to do was change that to hd1,0.  There's still something going on with this though. When I have my power cord plugged in (this is a laptop) it won't boot from the external drive.  It's not a big deal I just thought I'd share that.  It's actually kind of funny.

Could you post your vista entry from menu.lst?  Just curious.  

Maybe when you use the ac cord, it boots faster and it's not waiting long enough for the usb drive to spin up. Just a guess.  Do you have a Bios option for hard disk detect delay?  (My intel board does).  If so try enabling it, give more time for external

---

### Post by SkylineGT-R on 2008-01-08
Here's my Vista entry.  ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
chainloader	+1
```

And no, I don't have a BIOS option for that

---

### Post by logos34 on 2008-01-09
> **SkylineGT-R said:**
> Here's my Vista entry.  ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
chainloader	+1
```

And no, I don't have a BIOS option for that

I just don't get it--i.e. why windows is booting with that entry.  Will someone please explain this to me?  According to the Gnu Grub manual, you need to add mapping to effect a 'virtual swap'--windows won't boot if it thinks it's actually on the second boot disk.  So you have to trick it.  That's my experience.  Why are you able to boot windows on the internal from grub on the usb with no map switch?

Oh well, enough of that, if it works it works.  

(not sure what to suggest concerning the AC issue either)

---

