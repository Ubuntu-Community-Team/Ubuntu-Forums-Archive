---
title: "Xubuntu x2 and the list after booting computer"
date: 2015-06-08
forum: Installation &amp; Upgrades
---

### Post by dowoshek on 2015-06-08
I have two installations of Xubuntu 14.04 on my laptop, EFI mode. Whenever I upgrade kernel in one of them the booting options of my computer are changed (to the list of recently upgraded Xubuntu). Is it possible to prevent changing the list by one of the installations?

---

### Post by grahammechanical on 2015-06-08
An upgrade to the kernel by necessity also updates the grub configuration files otherwise we would not be able to load the new kernel. Sometimes, grub is re-installed. And so, the grub of the updated OS takes control of the boot menu. This will also happen if there is an upgrade to grub itself.

A practical method to keep a particular OS in charge of the boot menu is to update that OS after the other OS has been updated. To put an OS back in charge of the boot menu we load into that OS and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Where sda = the first hard disk. A second hard disk would be sdb. I have several installs of the Ubuntu family of distributions over 2 hard disks. And this is the method I use. I also use different background images as Grub splash screens so I notice when another OS has taken charge of the boot menu.

Regards.

---

### Post by dowoshek on 2015-06-08
I used this method in my old computer (no UEFI). But it doesn't work now. I already tried grub-install /dev/sda for the OS with preferred list and /dev/sda4 for the other and the commands end with no errors but there's no result and the lists are changed after update-grub. So I guess there's no option like this for EFI systems but keeping overriding the menus?

---

### Post by Bashing-om on 2015-06-08
dowoshek; Hello;

Never the mind;
Graham says it best.

But I will add that I too multi-boot on two hard drives. I find that disabling 30_os-prober in the alternate operating systems prevents iteration of entries in the main grub boot. This makes it much easier to keep the boot focus on the primary operating system.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Dennis N on 2015-06-08
I have seen the same problem in  my UEFI system and multiple OS installations. If I want to continue to use the grub menu from my first OS (and I do because it has a custom menu), I need to save the grub.cfg file from the EFI system partition before installing a new OS and replace it after the new OS is installed. 

After restoring the saved grub.cfg, the boot will return to the original OS. I have done this procedure five times now as my UEFI system has 6 OS installations with the boot menu still from the first installed OS.

Apparently, this will happen as well when grub is reinstalled by another OS, although I have anticipated this by locking the grub version in any new OS. 

```
dmn@Sydney:/boot/efi/EFI/ubuntu$ ls -l
total 3416
[COLOR="#FF0000"]-rwxr-xr-x 1 root root     126 May 10 13:51 grub.cfg[/COLOR]
-rwxr-xr-x 1 root root  956792 May 10 20:40 grubx64.efi
-rwxr-xr-x 1 root root 1178240 May 10 20:40 MokManager.efi
-rwxr-xr-x 1 root root 1355736 May 10 20:40 shimx64.efi

```

I also think it is possible to edit this file, and just replace the UUID with the one for the OS you want to use*. This should work if the entire grub.cfg file was not saved, but I haven't needed to try it out.

* EDIT: there is a bit more to it. One needs to fix the hd and gpt reference as well:

```
dmn@Sydney:/boot/efi/EFI/ubuntu$ cat grub.cfg
search.fs_uuid a9f12cc3-d420-488e-9b31-319689f5b2c9 root [COLOR="#FF0000"]hd0,gpt2[/COLOR] 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

This would be what I would try if I had not saved my grub.cfg. After this fix, lock the grub version in the other OS to prevent upgrades.

---

### Post by dowoshek on 2015-06-09
Thanks for your replies guys. If there's no straight built-in solution (like for good old MBR) then I guess I can live with it.

---

### Post by Bashing-om on 2015-06-09
dowoshek; Hey !

There is no
> 
straight built-in solution 

There are many paths to an end - this is linux - You tailor to suit your use case, the way you use your system.
What works well for me, may not be the way you want  . My thought process is in maintenance of how I want to boot my system(s).
The only time I break grub - and I know it is going to - is installing a new release.

We can but offer advise, and give our individual solutions.
What you do is up to you

[INDENT][INDENT][INDENT]it is your system
[/INDENT][/INDENT][/INDENT]

---

### Post by Dennis N on 2015-06-09
> Whenever I upgrade kernel in one of them the booting options of my computer are changed (to the list of recently upgraded Xubuntu).

Without grub also being upgraded and installed, I can't see how your system would change over to using the grub menu of the system that had a kernel upgrade when it was booting to the menu in the other one previously. If that is what's happening, it's really puzzling. My answer (#5) was meant to deal with the situation when grub DOES get installed by an operating system in a UEFI installation and you want to revert to the previous system.

---

