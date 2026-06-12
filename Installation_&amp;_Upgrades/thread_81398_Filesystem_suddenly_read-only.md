---
title: "Filesystem suddenly read-only"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by paul{nl} on 2005-10-24
Hi all,

I've had a lot of problems with upgrading Hoary to Breezy, I had a dual-boot setup, but after the upgrade I wasn't able to install grub propperly. At first I wasn't even able to do anything, later I was able to get into XP, but whatever I tried, Ubuntu was unreachable. 
I therefor decided to reinstall Ubuntu completely, on one partition so I woulnd't have the dual-boot/grub problem anymore. I lost quite a bit of data (I didn't back-up all my files before the upgrade :( ) by ding that.

Anyway, after the complete re-install I wasn't able to get into Gnome, all I got was tty. After fixing the dpkg it reinstalled all the files it missed and booted without a problem. But after a few hours, it suddenly gave errors saying the filesystem is read-only! :confused: While I was downloading and installing programs for hours.
Then, I decided to reboot and see what happens, but it didn;t shut down propperly, and after shutting down with the power button, rebooting wasn't possible. There were errors on the partition, and they had to be fixed. 

After fixing those errors, and rebooting, the same thing happend again; after a few hours Filesystem is read-only errors! :( I'm absolutely sure the file system was writeable before, and there was more than enough disc-space.

Does anyone know what causes this, adn how it can be fixed?

Here is my grub menu.lst setup.

```

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin  
boot

```

I didn't modify this at all, but I dont think this is causing the problem, because the filesystem was/is deffinately writeable. After a few hours is just crashes and sais the fielsystem is read-only... 

I hope this can be fixed, Ubuntu Hoary was awesome.

---

### Post by poptones on 2005-10-24
Your hard drive is likely failing. The reason the filesystem becomes read only is because ubuntu is detecting disc errors it cannot correct and so it makes the hard drive read only to protect what is left. If you can get back in you can check the System Log under system tools and see what messages you get about disc failures.

In a way it's better that you lost all that data and have resigned yourself to it, because it sounds like that was coming anyway. First thing to try would be to open the case and reseat all the cables going to your hard drives. If they go bad, bad things happen even with good drives.

---

### Post by paul{nl} on 2005-10-25
Hi, thanks a lot for your reply. I thought it might have been a HW problem, but I never encountered a problem under Hoary, so it's quite a coincidence that after the upgrade my hardware is suddenly broken.

When had access to my XP installation, I ran a program that checked my hard disk sectors, because I also first thought it was has HW problem. It didn't detect any errors, or broken sectors, everything was just fine. THe HDD itself is only 4 months old, its a Western Digital 80GB drive.

I'm gonna wait and see what happens, perhaps after an update the problem is solved. I've downloaded Fedora C4, perhaps I'm gonna try that distro...

---

### Post by poptones on 2005-10-28
Paul, you still here?

The reason you sometimes find "after I installed (some new operating system) the disc went bad" is because the drive likely had some bad clusters that didn't show up before because nothing was stored on them. When you reinstall another operating system a portion of the disc (that was failing) now gets some portion of a program written to it, and then dies. 

You can prevent this sort of thing by writing zeroes to a drive when you first get it. Manufacturers don't do this and the install programs don't do it. This is a habit I picked up when I started using encrypted drives - writing random data to the entire drive is part of protecting encrypted data. A side effect of this practice is it also acts as a self test for the drive wherein it will find and remap any portions of it that are bad.

---

### Post by paul{nl} on 2005-10-29
I'll try to install Windoze XP on it so I can run a few programs that check the disc.
I ran a program under Ubuntu, it said the partitions had "bad endings". if I can't reboot anymore, I'll throw it in the freezer and see what happens, I understand that often revives the drive for a short period of time.

Thanks for the reply.

---

