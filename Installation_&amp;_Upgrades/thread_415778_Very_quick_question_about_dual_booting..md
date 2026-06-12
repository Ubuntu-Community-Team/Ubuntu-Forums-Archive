---
title: "Very quick question about dual booting."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Quillz on 2007-04-20
I've heard horror stories about trying to dual boot between Vista and Ubuntu. I was able to dual boot perfectly between XP and Ubuntu, though. So, I just want a very simple answer... Is dual booting between Vista and Ubuntu possible, as easy as it was with XP? And please, no Windows bashing here, I just want a "to the point" answer.

---

### Post by tomexx on 2007-04-20
Hi,
I just wrote my little tutorial on how I did it safely with XP. I know you're asking about Vista but because of the way I'm doing it it should work exactly the same. Here it is:

[http://ubuntuforums.org/showthread.php?t=414454]("http://ubuntuforums.org/showthread.php?t=414454")

---

### Post by Quillz on 2007-04-20
Well, if it's like XP, then I just install Ubuntu like normal. I know how to do that, I'm more concerned if GRUB will still allow Vista to boot. I've never tried it, but some have said it doesn't always boot.

---

### Post by tomexx on 2007-04-20
I guess you didn't follow my link... Anyway it should work with any operating systems as I'm using two hard drives and a BIOS  boot menu (no Gurb or any other boot loader, so you can't screw up your windows MBR)

Safe and it will work providing your motherboard has a boot menu. Most newer ones do.

---

### Post by Quillz on 2007-04-20
Okay, I was busy, so I didn't get a chance to read your article yet. Will do now. Thanks for the help.

---

### Post by Quillz on 2007-04-20
The only problem is that this is on a laptop, with only one internal hard drive.

---

### Post by tomexx on 2007-04-20
Yeah you're right unless you connected an external USB drive but then there's probably a better way.
Keep looking

---

### Post by Madmoose on 2007-04-20
Just a note:

I've tried to do a vista/ Ubuntu boot, but it didn't work. Ubuntu was fine, but it messed up vista where it wouldn't load. I ended up having to fix the windows MBR, and delete my linux partition completely to get it working again. 

If you find an answer PM me! :lolflag:

---

### Post by Madmoose on 2007-04-20
Quillz, 

I came across this post this morning. I think it will help both of us. 

[http://ubuntuforums.org/showthread.php?p=2494979&posted=1#post2494979](http://ubuntuforums.org/showthread.php?p=2494979&posted=1#post2494979)

Moose.

---

### Post by Quillz on 2007-04-20
> **Madmoose said:**
> Quillz, 

I came across this post this morning. I think it will help both of us. 

[http://ubuntuforums.org/showthread.php?p=2494979&posted=1#post2494979](http://ubuntuforums.org/showthread.php?p=2494979&posted=1#post2494979)

Moose.
That sounds like that should do it. So I still install Ubuntu the same way as always, the only difference I have to have the new partition in place before the install, whereas normally I let Ubuntu create it.

---

### Post by az on 2007-04-20
> **Quillz said:**
> I've heard horror stories about trying to dual boot between Vista and Ubuntu. I was able to dual boot perfectly between XP and Ubuntu, though. So, I just want a very simple answer... Is dual booting between Vista and Ubuntu possible, as easy as it was with XP? And please, no Windows bashing here, I just want a "to the point" answer.

That's exactly why I started this poll:  To find out if there is a bug or two to be filed.

[http://ubuntuforums.org/showthread.php?t=415349](http://ubuntuforums.org/showthread.php?t=415349)

There seems to be two differnt problems, here.  The first is partitioning, which basically destroys the Vista partition.  That seems to be fixed,  The other is with the bootloader configuration.

> **Quillz said:**
> That sounds like that should do it. So I still install Ubuntu the same way as always, the only difference I have to have the new partition in place before the install, whereas normally I let Ubuntu create it.

Your problem is with the bootloader, not the partitionner.

Maybe this helps?

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

