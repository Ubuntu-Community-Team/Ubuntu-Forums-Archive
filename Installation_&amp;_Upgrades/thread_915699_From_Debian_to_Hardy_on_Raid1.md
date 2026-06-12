---
title: "From Debian to Hardy on Raid1"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by DeBsdTu on 2008-09-10
Installing ubuntu 8.04 on my Debian workstation proved to be not quite problemfree
Somehow the ubuntu installation disks are not able to correctly configure grub after installing on raid1.

On my Debian box I have the following setup.

IDE are the first system the bios looks at when both IDE and SATA interfaces are active so the bootloader will be installed on the bootsector of hda.
```
                           grub notation
hda 80 GB IDE		
hda1     /home/foo/one     (hd0,1)

hdb 250 GB IDE		
hdb5     /home/foo/two     (hd1,5)

sda 320 GB SATA		
sda5     /swap		
sda6     /         /md0    (hd2,5)
sda7     /home     /md1    (hd2,6)

sdb 320 GB SATA		
sdb5     /swap		
sdb6     /         /md0    (hd3,5)
sdb7     /home     /md1    (hd3,6)
```

To even try to install ubuntu on raid you are going to need the alternate install cd. So download it and burn it on cdrom.
Then load it and follow the same steps that you are used to follow when you install on a debian raid1 box. After grub is installed and the system reboots you are so screwed because grub will not be able to find your ubunut install.

To correct this boot your system with the alternate install cd and choose rescue system.
At some point it will ask you if you want to mount a root partiton from one of the harddisks...

Since /md0 and /md1 will be in the list, choose the one you installed / on, in my case /md0
Then it will ask you what it should do. Choose to open a terminal on the partition you just told to be /
It will present you with a rootprompt and at the prompt you sould type bash at the rootprompt (and a shell will be opened)

If you dont have a basic understanding about how vi (not vim) works you will have a problem. I havent tried if pico works here but feel free to experiment.

After bash is opened type vi /boot/grub/menu.lst at the rootprompt

look for
```
title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=/dev/md0 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet
```

and then change the root lines in this section to:
```
root		(hd2,5)
```
Then save the edited menu.lst file.

After that run update-grub you need this step to make the changes you just made effective if you leave it out grub will reload the old values at bootup.

The last step is to type exit and follow the menu's to exit to remove the cd and reboot.
Congratulations your system should be up and running now.

---

