---
title: "Can't dd over an image onto a newer PC with NVME drive"
date: 2024-04-16
forum: Installation &amp; Upgrades
---

### Post by fizgig on 2024-04-16
I have an old image for an old product that would be almost impossible to recreate at this point from scratch so just starting over with a new ubuntu install and installing all the custom stuff isn't an option for me.  The good news is that I have been able to, in the past, just boot an empty computer with a ubuntu live usbstick with the dd image added to it and simply dd over the image onto the new drive on the new PC and it boots.

The image is based on ubuntu server 16.04.  It is new enough to include uefi grub on it.  The new computer doesn't have legacy boot mode but it does have secureboot which I turned off.  When the computer boots into UEFI, I can see the **ubuntu (NVMe) **option to select so it at least sees it there.  When I click on it to say boot from this I get a black screen with a non-blinking cursor in the upper left.  I need to make sure I'm clear that I am not seeing the Grub boot screen where you can select which kernel or whatever to boot, I'm talking about the UEFI configuration page (pressing esc when turning the computer on) which allows me to see boot options available.

I've tried a boot-repair thumb drive but it fails repairing (grub purge failed - or something like that).  I can boot the ubuntu 18.04 live thumbdrive again and I see the partitions on the NVMe:

```
Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048   1050623   1048576   512M EFI System
/dev/nvme0n1p2   1050624 226213887 225163264 107.4G Linux filesystem
/dev/nvme0n1p3 226213888 234440703   8226816   3.9G Linux swap
```

If I mount p1 and look, I see the EFI folder with ubuntu inside with its grub files.  P2 shows the usual linux file structure.  All looks well.

I even tried updated the /etc/fstab in p2 and /EFI/ubuntu/grub.cfg in p1 to point to the new UUID values (something I haven't had to do before) but no change.  Can anyone recommend anything else I can try?  Thanks!

---

### Post by fizgig on 2024-04-16
I have made a bit of progress.  When I boot off the ubuntu 18.10 thumbdrive, instead of choosing a grub entry, i press "c".  In that new grub menu, I can find my grub.cfg location by typing: ls (hd<tab> and looking around.  For me, it's in (hd1,gpt2)/boot/grub/grub.cfg.  So, if I then type **configfile (hd1,gpt2)/boot/grub/grub.cfg**, I get the usual grub menu I normally expect to see showing the boot option, which I select, and it boots from the dd'd image just fine.

Trouble is, I'm not sure how to make it so I don't have to do that every time.  The help I found was that, from my now-booted machine, I should be able to run: **sudo grub-install /dev/nvme0 **which runs without errors but I still can't boot it from startup - same black screen with non-blinking cursor.

Feel like I'm pretty close.  I tried the grub-install with /dev/nvme0**n1** as well but no dice.

---

### Post by fizgig on 2024-04-16
I got it to work by installing grub2 on my old system.  I guess the old version of grub didn't know how to handle nvme drives.

---

### Post by #&amp;thj^% on 2024-04-16
> **fizgig said:**
> I  I guess the old version of grub didn't know how to handle nvme drives.

You beat to that.. :)

---

### Post by yancek on 2024-04-17
> For me, it's in (hd1,gpt2)/boot/grub/grub.cfg.  So, if I then type **configfile (hd1,gpt2)/boot/grub/grub.cfg**, 

There is also a grub.cfg file on the EFI partition and if you had placed the above 'configfile' entry there and saved the change I expect it would have booted showing the menu from the grub.cfg file on the system partition, /boot/grub/grub.cfg.

---

