---
title: "Computer won't boot after external drive install...please help!"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by alan_daniel on 2007-12-27
Ok, this is the third time I have installed to an external hard drive and the first time it has gone wrong. I followed the guide that I'm sure others know about, the "SUCCESS - Breezy loaded on external hard drive" but modified it via some posts in it to make it more current.

Everything installed fine, but when it came time to install Grub, out of confusion, I accidentally installed it to the main computer's MBR. This is a problem, because I only have Windows XP on the computer's internal hard drive. My linux install is only on my external, and I wanted to install to the external hard drive's MBR, not the internal. So now my computer won't boot.

First of all, when the external hard drive is NOT connected to the computer, I get an error code: "Error 21." I do not get a listing of my boot choices.

When the external hard drive IS connected to the computer, I get an error code: "Error 17." Again, I do not get a listing of my boot choices.

I have tried changing around some /boot/grub/menu.lst choices, but I haven't found anything that has worked. Please help me fix this!

A perfect solution to me would be to replace the internal hard drive's MBR with the XP loader and move the Grub loader to the external hard drive's MBR. Thanks for any help!

---

### Post by chewearn on 2007-12-27
> **alan_daniel said:**
> Ok, this is the third time I have installed to an external hard drive and the first time it has gone wrong. I followed the guide that I'm sure others know about, the "SUCCESS - Breezy loaded on external hard drive" but modified it via some posts in it to make it more current.

Everything installed fine, but when it came time to install Grub, out of confusion, I accidentally installed it to the main computer's MBR. This is a problem, because I only have Windows XP on the computer's internal hard drive. My linux install is only on my external, and I wanted to install to the external hard drive's MBR, not the internal. So now my computer won't boot.

First of all, when the external hard drive is NOT connected to the computer, I get an error code: "Error 21." I do not get a listing of my boot choices.

When the external hard drive IS connected to the computer, I get an error code: "Error 17." Again, I do not get a listing of my boot choices.

I have tried changing around some /boot/grub/menu.lst choices, but I haven't found anything that has worked. Please help me fix this!

A perfect solution to me would be to replace the internal hard drive's MBR with the XP loader and move the Grub loader to the external hard drive's MBR. Thanks for any help!

You can put back the XP bootloader by fixmbr
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

---

### Post by alan_daniel on 2007-12-27
> **AstalaVista said:**
> You can put back the XP bootloader by fixmbr
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

ok, thanks for that. Any idea about how to move Grub back to the external hard drive?

---

### Post by chewearn on 2007-12-27
Modify from instruction given here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the post here so you understand what's going on.

Then:
1. boot into ubuntu
2. sudo grub
3. find /boot/grub/stage1
4. root (hd?,?)
5. setup (hd?)
6. quit

In you case, you need to figure out what is the correct root(hd?,?) and setup (hd?) to use.

---

