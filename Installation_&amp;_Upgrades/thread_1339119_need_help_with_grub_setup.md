---
title: "need help with grub setup"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by ivago on 2009-11-27
Hi,

I've installed Ubuntu 9.10 last week on a new PC/HDD so it didn't install grub or created /boot/grub/menu.1st but the OS booted fine.
later this week I installed Windows 7 and after that I installed Fedora 12 on this same HDD (all x64)

Now I have a grub menu from fedora but it only showed the Windows 7 boot entry,, so I added my own entry to get back in Ubuntu but when I reboot and choose >Ubuntu it starts but drops me in some rescue shell.

This is what's in my menu.1st, all partitions are checked with fdisk -l and the initrid and kernel is what's in my ununtu's /boot folder...

What's wrong with this entry??

```

...
root=/dev/sda
default=0
timeout=3
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
title FEDORA 12                        
        root (hd0,2)
        kernel /boot/vmlinuz-2.6.31.6-145.fc12.x86_64 ro root=UUID=10ba22b3-4b0
        initrd /boot/initramfs-2.6.31.6-145.fc12.x86_64.img

title UBUNTU 9.10         
        root (hd0,0) 
        kernel /boot/vmlinuz-2.6.31-14-generic
        initrd /boot/initrd.img-2.6.31-14-generic

title WINDOWS 7                 
        rootnoverify (hd0,1)
        chainloader +1

```

---

### Post by darkod on 2009-11-27
Ubuntu 9.10 installed grub2 but I guess because it was only OS it didn't offer a menu at boot. Win7 probably rewrote the MBR with its own bootloader and then Fedora with grub1.

Not sure what is wrong with your entry but you might try reinstalling grub2 and it detects the other OSs automatically.

In case you don't have separate /boot partition the only thing you need is to boot with the ubuntu cd, select Try Ubuntu option and in terminal execute:

```
sudo -i
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt/ /dev/sda
```

From your input it seems sda1 is your root, otherwise change /dev/sda1 in the mount command.

After that run
sudo update-grub

in case it needs to update the OSs, reboot and see if it works as expected.

---

### Post by ivago on 2009-11-27
Hi,

I'm back in ubuntu but had an error 
```
grub-rpobe: error: cannot find a device for /.
```
but after rebooting ubuntu started again but no grub splash screen to choose between my other 2 OS.

When I check /boot/grub there's no menu.1st file that I can manually edit to add win7/fedora

Any idea what I need to edit? Don't think 9.10 has a new system like  lilo -> grub or does it?

All susggestions are welcome !

---

### Post by sisco311 on 2009-11-27
> **ivago said:**
> Hi,

I'm back in ubuntu but had an error 
```
grub-rpobe: error: cannot find a device for /.
```
but after rebooting ubuntu started again but no grub splash screen to choose between my other 2 OS.

When I check /boot/grub there's no menu.1st file that I can manually edit to add win7/fedora

Any idea what I need to edit? Don't think 9.10 has a new system like  lilo -> grub or does it?

All susggestions are welcome !

Karmic uses grub2: 
[uhelp]community/Grub2[/uhelp]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]
[thread=1195275]The Grub 2 Guide[/thread]

Grub2 should detect your other OSs automatically.

Open a terminal and run:
```
sudo update-grub
```

Then check if the OSs are listed in the /boot/grub/grub.cfg file.
(DON'T edit the file.)

---

