---
title: "[SOLVED] Edgy Install without grub"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by rusty4r on 2007-02-10
I have two hard drives. The first has win98 and winxp. The second has Ubuntu 6.06, and Fedora Core 6.

Ubuntu's grub controls the boot. Which I like, so here is my question.

I want to install Edgy on a blank partition, but I don't want to start over with grub, I'd rather install it without grub, I think, and then just edit Dapper's grub llike I did for Fedora.

Is that possible? When I was woking out these problems to get Dapper and Fedora going neither ever "saw" the other one, so I must have reinstalled three or four times before I figured out how to edit grub. But, I don't remember any way to install Ubuntu without grub. Fedora did give me that choice, hence Ubuntu's grub controls the boot.

Any advice would be appreciated. Thanks, Rusty

---

### Post by confused57 on 2007-02-10
The easiest way for me has been to install grub to the root partition of any additional linux distros that I install and just add an entry to the current mbr, using chainloading, to boot the new install.
   For example, I have a computer with 2 hard drives that are dedicated to Linux only and I'm currently booting 10 distros...I use Dapper on hda1 as the "system" mbr grub that I boot all of the other OS.   Anytime I install or test another distro, I choose to install grub to the root partition of the new distro, then I add an entry to Dapper's mbr, e.g.:

title    New OS
rootnoverify (hd0,7)
chainloader +1

The desktop cd should allow you to select where to install grub, see reply #13 in this thread:
[http://www.ubuntuforums.org/showthread.php?t=342663&page=2](http://www.ubuntuforums.org/showthread.php?t=342663&page=2)

I have installed distros that automatically installed their grub to hd0, which I didn't like, but it was easy to restore my original mbr, install the new distro grub to it's root partition, add the chainload entry to my Dapper grub & I was good to go with the new install.

You can use the live cd to reinstall grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

So if your mbr gets overwritten, fire up the live cd...reinstall your original grub to the mbr(e.g. hd0) and install the new distro grub to it's root partition, e.g. (hd0,7).

See this guide for booting multiple OS:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by rusty4r on 2007-02-10
Thank you, very much. I bookmarked all three links, something I am realizing that you must do everytime you come across these great how-tos. Sometimes I've seen the page I need before and can't remember where I found it. Since installing my first distro about three weeks ago I've never read so much in my entire life, but I love it.

Thank you again for your help, this Linux stuff is so cool and fun to learn

---

### Post by confused57 on 2007-02-10
> **rusty4r said:**
> Thank you, very much. I bookmarked all three links, something I am realizing that you must do everytime you come across these great how-tos. Sometimes I've seen the page I need before and can't remember where I found it. Since installing my first distro about three weeks ago I've never read so much in my entire life, but I love it.

Thank you again for your help, this Linux stuff is so cool and fun to learn

I have a plethora of bookmarks, which can get rather cumbersome when I need to find what I'm searching for.

You might want to bookmark Herman's homepage:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

as well as, aysiu's excellent site:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

You might want to bookmark this:
[http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)

---

### Post by rusty4r on 2007-02-10
Yes those are great too. Didn't have that last one.

My problem is I'm always working on my Linux distros and reading about it at the same time on another PC. I've got several links on my laptop and my wife is complaining about all the links I have saved on her PC. I need to sync them all. But who wants to stop learning and take time for that.

Thanks again

---

