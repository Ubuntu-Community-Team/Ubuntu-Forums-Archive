---
title: "Wubi install fails to launchi in XP"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Geryon on 2011-10-16
I have a Windows XP Service Pack 2 install on a IBM Thinkpad t42.  It's a fresh factory install of XP.  I downloaded the latest Wubi installer and when I launch it I see the process pop up in the task manager but after about 5 seconds it just dies.  I don't any error messages or any indication of what may be wrong.  I'm really not a Windows guy so I don't know where to troubleshoot further.  Any ideas or suggestions?

Thanks.

---

### Post by ralph_pt on 2011-10-16
if you could'nt solve your problem yet,

1) i sujest you to create a botable pen drive or a live cd.

2) change your bios priority to boot from the pen or the cd you have created in 1)

3) install the distro you've selected in 1)

if you have further questions just ask.

*

---

### Post by Geryon on 2011-10-16
My goal here is to install this alongside windows.  For some reason this default install of Windows places unmovable blocks at the end of it's partition and I can't resize the partition to more than around 40MB.  I really want to leave the default Windows on here as I don't have the time or patience for screwing with it and still need it for a couple of things.  Normally, as with all my other machines, I just toss on my choice of distro.  Unfortunately I need one Windows-based system handy.

---

### Post by ralph_pt on 2011-10-16
so probably its better to chage the partition in the windows system,

not sure if the windows partition manager of the windows xp is easy to work or not.
there is a video showing how to:
[http://www.youtube.com/watch?v=pmpazHBzXjY](http://www.youtube.com/watch?v=pmpazHBzXjY)

when i used windows i use to use this "partition magic" 

```
http://www.softpedia.com/get/System/Hard-Disk-Utils/Partition-Magic.shtml
```

hope it can help

---

### Post by bcbc on 2011-10-16
> **Geryon said:**
> I have a Windows XP Service Pack 2 install on a IBM Thinkpad t42.  It's a fresh factory install of XP.  I downloaded the latest Wubi installer and when I launch it I see the process pop up in the task manager but after about 5 seconds it just dies.  I don't any error messages or any indication of what may be wrong.  I'm really not a Windows guy so I don't know where to troubleshoot further.  Any ideas or suggestions?

Thanks.

IBM's use python for some utility and this interferes with wubi (also written in python). There is a workaround for it. [lpbug]819318[/lpbug]

---

