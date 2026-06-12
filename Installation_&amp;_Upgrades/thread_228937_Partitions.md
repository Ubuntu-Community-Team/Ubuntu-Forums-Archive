---
title: "Partitions"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by elevate on 2006-08-03
I'm sure there are plenty of questions regarding this but all I'm aksing for is if my plan sounds correct!

I have experience in Linux through terminals as well as Mandrake KDE although these have been on computers where it is the only OS. 
I need to dual boot Windows/ Ubunto so I can use Visual Studio.NET while I evaluate momo. 

I plan for install is: 

Create NTFS partition and install XP

Install Ubuntu on same HD with partitions for root and swap (ex3 for both?)

Then I would like to format a second HD in ex3 for sharing files between windows and ubuntu. This will be mounted as my /home. 

Or would I be better to have /home on the ubuntu HD and simply make the second HD public access for all files?

Does this sound like the best way to have both OS's installed and share data between the two?

With the ex2 driver for XP that can read ex3 installed, if I try to access a folder in the /home directory will I be prompted for a password? 

Finally, once I am familiar with momo and decide I can run ubuntu on its own, I can delete the XP partition and redistribute space to root as well as the possibility of creating new partitions for /usr and /var.

All up does this sound like a good way to go?

Thanks for any help/suggestions :)

---

### Post by H.E. Pennypacker on 2006-08-03
> Or would I be better to have /home on the ubuntu HD and simply make the second HD public access for all files?

I would advice against having / and /home on seperate harddrives.  Intead, have Windows on a seperate harddrive.  You could be saving yourself a lot of time and trouble.  Make sure to remember to place / and /home on seperate partitions.

> With the ex2 driver for XP that can read ex3 installed, if I try to access a folder in the /home directory will I be prompted for a password?

No.

By the way, I believe you mean Mono, not Momo.  I don't know what Momo is.

---

### Post by elevate on 2006-08-03
Thanks, Mono is what I meant :) I think I'll go for what you suggested and have the shared parition an ex2 filesystem on the same drive as the windows install, that way when/ if I no longer require Windows I can redistribute free space over the single drive.

---

### Post by H.E. Pennypacker on 2006-08-03
> **elevate said:**
> Thanks, Mono is what I meant :) I think I'll go for what you suggested and have the shared parition an ex2 filesystem on the same drive as the windows install, that way when/ if I no longer require Windows I can redistribute free space over the single drive.

Use ext3, not ext2.  The Windows "plug-in" you're talking about has support for ext3 as well.   Check out its homepage.  It definitely supports read/write ext3.

---

