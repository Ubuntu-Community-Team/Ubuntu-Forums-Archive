---
title: "Tried new 6.06 install - Won't install - GRUB error 15"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by Optiker on 2006-06-25
Although I've been trying to get into Linux for some time, and have learned a lot, I am still very unskilled and very much a noob in the installation process, so in any replies, please reply as to a beginner - thanks.

After a fairly benign Kubuntu 6.06 installation on my work computer, I decided to try it on my home computer, replacing Breezy. I was using the manual partition method in the graphical installation process. The installation seemed to be going OK, until it got to the step after I chose the partition (existing Breezy and Linux swap partitions), and verified that the other partitions (Windows partitions) were not checked to reformat.

At that point, I got an error box that was titled something about uncorrected errors on my fat16 partition and to go back and correct them. I tried to proceed, but it wouldn't let me, so went back, but seemed to be into that same loop.

My partitions, from my Breezy installation, for reasons I don't understand, are set up with a separate Linux ext3 partition, then what looked like (can't get back in to verify) the swap partition set up within the Windows fat16 partition that is my data partition in Windows.

At that point, not knowing what or how to make the correction that was indicated but not specifically described, I chose to abort the installation and reboot.

On reboot, Just when GRUB loads, it hangs and gives me an "error 15" which I presume has to do with the GRUB loader having been corrupted in the aborted installation. Now I can't get back to Windows.

That's a disaster!

What do I do? I haven't tried, but assume I can still boot the 6.06 CD, so I can probably access my Windows data partition from there, and assume I can access my Windows C-drive (program drive) as well, but it's NTFS, so can't write to it.

I have seen posts where people have said they've lost their boot loader while trying to install, and replies said something about needing their Windows installation disk to get back to the Windows loader - is that what's happening? I hope not since I've not needed that disk in the several years since I bought the computer and will need to do some digging to even find it. If there's another answer, I'd sure appreciate it.

Thanks for any help you can give.

Optiker

---

### Post by Optiker on 2006-06-25
Close thread...resolved.

I did a search and found that GRUB error 15 looks fairly common in the 6.06 update. Among the previous threads, many with no replies, I found a link to a tutorial to restore GRUB when the MBR is corrupted and decided to try it ...

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

I'm either very naive and deluded, or very impressed because although it didn't respond as the tutorial, it did complete the installation - without formatting the two previous Linux partitions (OS and swap) and I am now replying using Konqueror from 6.06! Next operation will be to Adept install Firefox, and begin the process of correcting the inevitable glitches.

So, this can be one more thread referencing error 15.

Onward!   :) 

Optiker

---

