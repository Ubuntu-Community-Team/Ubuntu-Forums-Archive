---
title: "What are the Recomendations for the discks and root folders?"
date: 2021-02-08
forum: Installation &amp; Upgrades
---

### Post by erdur on 2021-02-08
I might ask a redundant question because i am searching using the wrong terms.
The closest i can find is this guide: [https://help.ubuntu.com/lts/installation-guide/armhf/apcs02.html](https://help.ubuntu.com/lts/installation-guide/armhf/apcs02.html)

But is for example /etc recommended on the root partition or can i move it to another one.

As i understand it right now the requirements/recomendations are:

Main disc (ssd m.2):
[LIST]
[*]boot (obviously) 
[*]bin 
[*]usr 
[*]... 
[*]etc ??? 
[/LIST]
Second disk (raid mdadm ssd)
[LIST]
[*]/home (most data goes here) 
[*]/var (or just /var/log to decrease wear on the main ssd) 
[*]maybe a copy of etc if it is on the main disc?? 
[/LIST]
A separate disc for tmpfs?

PS: The setup is for a home server, but will probably use the normal version, since i failed to set up cockpit on the server version.

---

### Post by Holger_Gehrke on 2021-02-08
/etc contains configuration files that are needed during boot. Among them the fstab, so the system wouldn't know to mount anything beyond the root if /etc/ wasn't on the root fs.  /var/log/journal is needed quite early in the boot process by systemd (to write it's binary log of the boot process), so mounting that from another disk might be problematic. 

tmpfs is a RAM disk often used for /tmp. It's dynamic, so it only takes as much RAM as the combined size of the stored files with a small overhead for metadata. It is configured to have a maximum size beyond which it won't grow which is adjustable through mount options. Obviously having /tmp in RAM is not an option for machines that run programs that produce lots of big temporary files.

There's a mount option noatime for several types of filesystem to stop them from storing access time (atime) for files. If you're concerned about wear reduction, that option is important. Without it any access to a file will make a change to it's inode which will at some point get written to disk ...

Holger

---

### Post by TheFu on 2021-02-08
/etc/ is tiny.  keep it with the OS.  There is a "Linux file system hierarchy standard" document - easily found - which spells out what must be where. 
Don't over think this stuff. It generally isn't worth the effort after about 4 partitions for a normal desktop.
However, I wouldn't put most data into HOME.  Definitely no media files.  Partitioning is mostly about backup and recovery plans.

RAID doesn't replace the need for backups. Current SSDs just don't fail much within their endurance specs. Stay away from any SSD that refuses to provide endurance specs and a warranty for those specs. There are surprisingly well-marketed SSDs that don't.

If you want flexible storage, learn to use lvm or zfs.  Just be certain to pick a flexible file system as well, like one that can be reduced and enlarged. XFS cannot be reduced, ever.

---

### Post by erdur on 2021-02-08
The idea behind the question to have tmpfs not on the main disc was that it seems to be written often,
and i don't want my system-disc to degrade prematurely.

---

### Post by erdur on 2021-02-08
Its more meant for a smale server. (some linuxgsm, a bit NGINX-Flasck).

If i understand your comment correctly, you would combine all discs to a single pool, and them install the system onto a Logical volume containing all the space.
(plus a regular rsync to my Backup nas, and a alarm from smartmontools?)

> Don't over think this stuff.
That would be the reason most of my home project got stuck, in the planing phase.
(e.g. I want to write a simple webpage, so i start reaing different web frameworks ...)

PS: I had two devices (1 PC ,1 NUC) fail due to a dying m.2-ssd, so i want to move everything often written off it.
But Linux tends to cache often used commands, so access time shouldn't be a concern here?

---

### Post by TheFu on 2021-02-08
I use the noatime mount option too.

"prematurely" is subjective.  For average use, most reputable SSDs should last 10 yrs based on non-data center endurance numbers.  SSDs aren't like HDDs.  All the storage used inside is virtual. We don't know what actually happens and write-leveling is automatically handled for us. 

Here's a system with an SSD (sdb) and backup storage on sda - a regular HDD.
```
NAME                              SIZE TYPE FSTYPE      MOUNTPOINT
sdb                               477G disk
&#9500;&#9472;sdb1                            731M part ext2        /boot
&#9500;&#9472;sdb2                              1K part
&#9492;&#9472;sdb5                          476.2G part LVM2_member
  &#9500;&#9472;hadar--vg-root               32.3G lvm  ext4        /
  &#9500;&#9472;hadar--vg-swap_1              4.3G lvm  swap        [SWAP]
  &#9500;&#9472;hadar--vg-libvirt--lv         175G lvm  ext4        /var/lib/libvirt
  &#9500;&#9472;hadar--vg-lxd--lv              60G lvm  ext4        /var/lib/lxd
  &#9500;&#9472;hadar--vg-lv--vpn09--1804     7.5G lvm
  &#9500;&#9472;hadar--vg-lv--xen41--1804    12.5G lvm
  &#9500;&#9472;hadar--vg-lv--blog44--1804   16.2G lvm
  &#9500;&#9472;hadar--vg-lv--zcs45--1604      25G lvm
  &#9500;&#9472;hadar--vg-lv--spam3            10G lvm
  &#9500;&#9472;hadar--vg-lv--opnsense          5G lvm
  &#9500;&#9472;hadar--vg-lv--regulus          30G lvm
  &#9500;&#9472;hadar--vg-lv--regulus--2       10G lvm
  &#9500;&#9472;hadar--vg-lv--tp--lxd_tmeta   108M lvm
  &#9474; &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm
  &#9492;&#9472;hadar--vg-lv--tp--lxd_tdata  32.2G lvm
    &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm

sda                             465.8G disk             
&#9492;&#9472;sda1                          465.8G part LVM2_member 
  &#9492;&#9472;vg--hadar-lv--backups       465.7G lvm  ext4        /Backups
```
I use LVM and each virtual machine gets a separate LV (like a partition, but much more flexible).

On the VM host, I use KVM.  The storage looks like this:
```
$ df -Th
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   32G   18G   13G  59% /
/dev/sdb1                         ext2  720M  225M  459M  33% /boot
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   14G   42G  25% /var/lib/lxd
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  123G   41G  75% /var/lib/libvirt
/dev/mapper/vg--hadar-lv--backups ext4  459G  425G   34G  93% /Backups
lxd/containers/pihole             zfs    13G  818M   12G   7% /var/lib/lxd/storage-pools/lxd/containers/pihole

```

I monitor storage using SMART every week. On an almost 2 year old SSD (power on hours: 16091), none of the reserved block storage areas have been touched yet and this system is on 24/7/365 with 10-20 VMs running all the time.  My other "quality" SSDs are similar.  I started out using cheap SSDs. Those only lasted about 2 yrs before going read-only, then eventually dying. These days, there is plenty of information about which SSDs work long and fast. The quality ones are about 10% more costly, which seems to be a bargain. Plus, if we don't allocate 20% of the SSD space, we'll drastically improve the number of wear-level blocks available.  Drastically.

Never forget that what happens inside any SSD is 100% virtual. The internal electronics manages the wear-leveling for us and maintains the logical "views" for the OS.

Regardless, only you can decide what "degrade prematurely" means.

---

### Post by erdur on 2021-02-08
I don't know what the "hadar" entry's mean, 
the first view seem to be "Logical volumes", and listed in your df.

For the backup, do you backup using rsync?
(I know LVM has snapshots, but to my knowledge they are only on the device itself.)

> "degrade prematurely"
My PC (windows) failed after 4Y without warning.
The NUC had a similar pattern. (Archlinux-KDE)
So my worrys are probably from being burned by those early models. (For the PC it was the "new performance boost")

BUT, when i told the story even the store that originally recommended them asked "was it <BRAND>?"
(I know another system using <BRAND> where "GSmartControl" shows 231 SSD Life Left as red after 2y.)

---

### Post by TheFu on 2021-02-08
"hadar" is the hostname.

rsync isn't a good backup too. It is a great mirror tool.  I've posted hundreds of posts in these forums about backups. No need to repeat those.
NUCs have overheating issues. If thermal control isn't managed carefully, the heat will destroy any computing or storage device.

I've never used GSmartControl.  I'm a CLI person for almost everything. GUIs lie all too often. They simplify the output usually beyond the point where the truth is still available.  What were the endurance specs and warranty for those SSDs?  Those answer all questions. Brands have different models and different lines. If we buy the cheapest with the shortest warranty, don't be surprised when it fails quickly.  SSDs routinely can be found with 5 yr warranties - still check the endurance specs. That is reported in the SMART output, so there isn't any need to be surprised.

---

### Post by erdur on 2021-02-09
"I've posted hundreds of posts in these forums about backups"

The first results i find (that seems to apply) is the rsync-backup script.
[https://ubuntuforums.org/showthread.php?t=2457553&highlight=backup](https://ubuntuforums.org/showthread.php?t=2457553&highlight=backup)
(looking kind of what my workplace seems to be using ...)

Other solutions seem to at least contain rsync as protocol.
[https://ubuntuforums.org/showthread.php?t=2457515&highlight=backup](https://ubuntuforums.org/showthread.php?t=2457515&highlight=backup) 
RSnapshot seems to make the setup for keeping version-folders way easier.

---

### Post by TheFu on 2021-02-09
Article about SSD considerations: [https://www.nytimes.com/wirecutter/reviews/best-ssds/](https://www.nytimes.com/wirecutter/reviews/best-ssds/)
I have both a Samsung 860 and 970 EVO. Also have a Micron 1100 ssd.

For backups, I stopped using rsync after finding issues with that method and versioning though hardlinks. Using **rdiff-backup** about 10 yrs now. It isn't perfect, but as close as I've found looking at 20 tools. I tested at least 15 of them.

---

### Post by erdur on 2021-02-09
"SSD-Artickle" thanks

"issues with that method and versioning though hardlinks.": I found an post mentioning a limit to the number of links, do you mean that?

The main benefit of rsync would be that my Synologfy-NAS already supports it, so it would be a easy target for the backups. (Btrfs)

---

