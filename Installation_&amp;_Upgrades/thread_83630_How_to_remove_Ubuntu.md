---
title: "How to remove Ubuntu?"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by 117 on 2005-10-29
Hi guys,

Don't worry, I'm not migrating away from Ubuntu, it's just that I was borrowing a PC for a while and using Ubuntu on that, now I gotta give it back (have my own PC now which i'm just gonna install 64bit Breezy on :) ), the person it belongs to doesn't want Ubuntu and would like me to get rid of it but leave the Windows XP install there. 

What's the best way to remove Breezy completely without removing the Windows install that's also there, and revert back to a single-boot Windows install?  (i'd really rather not have to reinstall Windows from scratch coz it's a complete pain, so any way around it will be much appreciated)

---

### Post by codejunkie on 2005-10-29
[quote=117]Hi guys,

Don't worry, I'm not migrating away from Ubuntu, it's just that I was borrowing a PC for a while and using Ubuntu on that, now I gotta give it back (have my own PC now which i'm just gonna install 64bit Breezy on :) ), the person it belongs to doesn't want Ubuntu and would like me to get rid of it but leave the Windows XP install there. 

What's the best way to remove Breezy completely without removing the Windows install that's also there, and revert back to a single-boot Windows install? (i'd really rather not have to reinstall Windows from scratch coz it's a complete pain, so any way around it will be much appreciated)[/quote] 
first restore the windows xp boot loader by booting from the windows xp cd when it boot's up choose recovery console, and when you get to the command prompt type fixmbr this will remove grub and replace it with the default windows bootloader, then you can use a tool like partition magic to delete the ubuntu partition and resize the windows xp ntfs partition to take up the whole harddrive. if you can't get access to partition magic just restore the windows boot loader and then boot into windows rightclick on the My Computer icon choose manage and then Disk managment from here you can delete the linux partitions and create a new ntfs partition with the free space.

---

### Post by MichaelM on 2005-10-29
I have a strange problem. My computer won't boot from the cd (but that's not the strange part). I followed instructions I found somewhere which said to remove unnecessary hardware until it works, so I removed what I thought was my PCMCIA card slot. It turned out that it was actually my hard drive. And... without the hard drive, it booted from the cd with no difficulty! The only problem is that even when I replace the hard drive, when I push 'R', it says that no hard drives were found. I tried taking it out, then replacing it the instant the CD starts booting, but I get the same error. What's going on? How can I repair the MBR?

P.S. I had already set the BIOS to boot from CD first.

P.P.S. I don't have a floppy drive, so that's not an option.

---

### Post by 117 on 2005-10-29
codejunkie - cheers for that, one other question tho:  will an XP Pro disc work for this on an XP Home install?  I've managed to lose the Home disc but have a Pro disc I can use if it'll work without fubaring anything?

---

### Post by codejunkie on 2005-10-29
[quote=117]codejunkie - cheers for that, one other question tho: will an XP Pro disc work for this on an XP Home install? I've managed to lose the Home disc but have a Pro disc I can use if it'll work without fubaring anything?[/quote]
yes the xp pro disc should work just fine, but with windows i've found that it's better to be safe than sorry so you might wan't to backup any important files before you try it.

---

### Post by Darrin on 2005-10-29
Will these steps work for removing Linspire? Dont know if it uses grub or not.

---

### Post by Plank117 on 2005-10-31
Heresy!

---

