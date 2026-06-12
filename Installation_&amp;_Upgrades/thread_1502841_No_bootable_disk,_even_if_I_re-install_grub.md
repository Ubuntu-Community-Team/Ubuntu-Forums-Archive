---
title: "No bootable disk, even if I re-install grub"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by sydesy on 2010-06-06
Hi all,

Installed a 9.10, updated to 10.4 and everything was fine until I booted on the Win7 partition, and its update/anti-virus/something decided to fubar the mbr.

I tried to reinstall grub using that method (I have a live CD 10.4 64)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
or by 
mount /dev/sda5 /mnt
chroot /mnt
grub-install

Neither works, I don't have the grub menu, just the laptop (acer4810) saying that it can't find a bootable disk. 

I have 6 partitions where I have probably messed up quite a few things while trying to recover. 

/dev/sda1   *           1        1530    12288000   83  Linux
/dev/sda2            1530        1543      102400    7  HPFS/NTFS
/dev/sda3            1544        6578    40443637+   7  HPFS/NTFS
/dev/sda4            6579       38913   259730857    5  Extended
/dev/sda5            6579       37598   249168118+  83  Linux
/dev/sda6           37599       38913    10562706   82  Linux swap / Solaris


The main original partition is sda5, that was the one working. The bootable partition was one of the windows one, not sure if it was sda2 or sda3 (tried both, neither work).

Out of desperation, I tried to install a new linux on sda1 (where the acer recovery partition was), but doesn't work either. 

Can boot from the live CD, can't from the hd.

Do you have any suggestion? Is there a way to check that the mbr is there, and points to the right partition?

Been using the laptop for a week by booting on the live cd, then chroot on the main partition and mostly work, but not fun at all, and I'd really like to have a hard disk that boots again.

Xavier

---

### Post by sydesy on 2010-06-06
I'm adding the result of boot_info_script055

I have tried either sda1 or sda5, no difference, still the no bootable disk error message.

---

### Post by darkod on 2010-06-06
The grub2 reinstall commands are wrong. You should have asked in the forum before trying to reinstall ubuntu just to get grub2 back.

From live mode:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should get your ubuntu from /dev/sda5 booting again.

Lets look at the results file what else is going on after everything you tried.

---

### Post by darkod on 2010-06-06
/dev/sda3 is not recognized as win7 system partition, and that doesn't look good. Also, I don't know how but you have Grub2 files ending up on the win7 boot partition /dev/sda2.

---

### Post by sydesy on 2010-06-06
> **darkod said:**
> /dev/sda3 is not recognized as win7 system partition, and that doesn't look good. Also, I don't know how but you have Grub2 files ending up on the win7 boot partition /dev/sda2.


Hi,

As for the win7 partition, that's not a big problem if it goes missing, right now my main concern is to get back ubuntu ;)

As for the grub there, I did try to install it in this partition as well (yeap, stupid).

Ok, I've run your command as suggested, I'm rebooting and let you know.

---

### Post by sydesy on 2010-06-06
> **darkod said:**
> 
From live mode:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should get your ubuntu from /dev/sda5 booting again.



Unfortunately, it didn't. Still have the same message "No bootable device -- Please restart".

When I go on the bios, I don't have the IDE0 listed in the page to set the boot order, even so it says it has the disk listed in the devices.

I tried to set the sda1 as the boot disk (the fresh install I did on the first partition on sda1), same no bootable device error message.

Seems that the file is too big, put the result of boot_info there:
[http://pastebin.com/Xjb2mNV8](http://pastebin.com/Xjb2mNV8) (trying to boot on sda1)

Any more suggestions?

---

### Post by oldfred on 2010-06-06
No bootable device sounds more like a BIOS error. There are some BIOS that check for a boot flag on a primary partition. I do not know if it now check for windows in that partition. Grub does not use the boot flag.
You may want to check and see if that is a setting in BIOS. And move boot flag back to the windows partition.

Windows/NTFS does not see capitals different than small letters so you  have two boot folders and windows cannot deal with two folders. You have to delete the /boot folder, do not delete the windows /Boot folder.
/Boot/BCD  /boot/grub/core.img

---

### Post by darkod on 2010-06-06
You have only one hdd, so boot options in BIOS are rather simple. You just control boot devices, not exactly hdds.

When you mentioned win7 had some anti-virus or what ever issues, were they anti-virus or virus? :) I'm just thinking if you got one of those nasty viruses messing up everything.

The script still can't mount /dev/sda3 properly to report it. But fdisk sees it as ntfs.

Maybe the boot error comes from that too?

Otherwise, /dev/sda1 has the boot flag on it, so it's not like it's missing totally.

---

### Post by sydesy on 2010-06-07
> **darkod said:**
> You have only one hdd, so boot options in BIOS are rather simple. You just control boot devices, not exactly hdds.


Ok, big progess: The issue seems to be on the bios, not on the HDD. I have my live CD on a memory card, did the suggested change, rebooted, got the bios flashing info about the HDDs and I pressed to take out the card and try booting on the HDD,  AND IT WORKED.

A tried to reboot, and I still have the bios message about no bootable devices.

switched it off/on, with the live cd on memory card, waited until I got the bios msg, then took the card off, and it booted for the HDD.

Just having the flag bootable doesn't seem to be enough (I tried to put it on partition 1, 2 and 3, doesn't boot. Having a bootable partition with grub doesn't seem to be enough either (otherwise, it would have booted on sda5

Do you have any idea ? what should I install on one of the partitions to make the bios happy ?

> **darkod said:**
> 
When you mentioned win7 had some anti-virus or what ever issues, were they anti-virus or virus? :) I'm just thinking if you got one of those nasty viruses messing up everything.


Hey, I solved it as I've learnt to do it on windows: by clicking "yes" on random popups that come on a regular basis. Might have been "next" instead of yes, but unfortunately, remains the same: no clue what I did.

> **darkod said:**
> 

The script still can't mount /dev/sda3 properly to report it. But fdisk sees it as ntfs.

Maybe the boot error comes from that too?



Now that I am on my normal ubuntu, I still can't mount sda3. I certainely have frozen the laptop several times, and that's likely that at least once it happened with sda3 mounted. is this possible to inspect/restore a win7 partition from ubuntu ?

Again, don't care that much about windows 7, but I would like to be able to boot from the hdd, without having to have the memory card trick ;)

Thanks for your help so far, it is certainly very appreciated.

X+

---

### Post by darkod on 2010-06-07
Yes, grub2 doesn't care about the boot flag although some BIOS version do need a boot flag present on one partition.
I don't know what to say about the memory card issue. I really can't see how it would influence whether it boots from the hdd successfully or not. Earlier in the posts you seem to execute the commands to reinstall grub2 on the MBR of /dev/sda, and it should be there. So just booting without the card, from the hdd should work fine.

---

### Post by sydesy on 2010-06-07
> **darkod said:**
> Yes, grub2 doesn't care about the boot flag although some BIOS version do need a boot flag present on one partition.


It seems to be the case, but I've tried to put it on the partitions (tried only 1, only 2 and only 3. Didn't help

> **darkod said:**
> 
I don't know what to say about the memory card issue. I really can't see how it would influence whether it boots from the hdd successfully [QUOTE=darkod;9424350]

My _guess_ was that the bios didn't detect any bootable partition (or with the right formatting, or the right whatever it is testing), and hence didn't try booting (no bootable device error msg). Having the livecd on the memory card (syslinux) kept the bios happy and willing to try booting, and taking out the card before the boot would force it to try the hard disk, and succeed. 

Might be 100% wrong, obviously.

[QUOTE=darkod;9424350]

Earlier in the posts you seem to execute the commands to reinstall grub2 on the MBR of /dev/sda, and it should be there. So just booting without the card, from the hdd should work fine.

It does boot fine, the problem seems to be before that, and to try convincing the bios to have a go at reading the mbr on sda. 

Yeap, weird.

Found that thread about the same bios 
[http://forum.notebookreview.com/sony/403065-problems-installing-x64-os-my-vgn-z21wn-b-3.html](http://forum.notebookreview.com/sony/403065-problems-installing-x64-os-my-vgn-z21wn-b-3.html)


> It's a Windows/BIOS issue. As soon as the Windows installler detects an EFI it requires a GPT layout.


They seem to suggest try changing to boot order (find it weird, in my case IDE0 isn't in the list of bootable part anymore);

---

