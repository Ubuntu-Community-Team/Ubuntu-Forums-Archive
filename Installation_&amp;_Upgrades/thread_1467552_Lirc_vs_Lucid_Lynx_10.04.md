---
title: "Lirc vs Lucid Lynx 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Kheops_74 on 2010-04-30
I hate ubuntu so much when it does that. It does this at each update :-(. I upgrade to 10.04 and lirc is not working anymore. In 9.10, i was able to get lirc working using lirc_zilog. zilog is not loaded anymore. If i try to compile it and modprobe it. It didn't work.

My question:
Am i the only one with problem with lirc anr Lucid?
Must i continue to use lirc_zilog?
How to compile it?

Thanks

K

---

### Post by Kheops_74 on 2010-04-30
when i launch lsmod|grep lirc, i only have :

lirc_i2c                5845  0 
lirc_dev                8890  1 lirc_i2c

where is lirc_zilog?

---

### Post by cctsurf on 2010-05-10
Unfortunately, lirc_zilog is an unloved lirc driver, because it uses a "binary blob" which is construed by free software absolutists to be non-open source code.  while I agree with their desires, sometimes we have to deal with what we have.  I am surprised that you had lirc_zilog working under 9.10 so easily, I know there were a few blogs to that effect, but I could never get them to work for me.
The following will scare small children, please do with it what you will.:(
Anyway, lirc_zilog it is available through [http://wilsonet.com/?p=40](http://wilsonet.com/?p=40) (Jarod's the one developing it), though he needs to update his security certificate.  The git source is available at: [http://git.kernel.org/?p=linux/kernel/git/jarod/linux-2.6-lirc.git;a=tree;f=drivers/input/lirc;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/jarod/linux-2.6-lirc.git;a=tree;f=drivers/input/lirc;hb=HEAD)  Download the "Snapshot"
So far I have not found a way to compile this against the linux-headers included with ubuntu, I have had to download the whole source (If anyone can tell me how to do this without recompiling the whole lucid kernel in the source directory, etc., etc. etc. do tell!)
but what I have done is apt-get install all of the things to build the kernel, copy the config file from /boot to .config in /usr/src/linux-source-......., and make it like I used to do on gentoo or even older than that (sudo -i, make oldconfig; make; make modules_install; make install).
(Edit: this plan might work, but I haven't tested it [http://dinomite.net/2007/setting-up-ubuntu-for-building-kernel-modules/](http://dinomite.net/2007/setting-up-ubuntu-for-building-kernel-modules/) )
now I finally get to the lirc_zilog stuff:
I go where I have unzipped the snapshot of the lirc drivers, and run:
make CONFIG_INPUT_LIRC=m CONFIG_LIRC_ZILOG=m -C /usr/src/linux-source-.... M=$PWD modules
make CONFIG_INPUT_LIRC=m CONFIG_LIRC_ZILOG=m -C  /usr/src/linux-source-.... M=$PWD modules_install
and I am finally able to modprobe the lirc_zilog module.
I'm sorry this isn't too ubuntuy, if someone could point out how better to do this, I'd be thrilled!
I hope this helps,
James

---

### Post by cctsurf on 2010-05-11
A far better solution is available via the zilog.diff listed here:
[http://ubuntuforums.org/showthread.php?t=1294825&highlight=zilog+lirc&page=7](http://ubuntuforums.org/showthread.php?t=1294825&highlight=zilog+lirc&page=7)
hope that helps more
James

---

### Post by Kheops_74 on 2010-05-11
cctsurf is right. You will find the new lirc_zilog patch. It works.

K

---

### Post by AlliAnne on 2010-05-15
Does anyone have any luck with this on AMD64?  I've been trying all day to get it my pvr250 to work as a receiver and blaster.  I used to follow the instructions at blushing penguin, but they have not been updated in a long time.  I can get everything to compile and install, but I have this problem:

May 15 17:34:04 media-pc lircd-0.8.6[5590]: error in configfile line 62:
May 15 17:34:04 media-pc lircd-0.8.6[5590]: "2147549184": must be a valid (lirc_t) number

when trying to use the correct config file.

I can see I'm not alone in my struggles: [http://www.gossamer-threads.com/lists/mythtv/users/428902](http://www.gossamer-threads.com/lists/mythtv/users/428902)

---

### Post by Kheops_74 on 2010-10-16
Guess what. New version of Ubuntu 10.10, no more lirc. MrPlow whare are you? 

The lirc source are 0.8.7 not 0.8.6 and the patch don't seems to work anymore.

---

### Post by Kheops_74 on 2010-10-21
Ok i solve my problem ([http://ubuntuforums.org/showthread.php?t=1598968](http://ubuntuforums.org/showthread.php?t=1598968)). Thanks

---

