---
title: "overwriting grub"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by dhawk312 on 2006-10-16
how can i overwrite grub so that only MS based OSes will boot?  i am selling my laptop with the original factory settings installed but when i reinstalled the original OS using the recovery DVD it did not overwrite grub.

---

### Post by Kateikyoushi on 2006-10-16
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

---

### Post by dhawk312 on 2006-10-16
Can i use a Vista DVD to do this instead of xp?

---

### Post by bulldog on 2006-10-16
Don't think so,Vista uses another bootloader as XP.

---

### Post by dhawk312 on 2006-10-16
well i do not have an xp install cd/dvd, i only have the recovery dvd....is there any way to overwrite the bootloader without one? like from a livecd or on my linux partition? i dont care if i cant log back in to my linux partition bc i will erase the entire HD after i do this.

---

### Post by bulldog on 2006-10-16
You can download XP-install floppy's [6] from windows somewhere on that site.

Maybe you can use them,but I'm not sure.

---

### Post by dhawk312 on 2006-10-16
nope cant use floopies...no drive.

---

### Post by dhawk312 on 2006-10-16
can i just boot into xp home and use a ms-dos prompt to overwrite grub?

---

### Post by bulldog on 2006-10-16
Shouldn't know if that's possible,guess not actually.

You need a bootloader to overwrite GRUB,like there's one in Partition Magic if I remember correct.

But the simplest way is to get your hands on a XP-cd and use it.

---

### Post by dhawk312 on 2006-10-16
thanks for the advice. ill try to find one.

---

### Post by Kateikyoushi on 2006-10-16
Use the super grub disc. [LINK.]("http://adrian15.raulete.net/grub/tiki-list_file_gallery.php?galleryId=1")

---

### Post by confused57 on 2006-10-16
Here's a Super Grub Disk "howto":

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by dhawk312 on 2006-10-16
thanks for the howto link. it definitely looks like it could be a difficult program.

---

### Post by Herman on 2006-10-17
Heloo dhawk312,
[Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") is actually *very* *easy* to use and offers some of the simplest and fastest ways to do just about any job you can think of with bootloaders. 
If you can think of something that needs adding to it, or a way to make it easier, let me know and I'll pass your request on for consideration by the developer, adrian15, who is also a member of this web forum. 

In case that's not enough, you can also see a whole list of other ways to overwrite Grub's IPL in your MBR with Windows bootloader's IPL code, here in my 'Uninistall (Ubuntu) Page', choose one which suits you. [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
I have tested all those ways myself and they all work well for my Windows XP and 98SE and Ubuntu computers. 

I know nothing about Vista or its bootloader. If you want to find out about that, another website deals with Vista-Ubuntu Dual Boots,  here's the link for that, **[http://tinyurl.com/hrbhy](http://tinyurl.com/hrbhy), **They even have thier own web forums set up there, so head there for help with Vista-Ubuntu.

All the best, Regards, Herman :D

---

