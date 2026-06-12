---
title: "Grub Issues, Help Please"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by jpichie on 2010-01-01
Hey All:
Here is my dilemma, I love Linux, but it does not love my FakeRaid :p

I have a 500GB non-raid HDD in my system, used for backups. I ended up creating a 100MB partition, just for /boot (sdd2).
I can boot into Kubuntu 9.10 no problems, but when I try to boot into my Windows 7 partition, I get "error: Invalid Signature", then back to the grub menu. I can still boot into Win7 if my change my HDD boot order, and boot with my Raid Partition (MBR).

Here is my blkid output.
```
/dev/sdd1: UUID="2F41427EA68EDCB0" LABEL="Backup" TYPE="ntfs"
/dev/mapper/isw_cddbdjghb_storage1: UUID="5EC9BC8B8E1D4B71" LABEL="Storage" TYPE="ntfs"
/dev/mapper/isw_cddbdjghb_storage6: UUID="4bb645aa-53b4-45f8-b58c-a3bdb85f69c5" TYPE="swap"
/dev/mapper/isw_cddbdjghb_windows2: UUID="9343A785226631CF" LABEL="Games" TYPE="ntfs"
/dev/mapper/isw_cddbdjghb_windows5: UUID="F2CCB2DFCCB29CF3" TYPE="ntfs"
/dev/sda: TYPE="isw_raid_member"
/dev/sdb: TYPE="isw_raid_member"
/dev/sdc: TYPE="isw_raid_member"
/dev/sdd2: UUID="a1cd5fdc-0d27-4cc3-8d7b-ae53113d4b40" TYPE="ext4"
/dev/mapper/isw_cddbdjghb_storage5: UUID="53306817-2f2f-49a5-b6fb-3aa1ed0a6d7e" TYPE="ext4"

```

And here is the output I get when I try to "update-grub".

```
root@Ascension:/home/jason# os-prober
/dev/mapper/isw_cddbdjghb_windows2:Windows 7 (loader):Windows:chain
/dev/mapper/isw_cddbdjghb_windows5:Windows 7 (loader):Windows1:chain
root@Ascension:/home/jason# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/mapper/isw_cddbdjghb_windows2
grub-probe: error: no mapping exists for `isw_cddbdjghb_windows2'
Found Windows 7 (loader) on /dev/mapper/isw_cddbdjghb_windows5
grub-probe: error: no mapping exists for `isw_cddbdjghb_windows5'
```

And my device.map output, I thought I added the entries correctly, but something is still not jiving.
```
(fd0)   /dev/fd0
(hd0)   /dev/mapper/isw_cddbdjghb_windows5
(hd1)   /dev/mapper/isw_cddbdjghb_windows2
(hd2)   /dev/sdc
(hd3)   /dev/sdd

```

Thanks in advance guys, I'm really hoping Kubuntu 10.04 Alpha 2 will fix the issues were having with Grub and fakeraid as I had issues installing Alpha 1

---

### Post by presence1960 on 2010-01-01
Let's get a better look at your setup & boot process. Boot into Kubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

