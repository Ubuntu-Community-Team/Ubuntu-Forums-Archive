---
title: "[SOLVED] Kernel update results in boot failure"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by Aiman on 2008-10-17
Everything worked fine on kernel 2.6.24.19 until the system upgrade yesterday that included the 2.6.24.21
When rebooted,none of the kernels worked due to grub updating the menu.lst
all kernels were mapped to hd (0.6) just had to change them back to (0.1)
when i tried booting,seemed fine when the splash screen appeared,but it took a while then i was given the busy box console,tried to boot the -19 kernel and the same thing happened
so i tried to boot in the recovery mode for both -19 and -21
this is the last few line that i got:
> 
Write Protect is off
Assuming drive cache: write through
976773168 512-byte hardware sectors (500108 MB)
Write Protect is off
Assuming drive cache: write through

Attached SCSI disk
Attached scsi generic sg2 type 0

it get stuck for a minute or so on that msg and then i get this:
> 
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT ! /dev/disk/by-uuid/d2a9.............. does not exist

then it starts the built in shell (busy box)

none of the entries on the grub menu work,all leads to the same results as above mentioned,i tried disconnecting the external drives but i still can't boot,what should i do ?
cant afford to reinstall,everything was working fine with -19

---

### Post by Blue Snapper on 2008-10-17
My laptop (HP Pavilion dv6000) seems to freeze (will not boot) with the caps light flashing during boot with kernel 2.6.24-21. If I chose kernel 2.6.24-19 generic everything seems to work ok. How can I force Ubunutu to automatically boot with the with the older kernel (19) that seems to work?

---

### Post by Herman on 2008-10-17
> Everything worked fine on kernel 2.6.24.19 until the system upgrade yesterday that included the 2.6.24.21
When rebooted,none of the kernels worked due to grub updating the menu.lst
all kernels were mapped to hd (0.6) just had to change them back to (0.1)
when i tried booting,seemed fine when the splash screen appeared,but it took a while then i was given the busy box console,tried to boot the -19 kernel and the same thing happened
so i tried to boot in the recovery mode for both -19 and -21
 Hello Aiman, 
When we get a kernel upgrade, the script called 'update-grub' is run automatically, and that creates a new (updated) menu.lst file for us.
Normally that all works fine, and we can boot happily with our new kernel.

The update-grub script looks at our '[DEBIAN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST")' for information about how to construct the new GRUB menu.
If the information in the 'debian automagic kernels list' is wrong or out of date, we will get a new GRUB menu that will be wrong.

You probably just need to edit your /boot/grub/menu.lst file with the currently correct partition number,  and file system UUID number.  [Operating System Entries]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries").
You also need to update the debain automagic kernels list in your /boot/grub/menu.lst to make those changes persistent over future kernel updates. (in [groot=]("http://users.bigpond.net.au/hermanzone/p15.htm#groot") and in  (in [kopt=]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt")).

Regards, Herman :)

---

### Post by Herman on 2008-10-17
:) Hello Blue Snapper,
You can simply scroll down to the old kernel entries in your GRUB menu by using your arrow keys if you want to boot by an earlier kernel.

 You can 'comment out' the lines in your /boot/grub/menu.lst by placing a hash mark: # in front of the lines that you don't want GRUB to read at boot time.
Here's a link about how to comment out the old kernel entries, [Hide titles in the GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#hide_items"), but you might want to comment out the most recent ones instead.

Regards, Herman  :)

---

### Post by Herman on 2008-10-17
I forgot to mention, in case anyone is new to Ubuntu, we normally open our /boot/grub/menu.lst files with 'gksudo gedit /boot/grub/menu.lst', (of course),
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Aiman on 2008-10-17
Herman,you're the MAN :)
i didn't think it could be a grub issue
first i tried using the uuid and i did add it to all entries,but that didn't work,then instead i used root=/dev/sda2
the new kernel (21) didn't work,but the 19 did work fine
is there anyway i can uninstall the -21 kernel ?
i did remove it from my menu.lst,but i don't think i need to be around after all the problems it caused :)

---

### Post by Herman on 2008-10-17
:) If you're really sure it's a problem with your new kernel, you can uninstall it if you like.
Here are a few links about how to uninstall old kernels, if you have to,
[Remove Ubuntu Kernels You Don't Need]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") - Tombuntu,  
[Removing Those Extra Kernels in Ubuntu]("http://www.alterego7.com/2008/04/removing-those-extra-kernels-in-ubuntu.html") -Alter Ego, 
[How to: Linux delete or remove kernel]("http://www.cyberciti.biz/faq/debian-redhat-linux-delete-kernel-command/") - Nixcraft, and, 
[Remove Old Kernel From Ubuntu]("http://sandakith.wordpress.com/2007/11/25/remove-the-old-kernel-from-ubuntu/") - Lahiru Sandakith’s Web Log. 

Regards, Herman :)

---

