---
title: "Grub is toast"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by ftblstr2319 on 2008-03-12
Running 8.04 and 7.10  as of yesterday.  I decided to install vista again to help my pappy.

I blew away 7.10 on the partition to free up some space.  Ubuntu 8.04 still worked before installing vista.

I know that installing windows blows away grub.  

Windows booted fine but then I went to reinstall grub

Booted to live cd 

I entered the correct commands 
found which drive I had my boot/grub/...whatever that was

root (hd0,1)
setup (hd0)

it installed successfully

reboot and it books back into grub

However.  It is my old boot information from the two kernals of 8.04 and 7.10.  It seems like grub didnt get updated. When I select a partition I get error 17. Cant find partition

I went into vista and (bootrec fixmbr) and im able to boot into windows

Downloaded the windows automated grub installer that reboots you into a grub prompt where you can reinstall(supergrub?).  Walked through that and after reboot I was at the same screen with my old installations.  Still is looking at OLD grub.

I guess I'm looking for a way to completely blow away grub and reinstall it with the new partition information.

Couldn't find my situation under search

---

### Post by sandysandy on 2008-03-12
u may like to use Super Grub Disk to fix your grub.
 
here´s the link. 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

burn it as iso image on a Cd and then boot from it. u will get option to fix ur grub.

regards

---

### Post by ftblstr2319 on 2008-03-13
I did run that last night its called Easy GRUB Repair without external media thanks to **UNetbootin**

Booted into the grub menu and whenever I repair it, it references my old boot menu before installation of windows.  I looked all around that program and the grub menu still has my old info in it.

Currently I only have 2 OS partitions (VIsta and 8.04) and a little free space and some swap space

It is showing no windows partition, 2 different versions of Ubuntu.  Whenever I rebuild it, it just keeps going back to an old version

Is there a way to rebuild the MBR from scratch automatically or by hand?

---

