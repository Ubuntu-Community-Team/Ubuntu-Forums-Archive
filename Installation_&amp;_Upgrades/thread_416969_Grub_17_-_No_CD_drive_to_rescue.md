---
title: "Grub 17 - No CD drive to rescue"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by powpow on 2007-04-21
Hi, Just want to confirm that I'm hosed...

Long story short, I have a Grub error 17, and I don't have a CD drive on this laptop (IX250).  I installed ubuntu a while ago using [this HOWTO]("http://ubuntuforums.org/showthread.php?t=28948").

At startup, I just get the grub error and don't know how to get past it/out of it.  I've searched quite a bit and I think I'm in trouble.  I guess I'll need to get a CD drive to rescue this thing (so I can boot from CD)?  **Is there a way to exit from Grub**?




Here's the gory details:
I was planning to install an "alternate" version to see if it ran a little faster.  I made a new partition in Windows with Partition magic.  Then I copied the boot and grub folders from C: into the new partition, along with the alternate iso.  If I had to guess, I'd say it wasn't wise to just copy the folder(s), and I should have reinstalled Grub on the C drive?  Also, maybe it's bad to have two boot folders with Grub on 2 partitions?

BIOS won't boot from USB, and I don't have a floppy drive either -- don't know if I can even connect one.  However, that brings up a question -- are there other ways to trick BIOS into booting for me if it's impossible to exit from Grub?  Would an external/USB CD drive be recognized?  Can you make a USB appear to be a floppy, similar to [this strategy]("http://www.pendrivelinux.com/2007/02/20/booting-linux-from-usb-zip-on-older-systems/#more-180")?

Anyway, what do you suppose I should do?  I guess I could use a CD drive anyway, but they're hard to find for this laptop and a bit spendy... 

Thank you!

---

### Post by bulldog on 2007-04-21
Well you have a little time to spare I suppose :) 
When you highlight the line in grub to boot ubuntu,you can hit the 'e' key to alter the line [just read the screen]
It all depends on how  many partitions you had before you created some more,and if you can remember on which partition your ubuntu was before you altered the system.

Edit the boot partition by changing the partition (hd0,1) (hd0,2) and so on,and try to boot by every change you make,
Finally you should find the right one:)  note it down and if you are in ubuntu,modify the menu.lst and the fstab to make it permanent.

---

### Post by powpow on 2007-04-21
Thanks for the reply Bulldog.

I'm not sure how to even stop GRUB from going too far...

When my computer starts up, the screen shows it loading BIOS, Searching for Boot on Floppy..none, Searching for Boot on IDE-0...OK, then it goes straight to GRUB Loading stage1.5.

I was hitting "e" really fast during all this (just hoping, you know) but it went on to GRUB loading, please wait...  Error 17.

Any thoughts on what I'm missing?

Thanks again.

EDITED:  In other words, I don't even get the menu to highlight anything -- it gets stuck before that.

---

### Post by bulldog on 2007-04-21
Hmmm,by default grub would stop booting for ten seconds,so you have the time to choose the kernel you want to boot.
This gives you the opportunity to alter the boot options.
If you altered that line and set it to 0 seconds, well we've got a problem.

You should know,if you make some extra partitions the naming is changed and grub will give an error 17 instead.
To boot into ubuntu it's essential to change your boot partition to the right one.
When you see grub loading stage 1.5,you're to far already.
The line I refer to is before it begins booting.
It will list all the kernels installed and the recovery mode and all that
Use the arrow keys to stop grub and than choose the right kernel and hit the 'e'

---

### Post by powpow on 2007-04-21
Thanks again, I don't think I changed the line, but you're right that it should give me some time/options...

This reminds me that I also tried WUBI (but it didn't work or something), and that may have messed with the boot procedure.  If I recall, the last time I got this computer working it was like I was in GRUB twice:  I'd choose to not run Windows (don't remember what the choice was) and then it'd give me that grub menu you're talking about.  Then I'd choose to run ubuntu somehow.

Don't know if that helps or not...

So probably the only way out of this is to make it boot from a CD I'm guessing?

---

### Post by powpow on 2007-04-29
This thread is continued..... [here]("http://ubuntuforums.org/showthread.php?p=2558817#post2558817")

---

