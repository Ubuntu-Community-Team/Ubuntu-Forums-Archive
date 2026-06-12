---
title: "How to install Windows 7 on a HD already containing Karmic Koala"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by surfinmdq on 2009-11-17
(background music: oops, i did it again)

Hi forum! I'm using Karmic Koala as my everyday desktop and installed it on a 35GB partition of the SATA drive, I left a 55GB for W7 because I knew I had to install it somewhere near in the future.

I want to know, since Micro$oft don't care about other OS -I dislike a lot Micro$oft- how do I do to install W7 in the free space and make Ubuntu boot again using LiveCD or other technic.

---

### Post by darkod on 2009-11-17
Just install win7 as normal, that will destroy grub2 on the MBR. Read here (item number 13) how to reinstall grub2 from livecd:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Of course livecd means you will have to boot with the ubuntu cd and select Try Ubuntu. Like you said yourself, livecd. :)

---

### Post by surfinmdq on 2009-11-17
cool.

I have another little question if answer is short enough, if not I will post in appropiate category.

I used to love the way Ubuntu booted when the 'quiet' parameter was deleted from the kernel line in 'menu.lst'.
Is there any way I can see again what probing is doing the kernel and what services are being loaded by Ubuntu?

Thanks!

---

### Post by darkod on 2009-11-17
If I understood your question, when you are in the grub menu on a particular option, you can hit TAB and it will show you the command. You can make some changes to it (delete quiet) and press enter to continue booting like that.
This option to make changes with TAB is also available when starting as liveCD.

If you like any of the changes you can make it permanent in an installation but I don't recall right now where do you need to do that. I've seen it around in forums.

---

### Post by surfinmdq on 2009-11-18
Ok, I was talking about editing the grub menu, gotta check the link you give me for directions then.

Thanx darkod!! =D

---

### Post by Mark Phelps on 2009-11-19
If you installed 9.10 clean (as in, NOT an in-place upgrade), there will be no menu.lst to edit.  9.10 defaults to the new GRUB2 -- which doesn't use menu.lst.

---

### Post by raymondh on 2009-11-19
Also, Drs305 and Herman have links/sites dealing with GRUB2.  Check it/them out for reference.

Here's Herman's

[http://members.iinet.net/%7Eherman546/p20.html](http://members.iinet.net/%7Eherman546/p20.html)

Here's Dave's

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)

Have fun.

---

### Post by surfinmdq on 2009-11-28
Sorry for the late reply guys, already checked links @raymondh, thank you!!

---

### Post by raymondh on 2009-11-29
> **surfinmdq said:**
> Sorry for the late reply guys, already checked links @raymondh, thank you!!

De nada :)

---

