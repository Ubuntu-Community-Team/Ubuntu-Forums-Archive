---
title: "Dual Booting help! (Ubuntu noob kinda)"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by Patrick793 on 2007-08-15
Hello! I'm new to Ubuntu. I've familiarized myself with the User Interface, and like it. The thing is, I'm using the Live CD. I would like to install it. Here's a problem. My laptop is broken, and won't be fixed, (to old), and the only other computer is the family computer. I would like to dual boot my already installed OS (Windows Vista) and Ubuntu. But, I've read that doing so will remove the boot splash images. So, I would like some help on installing Ubuntu to dual boot, while keeping Windows Vista and the boot splash screens.

Thanks!
-Patrick

[SIZE="1"]Posted with an ubuntu live cd! woot[/SIZE]

---

### Post by flatwombat on 2007-08-15
Got to tell you that I sense you might be doing this behind the back of the family.  Hope you really aren't planning that, since it's one great way to get people ticked at you. 

Anyway, let's say that you have discussed this with the family and gotten permission to install Ubuntu.  First things first, make sure you back up everything since there's always the chance that you'll make a mistake and lose your data (you can read that as "completely destroy Vista!") .  Now, normally you'd allow Ubuntu to partition your drive and overwrite the mbr (master boot record) with Grub.  That will allow you to boot into either Vista or Ubuntu...but it will look a bit different to the rest of the family.  You want to avoid that.  

Unfortunately, you're up against a couple of things.  First of all, Vista is apparently not too easy to configure for dual-booting.  Second, Ubuntu is not one of the distros that easily allows you to install Grub on the root (/) partition instead of the mbr.  You will have to become quite advanced to make this work well that way, so I REALLY hope you have backed up your data before attempting it.

What I'd do is another alternative; a second hard drive, just for Ubuntu.  Here's the benefits: 1). Ubuntu doesn't take much space so even a recycled drive or a cheap new drive will be fine for the project.  2). Since you'll be installing it on a different drive, you won't risk damaging your Vista data.  3). Your family's Vista will boot completely normally, ignoring Ubuntu.  4). Even if you decide you don't like Ubuntu (or other linux distros) down the line, you'll still have extra drive space for Vista.

So, here's what I propose:  Buy or salvage a drive and explain to the family what you're going to do.  Open the case and disconnect the existing Vista drive and plug in the Ubuntu drive.  Remember that if you've got IDE drives, you're going to set the Ubuntu drive to "single" or "cable-select".  Next, go into the BIOS and make sure that the drive is recognized and then change the boot sequence to have your CD-RW or DVD-RW boot before the hard drive so you'll be able to install Ubuntu from the CD or DVD.  Then, install Ubuntu and use the standard install so that it will put Grub on the Ubuntu drive's mbr.  You now have TWO mbrs; one for each OS.  Finally, reset the Ubuntu drive to "slave" (if IDE) and the Vista drive to "master" (if IDE) and then go into the BIOS and make sure both drives are recognized. 

So, for family use, leave the BIOS booting Vista as the primary boot device, however if you want to boot Ubuntu, then simply enter the BIOS and switch the boot order to the Ubuntu drive.  Just remember to switch it back when you're done.

This is not exactly what you wanted, but I think you'll find it a very good solution anyway.

---

### Post by logos34 on 2007-08-15
If it has a floppy drive, send grub to a floppy diskette during install (at the 'Ready to Install' screen, click on the 'Advanced' button lower right and replace '(hd0)' with **(fd0)**.  What could be easier?

---

### Post by Patrick793 on 2007-08-15
Okay. I think I know what to do. I'm only 13. And other than me, my sister uses the computer. I made sure it was okay with her. My parents don't go on. By dad used to, but that was when he was looking for a better job. So, it's okay if I install Ubuntu.

Anyway, I found something called [Wubi]("http://wubi-installer.org/"). Do you think this would be good for installing Ubuntu?
What do you think?

---

### Post by logos34 on 2007-08-15
Thirteen years old?  You sound more mature.  

Sure, Wubi will probably work just fine.  One thing to consider, though: it will run a little slower because it mounts as a loopback filesystem from a folder within windows.  But you can always change that later by converting it to a permanent installation on a separate partition.

---

### Post by Patrick793 on 2007-08-16
> **logos34 said:**
> Thirteen years old?  You sound more mature.  

Sure, Wubi will probably work just fine.  One thing to consider, though: it will run a little slower because it mounts as a loopback filesystem from a folder within windows.  But you can always change that later by converting it to a permanent installation on a separate partition.

Well, Ive installed Ubuntu using Wubi, and its working like a charm! Other than some symbols, the at symbol comes out as "
lol
Anyway, other than that Its fine. Thanks for the help!

---

