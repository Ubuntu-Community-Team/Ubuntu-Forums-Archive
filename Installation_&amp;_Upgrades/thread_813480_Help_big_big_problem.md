---
title: "Help big big problem"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by dcruwys on 2008-05-30
Well I told my friend he should download ubuntu, he did.

He says now that the windows part wont work because whenever he boots it tells him he needs a CD and wont let him choose Windows. 

I feel guilty and he says his dad is mad.

So what I need is.

A way to manually boot into windows and remove the ubuntu partion.

He also lost his Xp disk

---

### Post by Pumalite on 2008-05-30
Get Gparted Live CD to remove/resize the partition:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Get Super Grub to fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by lisati on 2008-05-30
It sounds like the installation of Ubuntu might have over-written Windows - this can happen when you choose the "Use full disk" option whan the installer asks about partitioning. Could this have happened?

A couple of possibilities for dealing with this come to mind, if you really need Windows back:

Some computers come with a recovery partition that let you repair or re-install Windows. On my desktop, it can be accessed by pressing "F10" on system startup.

My laptop came with a "Recovery DVD" instead of a recovery partition. This too can let me re-set my laptop to an "out of the box" state.

Have a look through the stuff that came with your computer - there might be something there that can help you.

Good luck!

---

### Post by ugm6hr on 2008-05-31
> A way to manually boot into windows and remove the ubuntu partion.

I think you would be better off getting your friend to post and read directly here.

Your post is unclear about:
1. Whether he actually installed Ubuntu (I am assuming yes)
2. How he installed Ubuntu (i.e. Wubi or full)
3. What options he selected during the install
4. What CD it is asking for
5. Exactly what his boot options are - i.e. did Grub install

Obviously, it would be easier for someone sat in fornt of the computer in question to fill in the blanks.

As a general rule, new installations of OS are not to be recommended to people who don't know what they are doing.

---

