---
title: "Install/uninstall Ubuntu"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by jwgoodman on 2007-09-13
I've just begun working with Ubuntu for about two weeks.  And it's going to be really fine.   I've installed it on several computers each of which also has Win 2000 Pro.  I've worked enough with it by now that I know how I want it to work and partition.  I've use 6.00+ and then upgraded to  added 7.04.   When I did that, I ended up with even more and smaller partitions.  So, I'd like to uninstall each of the installations and install 7.04 as a new virginal installation beside Windows so that I can partition in a more useful way. And, of course, I don't know what to do about the dual boot situation.  I can obviously delete the partitions that use Ubuntu and begin again. I do use Partition Magic well.  But, that doesn't sound wise to me and I don't know what that would do to the boot section.  Anyone know how to completely uninstall Ubuntu and the dual boot section without having to completely reformat the whole disk and reinstall Windows and Ubuntu?

Eventually, all but one machine will use Ubuntu only.  One machine must continue to use Windows 2000 Pro.

Many thanks.

John W Goodman, MD
[email]jwg2@cebridge.net[/email]

---

### Post by eggdeng on 2007-09-13
If you installed ubuntu over W2K and can dual boot, presumably  the W2K installs are on the first partition of the first hard disk and Grub is installed to the MBR. In this case you can safely delete any other partitions & reallocate space. You can check your layout with 
```
sudo fdisk -l /dev/sda
``` (sda for the first HDD, sdb for the second etc). There is no need to delete the MBR as new installs will overwrite it.
Edit: For the box with a W*nd*s-only install, better to follow [http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

---

### Post by jwgoodman on 2007-09-13
Thanks so much for the reply. And thanks especially for the code.  Can you recommend and book for the linux commands that is not for professionals but for those who do know how to use code at a lesser level?

John Goodman,  [email]jwg2@cebridge.net[/email]

---

### Post by eggdeng on 2007-09-14
I have a copy of O'Reilly's Linux Pocket Guide for reference but I think the command line is something you pick up as you go along - you learn a command when you need to use it. 
What is really important is to learn to use the man command, which will help when you are unsure of usage. Try ```
man fdisk
``` to see how the fdisk command works and its different options. When you finish reading, press q to escape. Apart from that, there are lots of webpages with lists of commands. Google will help you find the one which suits you best.

---

### Post by mostwanted on 2007-09-14
> **jwgoodman said:**
> Thanks so much for the reply. And thanks especially for the code.  Can you recommend and book for the linux commands that is not for professionals but for those who do know how to use code at a lesser level?

John Goodman,  [email]jwg2@cebridge.net[/email]

[http://linuxcommand.org](http://linuxcommand.org) is an excellent site for learning about the shell. It takes you from complete newbie to advanced user depending on how far your go with it.

---

### Post by dabl on 2007-09-14
> **jwgoodman said:**
> 

Can you recommend and book for the linux commands that is not for professionals but for those who do know how to use code at a lesser level?



"Beginning Ubuntu Linux" by Keir Thomas  :)

---

### Post by Pumalite on 2007-09-14
> **jwgoodman said:**
> Thanks so much for the reply. And thanks especially for the code.  Can you recommend and book for the linux commands that is not for professionals but for those who do know how to use code at a lesser level?

John Goodman,  [email]jwg2@cebridge.net[/email]

Ubuntu Linux Bible.-Wiley

---

