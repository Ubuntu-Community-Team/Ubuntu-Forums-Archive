---
title: "Ubuntu (fake)RAID installation problems"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by IrrationlArtist on 2012-06-16
I would really like to install Ubuntu on a small partition on my main desktop. However, this machine has some sort of RAID configuration.

Let me begin by saying that I don't really know what RAID is or why its affecting my disk. It's a 1.5 TB with Windows already on it, and a recovery partition. I'm fairly sure it is only 1 disk, which would make this fakeRAID?...

I started off thinking this would be no problem. I defragged/resized the partition in Windows, booted into Linux, created a small 30GB partition with GParted, gave myself some swap, and started up Ubiquity. Only Ubiquity refuses to play nice with the disk.

I did some research on dmraid but I still don't really understand what it is / what I'm doing and I *cannot* screw up this machine, as it is used by other members of my family who would be boiling mad if it was down for even a day. 'dmraid -r' returns this:


/dev/sda: pdc, "pdf_fcbchegef", stripe, ok, 2930146048 sectors, data@ 0

After this, Ubiquity will at least recognize the disk as /dev/sda, but won't show any partitions. 

How can I fix this? Thanks beforehand for your help.

---

### Post by darkod on 2012-06-16
The term fakeraid is not because of one disk. It's used to specify raid implemented on the board/bios, hence fake because there is no dedicated hardware raid controller card with it's own cpu and memory. It uses the system cpu and memory.

If you are sure you have only a single 1.5TB disk, your problem is that it was used in fakeraid and still has meta data remains. Windows ignores this and works fine like it would on a single disk, but linux gets confused thinking the disk is part of a raid array.

You can remove the meta data from live mode with (but do this only if you ARE SURE you ARE NOT running raid):
```
sudo dmraid -E -r /dev/sda
```

Confirm, and that's it. It should install fine after that.

To double check how many disks you have (only /dev/sda or /dev/sdb too), you can use:
```
sudo fdisk -l
sudo parted /dev/sda print all
```

---

### Post by IrrationlArtist on 2012-06-16
I am 100% sure that I have only one 1.5 TB disk.

However, when I experimentally disabled RAID in the BIOS, Windows 7 failed to boot.

Does this mean that Windows is using RAID?

---

### Post by darkod on 2012-06-17
I am not sure. It could be that win7 doesn't like the change only.

For example, if you install a dual boot when the SATA mode is in IDE in the bios, and then change it to AHCI, ubuntu will continue working while win7 won't. It doesn't like the change from IDE to AHCI.

So, your staa mode needs to be in AHCI before you start. Or you need to make a change in the windows registry before doing the change IDE to AHCI in the bios.

But I am not sure if that applies to RAID too. You shouldn't even have RAID active in bios if you were not using it.

---

### Post by IrrationlArtist on 2012-06-17
So you're saying I should try something like this:

[http://www.askvg.com/how-to-change-sata-hard-disk-mode-from-ide-to-ahci-raid-in-bios-after-installing-windows/](http://www.askvg.com/how-to-change-sata-hard-disk-mode-from-ide-to-ahci-raid-in-bios-after-installing-windows/)

and then try to install Ubuntu?

---

### Post by darkod on 2012-06-17
According to that article, it looks like it. Since you are running it in RAID mode right now, don't forget to set the RAID key to 0 also, as mentioned in the article.

Note that I have never tried anything like this, but it does sound like the right thing to do so that you can use your windows in AHCI.

After that you will remove the meta data using dmraid and install ubuntu.

---

### Post by IrrationlArtist on 2012-06-22
I tried modifying the registry as described in the article and then switching to AHCI, Windows would still not boot. 

Still looking for solutions, if I find another one I'll post it.

---

### Post by ben aveling on 2012-06-24
What sort of PC?

I am struggling with RAID too. See [http://ubuntuforums.org/showthread.php?t=1988364](http://ubuntuforums.org/showthread.php?t=1988364), maybe the problem is similar.

Can you boot from a live disk?  

Is so, maybe try "sudo blkid -l" then share what you get?

---

