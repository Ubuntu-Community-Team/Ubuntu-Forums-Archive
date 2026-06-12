---
title: "kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by kuv02 on 2015-11-15
I'm helping my uncle who is only using the laptop.
He told me after installing a recent security update, the laptop did not boot.


I found an [older thread]("http://ubuntuforums.org/showthread.php?t=1751574") in this forum but didn't want to wake up zombies...


I logged into grub console and executed "ls". Result:


> (hd0), (hd0,msdos1), (hd0,msdos5)


I tried to find the grub modules but was not sucessfull.


with ls (hd0,msdos1)/ i got
> grub/ abi-3.19.0-15-generic memtest86+.bin memtest86+.elf [...] vmlinuz-3.19.0-18-generic System.map-3.19.0-18-generic [...] config-3.19.0-32-generic

(I appreviated the list, because I have to type it by hand.)


with ls (hd0,msdos1)/grub i got:
gfxblacklist.txt unicode.pf2 i386-pc/ locale/ fonts/ grubenv grub.cfg

There is no /boot/ folder.

I could not find any modules. (I [read here]("http://askubuntu.com/questions/142300/fixing-grub-error-error-unknown-filesystem") that I should look for them)


With a live system I checked what partitions I have:
/dev/sda1 (Ext2 V1, Linux Bootable)
/dev/sda2 (Extended partition)
/dev/sda5 (Linux LVM, LVM2 Physical Volume)

I really need your help, because my knowledge regarding system internals is slim.

---

### Post by yancek on 2015-11-15
I don't know how doing a security update would remove the boot directory and leave the grub directory intact, sounds pretty weird to me.

The output you show for the command "ls (hd0,msdos1)/" actually shows what would ordinarily be in the boot directory.  I don't use LVM but the standard as I understand it is to have a separate boot partition which should be (hd0,1) in your case.  You might go to the boot repair site below and download that script and run it, just select the option to Create Bootinfo Summary and post that output here.  That will give a lot more information and someone should be able to help.

---

### Post by kuv02 on 2015-11-15
Thank your for the answer. What repair site? I see no link

---

### Post by kuv02 on 2015-11-20
Hi I'm back. Sadly there was no further answer in the last days. What boot repair site shall I visit?
I would be really happy to get this sorted.

---

### Post by yancek on 2015-11-20
The boot repair site is at the link below.  Sorry about that.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

> with ls (hd0,msdos1)/ i got

The output you show running the above command is your boot partition showing all the directories/files normally shown under the boot directory.
The files referred to in the link you posted, thos with the '.mod' extension are in the /boot/grub/i386-pc directory.
When you run the boot repair, select the Create BootInfo summary and it will output a file which you can post here.

---

### Post by kuv02 on 2015-11-22
I created the boot repair disk and started the process. A window appears with 2 options. One is Apply Repair. I tried this first. It then asks me to execute some commands. I tried them, but already the first one 
```
sudo chroot "/mnt/boot-sav/mapper/kubuntu-vg-root" dpkg --configure -a"
```
will throw an error 
```
gzip: stdout: No space left on device
```

I then canceled the wizzard and restarted it to select the "create report" option

Here it is: [http://paste.ubuntu.com/13441685/](http://paste.ubuntu.com/13441685/)

[SIZE=1]Btw: If you know somebody who maintains the boot-repair-disk, tell them to remove the second desktop. I accidentally moved the wizard-window to another desktop and didn't find an obvious way to get there. People like my uncle would have not had a clue what to do then.[/SIZE]

---

### Post by kuv02 on 2015-11-22
It looks like a common problem. I've read about old kernel files that trash the boot partition and eat up all space/inodes. But I'm not sure about it, and how to go on with this.
Is there anybody out there? I hope yancek is not the only person with knowledge in this forum?

---

### Post by kuv02 on 2015-11-22
I got a tip [over here]("http://www.ubuntu-forum.de/artikel/65502/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-0-0.html") on how to clean up some space, but still the boot-repair can not performe, because there is not space left on devise.

---

### Post by kuv02 on 2015-11-22
Really nobody around? Wow....sad

---

### Post by yancek on 2015-11-23
The information you posted from boot repair shows that it is using LVM (Logical Volume Management) which requires a separate boot partition.  In this case it is sda1.  The output below:

```
/dev/sda1                    ext2       236M  225M     0 100%
```

shows it is 100% full although there should be 9MB still available 5% approximately is reserved for the filesystem.  What you need to do is to remove some old kernel files.  Check the link below which is the official Ubuntu documentation on how to do that.  If you can't get it to work, start a new thread with a title something like boot partition full.  I don't use LVM so I don't have a separate boot partition and don't have this problem.  Good luck.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

---

### Post by kuv02 on 2015-11-28
It's not that easy. The article describes how to remove old kernels from inside a running system. I'm outside of the system, looking from Boot-Repair live system. So I'm stuck again. I have opened a [new thread]("http://ubuntuforums.org/showthread.php?t=2304584") for this. If the kernels als cleaned up, I will continue in this thread.

---

### Post by kuv02 on 2016-01-02
I just want to tell how I finally fixed the problem. It was much easier than I thought.

I completely ignored the "Unbuntu advanced boot options" menu in grub. There I could select to boot into the previous kernel.
From there I could remove older kernels via the package manager and finally perform the update to the newest kernel again.

---

