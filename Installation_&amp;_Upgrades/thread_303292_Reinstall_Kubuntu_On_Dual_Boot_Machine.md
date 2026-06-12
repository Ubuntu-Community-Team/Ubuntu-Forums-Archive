---
title: "Reinstall Kubuntu On Dual Boot Machine"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by DougS on 2006-11-20
I have dual boot machine (new user, testing out Kubuntu, keeping Windows for the moment)

Somehow (probably me) Kubuntu won't log in. Password is fine, it just reverts back to login screen (display issue?)

In any case I want to simply reinstall Kubuntu as no real work done with this OS.

Can I just delete Linux partition using Live CD and reinstall?

Concern being that what will happen to Grub?
Will it simply be overwritten, another menu item appear or not be able to boot at all! (biggest concern as some time invested in setting up Windows partition)

I have practically no knowledge of sorting out Linux problems so need to have VERY simple way to sort this out without getting involved with detail of operating system until I can get more experience.

Thanks for any confirmation or otherwise.
Doug

---

### Post by DougS on 2006-11-20
This seems to help but confirmation would still be nice thanks...

[http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr](http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr)

And thank you Herman in anticipation...
Doug

---

### Post by kno712 on 2006-11-20
I want to do the same; any help, will be wellcome.

Thanks a lot.

---

### Post by tredegar on 2006-11-20
This is really easy: have courage & jump in!
Boot from your kubuntu disk to the live version.
Open a terminal and become root:
**sudo -i**
Then see what your partitions are:
**fdisk -l** * Edit: that's an "ell" in lower case, not a "one"*
Make a note of these!
Now delete all the linux ones with:
**fdisk /dev/hda** and then follow the menus
Write the changes to disk when you are sure.
Do not delete your windows partitions unless you really want to!
Close the terminal.

Now click the Install icon.
When you get to the partitioning bit let it "Use free disk space"

Grub will be reinstalled on the MBR, you'll still get an option to boot win.
That should be it.

---

### Post by bigken on 2006-11-20
just boot with the live disc at the partition edit select manual edit and delete your ext3 and swap partitions and click apply now you can create 
your own partitions with the free space

---

### Post by DougS on 2006-11-20
Thanks guys and especially HERMAN
fdisk /mbr got trid of grub allowed Widows to take over.

Live CD and QTParted delete partition (although a bit worryingly the 3 partitions still seems to be there but empty)

Reinstall Kububtu from live CD...BINGO.

Getting much more confident that I can handle the dual boot set up whatever.
Herman pages are REALLY good reading.
Doug

---

