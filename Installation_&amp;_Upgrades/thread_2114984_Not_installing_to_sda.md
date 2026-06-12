---
title: "Not installing to sda"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by schander on 2013-02-11
Hi,
I have been trying to install 12.10. My system is as follows:
I have 6 x250gb disk attached to the main sata controller on the motherboard (x58). I have added a [u3s6]("http://www.amazon.co.uk/ASUS-U3S6-USB-SATA-PCIe/dp/B002VVQ58M") and atached to that is a 64gb ssd.

In the bios the boot drive is the 64gb ssd. Using the live cd I install to sdg (64gb ssd), using LVM option. However when it comes to install grub it fails, saying that it can't install to sda, after canceling the error i try and install to sdg1 and i get the same error.

I found this [bug]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1053687") which seems to be a duplicate of this [bug]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1053317") which is apparently fixed.

Can anyone help me out.

Thanks
Satpal

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by darkod on 2013-02-11
If the ssd where you are installing is /dev/sdg, then use the manual options to install and specify /dev/sdg for bootloader destination.

You can probably add only grub2 now, if it failed installing only grub2 to the MBR. From live mode post the output of:
sudo parted -l (small L)

That will show us all partitions.

PS. What are the 6 disks for, some kind of raid? SW raid? Fakeraid?

---

### Post by schander on 2013-02-12
> **ahallubuntu said:**
> Boot up your a live CD/live USB.  Where does your install disk now live?  If not sda, try repairing Grub and installing on whatever device id it shows up as.

There is an automatic boot repair, but I have repaired Grub manually many times using the "chroot" method:

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

although I haven't yet tried it with 12.10.  Works great with 12.04 though.

Thanks will have a look.

> **darkod said:**
> If the ssd where you are installing is /dev/sdg, then use the manual options to install and specify /dev/sdg for bootloader destination.

You can probably add only grub2 now, if it failed installing only grub2 to the MBR. From live mode post the output of:
sudo parted -l (small L)

That will show us all partitions.

PS. What are the 6 disks for, some kind of raid? SW raid? Fakeraid?
My idea was to try and run a XEN server on the system. So they would be SW Raid

Thanks for your help.
Satpal

---

### Post by schander on 2013-02-12
This is what I've just done:
Installed ubuntu to sdg with lvm:
Grub still failed to install. Initially it tried to install to sda again :confused:
Then I tried installing to sdg, sdg1 (boot partition), sdg5 (lvm with root and swap)
I followed the link:
[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)
Given that most everything was already mounted I followed the steps.

root@ubuntu:/# grub-install --recheck /dev/mapper/ubuntu-root 
/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.

This was error output of trying to install grub :(
Reading further down I uninstalled and reinstalled grub. Upon reinstalling i was asked which drive to install grub on I selected sdg and it seems to have installed correctly.

Going to reboot now and see if it's worked.
**EDIT:**
Just rebooted and I have been presented with a grub command prompt :(
So grub installed correctly however the boot config was not setup. Maybe i should chroot and then also issue the update-grub command, which is listed [here]("https://help.ubuntu.com/community/Grub2/Installing#Post-Restoration_Commands") on the page provided by ahallubuntu.

Satpal

---

### Post by darkod on 2013-02-12
Grub2 goes to the MBR of the disk, not to the root LV. The /dev/mapper/ubuntu-root is not where you should try to install it.

Assuming it installed correctly during your last attempt to sdg, are you sure you are booting from sdg?

When you are purging and reinstalling grub it is useful to run (while still inside the chroot):
grub-mkconfig

to make the initial config files. If you are not doing this from inside chroot, the command will need to be adjusted too.

Can you run boot-repair to create bootinfo summary and post the link so we can see the details? It's getting confusing and you are trying too many things at once.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by schander on 2013-02-12
> **darkod said:**
> 
Can you run boot-repair to create bootinfo summary and post the link so we can see the details? It's getting confusing and you are trying too many things at once.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I tried runing boot-repair however it just sit there with the progress bar pulsing, left it running for 20+ mins.
The following is the output from parted -l
```

Model: ATA ST3250318AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  250GB  250GB  ext4


Model: ATA WDC WD2500AAJS-7 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  250GB  250GB  ext4


Model: ATA VB0250EAVER (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  250GB  250GB  ext4


Model: ATA ST3250318AS (scsi)
Disk /dev/sdd: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  250GB  250GB  ext4


Model: ATA ST3250318AS (scsi)
Disk /dev/sde: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: ATA KINGSTON SNV425S (scsi)
Disk /dev/sdf: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2
 2      257MB   64.0GB  63.8GB  extended
 5      257MB   64.0GB  63.8GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-swap_1: 12.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  12.9GB  12.9GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 50.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  50.9GB  50.9GB  ext4


Model: CBM Flash Disk (scsi)
Disk /dev/sdg: 2121MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  2121MB  2121MB  primary  fat16        boot

```
I removed one of the disk, so sdf is the now the 64gb ssd.

Thanks
Satpal

---

### Post by darkod on 2013-02-12
Another reason could be that it doesn't want to boot from the sata card.

If you plan to use SW raid anyway, it doesn't really matter which disk is plugged where. You can try connecting the ssd directly to the motherboard, in the first sata port, so that it becomes sda.

And move one of the other disks to the sata card.

After you do that you will probably need to install grub2 to the MBR of the disk. If you move the disk and want to try adding grub2 to the MBR, let us know and I can provide the exact commands.

---

### Post by schander on 2013-02-13
> **darkod said:**
> Another reason could be that it doesn't want to boot from the sata card.

If you plan to use SW raid anyway, it doesn't really matter which disk is plugged where. You can try connecting the ssd directly to the motherboard, in the first sata port, so that it becomes sda.

And move one of the other disks to the sata card.

After you do that you will probably need to install grub2 to the MBR of the disk. If you move the disk and want to try adding grub2 to the MBR, let us know and I can provide the exact commands.
This sounds reasonable, the only reason I had the ssd on the sata card was that the port was sata III, which i don't have on my motherboard, however as it stands at the moment, I'm using a old ssd which is only sata II so it's not going to be a problem. IMO this should still be fixed in the installer.

I left boot-repair running and it seem to think that i was running raid? Could this be because of the GPT partitions?

I will move the disk and then ask for the commands to install grub2 to the MBR. Probably be tonight that i do it.

Thanks
Satpal

---

### Post by darkod on 2013-02-13
> **schander said:**
> 
I left boot-repair running and it seem to think that i was running raid? Could this be because of the GPT partitions?


Not because of the gpt but I think in one part of the script boot-repair doesn't understand LVM and incorrectly calls it raid.

The fakeraid (bios raid) devices are called /dev/mapper/... and the LVM devices also start with /dev/mapper/... and i think this might create the confusion. Just ignore that message.

---

### Post by schander on 2013-02-13
> **darkod said:**
> Not because of the gpt but I think in one part of the script boot-repair doesn't understand LVM and incorrectly calls it raid.

The fakeraid (bios raid) devices are called /dev/mapper/... and the LVM devices also start with /dev/mapper/... and i think this might create the confusion. Just ignore that message.
It doesn't allow you ignore it :( It tells you to install dmraid. I left it running last night after installing dmraid, didn't get chance to look at this morning before coming to work to see if it had come up.

Thanks
Satpal

---

### Post by darkod on 2013-02-13
dmraid is the package for fakeraid. Do you have fakeraid configured on your 6x250GB disks? Or maybe some of them have been used in raid before?

Linux can detect the meta data remains even if you don't have fakeraid configured right now. Many people don't destroy the previous array properly, or the fakeraid leaves meta data in any case, so to linux tools it might look like you have raid running.

---

### Post by schander on 2013-02-13
> **ahallubuntu said:**
> Boot up your a live CD/live USB.  Where does your install disk now live?  If not sda, try repairing Grub and installing on whatever device id it shows up as.

There is an automatic boot repair, but I have repaired Grub manually many times using the "chroot" method:

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

although I haven't yet tried it with 12.10.  Works great with 12.04 though.

I didn't want to go through the pain of change the port the ssd was one, so I thought I'd give the above another go.
Followed the instructions, checking each step. I managed to get grub to boot with a menu. When I booted the Ubuntu dots just kept spining. I did an alt-tab and it said:
fsck the root partition
Started the following daemons:
[LIST]
[*]mDNS/DNS-SD daemon
[*]Bluetooth
[/LIST]
And started the Cups printing spoller/server

Then it just sits there.... :(

When i got the recovery options most everything I try just hangs, freeing space, fsck, grub.

Thanks for your help
Satpal

**EDIT:** I booted the usb live and then just did another install onto the ssd. Failed the grub bit, just selected continue without grub install.
Rebooted Ubuntu booted. Thank you to everyone for helping.

---

