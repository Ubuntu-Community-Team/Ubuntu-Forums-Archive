---
title: "Installed 9.10 on external HDD - question RE: GRUB on internal HDD"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by MattP220 on 2010-01-16
A few weeks ago I installed 9.10 on an external hdd, but unfortunately I forgot to install GRUB exclusively on that disk. I found this out the other day when I tried to boot into Win (Vista) without the external drive attached; it gives me a "disk not found" error.

For the moment this isn't a problem since my laptop isn't going anywhere, but just for future reference I'd like to solve the matter. I've downloaded a copy of SuperGrubDisk, which I discovered in other threads here, so I can probably restore it using just that.

What I want to know is this:

I have an existing install of 8.04 on a partition on the internal disk, which I've been planning to nuke because it's too far gone to recover - all the files and whatnot are transferred off it, so I just have to use the live disc to pave over it with a fresh install 9.10.

If I do that, a fresh install on the internal HDD, will it reinstall GRUB properly? And will that screw up the loader for my external drive? 

Cheers.

---

### Post by Leppie on 2010-01-16
> **MattP220 said:**
> I have an existing install of 8.04 on a partition on the internal disk, which I've been planning to nuke because it's too far gone to recover - all the files and whatnot are transferred off it, so I just have to use the live disc to pave over it with a fresh install 9.10.

If I do that, a fresh install on the internal HDD, will it reinstall GRUB properly? And will that screw up the loader for my external drive?
yes, it will re-install grub to the internal hdd.
and yes, it will remove your grub entries to your external hdd.

what you could do is plug in the external drive, boot into system on the external drive and install grub2 to the mbr of the external drive. after this you can install karmic on the internal drive and install grub2 to the mbr of the internal drive. you can then use the bios option to boot usb first, so you can boot from your external drive.
if you want, you can then update the grub config of the external drive to add the newly installed system on the internal drive to the menu of the exernal drive and you're all set

---

### Post by kansasnoob on 2010-01-16
Actually I've found Super Grub Disk to be a bit of a pain since grub2. It works fine just for booting, not so much for actually restoring things.

Even their own website recommends using the older disc, but that aside what we really need to be able to sort this out is the output of the Boot Info Script with all drives plugged in as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Then we should be able to restore the proper bootloader to the proper drive's mbr, etc.

Without that there's too much guess work involved.

---

### Post by MattP220 on 2010-01-16
Do you need the entire file? It's rather long.

---

### Post by MattP220 on 2010-01-16
[This thread]("http://ubuntuforums.org/showthread.php?t=1195275") on GRUB2 and [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435") both list this as an option:

```
sudo dpkg-reconfigure grub-pc
```

My internal hdd is sda (with Vista/8.04), and the external is listed as sdb (with 9.10 filesystem and /home partitions) - so if I understand this right, what I want to do after running that command is to move the GRUB to sdb (external hdd)

Then reinstall GRUB2 with 9.10 on my internal hdd. 

Am I on the right track?

---

### Post by kansasnoob on 2010-01-16
> **MattP220 said:**
> Do you need the entire file? It's rather long.

Yes. Just right click it, choose Compress, then here at the forum reply form click on the paper clip thingy and follow the instructions to attach.

---

### Post by MattP220 on 2010-01-16
> **kansasnoob said:**
> Yes. Just right click it, choose Compress, then here at the forum reply form click on the paper clip thingy and follow the instructions to attach.

Excellent. I've attached the file.

---

### Post by kansasnoob on 2010-01-17
Sorry to take so long. Just going to look this over now.

---

### Post by kansasnoob on 2010-01-17
This is fairly simple. From this:

> => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=837aaaaf-dd76-45fd-ac5a-8f62b20457d7)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

We can see that Karmic's grub2 installed to the mbr of the Windows/Hardy drive (sda) instead of sdb. That's simple to fix.

Just so you know how to see where grub/grub2 is going to install in the future, and change it if need be look at this:

[ATTACH]143896[/ATTACH]

The background screen is the final screen you see during installation where you can review the installation info you've provided and choose to Quit, Go Back, or Proceed. If you click on the Advanced button in the lower right hand corner the screen in the foreground pops up and you can see where the bootloader is going to be installed.

It is seldom a good idea to install a bootloader to a partition, ie: sda1, sdb3, etc. You almost always want the bootloader installed to the mbr of the "boot" drive. In this case you wanted it on the USB drive or /dev/sdb. Of course you must also have the system BIOS set to boot the USB drive before trying to boot an internal hard drive.

Anyway, to fix this just boot into your Karmic installed on the external drive and run these commands:

```
sudo grub-install /dev/sdb
```

If that returns any errors:

```
sudo grub-install --recheck /dev/sdb
```

Then to make grub2 recognize the changes:

```
sudo update-grub
```

Wait until it says "done"!

Now to make the Windows drive bootable until you reinstall your choice of *buntu on that drive you can give it a generic Windows readable mbr while you're still in Karmic with a couple of simple commands: 

Note: we're only using "lilo" as a tool so we'll remove it when we're done so it doesn't somehow mess with the grub2 configuration later on.

```
sudo apt-get install lilo
```

Ignore the warning and just press the Enter key.

```
sudo lilo -M /dev/sda mbr
```

```
sudo apt-get remove lilo
```

Now if your BIOS settings are correct you should be able to choose either Ubuntu or Windows when the external is plugged in, or just boot directly into Windows if the Ubuntu drive is not plugged in.

When you install the new *buntu on the internal drive I'd just be sure to **not** have the external plugged in. That way it's mbr should be left alone.

Of course the first time you boot into the external drive after reinstalling Ubuntu on the internal you'll want to run:

```
sudo update-grub
```

So it recognizes the changes.

Screenshot courtesy of Herman's Illustrated Dual Boot Site:

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by MattP220 on 2010-01-17
Excellent stuff! That seems to have gotten me sorted.

Cheers!

---

