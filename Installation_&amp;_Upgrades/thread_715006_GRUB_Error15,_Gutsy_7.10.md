---
title: "GRUB Error:15, Gutsy 7.10"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by shanabino on 2008-03-04
Hello guys.

OK I messed it up!! I was doing a regular apt-get update command, when a window kept popping up that i didnt really care for its content as it looked irrelevant; but i noticed the title bar which referred to DEBCONF!! not to make this longer, I went to the manager and uninstalled that package!!!!!!! mid way through I felt like i did a terrible thing, so I stopped the process and confirmed that I DONT WANT TO COMMIT CHANGES!!!

I lost my wireless connection, and some other features, and when I rebooted the system GRUB ERROR 15: CANT FIND FILE!!!

I did some research on how to recover GRUB, but most of the posts talked about corrupted GRUBS due to dual installation on OS on the same machine!!!

any advices would be highly appreciated as I have all life on that laptop where I hope I wont lose.

---

### Post by wolfen69 on 2008-03-04
Quoted from the GNU/GRUB manual
> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.
For example, if you get this error during booting, maybe GRUB is telling you it can't find the specified kernel or initrd.img file. Usually this is because of a mistake in editing your menu.lst file, for example, the exact path or name of your kernel or initrd.img contains an error or a typo.
> title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,2)
kernel        /boot/vmlinux-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
'vmlinuz' is spelled wrong here, it is 'vmlinuz', not 'vmlinux'.
> title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/intrid.img-2.6.20-15-generic
quiet
savedefault
    'initrd.img' is spelled wrong here, it is 'initrd.img', not 'intrid.img'.
    Super GRUB can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...

Boot with Super GRUB Disk instead, and then with your operating system running you can check your file and correct your menu entry for Linux.
Open your menu.lst file with 'sudo gedit /boot/grub/menu.lst', if you are using Ubuntu Linux.
Use the command 'ls /boot' to check for the correct name for your Linux kernel and initrd.img.
Copy the correct name from the terminal output to the text file and paste it to avoid typos. Don't forget to save the changes in your menu.lst file before your close it.

This error can also occur if the files needed to boot with are missing or corrupt in the /boot/grub directory. Refer to Grub loading stage1.5 for how to completely delete possibly corrupted GRUB files and restore them again from /sbin/grub.
[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors)

---

### Post by shanabino on 2008-03-04
Thank you for an objective response; I checked for any typos "vmlinuz" is the one being used; so, I think the second option is whats most probably my case, I will be reading over the link you've posted and see if I can work it out... I shall keep you posted, thanks again.

---

### Post by shanabino on 2008-03-04
well, tried Gparted and Super GRUB, and still having the same problem!!! the best i could get to is to get Gparted to understand that my file system is EXT3 not 2.

Any further inputs would be highly appreciated.

The problem is that I think I have a damaged GRUB files that I need to restore!!

---

