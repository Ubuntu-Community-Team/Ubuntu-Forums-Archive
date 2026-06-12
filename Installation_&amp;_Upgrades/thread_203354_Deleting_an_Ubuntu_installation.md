---
title: "Deleting an Ubuntu installation"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by medialdesign on 2006-06-25
Hi!  I want to install the new release of ubuntu on my other computer and completely remove the installation that is currently on my laptop, along with winXP.  If I just delete the ubuntu partitions and resize the windows one to use the whole space, will GRUB (wich is in the MBR) still be installed?  If yes, how to delete it after the partition operations?

thanks a lot in advance,

Blaise

P.S.: Sorry if this post is not at the good place!

---

### Post by Herman on 2006-06-25
Hello, Blaise, here's a link to a web-page with instructions for how to unistall Ubuntu [*click here*]("http://www.users.bigpond.net.au/hermanzone/p18.htm").
I hope that will be some help, Regards, Herman :D

---

### Post by ajgreeny on 2006-06-25
On the laptop with windows XP and ubuntu you will lose the grub along with ubuntu if you just delete the ubuntu partitions.  This is not a major problem if you have a full winXP install cd as you can run fixmbr from the recovery module of winxp to restore the original MBR.

If your laptop came with just a recovery cd, as many do, then you may have more of a problem, and even have to do a complete reinstall of XP.

Once you have winXP back you can go into the disk management (right click My Computer on the desktop) and increase the winXP partition size to use the whole space available.

---

### Post by medialdesign on 2006-06-26
[QUOTE=ajgreeny]
If your laptop came with just a recovery cd, as many do, then you may have more of a problem, and even have to do a complete reinstall of XP.
[/QUOTE]

I faced that problem, but when I read the page herman posted, I found that installing the GAG bootloader is a quick and nice solution to avoid reinstalling windows.  I took me about 5 minutes to install it, boot windows and delete the linux partitions with the disk management utility.

Thanks guys!

---

