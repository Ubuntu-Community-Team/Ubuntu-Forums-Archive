---
title: "[SOLVED] ubiquity fakeraid installation support in 8.10 ?"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by brazzmonkey on 2008-10-03
hello there,

lately i gave a shot to openSUSE because i was in the need of a massive cleanup. so i installed openSUSE KDE4 64-bit edition. good thing is that i was able to install it on an intel matrix fakeraid setup (/ is stripped, /home is mirrored).

there are a few thing i like in openSUSE. but there are many more i dislike. overall it hasn't been a good out-of-the-box experience and i'm looking forward to installing ubuntu again on my laptop.

so my question is : will it be as easy as 1-2-3 for me to install kubuntu 8.10 64-bit on my fakeraid array ?? i know this feature has been announced for a while, and it's marked as confirmed on launchpad, but i don't know if it will eventually be implemented on intrepid ibex.

if so, is it already available in the recent intrepid beta ??

thx

---

### Post by Sef on 2008-10-03
moved to ibex forum.

---

### Post by brazzmonkey on 2008-10-03
wooops, sorry for having posted in the wrong forums. i didn't know about this category, though.

still, anyone knows the answer to my question ??

---

### Post by brazzmonkey on 2008-10-05
*bump*

---

### Post by brazzmonkey on 2008-10-06
am i the only one who wants to install ubuntu on fakeraid ??

---

### Post by chrisccoulson on 2008-10-06
FakeRAID is now fully supported out of the box on the Intrepid Beta Alternate CD. There is no support on the live CD.

Note there is currently a problem with dmraid not depending on dmsetup, which means that the installed system may not work properly until this package is installed. This will be fixed very soon though.

---

### Post by brazzmonkey on 2008-10-06
ok, thanks.

is there a workaround to this dmraid/dmsetup issue ? a bug entry to check whether this has been fixed ?

---

### Post by chrisccoulson on 2008-10-06
The workaround is to install dmsetup. The bug report is [https://bugs.edge.launchpad.net/ubuntu/+source/dmraid/+bug/278052]("https://bugs.edge.launchpad.net/ubuntu/+source/dmraid/+bug/278052")

---

### Post by brazzmonkey on 2008-10-06
thanks again, chris.

there's something i don't understand, though: how do i install a specific package during ubuntu installation?
if there no such way, does this mean i have to let the installation fail, reboot on cd-rom and manually install dmsetup thereafter (chroot needed?)?

---

### Post by chrisccoulson on 2008-10-06
The installed system will still boot and the root filesystem will still mount as it is identified by device node in your /boot/grub/menu.lst. However, any other filesystems specfied in your /etc/fstab will fail to mount. In my case, the system booted in to a state sufficient to modify my /etc/fstab to remove the UUID's and replace them with device nodes. I could then mount all of my filesystems, install dmsetup, then restore my original fstab with UUID's in it.

---

### Post by brazzmonkey on 2008-10-06
ok then. that sounds a bit risky to me&#8230;
actually i hesitate to give the alternate beta cd a shot, or use beta livecd and follow a step-by-step guide such as this one : [http://hol.net.nz/blog/kubuntu-with-fakeraid](http://hol.net.nz/blog/kubuntu-with-fakeraid) (which in my opinion is much simpler than the fakeraid article on ubuntu's wiki).

---

### Post by brazzmonkey on 2008-10-07
eventually i got it installed with the livecd, following the guide i mention in my previous post.

---

