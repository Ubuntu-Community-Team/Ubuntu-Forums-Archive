---
title: "Uninstall Ubuntu, Go Back to WIndows"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by EvyBear on 2013-02-26
Hi everyone, I would like to know how to know how to uninstall Ubuntu and go back to Windows. Ubuntu is very frustrating to me, and I had to get it in the first place because something corrupted my windows OS.I don't think I'll ever get used Ubuntu due to the complications for a non-Tech Savvy person. :confused::( Thanks for your help.

---

### Post by BarfBag on 2013-02-26
What kinds of issues are you having with Ubuntu?  We might be able to help find solutions for you.

In regard to returning to Windows, did you dual boot the system when you installed Ubuntu?  Or, did you erase Windows from the hard drive altogether?

---

### Post by EvyBear on 2013-02-26
> **BarfBag said:**
> What kinds of issues are you having with Ubuntu?  We might be able to help find solutions for you.

In regard to returning to Windows, did you dual boot the system when you installed Ubuntu?  Or, did you erase Windows from the hard drive altogether?


I was having problems connecting to my Xfintiy Wifi. [http://ubuntuforums.org/showthread.php?t=2116776](http://ubuntuforums.org/showthread.php?t=2116776)

I believe my Computer Teacher erased windows completely. He was telling me how awesome Ubuntu is, and it was awesome for a couple of days.

---

### Post by BarfBag on 2013-02-26
> **EvyBear said:**
> I was having problems connecting to my Xfintiy Wifi. [http://ubuntuforums.org/showthread.php?t=2116776](http://ubuntuforums.org/showthread.php?t=2116776)

I believe my Computer Teacher erased windows completely. He was telling me how awesome Ubuntu is, and it was awesome for a couple of days.

I replied with a possible solution in that thread.  Please report the results there.

If Windows was completely erased, you will need either your original boot disc, or a recovery partition.  If you have neither, you will need to purchase a new copy of Windows and install it by booting off the disc.

---

### Post by westie457 on 2013-02-26
A plan to get you back to Windows.

1 Make a backup of your personal files (Windows and Ubuntu) in case something goes wrong.

2 If not already done, make a Windows recovery CD (if you have mislaid your Windows DVD)

3 Make a backup of your Windows installation (see above)

4 Boot a Ubuntu LiveCD/USB in try mode open 'Gparted' and delete the Ubuntu partitions including Swap, you might have to unmount  Swap first. Leave the space blank for now. More on this later.

5 Boot using the Windows recovery CD or install DVD, Take the option to 'Repair your computer'. If possible cancel the 'Automatic Repair' **it will not work**.

6 Drop to the Windows Command Line (Dosprompt)

7 Run these three commands - bootrec.exe /fixboot
                             bootrec.exe /fixmbr
                             bootrec.exe /rebuildbcd
8 Close the window and click 'Restart' 


Windows should now boot without problems.

Now go to 'Disc Management' > Storage to see your hard drives.

Right-click on the area next to the empty space and select resize, in the pop up window adjust the number to the maximum size. Wait for this to finish.

You are now back to Windows with no Ubuntu.


Good luck.

---

### Post by Mark Phelps on 2013-02-27
> **EvyBear said:**
> ... I believe my Computer Teacher erased windows completely...

If this is true, then barfbag is correct -- you will have to go out and acquire Windows in order to reinstall it.

One way to check on this is to open at terminal, enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your PC and we can then see if there are any Windows filesystems or a Recovery partition still there.

---

