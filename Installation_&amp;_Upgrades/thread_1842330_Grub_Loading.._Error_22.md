---
title: "Grub Loading.. Error 22"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by brianocw on 2011-09-11
Hello All

I've mistakenly deleted some of the parttiions when upgrading to 11.04 and am now getting a Grub Loading...error 22 message.  

I've looked in the archive section and found the link to [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I've created the livecd and booted from this.  When the desktop loaded (after I selected Try Ubuntu instead of the Install Ubutu opetion from the CD), I got to the terminal and tried the commands  to fix the issue using the prompts  from [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

When I ran "sudo grub" it came back with "command not found"
I ran "find /boot/grub/stage1" - "No such file or directory"
Next I tried "find /boot/grub" and it returned:
/boot/grub
/boot/grub/gfxblacklist.txt
/boot/grub/grubenv

Is there something that I am doing wrong such as missed a basic step?  

Ant help would be appriciated!

Thanks

Brian

---

### Post by Quackers on 2011-09-11
Welcome to UF :-)
You appear to have followed instructions written in 2006. These instructions refer to grub (legacy) which is the old version of grub.
The correct version of grub for 11.04 is grub2.
Try the instructions in the guide below, which should work better

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

