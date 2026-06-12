---
title: "Triple boot - XP/98/Ubuntu"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by Ron W on 2005-06-09
I'm being given a computer with XP already on it. I want to add Windows 98 and Ubuntu onto it. Has anyone tried this? If so, what are your experiences? Are there any documents that might help me?

Thanks

Ron

---

### Post by ruben_b on 2005-06-09
installing ubuntu on a xp machine is no problem.
but installing 98 on a xp machine won´t work that easy. if you like to install those 3 os, then you should first install 98, then xp and then ubuntu.

---

### Post by zwaardmeester on 2005-06-09
I think the order you install them doesn't matter, as long as you have enough partitions for it. And a decent bootloader of course, to make it possible to boot the OS's. I recommend ubuntu's Grub, it has suppport for Linux/Windows/dos/FreeBSD. Check [www.ubuntuguide.org](www.ubuntuguide.org) for more info about grub.

---

### Post by wvslkr on 2005-06-09
It does matter on the order you install.  You need to do 98 then XP then Ubuntu.
If you install 98 after it will rewrite the boot and that is all you will have. Win 98 assumes the whole drive for itself.  If I remember correctly it won't install unless 
it thinks it has the primary partition.

My setup has 98 on a second hd so it actually knows nothing about the other
installs. 

There should be a How To in the forums or wiki.  Or google. In the end grub will
handle the boot for you. 

GL  
    :)

---

### Post by mingus on 2005-06-09
wvslrk is correct about this.  Furthermore, W98 expects to *entirely* be on the first partition, where XP only requires it's "system partition" be the first partition, and it can share that with 98 (it's only a few files inside of 98's C:), the rest of XP can go on another partition.

There are a few articles on MS's support site that discuss what can & cannot be done, with recommended approaches.  Required reading.

Also, be very careful about assuming what grub will do.  If will depend on how you set up Windows, ref MS articles again.  Remember that both W98 and XP's boot loaders are on that same partition.  It may be easier to use the primary Windows loader and have it point to Ubuntu, rather than the other way around.

---

### Post by The Mouse on 2005-06-09
I want to do something similar.  I want to do 3 partitions.  1 of 14G for XP, 1 of 11G for pictures and music, and 1 of 5G for ubuntu.  My question is, what file system format shall I use on the 11G partition so that I can access my music and pictures from both XP and ubuntu?

Also, if anyone has any suggestions, cautions, or advise for me I would appreciate it.  I am learning as I go.

Also 2, I am planning to do this on a Dell Inspiron 8100.  I would like to run a Linksys wireless b pcmci card with ubuntu if possible.  Will I have hardware issues with anything?

Thanks, the Mouse

---

### Post by mingus on 2005-06-10
Welcome.  Let me encourage you to search the forums first.  There are a ton of postings on pcmcia wireless, and those threads are typically in the hardware forum.

To get you started, there is a great Starter Guide.  If you haven't installed yet, a pretty exhaustive installation manual.  All of this and many howto's are in the wiki.  Also look for sticky's and howto's in the forums.

As far as your filesystem question for the 11GB partition, you have 2 choices.  NTFS can be read from by not written to by Linux (well, there is a technology that claims to support this, but it is very new).  FAT32 can be both read and written to by Linux.  Of course, XP can do both with both.  Usually the decision therefore is FAT32.

---

