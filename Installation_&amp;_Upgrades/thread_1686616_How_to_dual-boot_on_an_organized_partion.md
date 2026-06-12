---
title: "How to dual-boot on an organized partion"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by F8M on 2011-02-12
I need help here.
When I go to Gparted, I get the following:
 
Partition---------File System-----Label-------Size-------Flags
/dev/sda1----------ntfs----------Vista------214.23GB-----boot-
/dev/sda2----------ext4---------Ubuntu-------78.12GB----------
unallocated-----unallocated-------------------4.49GB----------
/dev/sda3--------extended---------------------5.74GB----------
/dev/sda5-------linux-swap--------------------5.74GB

Now,how do I dual-boot WITHOUT LOSING MY UBUNTU FILES?
Thank you

---

### Post by metalf8801 on 2011-02-12
Your running Vista and Ubuntu on the same system so your already dual-booting. Can you try to reword your question?

Are you trying to use the unallocated space on your hard drive?

---

### Post by F8M on 2011-02-12
After reinstalling grub after installing Vista, it boots up in Ubuntu instead of the dual-boot page of windows/ubuntu option.

And as in regards to the unallocated space - should I flag it as a boot file instead of the ntfs(Vista).

Thanks for the quick reply.

---

### Post by metalf8801 on 2011-02-12
From what I can find the first thing you need to try is to update grub using this command 

sudo update-grub

---

### Post by metalf8801 on 2011-02-12
If that doesn't work take a look at this how to 
[http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub](http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub)

---

### Post by metalf8801 on 2011-02-12
> **F8M said:**
> After reinstalling grub after installing Vista, it boots up in Ubuntu instead of the dual-boot page of windows/ubuntu option.

And as in regards to the unallocated space - should I flag it as a boot file instead of the ntfs(Vista).

Thanks for the quick reply.

PS you should be able to run gparted from a live CD/USB to expand your existing Ubuntu partition to use the unallocated space. However, I would not mess with the partition that Vista is on. If you don't have a Ubuntu Live CD I would use Parted Magic (not partition Magic) which you can download here [http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)

good luck 
Dan

---

### Post by F8M on 2011-02-12
Thanks for the info Metalf8801. Let's do one step at a time. The following is the error I got from the sudo command.

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

If my unallocated space is 4.5GB, should I increase it to 7GB. Would that be big enough.
At the present time, I have both live CD's of Ubuntu & Vista.
Any suggestion would be helpful. Thanks Dan.

---

### Post by oldfred on 2011-02-12
You cannot run sudo update-grub from the liveCD. You run that after you have booted into your install.

Since you reorder partitions you probalby have to reinstall grub2 to the MBR and may have to run Vista repairs as the Vista NTFS boot partition has to match. 

I would fix Vista first with your Vista CD. Once you get Vista working then you can reinstall Grub2 from liveCD.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda2 and want grub2 in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

Note that the grub install is to drive sda not partition sda2 or any other partition.

---

### Post by F8M on 2011-02-12
Ok Dan I did the sudo update-grub comand again.

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
done
 
Now let´s see if it dual-boots.Thanks

---

### Post by F8M on 2011-02-12
Ok Dan, I got on the "GNU GRUB  version 1.98-1ubuntu7" Dual-boot page.
Wow, what a mess. I have 4 ubuntu versions. I'm gonna need your help on what to keep & what to get rid of - Here´s the list:

Ubuntu, with Linux 2.6.32-29-generic
Ubuntu, with Linux 2.6.32-29-generic (recovery mode)
Ubuntu, with Linux 2.6.32-28-generic
Ubuntu, with Linux 2.6.32-28-generic (recovery mode)
Ubuntu, with Linux 2.6.32-27-generic
Ubuntu, with Linux 2.6.32-27-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115 200
Windows Vista (loader) (on /dev/sdb1)

Now, where should I start. Any suggestions Dan. Thanks

---

### Post by metalf8801 on 2011-02-12
> **F8M said:**
> Ok Dan, I got on the "GNU GRUB  version 1.98-1ubuntu7" Dual-boot page.
Wow, what a mess. I have 4 ubuntu versions. I'm gonna need your help on what to keep & what to get rid of - Here´s the list:

Ubuntu, with Linux 2.6.32-29-generic
Ubuntu, with Linux 2.6.32-29-generic (recovery mode)
Ubuntu, with Linux 2.6.32-28-generic
Ubuntu, with Linux 2.6.32-28-generic (recovery mode)
Ubuntu, with Linux 2.6.32-27-generic
Ubuntu, with Linux 2.6.32-27-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115 200
Windows Vista (loader) (on /dev/sdb1)

Now, where should I start. Any suggestions Dan. Thanks

Ok you can remove old versions of the Linux kernel which is what thess different versions are using the Synaptic Package Manager 
System > Administration >  Synaptic Package Manager 
Just put Linux 2.6.32-24-generic, for example, in the text box then mark them for removal and then click apply. I would keep the 2 newest versions of the kernel in case you run into a driver problem with the newest kernel you will have a backup.

---

### Post by F8M on 2011-02-12
After more than three days of getting this dual-boot computer to work, I would like to thank Dan for the help. A Big Thank You.
Claude.

---

