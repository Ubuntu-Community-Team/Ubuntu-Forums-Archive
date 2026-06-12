---
title: "Changing grub default root and prefix"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by michael8 on 2013-07-31
My ubuntu partion changed, and now I'm having trouble booting.  It was (hd0,gpt5), now it is (hd0,gpt6).
So, when I start my computer, I have to type
```
set prefix=(hd0,gpt6)/boot/grub
set root=(hd0,gpt6)
insmod normal
normal
```
Is there a way that I can change the defaults?
I've tried using boot-repair - no effect.
I've tried boot-repair's advanced repair - nothing
I've tried reinstalling grub using grub-install - successful, but still wrong defaults.

Is there anything short of reinstalling Ubuntu that I can do?



PS, I have another account on here somewhere, I just don't remember the username or email.  In it, I pointed out that one of the files in the 12.04.2 disk was named wrong, after I downloaded the disk four or five times having the wrong md5 sum.  If an administrator could link them, I'd appreciate it.

---

### Post by grahammechanical on 2013-07-31
Have you tried ?

```
sudo update-grub
```

  That will run Grub OS-prober utility. It may identify where you are running the command from. Ubuntu/Grub boot parameters usually use a Universally Unique  Identifier (UUID) to distinguish each partition. So, if we add a partition the label of sda1; sda2 will change but the boot parameters would still point to the correct partition.

Regards.

---

### Post by michael8 on 2013-07-31
That would update the grub.cfg script - however, does not solve the problem of grub being unable to find the partition grub.cfg is stored on.
In other cases, reviews said to fix the mbr.  However, I use UEFI/GPT and so don't have MBR.  (Sorry, forgot to mention this)

---

### Post by dino99 on 2013-08-01
im not used with gpt, but ive got an issue on my end too : this seems that update-grub does not call os-prober as it might. After running both commands, my issue were gone

sudo os-prober
sudo update-grub

---

### Post by oldfred on 2013-08-01
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If booting with UEFI, I would think Boot-Repair should have reinstalled grub to the efi partition. It probably is core.img that needs updating which a reinstall to the MBR with BIOS or to efi partition with UEFI should update.

If you can boot does this reset with UEFI? I know it works with BIOS.

With UEFI you reinstall to the efi partition.

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

