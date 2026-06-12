---
title: "Multiple bootable disks all with Ubuntu problem"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by jru on 2011-11-19
I have 3 internal drives with multiples copies of Ubuntu:
 
Disk one is my "main" drive (currently running 10.10 64bits)
Disk two is a "backup" of one (basically a disk image made with rsync).
Disk three is used to try new Ubuntu distributions (either as new installs or upgrades, currently 11.10 new install).

I select which disk I boot on startup with the BIOS.

That setup feels good to me: I have full redundancy with a MBR and grub2 on each disk.

One thing that drives me crazy is that every time I install a new distribution on disk three disk number one and two become unbootable! I am able to fix this by recovering the MBR and doing update-grub (it's quite a bit of error prone work). I would love to understand why!!



Note that my "bomb proof" setup has 2 other more minor annoyances:

update-grub attempts to find kernels all over the place on all disks. Depending where I run it from it gives grub menus in different orders; sometimes I get wrong UUID. I am simply trying to have the latest kernel from a given disk be the first entry of the menu on that disk. I don't want to see all the kernels on all the other disks (it's just too confusing as menu entries for the same kernel version are exactly the same).

Making the disk image backup with rsync is not as easy as I initially hoped for; but it works. I exclude the correct files (bellow), edit /etc/fstab UUID's, edit conf.d/resume UUID, run update-grub after on disk two after each update of disk one. I wish it was easier.

--exclude=/etc/fstab --exclude=/boot/grub --exclude=/proc --exclude=/etc/initramfs-tools/conf.d/resume --exclude=/media --exclude=/sys --exclude=/dev

---

### Post by darkod on 2011-11-19
Follow the link in my signature and run the boot info script. It shows detailed info about the boot process. It seems you have plenty ubuntu experience so you can probably understand the results without help, but if you don't mind you can also post it here included in code tags for easier reading.

One idea about your disks one and two: Why not a software raid1 mirror instead of rsync? I understand rsync has its benefits, but won't raid1 serve you better?

That will also give you one disk less and one MBR less to worry about.

---

### Post by boblemur on 2011-11-19
RAID while good against disk failure doesn't help if the reason why he is backing up is to always have a good config he can revert to, if you are only protecting against disk failure then raid is defiantly a better option (doesn't rely on you remembering to do it).

what do you mean that the other two drives become unbootable? as they not listed in grub? is grub missing? 

One option (admittedly kind hacky) is to go into your BIOS and disable the other two drives when you wish to install something on disk 3. (although this wont solve the problem when you want to run grub-update unless you turn them off then too).

With updating the UUID's you can use a little script something like:
```

set -e

rsync command 

sed -i '.bak' 's/UUID=<uuid of the first partition>/UUID=<uuid of the second partition>/'

(something similar to above but for the resume file)

```

---

### Post by oldfred on 2011-11-19
When you install to sdc, are you letting it install the grub2 boot loader to the MBR of sda?  And you rsync to another drive will not work as you found out as the UUIDs used by fstab & grub will be different on sdb from what they were in sda.

I use boot script before & after every install just to know what is where and to be sure I installed to where I thought I want. (I have installed to the wrong partiiton as I have a lot).

---

### Post by jru on 2011-11-19
> **oldfred said:**
>  > When you install to sdc, are you letting it install the grub2 boot loader to the MBR of sda?  

I am not sure: When I install from an installation CD it lets me pick which drive to partition and install. If I pick sdc I am was assuming that it should not touch sda and sdb MBR or grub; am I wrong about that? If I am wrong; is there a way to just have the installer touch one disk and leave the others "as is"? 


> And you rsync to another drive will not work as you found out as the UUIDs used by fstab & grub will be different on sdb from what they were in sda.

Yes... I edit the UUIDs (sed or ...) or if I am lazy replace them with the partition (/dev/sda1 ...)


> I use boot script before & after every install just to know what is where and to be sure I installed to where I thought I want. (I have installed to the wrong partiiton as I have a lot).

The boot script is very nice. Thanks to darkod and olfred for the recommendation. My output looks right currently ... not worth posting I think.

> Why not a software raid1 mirror instead of rsync?
I do like rsync over raid as I can boot either configurations.

> what do you mean that the other two drives become unbootable? as they not listed in grub? is grub missing?

If fails before it gets to the grub menu.  
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) is one way to recover 
Or this also works as a fix (booted on a drive that still works): 
dd if=mbrsda.bck of=/dev/sda bs=446 count=1,
sudo grub-mkconfig -o /mnt/a/boot/grub/grub.cfg,
fix the UUIDs in grub.conf by hand to the UUID of sdb1 (!))
I am not certain if the MBR or somehow grub corruption is the problem as I tend to try both. 


Thanks to all for the help.

---

### Post by jru on 2011-11-19
> **oldfred said:**
> When you install to sdc, are you letting it install the grub2 boot loader to the MBR of sda?  And you rsync to another drive will not work as you found out as the UUIDs used by fstab & grub will be different on sdb from what they were in sda.

I use boot script before & after every install just to know what is where and to be sure I installed to where I thought I want. (I have installed to the wrong partiiton as I have a lot).

I am not sure: When I install from an installation CD it lets me pick which drive to partition and install. If I pick sdc I am was assuming that it should not touch sda and sdb MBR or grub; am I wrong about that? If I am wrong; is there a way to just have the installer touch one disk and leave the others "as is"?

---

### Post by darkod on 2011-11-19
If you are using the manual partitioning option when installing, below the partitions list there is a field to select where the bootloader will be installed (on the latest 11.10 it is there, in earlier versions it was an Advanced button on the last step of the installer). The manual option gives you best control over partitions of course.

If you are using one of the auto options, I'm not sure how it goes because I never use them. But the guess would be that it installs grub2 on the same disk.

---

### Post by darkod on 2011-11-19
One more idea: Since you said you select with the bios boot menu from which disk to boot, I assume you don't actually need grub2 to search for and detect other versions of ubuntu on the other two disks.
The grub2 on each disk will boot only ubuntu on that disk. If you want another disk, you select it in the bios boot menu.

In this case you can disable the os-prober part of grub. I usually make it non-executable, so you can revert the change easily.

sudo chmod -x /etc/grub.d/30_os-prober

To create new grub.cfg after this change:

sudo update-grub

That will make each grub to boot its own ubuntu, not detecting the ubuntus on the other disks.

---

### Post by jru on 2011-11-21
> If you are using the manual partitioning option when installing, below the partitions list there is a field to select where the bootloader will be installed

Great, I will try that next time.

> Since you said you select with the bios boot menu from which disk to boot, I assume you don't actually need grub2 to search for and detect other versions of ubuntu on the other two disks. In this case you can disable the os-prober part of grub. I usually make it non-executable, so you can revert the change easily.
sudo chmod -x /etc/grub.d/30_os-prober
To create new grub.cfg after this change:
sudo update-grub

Great, exactly what I was trying to do! I will mark this tread "SOLVED".
Thanks for the help.

---

