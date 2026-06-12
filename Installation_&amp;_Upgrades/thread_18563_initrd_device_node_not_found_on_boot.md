---
title: "initrd device node not found on boot"
date: 2005-03-07
forum: Installation &amp; Upgrades
---

### Post by kadissie on 2005-03-07
I have just installed Ubuntu warty [via the Knoppix Live CD today](http://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto)  today; install went fine, all the packages arrived in their places without a problem. Then I configured my apt sources.list and told it to go fetch me some kernel images, and I've ended up with both vmlinuz-2.6.8.1-3-386 and vmlinuz-2.6.8.1-3-686 and their corresponding initrd.img files in my /boot partition. I've got
```
root@Knoppix:/ # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             9.7G  457M  9.3G   5% /
devpts                9.7G  457M  9.3G   5% /dev/pts
tmpfs                 9.7G  457M  9.3G   5% /dev/shm
/dev/hda1              29G   23G  5.4G  82% /mnt/windows
/dev/hda2              99M   24M   71M  25% /boot
/dev/hda6             5.6G   33M  5.6G   1% /home
```
with
```
root@Knoppix:/ # cat /etc/fstab | grep -v ^#
/proc      /proc       proc   defaults            0 0
/sys       /sys        sysfs  noauto              0 0
/dev/fd0   /mnt/floppy auto   user,noauto,exec,sync 0 0
/dev/cdrom /mnt/cdrom  auto   user,noauto,exec,ro 0 0
/dev/cdrom1 /mnt/cdrom1  auto   user,noauto,exec,ro 0 0
/dev/hda1 /mnt/windows vfat defaults 0 0
/dev/hda2 /boot ext3 defaults 0 0
/dev/hda3 / reiserfs defaults 0 0
/dev/hda5 none swap defaults 0 0
/dev/hda6 /home reiserfs defaults 0 0
```
I've configured my grub with, for example,
```
title=Ubuntu 2.6.8 i386
        root (hd0,1)
        kernel /vmlinuz-2.6.8.1-3-386 root=/dev/hda3
        initrd (hd0,1)/initrd.img-2.6.8.1-3-386
```
and likewise with the 686 image.

During bootup, I get an error complaining"Cannot find initrd device!" and then later it stops after saying something about unable to use resolv.conf or something like that. There are also miscellaneous errors to do with ext3 filesystems which I'll try to record next time.

Essentially the boot proceeds fine - if I don't specify an initrd or specify the wrong one, it complains quite early on and bails out.  It actually gets to the stage of transferring to init, I think, and then complains about being unable to complete various init actions like find the other partitions.

Any ideas? Doing a search for "cannot find initrd device" gets you a googlewhack, and in French, which explains the problem but doesn't offer any advice.

R.

PS - This is a post copied over from linuxquestions.org, where I found a [related thread](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=280940)

[Quantum Archaeology]("http://quantumarchaeology.com")

---

### Post by alastair on 2005-03-07
You have :

initrd (hd0,1)/initrd.img-2.6.8.1-3-386

But ... this seems odd. Shouldn't it be :

initrd  /initrd.img-2.6.8.1-3-386

---

### Post by hal8000 on 2005-03-07
The grub lines look OK to me, change into your boot partition and make sure that the initrd file is actually there.  Pay particular attention to the spelling as a  "." or a "-"
in the wrong place will also give you this message. Also again double check the spelling of initrd matches with the corresponding line in /boot/grub/menu.lst

---

### Post by abhaysahai on 2005-03-08
Hi,
I had the same problem while installing Ubuntu from Knoppix Live CD.   I have tried grub and lilo both with same error. 
Though I have installed Knoppix on my hard disk now, but if a solution is there for this error, I would love to shift back to Ubuntu.

Regards,
Abhay

P.S : I have checked teh spellings and the files multiple times.

---

### Post by kadissie on 2005-03-08
My problem is not a spelling error, and the kernel/image files are unquestionably there since I have been able to do this from the Grub command-line with auto-completion.  The initrd.img is a valid ramdisk image; from what I understand (from reading the grub man page) everything works fine from the boot loader's point of view and it hands off control to the kernel with no problem.

It is only after handing off to the kernel that trouble starts, and the initrd device can't be found (is it still supposed to be found?  Has it not been removed from memory by this point?).  I'm pretty sure it is not a Grub problem, nor a Knoppix-related problem.

Any further ideas?

R.

---

