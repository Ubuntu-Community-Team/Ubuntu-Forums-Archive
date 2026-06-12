---
title: "Unable to boot after new kernel installation"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by robheus on 2010-04-13
I am using Ubuntu from a Wubi installation under Windows XP. 
The ubuntu installation is on the second partition of my laptop drive, installed on d:\ubuntu\disks\root.disk.
The (original) kernel was version 2.31-14.

Now I installed a new kernel (2.31-20) with aptitude, but when choosing that kernel from the Grub menu it says: kernel not loaded.

Thereafter I installed kernel sources (2.33-2), and made a package which I then installed.

But then I guess I have a new Grub (Grub2 -- v1.97) and instead of being able to boot into Ubuntu, I now arrive at a command shell with some limited options.

I looked up what I was supposed to enter, which is something like:

```

ls
search -f /vmlinuz
set
set prefix=(hdx,y)/boot/grub
set root=(loop0)
ls /boot
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img

```

ls - this shows me the available drives in format (hdx,y) and (loop0)

search -f /vmlinuz -- returns: (loop0)

set -- shows the settings (can't remember, but prefix and root were already set)

ls /boot  -- shows the files in the /boot directory

insmod /boot/grub/linux.mod -- It seems there is no linux.mod

linux /vmlinuz etc. -- Tried diverse combinations for this, with and without the root and loop options.

initrd /initrd.img -- 

But when I then boot again, the boot process goes on for a while, the screen sets to a different mode, but the scripts ends prematurely when trying to fetch the root directoty, and another shell (BusyBox or something) is entered (initramfs).

What commands and/or options should I use from the first command shell and/or what options should I set in grub.cfg for me to boot properly into Ubuntu?
(I can''t access the Ubuntu filesystem at the moment, so at first I need to know what commands to enter to boot properly from the Grub2 command-shell).

---

### Post by oldfred on 2010-04-13
this is often a fix.
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If you installed to the second partition then it is not sda1 but sda2 or even possible sda3 depending on your partitions.

linux /vmlinuz root=/dev/[COLOR=DarkRed]sda1[/COLOR] loop=/ubuntu/disks/root.disk ro

---

### Post by robheus on 2010-04-28
Thanks.

But I already solved it in another way, uninstall WUbi and re-install it, after I backed up disk.root. Is there any way I can acess disk.root to retrieve my files?
Can I recopy that old disk.root onto the new disk.root and everything runs fine?

---

### Post by robheus on 2010-04-28
> **oldfred said:**
> this is often a fix.
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If you installed to the second partition then it is not sda1 but sda2 or even possible sda3 depending on your partitions.

linux /vmlinuz root=/dev/[COLOR=DarkRed]sda1[/COLOR] loop=/ubuntu/disks/root.disk ro

When I used the little shell in Grub2, this specific command did not work.
I got an error like that the binary format of /vmlinuz was invalid or something.

---

### Post by oldfred on 2010-04-29
You can directly boot the root.disk with grub2 if you have Ubuntu/grub2 installed. You also can mount the root.disk from another install.

Wubi is for windows users to try out Ubuntu without having to repartition and easily uninstall if they do not like it.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[Script] Mount Wubi Disk from Linux 
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

I do not know if you can copy it into your new install or not.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by londonlad on 2010-04-29
open the synaptic package manager, type 'linux-image' & find the new kernel, then select 'completely remove' then reboot............sorted!

---

