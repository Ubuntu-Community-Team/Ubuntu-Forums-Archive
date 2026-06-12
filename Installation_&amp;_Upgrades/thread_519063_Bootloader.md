---
title: "Bootloader"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by Hickler on 2007-08-06
I recently partitioned my hard drive and installed Ubuntu, then Sabayon. During the Sabayon install, it asked me if I wanted the bootloader to boot into another OS, so I said yes, typed Ubuntu and specified the partition it was on. When I boot the pc, it shows "Sabayon Linux 6.6" or something like that and then Ubuntu under it, Sabayon works but when I try to boot into Ubuntu it says that it is not the right file type or doesn't exist I think. What have I done wrong and can it be fixed?

---

### Post by rillip on 2007-08-06
I'm not familair with the Sabayon OS, does it use Grub?  If so, you've probably got the wrong setup for Ubuntu. I don't suppose you made a backup of your menu.lst?  You could look at that, then configure the Sabayon bootloader accordingly.

---

### Post by Hickler on 2007-08-06
> **rillip said:**
> I'm not familair with the Sabayon OS, does it use Grub?

Yes, it uses grub.

> **rillip said:**
> I don't suppose you made a backup of your menu.lst?  You could look at that, then configure the Sabayon bootloader accordingly.

I never but where could I find menu.lst?

---

### Post by confused57 on 2007-08-06
> **Hickler said:**
> I recently partitioned my hard drive and installed Ubuntu, then Sabayon. During the Sabayon install, it asked me if I wanted the bootloader to boot into another OS, so I said yes, typed Ubuntu and specified the partition it was on. When I boot the pc, it shows "Sabayon Linux 6.6" or something like that and then Ubuntu under it, Sabayon works but when I try to boot into Ubuntu it says that it is not the right file type or doesn't exist I think. What have I done wrong and can it be fixed?
I would recommend reinstalling Ubuntu's grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then you can add a configfile entry to boot Sabayon...open a terminal in Ubuntu:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Then add a configfile entry to the very end of your menu.lst:
```
title   Sabayon
configfile (hd0,2)/boot/grub/grub.conf
```
You would need to adjust the (hd0,2) for Sabayon's root partition:
e.g. /dev/sda3  =  (hd0,2)
/dev/sda4  =  (hd0,3)

Here's a link explaining configfile entries:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by rillip on 2007-08-06
As you probably gathered from the above post, the menu.lst is in /boot/grub.  Confused 57 is basically proposing the same thing I did, but backwards.  Make a backup of your current menu.lst, reinstall grub to get the correct Ubuntu one, then edit it to add the Sabayon.  Good luck!

---

### Post by logos34 on 2007-08-06
[sorry--late post]

---

### Post by Hickler on 2007-08-06
I think I'll try confused57's post first, thank you everyone.

---

### Post by Hickler on 2007-08-06
```
ubuntu@ubuntu:~$ cd /boot/grub
bash: cd: /boot/grub: No such file or directory
ubuntu@ubuntu:~$ sudo cp menu.lst menu.lst_backup
cp: cannot stat `menu.lst': No such file or directory

```

Hmm...??

---

### Post by Hickler on 2007-08-06
I have to go eat, please leave possible solutions for when I return. Thank you.

---

### Post by ajgreeny on 2007-08-06
If sabayon uses grub all you need to do is add the entry from the top of your ubuntu menu.lst file to the sabayon grub menu.lst file.

Start sabayon and mount ubuntu as superuser (**mount ubuntu/partition** [/dev/hda2 or whatever it is] **/mnt/ubuntu -t ext3**) having first made the mount point /mnt/ubuntu.  Now navigate to your ubuntu menu.lst and copy the entry from that for ubuntu into the sabayon menu.lst.  Now when you start you should be able to get into ubuntu from the sabayon grub.

---

### Post by Hickler on 2007-08-06
Okay, not sure what happened but I tried booting into Sabayon but now all I can boot to is Ubuntu. 
                                                                              |
So is there any way you could explain this \/  except for Ubuntu. And keep in mind I'm a novice Linux user so could you explain it a bit more please. Thank you.

> **ajgreeny said:**
> If sabayon uses grub all you need to do is add the entry from the top of your ubuntu menu.lst file to the sabayon grub menu.lst file.

Start sabayon and mount ubuntu as superuser (**mount ubuntu/partition** [/dev/hda2 or whatever it is] **/mnt/ubuntu -t ext3**) having first made the mount point /mnt/ubuntu.  Now navigate to your ubuntu menu.lst and copy the entry from that for ubuntu into the sabayon menu.lst.  Now when you start you should be able to get into ubuntu from the sabayon grub.

---

### Post by confused57 on 2007-08-06
> **Hickler said:**
> Okay, not sure what happened but I tried booting into Sabayon but now all I can boot to is Ubuntu. 
                                                                              |
So is there any way you could explain this \/  except for Ubuntu. And keep in mind I'm a novice Linux user so could you explain it a bit more please. Thank you.
Boot into your Ubuntu installation, then follow the directions I gave you in my other reply...copy & paste the commands into a terminal...I believe you may have entered  "cd /boot/grub" from the live cd, which doesn't have a /boot/grub.

To determine which is your Sabayon partition, enter:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by Hickler on 2007-08-06
Hmm, now it's the  Sabayon bootloader and Ubuntu no longer boots.

---

### Post by confused57 on 2007-08-06
> **Hickler said:**
> Hmm, now it's the  Sabayon bootloader and Ubuntu no longer boots.

Don't know what happened, but you can try adding a configfile to Sabayon's bootloader to boot Ubuntu, open a terminal(Konsole?):
```
su
```
you need root privileges to edit your grub.conf, then:
```
cd /boot/grub
cp grub.conf grub.conf_backup
nano grub.conf
```

Add a configfile entry to boot Ubuntu:
```
title  Feisty
configfile (hd0,0)/boot/grub/menu.lst
```
menu.lst is short for menu.list...again, use your Feisty root partition in place of (hd0,0), which would be correct if Feisty is on /dev/sda1.

Ctrl+X, y, enter...this will save your configfile entry.

If the configfile entry works, you can delete the other Ubuntu entries in your Sabayon grub.conf.

Added:  What error messages are you getting when "Ubuntu no longer boots"?

---

### Post by Hickler on 2007-08-07
> **confused57 said:**
> Added:  What error messages are you getting when "Ubuntu no longer boots"?

```

Rootnoverify (hd 0,2)
chainloader  +1
Error13: Invalid or unsupported executable format

```

Also, sorry for the late reply, my power supply for my laptop is very finicky.
Thank you very much, it worked but now I have 3 Sabayon Linux's in my bootloader, 2 Ubuntu's and 1 Feisty, the Ubuntu's are the ones that don't work. I understand that if I delete the entries from the grub.conf this will be resolved, my only problem is how do I delete them? Thanks.

**Added:** My apologies for needing these instructions, I just wanted to be sure about the process so I don't mess it up, I think I have a pretty good idea on how to remove the entries from the list and once again thank you very much for your help. This great community is one of the main reasons I'm sticking with Ubuntu.

---

