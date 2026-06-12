---
title: "Triple Booting - Two HDDs"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by gnarula on 2010-06-10
Hi!

I would like to install Lucid on my system. I have installed ubuntu previously (dual booted) but on a single hard disk. Now, with my 160GB Hard Disk full I've got another one (500GB). So, I would like to triple boot Windows 7(1st hdd - 160GB), Windows XP(2nd HDD - 500GB) and Ubuntu Lucid (2nd HDD - 500GB).

As I mentioned, the OS are installed in the order Windows 7, then XP and now finally I wish to install ubuntu. Please guide me as I don't want to lose any data :roll:

Also, while using the Live-USB (prepared using UNetBootin) the keyboard and mouse froze after the login. Would like some help regarding that too.

Regards,

Gaurav

---

### Post by oldfred on 2010-06-10
When I put a new motherboard in my system a year or so ago I had the mouse freeze issue and it worked with a PS/2 adapter. It turned out the BIOS has a setting for USB keyboards/mouse.

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

It is real important with multiple drives to install grub2 to the same drive as the Ubuntu install using the advanced button. Then set BIOS to boot with that drive.
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Grub will only find one bootable windows install since windows combines its boot into the windows with the boot flag (active partition).

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by wkulecz on 2010-06-10
> Please guide me as I don't want to lose any data 

Backup everything before you start!  That is the only way to be sure!

---

### Post by gnarula on 2010-06-11
Well, I installed Ubuntu 10.04 successfully on my 500GB hard disk(/dev/sda6) with GRUB on (/dev/sda). Now the problem is, when the system starts, I am able to access Ubuntu and Windows 7 Bootloader via Grub. Ubuntu starts fine and so does the Windows 7 bootloader. But I can only access Windows 7. When I start Windows XP, the system just reboots..

---

### Post by oldfred on 2010-06-11
Are you booting XP thru the win7 grub menu entry. Windows combines all windows boots into the windows partition that is active (boot flag *).

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

