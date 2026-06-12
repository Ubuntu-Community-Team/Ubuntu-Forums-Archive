---
title: "Help accessing existing Ubuntu install"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by aeroRunner on 2006-02-18
I have a dual boot setup with WinXP and Ubuntu.  I had always heard to install Windows first, to make configuring the boot loader easier.  Well, my Windows install became corrupt and I am going to format that partition and reinstall.  Can anyone explain to me how I can boot into Ubuntu and/or reconfigure the boot loader after I have reinstalled Windows?  I hope there is a way to do this as I do  not want to have to reinstall Ubuntu again also.  Any helpful links would be appreciated.  I searched but couldn't really find any help on the subject, though I wasn't quite sure what to search for to answer the question.

Thanks in advance.

---

### Post by Herman on 2006-02-18
The official Ubuntu Wiki has the best documentation on that now.
It explains how to do it using the install CD, the live CD, or the Super Grub disk. [Here's the link for the right page]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows"), choose whichever method you prefer, and happy Windows re-installing! :-D (Herman)

---

### Post by aeroRunner on 2006-02-18
Thanks for the link, its exactly what I was looking for.  I tried recovering from the Ubuntu install CD but I ran into a problem.  I get to the last step which says:

 type $ grub-install /dev/hdaX where X is your Ubuntu root install.

I assumed that the X was the same as my partition number X from a couple steps before.  Apparently it's not, because I got some error that said something to the effect of the root install does not have a corresponding BIOS entry.  Can someone explain how I might be able to determine what my hdaX value might be?  Thanks.

---

### Post by Herman on 2006-02-18
Maybe try looking at all your partitions with any partitioning software and make a note of the correct partition number.
 Perhaps run a live CD like 'Breezy' live CD and look at it with GParted, or use GParted on a CD of its own, or QTParted on a Knoppix CD to see what your partition numbers are. 

You can also use the install CD and run through all the first steps as if installing until you get to 'manually edit the partition table'. You can select that for a look at your partition information and then choose <Go Back>, and in the Ubuntu Installer Main Menu, scroll down to 'abort the installation'. Ignore the warning about your install not being complete, because you will not be trying to do an install, just look at your partitition numbers. 

Or try out the Super Grub Disk. :D (Herman)

---

### Post by aeroRunner on 2006-02-19
I started a normal install like you suggested and remembered that I am sdaX not hdaX.  So I tried again this time with sda3.  And I got an error that said:

/boot/grub/stage1 not read correctly

Just for fun, I tried sda1-sda5 and they all said the same thing.  I guess I'll keeping trying tomorrow.  Thanks.

---

### Post by aeroRunner on 2006-02-19
Ok, after using a Live CD and taking a look at GParted, I now know for sure that my root install is located on /dev/sda3.  I also tried another approach to reinstall grub and I received the same error message.

/boot/grub/stage1 not read correctly

I think I am going to try the Linux Super Grub Disk now.

---

