---
title: "HELP: Can't Boot Into XP"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by kshsj777 on 2008-10-31
I'm selling my old computer to my mother, and she wants Windows, so I deleted all the partitions except for the windows drive, but now the screen is trying to boot GRUB and it can't find it.  But the only partition left is Windows.  Shouldn't it boot right into Windows?  

I have to fix this.  My mom does NOT want Ubuntu or any linux distro!!!  And I don't want to have to wipe the drive and reinstall windows b/c there are some codecs/games I lost the reinstallation password to, so they'll be wiped out.

PLEASE HELP!!!!!!

Thanks
777

---

### Post by Pumalite on 2008-10-31
Fix your Windows MBR with your Installation CD or Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Installation CD:
hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by BenAshton24 on 2008-10-31
Super grub is the best bet! you can download it from here [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
:popcorn:

hope this helps :D

---

### Post by kshsj777 on 2008-10-31
THANKS!!!  I'm going to download it and try it out.

---

### Post by kshsj777 on 2008-10-31
I still can't boot into Windows.  Supergrub got rid of GRUB, but now I get this message:

Windows could not start because of computer disk hardware configuration problem.  Could not read from selected boot disk.  Check boot path and disk hardware.

Any ideas?

Thanks
777

---

### Post by caljohnsmith on 2008-10-31
Never mind.

---

### Post by 73ckn797 on 2008-10-31
> **kshsj777 said:**
> I still can't boot into Windows.  Supergrub got rid of GRUB, but now I get this message:

Windows could not start because of computer disk hardware configuration problem.  Could not read from selected boot disk.  Check boot path and disk hardware.

Any ideas?

Thanks
777


Try this:

If for some reason you find the need to get back to your Windows XP bootloader instead of the one installed by your Linux distro, simply follow these instructions:

1.  Boot up with your Windows XP disc.

2.  Select the option Recovery Console.

3.  At the prompt, type "**fdisk /mbr**" (without the quotes of course)

4.  Restart your computer.

I assume you will be using XP.

---

### Post by kshsj777 on 2008-10-31
Thanks.  I know I have the cd somewhere, just not sure where it is at the present moment...

---

### Post by 73ckn797 on 2008-10-31
> **kshsj777 said:**
> Thanks.  I know I have the cd somewhere, just not sure where it is at the present moment...


I had to use the exact procedure last week on another computer.

---

### Post by kshsj777 on 2008-11-01
I can't find the reinstallation cd anywhere.  What's even worse is that I can't get the Ubuntu Live CD to boot anymore.  I was going to reinstall ubuntu on a small partition, hoped that would reinstall grub and let me boot into windows, and then I could change it so that Windows would boot first.  

But the live cd asks me my language and lets me click "Try Ubuntu" but then it just sits there and doesn't do anything!!!  Does this mean it's really screwed up if the live cd won't boot?

Is there any other way to fix it?
777

---

### Post by kshsj777 on 2008-11-01
Instead of clicking "Try Ubuntu" I clicked "Install ubuntu"  It installed it and now when I try to boot xp through grub it tells me what file I'm missing.

<Windows root>\system32\hall.dll

Is it possible to copy this file from another Windows installation?  And if so how could I reinstall it?  (I think this is what I deleted earlier when trying to get Windows to boot when GRUB was gone.)  I can use gparted to make an unallocated space, but I don't how I'd get the file there.

Update: Found a reinstallation cd from another computer, but now it's asking for a password in the recovery console.  I entered in my admin password, won't accept it.  *Sigh*

Thanks
777

---

