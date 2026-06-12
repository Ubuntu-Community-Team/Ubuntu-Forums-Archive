---
title: "Boot problem, please help"
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by paulmcg on 2020-04-15
A few weeks ago I tried to set up file sharing and then couldn't reboot, it just hung.  I've partitioned the drive and installed a second user on sda4, to which I can boot.  I've run boot-repair many times and even been able to boot onto my sda2 user straight after running boot-repair but no longer.

I wonder if someone could look at my output from my latest boot-repair to see if the problem can be solved:  [http://paste.ubuntu.com/p/QRjfK89PcF](http://paste.ubuntu.com/p/QRjfK89PcF).  I did notice my boot/efi directory was empty on sda2.

Here's some other ones, if that helps: jPK4XFNVDK or XzSxGVQfRT

Thanks Paul

---

### Post by yancek on 2020-04-15
> installed a second user on sda4, to which I can boot. 

The boot repair output shows that you have installed a second instance of Ubuntu 18.04 on sda so now you have Ubuntu 18.04 on both sda2 and sda4.  Boot repair also shows that when you ran it, you were booted into the Ubuntu on sda2, line 12 of boot repair.  You should be able to verify this when booted into Ubuntu and from a terminal run:  df -h  Under the Mounted on column you should see /

> /dev/sda2:The OS now in use - Ubuntu 18.04.4 LTS CurrentSession:linux 

---

### Post by oldfred on 2020-04-15
See line 973 & 989.
I have never seen two ESP folders with Ubuntu.
In Linux case makes a difference. But in Windows and then FAT32 case is not used. So then you have duplicate folders which I think would create all sorts of issues.

Since boot stanza is identical, I would delete the one in lowercase.
> sda1/[COLOR=#ff0000]EFI[/COLOR]/ubuntu/grub.cfg
sda1/[COLOR=#ff0000]efi[/COLOR]/ubuntu/grub.cfg

My mount of ESP is /boot/efi
And ESP has /EFI/ubuntu.
Or full path once system starts is /boot/efi/EFI/ubuntu.

---

### Post by paulmcg on 2020-04-16
Yes, that what I did.  It's the install on sda2 that is having the problems.

---

### Post by paulmcg on 2020-04-16
If I go to where sda1 is mounted the directory structure is boot/efi/EFI/BOOT, boot/efi/EFI/ubuntu, boot/grub.  The boot/efi/EFI/ubuntu contains shimx64.efi which is missing from the grub menu on startup.   boot/efi is empty apart from the EFI directory.  So the full path looks like yours.  I'm not clear as to what I should delete.

It's interesting that boot/efi/EFI/BOOT contains: bkpbootx64.efi, bootx64.efi, fbx64.efi, mmx64.efi and  boot/efi/EFI/ubuntu contains: fwupx64.efi, grub.cfg, grubx64.efi, mmx64.efi, shimx64.efi.  On booting the grub menu is:

Ubuntu
Advanced options for Ubuntu
EFI/BOOT/bkpbootx64.efi
EFI/BOOT/fbx64.efi
EFI/BOOT/mmx64.efi
EFI/ubuntu/fwupx64.efi
EFI/ubuntu/mmx64.efi
Unbuntu 18.04.4 LTS (18.04) (on /dev/sda4)
Advanced options for Unbuntu 18.04.4 LTS (18.04) (on /dev/sda4)
UEFI Firmware Settings

Selecting ubuntu leads to the boot failure (hanging) and selecting Unbuntu 18.04.4 LTS (18.04) (on /dev/sda4) works but is not the user I want.

Would deleting boot/efi/EFI/BOOT be really bad?

I'm very close to reformatig the hard drive and installing unbuntu, I have a copy of my data.

---

### Post by paulmcg on 2020-04-16
Here's an odd thing.  Selecting Advanced options for Ubuntu then Ubuntu, with Linux 5.4.0-21-generic works!  I suppose I could just run with that.

---

### Post by paulmcg on 2020-04-16
Doesn't work a second time!

---

### Post by oldfred on 2020-04-16
The files in /EFI/Boot are the fallback or backup emergency boot.
Originally bootx64.efi would be a copy of Windows .efi boot file. But grub makes it a copy of shimx64.efi.
Boot-repair does that also, and makes the bkpbootx64.efi as a copy of the previous bootx64.efi, just in case you need it.
Boot-Repair may also add additional boot entries and puts them into 25_custom so grub-update includes them in the grub menu.

One of your entries looks like an BIOS boot? Direct entries to sda4?

Better to post exact output from 
sudo efibootmgr -v

---

### Post by paulmcg on 2020-04-22
So I'm able to boot with an advance option: Ubuntu, with Linux 4.15.0-96-generic every time and sometimes the default.  Here's the output from sudo efibootmgr -v:

BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001
Boot0001* ubuntu    HD(1,GPT,3e0ec810-de88-4cd7-96db-4e8227953163,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)

I removed the old windows boot 0000 a few days ago.

---

### Post by oldfred on 2020-04-22
That shows booting from first partition with the GUID of 3e0... using shimx64.efi.
That looks normal for an Ubuntu boot entry.
You can see GUID, which are also known as partUUID.
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

In /EFI/ubuntu/grub.cfg is a three line grub configfile to load the full install of grub from one install. Then from that grub you should be able to boot any other installs you have.

```
fred@fred-Z170N-focal:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid b913e1bc-6f08-4984-b653-9a604d95470a root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
fred@fred-Z170N-focal:~$ 

```
You may have permission issues seeing the ESP files from inside your install. Your fstab mounts with no permissions by default.

---

### Post by paulmcg on 2020-04-23
I really appreciate your help but I don't understand your response, at the moment grub works.  Is it possible that upgrading to 19.10 would solve the problem?

---

### Post by oldfred on 2020-04-23
Not a fan of upgrades, some have them work, but you have to have a vanilla install or remove all ppa and proprietary drivers like nVidia or wireless, if those are installed.

Note that 20.04LTS Long term support version just came out.
Standard upgrade to that will not be available until the point release or 20.04.1 is released in several months. 
But you can upgrade or reinstall with 20.04 now.

---

