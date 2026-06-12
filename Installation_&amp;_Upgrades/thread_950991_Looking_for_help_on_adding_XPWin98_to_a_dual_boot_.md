---
title: "Looking for help on adding XP/Win98 to a dual boot (making a triple boot)"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by BEND IT 7 on 2008-10-17
Hey.

I have an Acer Aspire 5610 laptop.  Vista Home Premium came default, and I added Ubuntu to make a dual boot.  I have a third partitioned drive, a FAT32, to make for easy file transfers.  I am very happy with Ubuntu and Vista looks nice and serves well for most stuff I have to do outside of Linux (which is narrowing down to few things as I learn more about Ubuntu).  However, multiplayer LAN gaming with some older Windows titles (such as my favorite game for LAN sessions: AOE 2 :)) just flat out doesn't work (note: I said multiplayer, not single player) in either OS (which is disappointing since I put in the money to buy Vista when I bought my laptop).  

So, here is what I would like to do:
install either Windows XP or Windows 98 (own the 98 disk but could find a friend with XP for me to use, to) to the third partition, while maintaining "bootability" for all of my OSes.  I would also like to point out that my laptop can NOT boot from a CD...I installed Ubuntu from a flash drive.  So, if anyone could please give me some tips on this, that would be great.  I don't even know if it's possible to install Windows without a disk and then go back into Ubuntu and reinstall Grub or whatever I would theoretically need to do, but if it is: GREAT.

Thanks!

---

### Post by StooJ on 2008-10-17
I was very doubtful, but turns out you would be able to after all.

Install XP, this will overwrite grub and the vista bootloader.

Repair your vista bootloader (instructions here: [http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm](http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm) )

Reinstall grub ( [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) )

I haven't installed XP on a vista machine personally so I can't vouch for the article.

And you still have the lack of CD drive problem. You might need to use a spare hard drive for that. [http://www.techspot.com/vb/topic14204.html](http://www.techspot.com/vb/topic14204.html) for more info.

Good luck

---

### Post by BEND IT 7 on 2008-10-17
Good advice.

Thank you very much for the reply.

However, I don't think I want to risk all of that on my system.  The margin for error is too great.  Although maybe worth it in the end, it would be very risky.

One last question: that tutorial says that you need a floppy disk.  My laptop can not boot off of a floppy disk...I didn't even think any laptops made within the last few years have floppy drives.  I know: it is dumb that a newer model of laptop can not boot off of either a CD or a floppy.  But, I still like it.  I have seen that Acer is less expensive but quite comparable to its competitors, generally speaking.

---

### Post by BEND IT 7 on 2008-10-17
Plus, the Win98 disk I own is a CD, not a floppy.  So, I think I might be out of luck unless you have another route (like somehow making a Windows bootable flash drive).

---

### Post by BEND IT 7 on 2008-10-21
(This maybe needed another thread, but I'll see...)

Okay...so, I think I can borrow an XP install CD, but I can't boot from a CD.  

Does anyone know of a way that definitely works to format a flash drive to boot the Windows XP installer?  Or boot and then let me run the XP install CD?  Thanks in advance.

---

