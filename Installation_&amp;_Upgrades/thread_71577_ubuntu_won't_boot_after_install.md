---
title: "ubuntu won't boot after install"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by escaria on 2005-10-03
hi, i'm really new to linux,
i have just installed ubuntum 5.04, then i have removed the cd rom and restarted the pc.

now when the system boot i see only that

--------------------------------------------
Booting 'Ubuntu, kernel 2.6.10-5-386 '

root  (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
   [Linux-bzImage, setup=0x1600, size=0x1209f6]
------------------------------------------------------
and that's all,nothing happend

i have tryed to search for solutions on google but found nothing, in fact i don't know what to search for

help please!

---

### Post by escaria on 2005-10-04
i have tryed 

grub> find /vmlinuz
hd(hd0,0)
grub> kernel /vmlinuz
[Linux-bzImage, setup=0x1600, size=0x1209f6]

and here it freeze :( what can i do ?

---

### Post by escaria on 2005-10-04
happen the same if i do 

grub>kernel /boot/vmlinuz-2.6.10-5-386

---

### Post by Mustard on 2005-10-04
I'd try to install again. Try expert mode if you want a bit more control over the install process.

I was curious what the -quiet part is referring to and whether it means the installation is proceeding quietly, as in no output on current process.  I don't really know enough to say.  Did you use any of the special options for installation? Or did you do the default install, by presseing enter at the boot prompt?

Usually after you are asked to remove the CD, it does a few more things and then reboots the computer.  When the prompt you see comes up, I would normally be seeing output showing the system starting itself up, followed by a quite significant wait while a number of packages are configured and installed.

---

### Post by escaria on 2005-10-04
i have used the default install process pressing enter

yes after reboot it have done some more things and then rebooted again and here i get the grub problem.
i'll try with advanced... but i'm not advanced.

thanks.

---

### Post by darkmatter on 2005-10-04
[QUOTE=Mustard]I was curious what the -quiet part is referring to and whether it means the installation is proceeding quietly, as in no output on current process.  I don't really know enough to say.[/QUOTE]

The 'quite' part only applies to the use of a bootsplash. It is the flag to display an image during startup as opposed to the 'verbose' option, which displays detailed output during the boot sequence.

Since he is running Hoary, this is not an issue, as bootsplah is not supported by the kernel, and verbose is displayed regardless as to which option is present in menu.lst.

I'm not quite sure what his problem is, but it does not involve the 'quite' option.

I will investigate further.

---

### Post by darkmatter on 2005-10-04
escaria, what are your system specs?

---

### Post by escaria on 2005-10-04
celeron(tm) at 466Mhz( 66x7.0)
memory 196608k
quantum fireball lm20.5

i don't know where to find other specs

---

