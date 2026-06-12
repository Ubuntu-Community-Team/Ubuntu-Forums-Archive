---
title: "Cannot access USB Hard drive after install!"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by DarkEden on 2008-04-06
Hi,
I've just installed ubuntu to my external hard drive, and it boots up fine, and everything works. But when using windows, the drive doesnt show up! It makes that annoying noise to confirm that its picked up the device, shows up correctly in the "safely remove hardware" dialog, and shows up in the computer management tool under disk management. I beleive I need to give the drive a letter. The only trouble is that it will only let me use the "delete volume" option. Thing is that really isnt gonna work, as I kind of want to keep linux on there. I need to be able to access the drive, as I also use it as a big memory stick.
Thanks
Dan

---

### Post by PmDematagoda on 2008-04-06
Your problem is because the external drive has been formatted using a file system that Windows does not support.

If you instructed Ubuntu to format the drive using ext2/3 then you can install [Ext2IFS]("http://www.fs-driver.org/") to read it.

But when using Ext2IFS with ext3, keep this in mind, since Ext2IFS is meant for ext2 not ext3(ext3 can be used as well), it may cause some corruption, so use it carefully.

---

### Post by DarkEden on 2008-04-06
Thanks for the fast reply, only trouble is I use this at school, so installing something such as that isnt an option. Is there a way around this? Or can I install using a different format? (I'm not bothered about reinstalling, not got anything on there yet anyway)
Thanks,
Dan

---

### Post by DarkEden on 2008-04-06
Sorry to go on, but any chance of someone replying to this tonight? Because I kind of need this working for tomorrow.

---

### Post by lacis_alfredo on 2008-04-11
Yep, same problem as the earlier poster.  (And DON'T BOTHER asking me about the drive working before.  It's worked for nearly a year on various 7.04 boxes, along with Windows boxes)

USB drive light blinks 3-4 seconds when inserted.... then nothing...  no icon on desktop, no entry if "mount" run from console.  No entry in System Monitor. 

Running lsusb gives this when USB drive inserted:
    homer@krusty:~$ lsusb
    Bus 001 Device 006: ID 13fe:1d00  
    Bus 001 Device 001: ID 0000:0000  
    homer@krusty:~$ 

And this when removed:
    homer@krusty:~$ lsusb
    Bus 001 Device 001: ID 0000:0000  
    homer@krusty:~$

---

