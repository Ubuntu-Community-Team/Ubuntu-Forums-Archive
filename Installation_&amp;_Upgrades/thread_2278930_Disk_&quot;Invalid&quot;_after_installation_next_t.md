---
title: "Disk &quot;Invalid&quot; after installation next to Windows 8.1"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by bio-collector on 2015-05-19
I recently attempted installing Ubuntu 15 on my MSI GS60. My configuration of the laptop comes with a 128gb SSD, and a 1TB HDD. I decided to install Ubuntu on a partition on the HDD, and keep Windows 8.1 untouched on the SSD.
Installation worked fine, I setup a swap space and all, and I can boot into both OSs, but the problem is that I can't access my original data on my HDD anymore. I still had data in a partition, and I didn't choose to touch it at all during the installation. When I try to inspect the disk in Windows Disk Manager, here's what it looks like:
[IMG]http://i.imgur.com/X6iT1Ox.png[/IMG]

It shows the disk as "Invalid" and the disk is not found in File Explorer anymore. (I can only access my C: drive currently through windows.)
On Ubuntu, I can't mount the disk/view due to something about Windows hibernation.

Is there a way I can restore access to this disk in Windows without losing all my data? (I'm fine with re-installing Ubuntu) Alternatively, is there atleast a way I can get data OFF the old partition so I can back it up and re-install Ubuntu while reformating the partition? (If this is the only choice, any help with properly installing Ubuntu for this setup would be greatly appreciated.)

Thanks!

---

### Post by ubfan1 on 2015-05-20
Looks like the hard disk had a Windows specific partitioning called "Dynamic partitions" -- I'm surprised you could even install to it in that case.  There is some way to convert to regular partitions I think, search this forum and askubuntu for that.  You might try the mount from Ubuntu using the remove_hiberfile option e.g.:
mount -t ntfs-3g -o remove_hiberfile /dev/sda3 /mnt
then you should at least be able mount it and to see the files.

---

### Post by bio-collector on 2015-05-20
I wasn't able to mount the disk with the command above, but there's a screenshot of the disk information being given off by Ubuntu:
[IMG]http://i.imgur.com/ibOjwtp.png[/IMG]

---

### Post by ubfan1 on 2015-05-20
Maybe booting Windows in recovery mode?  Can't help much with Windows.  If you eventually can see the disk, lookup the way to convert from dynamic partitions to normal partitions.

---

### Post by oldfred on 2015-05-21
LDM is still dynamic partitions, but usually with a gpt partitioned drive.

       Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

---

