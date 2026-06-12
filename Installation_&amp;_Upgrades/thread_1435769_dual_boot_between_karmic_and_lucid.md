---
title: "dual boot between karmic and lucid?"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by iduppe on 2010-03-21
can i dual boot between karmic and lucid?

What should i do to get this going?

My partition scheme looks like:

sda1 ---- swap

sda5 ---- / (karmic)

sda6 ---- /home (karmic)

sda7 ----  empty

sda8 ----  empty

So i plan to install lucid onto sda7 & sda8... but my question is..... WHAT DO I DO WITH THE BOOT LOADER? how to do it? how to install it?I think it would be better to use lucid's grub, but will I be able to use the karmic installation? should I edit the menu.lst on it?

thanks in advance

---

### Post by oldfred on 2010-03-22
Is your Karmic an upgrade from Jaunty that still has grub legacy (0.97) or a clean install that has grub2 (1.97 beta4). A new install of Lucid will use grub2 (1.98).

Grub2 is very good at finding other operating systems. It just will be which grub do you want to be in control. Worst case you can go back and reinstall grub for the version you want to boot.

You can share swap but should not share /home. If you are just upgrading, the newer version of the software may update entries in /home but they then may not work with the older version in karmic. It is meant as one way forward. If you want to share data you can make a data partition with just your data and share that. You can copy your settings in /home to keep those you want, if you are using both systems.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by iduppe on 2010-03-22
That was worth reading.

My actual question was how to do the actual installation, regarding the boot loader... What I did was: I put lucid's cd on the drive, rebooted, and installed next to karmic, like a good caveman would do.

And it works fine, I can use both systems so far :D

---

### Post by Pkirkham on 2010-06-18
Sometimes it's not so easy.
I installed Lucid 10.4 but then decided to fallback to Karmic 9.10 because Lucid currently has a problem with my Digium TDM400P card and won't boot. However the versions of grub 2 are different and grub 2 can't boot Lucid. I'm not sure it's because of the differences between 1.97 and 1.98. In the latter there are options on the menuentry line and a line which reads recordfail which apparently isn't present in 1.97.

---

### Post by oldfred on 2010-06-18
Pkirkham, This is an old solved thread. Most will only look at it for solutions not to help another user. Please start your own thread and post this in that thread.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

