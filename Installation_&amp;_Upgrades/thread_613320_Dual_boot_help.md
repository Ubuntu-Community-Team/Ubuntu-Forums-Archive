---
title: "Dual boot help"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by cpan on 2007-11-14
Hello everyone!  I am very excited to be installing Ubuntu on my laptop but I have a few questions.  I have done some research but I'd like to make this new thread in case I'm missing something that you can answer.

I'm going to dual boot but I would like to be able to read and write to my windows partition and vice versa.  I've heard that I should make a fat32 partition for this?  Are there any other ways to do this?

I want to use GParted as I feel that the premade options during install are not what I want and the manual partitioner is a little too advanced for me., does anyone have a link to a tutorial for partitioning my drive the right way with GParted?

I think that pretty much covers it.  Thanks in advance!

--
cpan

---

### Post by shad0w_walker on 2007-11-14
If you are installing the latest Ubuntu (7.10) then reading and writing to the Windows partition should be auto configured during the install.

You will need a seperate program/driver for windows as it only supports it's own filesystems. This should help you with that:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by cpan on 2007-11-14
Gah I forgot to include that.  I'm installing 7.04 and upgrading to 7.10 after the install.  Does 7.04 have read/write auto configured?  Many thanks for the link, that will help tremendously.

---

### Post by Saint Angeles on 2007-11-14
howdy!

you'll wanna have windows installed first because if you install windows after ubuntu, it will erase grub (your bootloader).

install windows on the whole thing, then when you install ubuntu, it will give you the option to resize the windows partition and use the available space for ubuntu.

hope that helps!

---

### Post by cpan on 2007-11-14
> **Saint Angeles said:**
> howdy!

you'll wanna have windows installed first because if you install windows after ubuntu, it will erase grub (your bootloader).

install windows on the whole thing, then when you install ubuntu, it will give you the option to resize the windows partition and use the available space for ubuntu.

hope that helps!

Thank you for the reply, but I think I need to be a bit clearer.

I have a laptop with windows already installed.  I've run my spysweeper with antivirus and defragged my HD.  I now want to install Ubuntu (7.04) but I want to be able to read/write to my windows partition.  The premade options during the Ubuntu install, from what I've read, do not support this....I've read that I need to create a fat32 partition.  Is this true?  Or as the first response to my post states that read/write is auto configured on 7.10, is it auto configured on 7.4?

---

### Post by cpan on 2007-11-14
Ok, I found the answer on my own.  Feisty Fawn (7.04) does support read/write capabilities but there have been some bugs with write functionality.

Here's the bug fix if 7.04 doesn't have srite capabilities after a clean install.
[https://bugs.launchpad.net/ubuntu/+bug/108980](https://bugs.launchpad.net/ubuntu/+bug/108980)

Thanks again to all those who replied...I'll update this post after installation!

---

### Post by cpan on 2007-11-14
OK more help.
I need to defrag my HD more.  I need to get some "unmoveable" files to move to make enough space.  I've heard you can disable them and defrag?  Anyone know what I'm talking about?

---

### Post by torgrot on 2007-11-15
In windows you can disable the page file if you have enough memory and then defrag.  The windows defragger can't move the page file while the computer is running windows.  After you install Ubuntu, you can boot back into windows and re-enable the page file.  It is on the computer properties virtual memory or something like that.  I don't remember off hand.

torgrot

---

### Post by cpan on 2007-11-15
> **torgrot said:**
> In windows you can disable the page file if you have enough memory and then defrag.  The windows defragger can't move the page file while the computer is running windows.  After you install Ubuntu, you can boot back into windows and re-enable the page file.  It is on the computer properties virtual memory or something like that.  I don't remember off hand.

torgrot

I figured it out...defragged well over 20 times and can't get the last bit over to the left.  Going to try the install anyway.  Thanks for your reply though...it's exactly what I needed.

---

