---
title: "help with Ubuntu and windows boot loader"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by alias.tdp on 2010-06-16
Okay, I've been trying to install Ubuntu 10.04 LTS alingside my Windows 7 installation using the windows boot loader instead of GRUB, but have had no luck. After reading up on numerous tutorials I have decided that I must install GRUB on the linux partition and then use EasyBCD to insert that into the Windows boot loader, but when I get to the last step of the installation, on the live CD, and try to install GRUB to the linux partition (dev/sda5) the okay button is greyed out and I cant do it. So now I'm at a loss and I have no idea what to do next.
 
one more thing, Ubuntu sems to skip drives, windows is sda1 and linux is sda5 It just skips 2,3 and 4, is this supposed to happen?:confused:

---

### Post by darkod on 2010-06-16
Is it a problem to use grub2 as bootloader?

---

### Post by oldfred on 2010-06-16
I agree with Darko, what is the advantage of adding a third party boot loader that is beta and requires you to install grub2 to a partition which is not recommended by grub.

Partitions are primary numbered 1 thru 4. You can convert one primary to extended and it will hold any number of logical partitions starting at sda5. You just have not used sda3 & 4. sda2 is then probably the extended partition which is only used as a container for all the logical partitions.

---

### Post by alias.tdp on 2010-06-16
Well I originally started out with windows and perfer the windows bootloader better. I dont plan to use ubuntu as a primary OS so I want the pc boot into windows by default
 
thanks for the clarification on the drive numbers, but does anyone know why I cant install grub to the linux partition?

---

### Post by darkod on 2010-06-16
Grub2 allows you to have any OS you select as default OS that will boot if you don't press a key. It doesn't have to be ubuntu.

It's not a question of preference but more of a practicality. You insist using a bootloader that MS doesn't want to design so that it can recognize and boot other OSs. Grub2 can do that without this fuss you are creating for yourself.

I don't know why you can't install it to a partition during the install. In 9.10 you could. Maybe the option was removed in 10.04 because it's not recommended to be installed on a partition and it affects the performance/stability.

---

### Post by alias.tdp on 2010-06-16
yeah, I see your point I guess I'll just use grub after all.
Thanks for your time and support I appreciate it

---

### Post by oldefoxx on 2010-06-16
A few things that may help.  The initial configuration for hard drives allowed no more than four partitions.  As drives got bigger, someone came up with the notion of making the fourth one an extended drive, then letting you create logical partitions inside the extended partitions.  Thus, if you have an extended partition, is is automatically designated number 4, and logical partitions begin an 5 and go from there.  In general. you need at least one primary partition in front of the extended one, which serves as primary/boot/active.  You can have two more primary partitions of course, and they may also be designated as boot, depending on whether an OS is installed there or not.

Grub 1, which is used before Ubuntu 10.04, allows you to make changes in the boot process and order by editing /boot/grub/menu.lst.  At the bottom of menu.lst, each Title designatess a separate boot process, with the most recently added at the top.  There are a number of neat tricks that can be done to the contents of menu.lst.  A few are noted there, and others can be read online.

I've no real experience with Grub 2, which is what 10.04 uses, but from my experience the two approaches to grub do not coincide with each other, meaning one or the other must go.  Seems grub 2 is the future, and so far is seems the more difficult of the two.  But we don't call the shots.  All that grub 1 needed was a decent tool to manage it, and I could write one in my sleep, but why bother if it is going away.

That brings up the Windows Boot loader, which depends on two things being present on drive C:  The first is ntoskrnl.exe, because it acts as a boot loader for cases like this.  The second thing is a text file, that like menu.lst, gives the user a number of boot options.  This file is named boot.ini, and it is normally not seen because it is flagged as hidden, may be flagged system, and always flagged read only.  You have to change the flags with ATTRIB in order to edit it.

The Windows approach is not as elaborate as grub, but simple is sometimes seen as better.  What you first have to do when installing Ubuntu is tell it to create a boot process, but make sure it is not on Windows' Drive C:  If on drive C, it will replace the Windows' method completely.  Now Grub is smart enough to leave you with a way to get to Windows. but it is different.  By putting the drive to something besides drive C, you leave the Windows' approach intact.  And if you put the Grub on the same partition with the /, you can have both Grub 1 and Grub 2 intersperced on the same system.

But now you can only boot to Windows still.  How to fix this?  Simple enough.  Get a decent boot manager that can help you deal with it.  One that I liked, it being free and all. is one named BOOTPART.  You can find it on the Internet.  It is very terse, instruction-wize, so you may have to play with it for a bit to get it right.  One real nice thing about it is that is has no problem flagging which partitions are bootable.  The only broblem might be understanding the need for a binary file, which it will make, that effectively transports that patition's boot method to coincide on the C drive along with Windows.
It is a small file, and you get to pick the name for it.  With both Grub 1 and Grub 2 present somewhere, it will likely make two binary files, one for each.

Oh, about Menu.lst.  I just noted that Grub may see hard drive order differently, but it gives its order in a file named device.map.  Because of this, what you think of as (hd0) may be (hd1) to Grub, and vice versa.  Not usually a problem, except with entries for root.  This would tell Grub to only check one drive, and if the UUID does not match that partition's, it bombs.  You can edit the boot process and see of changing (hd0,1) to (hd1,1) lets it boot up okay, and if so, just edit /moot/grub/menu.lst and make the change permanent.  Now in my menu.lst's history of entries, I find a number that do without the root designation, and these not only boot up just fine, but return the login screen to where you type in both the userid and password.  That I find really interesting, that you can make minor changes in menu.lst and have such a pronounced effect.  Hope this has been of some help.

---

### Post by alias.tdp on 2010-06-25
thanks for the reply, I acualy got it to work with Windows:guitar:

---

