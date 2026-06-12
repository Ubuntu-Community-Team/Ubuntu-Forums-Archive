---
title: "Failed to execute init (error -8) Starting init: /bin/sh exists but couldn't execute"
date: 2016-08-28
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2016-08-28
My Ubuntu 16 Gnome installation won't boot anymore. 

     Error Message: Failed to execute init (error -8) 
Starting init: /bin/sh exists but couldn't execute it (error -8) 
 Kernel Panic - not syncing: No working init found.  Try passing init= option to Kernel. 

    I tried booting to a live disk and running FSCK, but that didn't work 

   I was creating a MultiSystem multiboot flash drive, as part of that I selected "Try Multisystem Drive in Virtual Box" it started installing Virtual Box, but I think it didn't complete. That may have created the problem I'm now having. 

    Using a live disk, I confirmed that /sbin/init does exist 

   This forum post may be related "Try: Jessie early boot failure: "/sbin/init exists but couldn't execute it (error -8)" (initrd corrupt?)  [http://tinyurl.com/z549dag](http://tinyurl.com/z549dag)  [http://tinyurl.com/gqz2afk](http://tinyurl.com/gqz2afk)     A screenshot of the error message: [http://i1232.photobucket.com/albums/ff365/webmanoffesto/20160828_214851.jpg](http://i1232.photobucket.com/albums/ff365/webmanoffesto/20160828_214851.jpg)  [URL=http://s1232.photobucket.com/user/webmanoffesto/media/20160828_214851.jpg.html][http://i1232.photobucket.com/albums/ff365/webmanoffesto/20160828_214851.jpg](http://i1232.photobucket.com/albums/ff365/webmanoffesto/20160828_214851.jpg)

---

### Post by webmanoffesto on 2016-08-29
I successfully booted into my Linux 16 Gnome install using Super Grub2 Disk - [http://goo.gl/G7fT](http://goo.gl/G7fT).

At the commandline I updated and upgraded. I rebooted, still can't boot. I rebooted using Super Grub2 Disk.

---

