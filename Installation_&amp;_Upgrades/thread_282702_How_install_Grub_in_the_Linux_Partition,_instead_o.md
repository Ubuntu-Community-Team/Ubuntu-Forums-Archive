---
title: "How install Grub in the Linux Partition, instead of in MBR during Ubuntu install ?!"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by subvertigo on 2006-10-23
Can you tell me how installing GRUB in the Linux Partition, like doing othen distribution (Mandriva, Suse, ...) ??

Because i want to use the WinXP boot loader... Eg with mandriva i'm able to load linux using the NTLDR (editing boot.ini and using the sw bootpart). Is not possible with Ubuntu ?

---

### Post by gn2 on 2006-10-23
> **subvertigo said:**
> Can you tell me how installing GRUB in the Linux Partition, like doing othen distribution (Mandriva, Suse, ...) ??

Because i want to use the WinXP boot loader... Eg with mandriva i'm able to load linux using the NTLDR (editing boot.ini and using the sw bootpart). Is not possible with Ubuntu ?

Do you have more than one hard drive?
If so read this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

The standard Live CD install does not give any option on where to install Grub, but the Alternate install CD does.
[http://www.ubuntu.com/download](http://www.ubuntu.com/download) (Select your area, then look for the Alternate CD)

---

### Post by subvertigo on 2006-10-23
Thanks for the answer...

No... only 1 hard-disk.

I've already tried the Alternate. I thought I set to install lilo on the linux partition, but then, rebooting, lilo started (instead of NTLDR...). So I imagine lilo/linux installed on MBR.

A possibly important thing is that my SATA laptop HD is recognized as SCSI...

Is anyone able to install Grub in the Ubuntu partition during installing by the "alternate" ? Can tell me how?

---

### Post by subvertigo on 2006-10-23
Another question... in the Ubuntu Guide I found a graphical boot loader configurator... but it is not in the menu and doesn't run (command not found) in the terminal ( the command was boot-"somethingthatidontremember" ).

---

### Post by gn2 on 2006-10-23
Here you go, the download is at the bottom of the first post:
[http://www.ubuntuforums.org/showthread.php?t=228104&highlight=gui+grub+configurator](http://www.ubuntuforums.org/showthread.php?t=228104&highlight=gui+grub+configurator)

---

### Post by subvertigo on 2006-10-23
I solved...

---

### Post by inkbrush on 2006-12-24
Hey,
I know it's been a while, but I just found a quick way to install Grub in the Linux partition instead of the MBR. You can do it when installing Ubuntu using the standard Edgy Eft CD. You don't need the Alternate CD.

First, I assume that you have installed Windows first and have some other bootloader besides GRUB installed in the MBR (I use Bootpart, by the way).

When you are setting up the Linux partition in the Ubuntu graphical installer, make sure your Linux boot partition is a primary partition. Also, remember the order of your Linux partition. That is, if your Windows partition comes before the Linux partition, then the Linux partition will be the second partition. Number the Linux partition by counting from 0. In this case, where the Linux partition is the second one, it will have the number 1.

As you progress thru the graphical installer, you will come to the part that says "install GRUB on (hd0)" You only need to change this part to install GRUB on the Linux partition instead of the MBR. Remember the number of the Linux partition from the above example? Just put that number right after hd0, so you will change "(hd0)" to "(hd0,1)". MAKE sure there are NO extra spaces.

That's it.

---

