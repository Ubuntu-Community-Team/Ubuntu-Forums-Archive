---
title: "Grub Boot Menu Modifying??"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by scottyadam on 2008-09-15
Ok...So I have installed Windows XP quite a while ago and left a little bit of space so that when I had time I would be able to install Ubuntu yaaa!!!!

Now when I installed ubuntu everything went great but what I am hoping to do now is to customize my boot menu.  Is there a way that I could make my Xp System boot automatically by entering some commands (right now Ubuntu is startup) so that the boot menu will be better to use.  I am willing to learn so if there is any tutorials or anything...I just want to make it so that I just have a menu with:

Ubuntu OS
Windows XP OS

Now...what are the other Ubuntu files that I have on the boot menu?

I would imagine I would have to learn shell?

At this point I just need to know what to do and if it is possible?

Thanks!!!

Adam Scott

PS:Y es I know Linux kicks Window's *ss but I need XP for school everyday:)

---

### Post by Partyboi2 on 2008-09-15
You can change the default o/s by changing the default option in you menu.lst see [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc"). You can also adjust the timer see [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#timer") 
If you want to know more about the menu.lst and grub [[COLOR=Blue]Herman's grub[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm") page is full with plenty of info

---

### Post by iaculallad on 2008-09-15
To edit your menu.lst file:

Open /boot/grub/menu.lst for editing:

```
gksudo gedit /boot/grub/menu.lst
```

Find this line and change the default value to point to the value of your desired kernel.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]**default         0**[/COLOR]
```

Sample values using my current menu.lst file will be:

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic		**[COLOR="Red"]<----- 0[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)		[COLOR="Red"]**<----- 1**[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic		**[COLOR="Red"]<----- 2[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)		[COLOR="Red"]**<----- 3**[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+		**[COLOR="Red"]<----- 4[/COLOR]**
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If I want to boot on "Ubuntu 7.10, kernel 2.6.22-14-generic" as default, I would change the value of default to 2 instead of 0.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="Red"]default         2[/COLOR]**
```

After you had changed it, Save and close. And while on your terminal, reboot.
```

sudo shutdown -r now

```

---

### Post by scottyadam on 2008-09-15
Now can I change the names of the OS's when editing with gedit?

---

### Post by AndyCee on 2008-09-15
Yep. Just change the text following "title" on the same line to what you want.

eg.
```
title           Ubuntu 7.10, kernel 2.6.22-15-generic
```

to

```
title           Ubuntu which is so totally cool
```

etc.

---

### Post by scottyadam on 2008-09-15
Is there a way to make folders in the grub boot loader?

---

### Post by AndyCee on 2008-09-22
I'm afraid I don't know what you mean.

Do you mean make new folders in the /boot/grub/ directory?

I suppose so. I have occasionally made backup grub menus like:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bckup.030208

or such. I don't know how grub deals with folders in that directory though.

---

### Post by scottyadam on 2008-09-22
I mean like organizing the boot menu a little bit so that you only have two options instead of four.  There are 3 choices for Ubuntu and 1 option for Windows XP.  I was thinking of hiding them into "folder" that is displayed on the boot menu.  I guess the other question that I have is what are the other options for?

---

### Post by AndyCee on 2008-09-23
Ah, ok. I'm fairly sure you can't add folders to the menu in that sense.

The multiple Ubuntu entries are different versions of the linux kernel. Every time you get a kernel update, a new 2 entries is added: One for the normal log in, and one for "recovery mode". Depending on how you look at it, Grub is very messy or thoughtful in not removing them.

You can hide options you don't want. Or even delete them. Some people like to keep the current one and the latest previous one (which means 4 ubuntu entries) in case an update causes unforseen compatibility problems.

To organise this automatically, you can search for the line containing "howmany", remove the '#' and make the line say "howmany=1", if you want to keep only the latest entry when the kernel is updated.

The program "Startupmanager" provides a gui for this stuff, if you want to try that. Just back up /boot/grub/menu.lst before you make any changes.

My grub menu looks as follows. Comments follow '#' to explain:

```

# Current kernel
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5f75060d-e8b4-46bd-89c0-d1430709e9aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

# recovery mode using current kernel
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5f75060d-e8b4-46bd-89c0-d1430709e9aa ro single
initrd		/boot/initrd.img-2.6.24-21-generic

# Previous kernel
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5f75060d-e8b4-46bd-89c0-d1430709e9aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

# Previous kernel recovery mode
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5f75060d-e8b4-46bd-89c0-d1430709e9aa ro single
initrd		/boot/initrd.img-2.6.24-19-generic

# This option checks the validity of the computer's memory
title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

---

