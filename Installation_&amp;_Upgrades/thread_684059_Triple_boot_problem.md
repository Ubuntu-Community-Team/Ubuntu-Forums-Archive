---
title: "Triple boot problem"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by murlig on 2008-01-31
Hi all,

I previously had XP and MDK 8.x on my hard drive. I put in another HD and then installed 7.10 to have a triple booting system.

Yesterday, I installed pclinuxos in the mandrake partitions. I also installed the pclinuxos boot loader.

 I mounted the ubuntu drives and cut & pasted the ubuntu boot sections from my ubuntu menu.lst to the pclinuxos menu.lst

problem is that i cannot boot back to ubuntu. here are the errors:

FSCK on root partition, unable to resolve root=UUID=xxxx

now, i editted the menu.lst and replaced the UUID=xxx with /dev/xxx

this also does not make much progress.

what other ricks are out there, short of reinstalling 7.10 and installing all the updates since october?

thx

---

### Post by bucky0 on 2008-01-31
When you changed your menu.lst, did you rerun grub? Have you tried using the grub console to run the boot commands manually?

---

### Post by confused57 on 2008-01-31
> **murlig said:**
> Hi all,

I previously had XP and MDK 8.x on my hard drive. I put in another HD and then installed 7.10 to have a triple booting system.

Yesterday, I installed pclinuxos in the mandrake partitions. I also installed the pclinuxos boot loader.

 I mounted the ubuntu drives and cut & pasted the ubuntu boot sections from my ubuntu menu.lst to the pclinuxos menu.lst

problem is that i cannot boot back to ubuntu. here are the errors:

FSCK on root partition, unable to resolve root=UUID=xxxx

now, i editted the menu.lst and replaced the UUID=xxx with /dev/xxx

this also does not make much progress.

what other ricks are out there, short of reinstalling 7.10 and installing all the updates since october?

thx

What's happening is that the UUID on the partition you installed PCLinuxOS changed...you can leave the UUID in your menu.lst entry to boot Ubuntu.  You can edit your Ubuntu fstab to /dev/sda2(or whatever your PCLinux partition is or you can replace the incorrect UUID with the correct one.  Do you get a root prompt(#) after the UUID error?  If so edit your fstab to show /dev/xxx:
```
cp /etc/fstab /etc/fstab_backup
nano /etc/fstab
```
make the change to /dev/xxx, "Ctrl+X, y, enter" to save...reboot your computer.

If you're able to boot into Ubuntu, you can copy & paste the correct UUID into your fstab:
```
blkid
```
this should give you  the current UUID for your PCLinux partition.

Added:  You could also just comment out the Ubuntu fstab entry for your PCLinuxOS partition(place a # in front of)...this should enable you to boot into Ubuntu, then you can edit your fstab.

---

### Post by murlig on 2008-01-31
dear confused57,

i wanted to provide some more data.

firstly i can boot into pclinuxOS without problems.

This is my menu.lst (in the pclinuxos root partition) (at least the ubuntu settings)

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c312f8cb-235f-4202-ad17-f999145c224b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic

this is the output of grub (again run from pclinxOS
grub> find /boot/grub/stage1
 (hd0,6)
 (hd1,6)

here's the output from blkid (run from pclinxos)
dev/hda1: TYPE="ntfs"
/dev/hda2: UUID="C814-D00F" TYPE="vfat"
/dev/hda5: TYPE="swap" UUID="482bfd5c-8bc0-425b-89b4-4fdcc44a4057"
/dev/hda6: UUID="28b5e0e0-e51c-45e7-bc36-7d260fa16a99" SEC_TYPE="ext2" TYPE="ext                           3"
/dev/hda7: UUID="e6a81511-0cef-4d24-9ebd-e63d4c65fd72" SEC_TYPE="ext2" TYPE="ext                           3"
/dev/hdd1: TYPE="ntfs"
/dev/hdd5: TYPE="swap" UUID="08189afb-6510-4af1-a47e-035d26cdf47b"
/dev/hdd6: UUID="bfb78ff5-c6de-4ee2-8315-e1ad14d26609" SEC_TYPE="ext2" TYPE="ext                           3"
/dev/hdd7: UUID="**c312f8cb-235f-4202-ad17-f999145c224b**" SEC_TYPE="ext2" 
TYPE="ext      
note that UUID matches what's in the menu.lst

now please educate me on the correct settings to the menu.lst  so that ubuntu can boot properly or pls suggest what other data you would like to see.

thx again..

---

### Post by confused57 on 2008-01-31
It's not your Ubuntu partition's UUID that is causing Ubuntu not to boot...when you installed Ubuntu, an entry was added to /etc/fstab to mount your Mandriva partition, using UUID as the device.  When you installed PCLinux on the partition formerly occupied by Mandriva, the UUID for the partition changed...when you try to boot Ubuntu, it's trying to mount your former Mandriva in fstab, using the former UUID, which has changed...thus causing the UUID error that you're receiving.

Your Ubuntu partition should already be mounted in PCLinuxOS, either in /mnt/hdd7 or /media/hdd7...what you can do is edit your Ubuntu's /etc/fstab from PCLinuxOS:
From a terminal(konsole):
```
cd /media/hdd7/etc
or 
cd /mnt/hdd7/etc
```

Then you should be able to edit your Ubuntu fstab:
```
su
kwrite fstab
```

Comment out(place a # in front of) your PCLinuxOS partition in /etc/fstab...Then try rebooting into Ubuntu.
You probably should leave the root=UUID  in your Ubuntu menu.lst entry.

---

### Post by murlig on 2008-01-31
thanks confused57,

its all OK now, this reply is from ubuntu. here were the steps i followed.

- mounted ubuntu root drive to a drive in pclinuxos
- executed blkid 
- editted ubuntu /etc/fstab and matched *all* UUID's from blkid output.
(I'd forgotten that i has slightly resized the pclinuxos partition, so its UUID had also changed)

regards

---

### Post by confused57 on 2008-01-31
Glad to help...thought it would work, I've experienced the problem numerous times playing around with different distros...one day I'll remember to comment out the partition in fstab, before installing the new distro.

---

### Post by Brian96 on 2008-02-21
> **confused57 said:**
> Glad to help...thought it would work, I've experienced the problem numerous times playing around with different distros...one day I'll remember to comment out the partition in fstab, before installing the new distro.

Thanks for your help on this.

Question: Does commenting out the partition affect your ability to mount that partition in that distro?

---

### Post by confused57 on 2008-02-21
> **Brian96 said:**
> Thanks for your help on this.

Question: Does commenting out the partition affect your ability to mount that partition in that distro?
It shouldn't affect your ability to boot into the other distro...you can leave the fstab entry commented out or if you want to have the partition mounted in Ubuntu, you can change your /etc/fstab from UUID to /dev/xxx.  You can determine the  partition number with:
```
sudo fdisk -l
```
-l is a small "L"

Later, if you want to change it back to being mounted in Ubuntu using UUID, you can issue the blkid command to determine the new UUID, then you can use UUID instead of /dev/xxx in fstab.../dev/xxx should work just fine.  Make sure to backup your fstab before making any changes.

---

