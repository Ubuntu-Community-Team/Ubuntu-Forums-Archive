---
title: "Preparing to dual boot Windows 7 + 10.10"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by Berethorn on 2010-11-30
In a few days I'll be getting Windows 7 and a new hard drive, hoping to dual boot W7 and 10.10. I'm really just looking for confirmation before I go ahead and install anything and mess things up. :)

I have three hard drives. Windows will go on a 1TB HD, Ubuntu will take up part of a separate 500gb drive, and the other 500GB is NTFS storage.

Installing both OS from scratch, so I'll format those disks with gparted before installing Windows and then Ubuntu.

How should I format the Windows disk? A single primary NTFS partition?

And for Ubuntu, does this look right?:

15gb primary ext4 for root
XXGB ext4 for /home
4gb swap (to match RAM)


Am I missing anything? Thanks, just wanted to double check. I usually act first, ask questions later, but I'm being more cautious this time. :)

---

### Post by sikander3786 on 2010-11-30
Regarding Windows, you can choose any setup. Can install it on the whole HDD or make multiple partitions. I would recommend to give your Windows install some space, say 200 GB (if you are curious :P I have been comfortable with less than 100 GB on Windows 7) and add up all the left space to another NTFS partition and share it between Windows and Ubuntu.

I know you've got an extra 500GB NTFS drive but sharing the first one won't hurt either. If you think you'll have lots an lots of programs on C: drive, you can create a single 1TB partition for that.

Regarding Ubuntu, as you've got lots of space, I would recommend to extend the root space to something like 30-40 GB (you might not need that but you might need that at some point as well). /home and swap partition as you mentioned above.

And I think you know pretty much about Grub2 dual boot so you didn't ask that :-)

---

### Post by Berethorn on 2010-11-30
Well, I was hoping Grub would take care of itself after I installed Ubuntu. I'll just tweak the boot file if I need to. :)

Now I'm curious, since Windows will be on NTFS, why create a separate partition on that drive - Ubuntu will be able to access it anyway? Of course it's nice to keep things neat and tidy and separated, but is there another reason?

Thanks for the reply. :)

---

### Post by sikander3786 on 2010-11-30
Yes Grub will surely take care of dual boot but make sure you install Grub to the MBR of Ubuntu hard disk and make that your first boot device in Bios. It would also work if Grub gets installed to the MBR of Windows HDD or even the 3rd HDD but *"it's nice to keep things neat and tidy and separated"*. And if you install Grub to the Windows HDD, you will lose Windows bootloader and will need Grub to boot Windows unless you restore Windows bootloader. If Grub is installed to Ubuntu HDD and somehting bad happens to that HDD, Grub dies or Ubuntu gets broken somehow, you'll only need to change the boot device in Bios and you'll gain access to Windows regardless of Grub ;-)

In 10.10's installer, you'll get an option for location of Grub at the bottom of Manual Partitioing page. Identify and select the correct hdd e.g, sda, sdb or sdc.

For identifying HDD,

```
sudo fdisk -l
```

Yes you can access the whole Windows HDD. NTFS-3G driver is stable enough and shouldn't mess anything there. But you know when Windows drive is mounted in Ubuntu, you easily see all the files that are otherwise hidden/system files when you are using Windows. You can delete any of them by mistake...

And Windows doesn't like many changes to its partition with it being notified. So always better/safer not to mount Windows drive in Linux ;-)

But that is always your own call. I am not saying you cannot or shouldnot mount it under Ubuntu. I am only mentioning what I consider safe ;-)

---

### Post by Berethorn on 2010-11-30
Hmn, I'll have to decide between safety and convenience. 

Thanks for the help, I feel better about proceeding now. :D

---

### Post by sikander3786 on 2010-11-30
My Pleasure :P

Safety or Convenience.... Or both.

Feel free to ask any further :-)

---

