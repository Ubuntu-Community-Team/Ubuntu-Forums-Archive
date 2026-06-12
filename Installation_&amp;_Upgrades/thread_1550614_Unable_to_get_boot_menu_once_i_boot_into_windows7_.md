---
title: "Unable to get boot menu once i boot into windows7 with ubuntu dual boot"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by kask1984 on 2010-08-11
Hi everybody
This is shiva.I am trying to install ubuntu 10.04 on windows7.windows 7 was already installed.I followed these steps to install ubuntu 10.04.

1)First i made some freespace in hard disk to install ubuntu using windows7 default options(By shrinking).
2)I used USB drive to install ubuntu.I made it bootable using unetbootin.
3)I followed normal steps install(language,area,keyboard,using manual partition i installed ubuntu in free space,etc).
4)I got boot menu when it restarted.

PROBLEM is

As long i use only ubuntu (boot into ubuntu --shutdown--boot into ubuntu --shutdown) it works well.
If once i boot into windows 7 and restart the system i am loosing boot menu options.
The following error i am  getting
"no module name found 
Aborted.Press any key to exit".

If i press any key,I guess its trying boot using internet and lastly it says Operating system not found and hangs.

Please suggest me some remedies.
Right now i dont have windows7 installation cd.

Thank you.

---

### Post by Sub101 on 2010-08-11
What make is your laptop?

Many manufacturers (Dell for example) ship windows 7 with recovery features which unfortunately write to the MBR on every shut down.

---

### Post by kask1984 on 2010-08-11
Dell Studio

---

### Post by Sub101 on 2010-08-11
I think you need to uninstall the backup suite, however I cant remember what its called sorry!

---

### Post by kask1984 on 2010-08-11
Even if windows7 overwrites MBR every time on shutdown atleast i should be able to boot into windows7 ,isnt it.But i am not geeting any boot menu or not able to boot into windows7 ,directly it says No operating system.
Thanks for u r replies.

---

### Post by Sub101 on 2010-08-11
I dont know the reasons for it but it is the case im afraid.

You can either reinstall Ubuntu or use the Super Grub Disk to restore Grub.

---

### Post by kask1984 on 2010-08-12
I did that,but once we boot into windows7 again same problem occurs.

How can i get back windows7 to normal situation.
I mean,i want to uninstall ubuntu. 

Thanks for u r replies and i request please suggest me .

---

### Post by wilee-nilee on 2010-08-12
Here is a link to a forum stub on dell data safe.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

If you can remove it I believe grub2 can be reloaded and will stay in place.

Reinstalling grub from a live cd if you need help.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you want you can also post the bootscript in my signature as well.

---

### Post by kask1984 on 2010-08-12
Thanks for u r reply.
i will try this method.

---

### Post by Sub101 on 2010-08-12
> **wilee-nilee said:**
> Here is a link to a forum stub on dell data safe.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

If you can remove it I believe grub2 can be reloaded and will stay in place.

Reinstalling grub from a live cd if you need help.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you want you can also post the bootscript in my signature as well.

This is exactly what I had to do on my Alienware. So should hopefully work for you.

---

### Post by kask1984 on 2010-08-12
Thank you .
Its working.

---

