---
title: "Clicked wrong grub option, cant load Ubuntu or Windows, 'grub rescue'"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by PitaParkour on 2012-10-17
Hi,

I accidentally clicked Load Windows Recovery Environment from the boot menu (the first time in a year and half of dual booting windows 7 and ubuntu 11.04).

Now all I am getting is
"error: no such partition.
grub rescue>"

Couldnt have happened at a worse time, I have got to Spain for 10 days to film a video and really need my laptop - I have absolutely nothing with me in terms of backups or recovery disks.

What on earth do I do? Will BootRepair help if I can manage to create a CD or USB with it on?

#FMLaptop.

---

### Post by darkod on 2012-10-17
If you know your ubuntu partition, you can boot from that prompt without anything else. Even if you don't know the partition.

If you do know the root partition, tell us.

If you don't, at that prompt execute this and post the result:
ls (that's small LS)

---

### Post by PitaParkour on 2012-10-17
Hey man,

Music to my ears. The root partition being where I put ubuntu or grub? Cant remember the terminology. They were all called /dev/sdaX from memory...

ls gives,
"(hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)

Any good? Thanks

---

### Post by darkod on 2012-10-17
Where you put ubuntu. Usually it is /dev/sda5 (partition #5) but in that case swap is /dev/sda6 and I don't see partition #6 in the ls results.

Anyway, you can check where the files you need are. We are looking for vmlinuz and initrd.img. You can check the partition one by one with:
ls (hd0,msdos5)

If they are not there, try with 1, 2 and 3.

When you locate the files, use that (hd0,msdos[COLOR="Red"]X[/COLOR]) and execute these commands one by one:
```
insmod part_msdos
insmod ext2
set root=(hd0,msdos[COLOR="red"]X[/COLOR])
linux vmlinuz root=/dev/sda[COLOR="red"]X[/COLOR]
initrd initrd.img
boot
```

If that boots you, note down this sequence on a piece of paper. In the worst case, you can boot like this temporarily. Not a pretty solution, but fast and useful if it works.

If you do manage to boot, you can also try this. Open terminal and execute:
sudo grub-install /dev/sda

That should return grub2 to the MBR and after you reboot it should work without the above sequence. That's the best case.

---

### Post by PitaParkour on 2012-10-17
all that each 'ls (hd0,msdosX)' including just '(hd0)' gives me is;
error: unknown filesystem

also tried smdos6 and that said no such partition.

I read a lot before install and either put my swap at the very beginning or very end so it didn't need to move if I was reformatting or overwriting installs.

I think ubuntu was either sda2 or sda5 but cant rmbr. I did choose to have all my folders on a separate partition to the root folder tho, again for ease of updating etc, and may have had some unresolved issues because they weren't in root...

---

### Post by oldfred on 2012-10-17
I think on some of the recovery software, the first thing it does is rewrite partition table. But you must still have it if your ls show several partitions.

May be best to run this just to see where everything is at. Post the link from running the BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by PitaParkour on 2012-10-17
Thanks oldfred,

I saw that before but I won't be able to get a CD til tomorrow, and just using the net on a friends Mac for now...    I will try launching from USB once the ISO has arrived but looks like the download will take a while getting here.

I'm only slightly worried that I can't see a usb boot option in my computers bios...   back soon (tomorrow).

Thanks to you both.

---

### Post by oldfred on 2012-10-17
On my computer the USB boot of a flash drive is from the hard drive menu not the USB menu. And flash drive has to be seen as bootable or correctly configured to boot.

Both of my computers are 6 years old and boot from USB drives. That was about the time they started to update BIOS to boot from USB2 devices.

---

### Post by PitaParkour on 2012-10-19
Hi,

My laptop booted from a copy of BootRepair on a USB made bootable with UNetBootin, and I clicked the recommended option.

The link it generated is [http://paste.ubuntu.com/1286783/]("http://paste.ubuntu.com/1286783/")

Now, powering on takes me straight into windows, and it only shows my two main partitions (Windows itself and my Storage partition) - the partition I installed Ubuntu on is not visible, and neither is swap (altho I cant rmbr if windows could see that). Not quite sure what BootRepair has done.

Is there a way to get Ubuntu/Swap/Grub back or is it looking like a new install is needed?

---

### Post by darkod on 2012-10-19
Boot-repair didn't do anything, it simply made booting windows possible.

I was worried about this. The recovery process that was fired off (by mistake, I know) started modifying your partition table right away I guess. Look at all those /dev/sdaXXX partitions. Basically, it started deleting your linux partitions.

From live mode, you could be able to recover them with testdisk. The instructions are here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I suggest you first do the deeper search and make a screenshot of the results. Then sit down and make sure you recover the correct partitions. Testdisk can list some older partitions that you deleted on purpose, so you will need to be careful what you tell it to recover. If unsure, ask here for an opinion first. The testdisk search screenshot will come very handy if you attach it to your post.

---

### Post by PitaParkour on 2012-10-19
Thanks darkod,

I did wonder if all the partitions listed were normally reported or if there was a different problem. I will give Test Disk a go shortly and report back with a screenshot.

Another linux user here has suggested that it might just be a case of running Ubuntu from USB and doing a grubfix from there? I guess thats not an option if the Recovery environment start fiddling with things prematurely.

Peter

---

### Post by darkod on 2012-10-19
> **PitaParkour said:**
> Thanks darkod,

I did wonder if all the partitions listed were normally reported or if there was a different problem. I will give Test Disk a go shortly and report back with a screenshot.

Another linux user here has suggested that it might just be a case of running Ubuntu from USB and doing a grubfix from there? I guess thats not an option if the Recovery environment start fiddling with things prematurely.

Peter

Correct, reinstalling grbu2 to the MBR will do no good, it will only stop windows from booting because the root partition with the grub2 config files is not readable.

If the recovery process only deleted the bootloader (as I was hoping at first), reinstalling grub2 would do the trick. But in this case when the partitions are nowhere to be seen, it doesn't help at all. Further more, to reinstall grub2 you have to pass a parameter telling it where is the root partition, and that partition is not even visible right now.

---

### Post by PitaParkour on 2012-10-19
Cheers Darko,

I will report back with TestDisk findings then. Got work to do first unfortunately.

---

