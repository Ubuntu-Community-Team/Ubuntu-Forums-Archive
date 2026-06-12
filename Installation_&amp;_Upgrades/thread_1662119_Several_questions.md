---
title: "Several questions"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by James828 on 2011-01-07
FIrstly, I'm trying to use the Live CD on my Toshiba Satellite L450-188 laptop, but when I click on *Try Ubuntu*, the loading wheel just spins and doesn't do anything :confused:

Secondly, my laptop came preinstalled with Windows 7 (which I want to keep). I've noticed I have three partitions on my HD, so which one do I need to resize? I understand that one partition must be for recovery files.

Here's what the the current system looks like:

```
Windows NTFS-3g 149.0 GB
System NTFS-3g 400.0 MB
Data NTFS-3g 148.7 GB
```

---

### Post by Quackers on 2011-01-07
Welcome to UF :-)
It would be good to see a screenshot of your Windows disk management screen, so that more definitive advice can be given regarding partition changing.
Have you checked the cd for errors? At the purple boot screen press the Esc key and you will get a screen with some options. One of those options is to check the cd for errors.

EDIT: Sorry, that should be during boot from the live cd/usb, after the initial black screen with white writing at the top (that mentions Peter Anvin) but before the purple screen, press the Esc key. A new screen will appear with options, but it may be obscured immediately by a choice of language screen (or it is on mine :-) ) press enter after selecting the language, then you can choose the option to check the cd for errors.

---

### Post by mikewhatever on 2011-01-07
It doesn't look like any of the partitions you posted is a recovery one. You might want to talk to Toshiba about that.

---

### Post by James828 on 2011-01-07
Thanks for replying. I've managed to get into the live CD finally :D

Here's a Windows disk management screenshot

---

### Post by Old_Grey_Wolf on 2011-01-07
The fact that the Live CD doesn't work suggests that you have a bad download of the iso or a bad CD. 

Those Toshiba Notebooks do not have a recovery partition. What mikewhatever suggested is a good idea; however, if you have a DVD/CD drive you can use Toshiba's utility to burn your own recovery DVD/CD.

If you decide you what to install Ubuntu, use Windows 7 Disk Manager to shrink the Windows partition. You can search within Windows 7 to find out how to do that.

Edit: if you are trying Ubuntu 10.10, be sure to find instructions for installing 10.10 and not an earlier version; such as, 10.04 or 9.10. The installer works differently.

---

### Post by James828 on 2011-01-07
> **mikewhatever said:**
> It doesn't look like any of the partitions you posted is a recovery one. You might want to talk to Toshiba about that.

> **Old_Gray_Wolf said:**
> The fact that the Live CD doesn't work suggests that you have a bad download of the iso or a bad CD. 

Those Toshiba Notebooks do not have a recovery partition. What mikewhatever suggested is a good idea; however, if you have a DVD/CD drive you can use Toshiba's utility to burn your own recovery DVD/CD.

If you decide you what to install Ubuntu, use Windows 7 Disk Manager to shrink the Windows partition. You can search within Windows 7 to find out how to do that.

Thank you both. I'll have a look into this.

---

### Post by Quackers on 2011-01-07
You could shrink either the C: or the D: partition using the disk management screen. The choice is yours.
I would recommend, however, that you defragment the partition you want to resize at least once, and preferrably twice before shrinking it.

To shrink a partition from the disk management window, right-click on it and select "shrink" then choose the amount of shrinkage required.
After shrinking you should reboot Windows once or twice to make sure it's happy :-). Windows can be very picky about these things.

---

### Post by Old_Grey_Wolf on 2011-01-07
> **James828 said:**
> Thank you both. I'll have a look into this.

Just in case you didn't see the edit to my post...

"Edit: if you are trying Ubuntu 10.10, be sure to find instructions for installing 10.10 and not an earlier version; such as, 10.04 or 9.10. The installer works differently."

---

### Post by Quackers on 2011-01-07
> **Old_Gray_Wolf said:**
> Just in case you didn't see the edit to my post...

"Edit: if you are trying Ubuntu 10.10, be sure to find instructions for installing 10.10 and not an earlier version; such as, 10.04 or 9.10. The installer works differently."

I definitely agree with that! I would recommend that you DON'T use the "install alongside" option in the 10.10 installer! It has a nasty habit of eating existing operating systems!
Select the "specify manually" option in the partitioning section, and create your own Ubuntu partitions from the unallocated space that shrinking your C: or D: partition will create.

---

### Post by James828 on 2011-01-08
Many thanks to everyone for your help. I've installed Ubuntu alongside Windows with absolutely no problems whatsoever. 

:popcorn:

---

