---
title: "Lost, wondered if I took a wrong turn???"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by freepims on 2008-08-26
I am trying to install on an external drive or I am being lead to belive I already have the file on the external drive. If so how to get it to show up when I reboot. I am very new at this and hate to bother but I have run out of buttons to push.

**Here's a screen shot of what things look like.**
[http://www.MyEasyPics.com/is.php?i=465968&img=help.gif](http://www.MyEasyPics.com/is.php?i=465968&img=help.gif)



Sorry for being on the not so smart side but I would love to learn this systme and run it along with windows. 

Thanks

---

### Post by coffeecat on 2008-08-26
I'm a bit bewildered as to what you've already done, and what you're trying to do. Let's take the points one by one. I presume you're trying to install Ubuntu on an external drive and that you've downloaded the Ubuntu iso, correct? Which version of Ubuntu and which iso? You could post the iso filename - that will tell all.

> **freepims said:**
> I am trying to install on an external drive

Your screenshot shows that your external (E:) drive is formatted NTFS, which is a Microsoft filesystem. You can't boot Linux up from an NTFS filesystem on an external drive - well, not very easily. Can you provide a link to the method you are following? It's quite possible to install Ubuntu to an external drive and boot up from it, but it's not the usual way of doing it.

> **freepims said:**
> I am being lead to belive I already have the file on the external drive. If so how to get it to show up when I reboot.

Do you mean that you have the iso file on the external drive? What happens when you open a Windows explorer window for E:? What does it show?

You can't boot up from an iso file on a hard drive. The iso is meant to be burnt, as an image, to a CD. The CD is bootable. If you have the desktop iso, the CD can be run 'live', which means that you get a fully functional (but slow) Ubuntu OS and desktop running from the CD. You can also install Ubuntu to your internal drive with it.

**Edit:** or were you trying to do a Wubi install?

---

### Post by freepims on 2008-08-26
Maybe it would be best if I started from scratch. I downloaded this:  Ubuntu 8.04 LTS Desktop Edition 

And I have the iso file on a disk. Does it have to be partitioned in fat32, like I really know what that is all about. 

What do you think? I can tell you one thing, if I knew what I was doing it would be easy except it's just the opposite.

---

### Post by coffeecat on 2008-08-26
> **freepims said:**
> And I have the iso file on a disk. Does it have to be partitioned in fat32, like I really know what that is all about.

No, FAT32 is another Microsoft filesystem. You can use MS filesystems for data storage - Ubuntu will read and write to both FAT32 and NTFS - but for running Linux you need to use native Linux filesystems like ext3. But we're getting ahead of ourselves.

You have the Ubuntu desktop iso. Excellent. First thing is to burn that to CD. [Here is the Ubuntu BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto"). Once you've got that on disc, just try booting up with it. Don't forget to set your BIOS to boot up from the optical drive first. You don't have to install just yet. If you have wired ethernet to your computer you'll even get internet connection without having to do anything. Take time to explore the desktop. So long as you don't do anything unwise, it won't affect your internal hard disc.

Now [have a look at the Ubuntu Installation guide]("https://help.ubuntu.com/8.04/installation-guide/i386/index.html"). Take it easy. It's a lot to take in at one go. Now [have a look at this page]("https://help.ubuntu.com/community/Installation"), which offers you more options, including installing on an external hard drive.

When you've explored the live desktop a bit, and when you've had a chance to assimilate some of those guides, you'll know better what to do. Don't hesitate to ask here, and if you have trouble booting up from the CD, just ask. Someone will help.

By the way, what hardware have you got? How much RAM? What video card? That's just to make sure you aren't likely to encounter any of the most obvious hardware issue.

And above all, good luck!

---

