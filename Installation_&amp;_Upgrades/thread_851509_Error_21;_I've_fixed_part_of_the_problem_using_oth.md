---
title: "Error 21; I've fixed part of the problem using other forum posts."
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by Mizzou on 2008-07-06
I was receiving, "grub loading please wait... error 21
Goal: Dual boot vista and Ubuntu
Issue: Above error
How Ubuntu was installed on one HDD:
a) swap partition 8000 MB
b) ext 3 partition 10000 MB mount point /
c) ext 3        remainder HDD space mount point /home

How I attempted to correct error:
1) Used vista recovery dvd and at the c prompt in repair, typed
   bootrec/fixmbr    successful
   bootrec/fixboot   not recognizable
                     obviously not the exact words but you get 
                     the idea.
2) Removed disk, rebooted and UBUNTU works great
3) Went to terminal app in UBUNTU and typed,
   sudo grub
   find /boot/grub/stage1
   (hd0,1)
   setup (hd0)
   quit

4) Reboot and get Ubuntu 8.4, kernel 2.6. 24-16 generic
                   "      "    "     "         "   recovery mode
                  Ubuntu 8.4, memtest 86+

Focus: I still can't get vista home to boot.

Any help would greatly be appreciated. I know I probably didn't need to use half that sh*%, but I learned a lot. This may have needed to be posted in beginners, but I wont cross post.

---

### Post by Pumalite on 2008-07-06
Edit your menu.lst and add below the automagic line:
title Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Mizzou on 2008-07-06
Forgive my stupidity, but is this in the Ubuntu prompt? Also , what is the automagic line. Thanks again and forgive my ignorance.

---

### Post by Pumalite on 2008-07-06
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Edit:
gksudo gedit /boot/grub/menu.lst
Automagic line is at the end. Below that add what I told you.
Save, exit. Reboot.

---

### Post by Mizzou on 2008-07-06
I'm not getting a ~$ prompt. After "### END DEBIAN AUTOMAGIC KERNELS LIST" should I just type 
title Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

What is the proper procedure to save, exit, and reboot?

Thanks again.

---

### Post by Pumalite on 2008-07-06
Put a cursor with the mouse at the end of the automagig line. Hit 'Enter' a couple of times to leave some space. Add the entry for Windows. To save: File>Save. To exit, just close the window.

---

### Post by meindian523 on 2008-07-06
> **Mizzou said:**
> I'm not getting a ~$ prompt. After "### END DEBIAN AUTOMAGIC KERNELS LIST" should I just type 
title Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

What is the proper procedure to save, exit, and reboot?

Thanks again.
This is a file PumaLite is telling you to edit,not a command being entered.You don't NEED a $ prompt.

---

### Post by Mizzou on 2008-07-07
Thanks for all your help, guys. This is what makes Ubuntu a hell of a lot better than Windows, friendly help.

Okay, I went through those steps with success but now when I get to choose my OS and select Vista, I get the following message:

error 13: Invalid or unsupported executable format. Any ideas what to do next?

---

### Post by Mizzou on 2008-07-07
Can anyone help with the new error? After boot it now gives vista as a choice but I get error 13. Thanks in advance.
Could it be that the "remainder" partition is not in the Windows format NTFPS or something like that?

---

### Post by confused57 on 2008-07-07
> **Mizzou said:**
> Thanks for all your help, guys. This is what makes Ubuntu a hell of a lot better than Windows, friendly help.

Okay, I went through those steps with success but now when I get to choose my OS and select Vista, I get the following message:

error 13: Invalid or unsupported executable format. Any ideas what to do next?
Here's a description of grub error 13:
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)

It might help if you could post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"
and
```
gedit /boot/grub/menu.lst
```
you probably just need to post your Ubuntu & Windows boot entries.

---

### Post by Pumalite on 2008-07-07
Maybe you didn't use the Vista partitioner to allocate space for Ubuntu in the first place.

---

