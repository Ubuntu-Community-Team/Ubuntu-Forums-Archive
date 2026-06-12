---
title: "Preseed not loading"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by dockraz on 2011-01-14
Greetings to all - 

I am trying to set up an automated 10.10 install on a USBStick ( as I will be using this to install on multiple computers ).  I used UNetBootin to create the USBStick.  I get my boot screen and the default load to start.  So all is well there...

My directory structure:
```

01/10/2011  08:07 PM         4,335,760 ubnkern
01/10/2011  08:08 PM         8,091,176 ubninit
01/14/2011  09:32 AM               184 syslinux.cfg
01/10/2011  08:08 PM            54,836 menu.c32
01/10/2011  08:48 PM    <DIR>          .disk
01/10/2011  08:49 PM    <DIR>          boot
01/10/2011  08:49 PM    <DIR>          dists
01/10/2011  08:49 PM    <DIR>          doc
01/10/2011  08:49 PM    <DIR>          install
01/10/2011  08:49 PM    <DIR>          isolinux
01/10/2011  08:49 PM    <DIR>          pics
01/10/2011  08:49 PM    <DIR>          pool
01/10/2011  08:49 PM    <DIR>          preseed
01/13/2011  10:20 AM               494 preseed.cfg

```

My syslinux.cfg file:
```

default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit 
preseed/file=/preseed.cfg

```

My preseed.cfg file:  ( basically copied directly from the Online Ubuntu Install Guide )
```

d-i debian-installer/locale string en_US

d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us

```

I know I don't have much in my preseed file - but i'm using the KISS approach - and only putting in items - testing them as I go.

I figure with those items in there - it shouldn't ask me about languages or the keyboard layout.

However, when I boot using this stick - it begins the install, and the first thing it does is ask me about Choosing a Language, then a Region, then do I want to detect a keyboard.  

I assume that if everything was working - based on the preseed file, those questions should be skipped past.

So - can someone tell me what I'm doing wrong?!?

Thanks in advance!

---

