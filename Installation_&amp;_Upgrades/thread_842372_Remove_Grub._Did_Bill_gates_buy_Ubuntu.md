---
title: "Remove Grub. Did Bill gates buy Ubuntu"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by BorgCymru on 2008-06-27
Well after trying everything to get this new version to work I have given up. It seems to me, with limited *geekness*, that this version doesn't like the SATA/PITA mix.

So I have decided to remove Ubuntu. Stick to Vista, although I am not a Gates fan it works.

How do I repair my MBR to remove all the grubs and super grubs I have tried ?

Thanks

OK  I'll get some flack saying 'It's all my fault, some of which it probably is, but looking at the last few weeks of posts I'm not the only one having problems.

But in my defence Ubuntu was working find since 6 until this new version so not all of the problems are mine.

I have deleted the Ext3 and SWAP partitions now and I am back to 3 partitions on my SATA now.

Shame as I loved Ubuntu for doing my music work on and learning all about it but enough is enough I need my computer to boot up and work.

---

### Post by ibutho on 2008-06-27
You can use a tool like [Super Grub Disk]("http://www.supergrubdisk.org/") to remove grub. If you have a windows boot disk, you can run fixmbr or fdisk /mbr if you get into rescue mode.

---

### Post by maphilli14 on 2008-06-27
Hope to see you back again sometime!  

----------------
Now playing: [Soundgarden - My Wave](http://www.foxytunes.com/artist/soundgarden/track/my+wave)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by ilrudie on 2008-06-27
Just as a note:  One of the main functions of Ubuntu Forums is free support so if it seems like everyone on the forums is having problems its probably because thats what the forums are here for.

---

### Post by BorgCymru on 2008-06-27
I do hope to be back soon. Maybe some advive on how to set my SATA drive up.

I wanted to have it so 

Partition 1 = Vista 40 GIG

Partition 2 = My Work/Files 400+ GIG

Partition 3 = Ubuntu 10 GIG

Partition 4 = Home 10 GIG

Partition 5 = SWAP 2 GIG

At present it is 

C:\ = Vista  40 GIG

D:\ = My Work/Files  426 GIG

E:\ Spare  101 GIG


I also have a PITA drive which has my music files on.

Seems this is the problem.

---

### Post by BorgCymru on 2008-06-27
Well after some major re shuffling of the partitions I now have it back as a dual boot system.

Boy was that hard work.

I'm not looking forward to plugging in the PITA drive, bet that throws it all out again. But I have noticed a sub section in the BIOS where you can organise the HDDs so I might have a see what that does.

---

### Post by Rallg on 2008-06-27
I offer the opinion that most Linux installers need to be re-worked. Back when Linux users were all technically advanced, the questions posed during installation were evident. But now many Linux versions, especially Ubuntu, are addressed to less advanced users. Answers to the installer questions are not obvious. Also, many new users expect that it is simple to "uninstall" software that you decide not to use, just by clicking a button; but operating systems cannot be removed in that manner.

What would benefit Linux: Have an all-in-one program that can make a USB memory stick bootable, and install GRUB there, whether or not any version of Linux is on the hard drive. Later, when a Linux installer CD is used, it should be able to detect a pre-made USB, and offer to update its GRUB menu to reflect the new installation, without touching the boot record on the hard drive. This should be done without asking the user to provide device numbers.

---

### Post by BorgCymru on 2008-06-27
So that the Ubuntu system would be on the USB stick ?

That would be good.

---

### Post by Rallg on 2008-06-27
You can already put Ubuntu (or other Linux) on a USB stick, if that's what you want. You can find instructions elsewhere on this forum, and in many other places. However, many folks say that if you write data frequently to a USB stick (as you would with an operating system there), it shortens the device lifetime.

No, I meant Ubuntu (or any Linux) on the hard drive, but without installing Grub or altering the MBR. Instead, a pre-existing Grub, on a USB, would be used. When you change the Linux, you update the Grub menu.

That's how I have my system. But it wasn't done automatically. I made a USB bootable, put DOS from my own Windows sytem, and added GRUB4DOS. I still have to manually change the Grub menu, each time there is a change to the Ubuntu kernel. But my hard drive has no change to its MBR. Without the USB connected and slected via BIOS at boot time, the system goes directly to Windows (no Grub involved). If I ever decide to remove Ubuntu, all I need to do is delete the Linux partitions and expand the Windows partition.

I think more people would use Linux, and there would be fewer issues, if the installer was pre-configured to do this.

---

### Post by fela on 2009-03-04
> **BorgCymru said:**
> I also have a PITA drive which has my music files on.

Seems this is the problem.

You have a pain in the *** drive?!?!?! Or did you mean PATA?

And apparently you can fix the MBR by running (as root I think):

```
install-mbr /dev/sda
```

where sda is the harddrive you want to remove grub from.

---

