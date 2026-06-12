---
title: "How do i uninstall ubuntu?!"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by Jonathan45 on 2008-09-15
Hi i have got a new computer and im gonna install ubuntu on it.
but ive got ubuntu on this computer and only gonna use it for games and only use windows...
how do i uninstall ubuntu?
and repair the windows bootloader...
im using hardy heron and XP.

---

### Post by oilchangeguy on 2008-09-15
> **Jonathan45 said:**
> Hi i have got a new computer and im gonna install ubuntu on it.
but ive got ubuntu on this computer and only gonna use it for games and only use windows...
how do i uninstall ubuntu?
and repair the windows bootloader...
im using hardy heron and XP.

from the live cd, locate the partition manager. and delete the ubuntu partition, then you can increase the size of the windows partiton to use the entire hard drive. then using your windows cd, enter the recovery console, at the admin password prompt enter the password, if none press enter to bypass the prompt. then type fixboot and press enter, then type fixmbr and press enter, then type exit and press enter.

---

### Post by melojo on 2008-09-15
Boot from your windows xp cd and from a dos prompt type fixmbr.  You can use gparted to delete the linux partition and increse the size of nfts.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Jonathan45 on 2008-09-15
ok thanks but can i uninstall GRUB and use ubuntu as a virtual machine inside windows?
is there a tool in windows to change the partiton sizes?

---

### Post by oilchangeguy on 2008-09-15
> **melojo said:**
> Boot from your windows xp cd and from a dos prompt type fixmbr.  You can use gparted to delete the linux partition and increse the size of nfts.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

you may want to read post #2 on the proper way to fix the xp boot record. and there is no dos prompt. xp is not layered on top of microsoft's old operating system dos. windows me was the last os to be built on top of dos.

---

### Post by Jonathan45 on 2008-09-15
ok how do i repair it then?!

---

### Post by oilchangeguy on 2008-09-15
> **Jonathan45 said:**
> ok thanks but can i uninstall GRUB and use ubuntu as a virtual machine inside windows?
is there a tool in windows to change the partiton sizes?

no, and no (not xp any way). you'd have to do a complete install inside of the vm program, you can't just take your already installed ubuntu and move it to a vm.

---

### Post by melojo on 2008-09-16
> **oilchangeguy said:**
> you may want to read post #2 on the proper way to fix the xp boot record. and there is no dos prompt. xp is not layered on top of microsoft's old operating system dos. windows me was the last os to be built on top of dos.

I have alway used fixmbr with xp and it has worked
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
HELP
Use the help command to list all the following supported commands:

   attrib    del        fixboot   more     set
   batch     delete     [COLOR="Red"]fixmbr[/COLOR]    mkdir    systemroot
   bootcfg   dir        format    more     type
   cd        disable    help      net           
   chdir     diskpart   listsvc   rd            
   chkdsk    enable     logon     ren           
   cls       exit       map       rename  
   copy      expand     md        rmdir
As far as the dos promt , the recover console or command prompt looks an awful lot like dos to me.  Call it what you want but it acts similar and you can run old dos programs from windows xp so it must have something to do with dos I asume.
I also wanted to point out that number 2 post was listed while I was writing my post.

---

### Post by melojo on 2008-09-16
here is some info I found googeling
[http://ubuntuforums.org/showthread.php?t=210755](http://ubuntuforums.org/showthread.php?t=210755)
[http://ebestagent.com/how-to-uninstall-grub-or-lilo/](http://ebestagent.com/how-to-uninstall-grub-or-lilo/)
[http://www.planetamd64.com/index.php?showtopic=26486](http://www.planetamd64.com/index.php?showtopic=26486)
[http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html)
[http://www.wikihow.com/Uninstall-the-Grub-Bootloader-from-a-Dual-Boot-XP-System-With-an-XP-CD](http://www.wikihow.com/Uninstall-the-Grub-Bootloader-from-a-Dual-Boot-XP-System-With-an-XP-CD)
[http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)

---

### Post by Jonathan45 on 2008-11-02
Thanks for the help every1!

---

