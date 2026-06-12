---
title: "Help with installation on zfs system with additional encrypted mirror zpool"
date: 2022-08-29
forum: Installation &amp; Upgrades
---

### Post by justthenextuser on 2022-08-29
[FONT=Helvetica]Hello together,[/FONT]

[FONT=Helvetica]first of all:[/FONT]
[FONT=Helvetica]My knowledge in Ubuntu/Linux is limited. It is even worse with ZFS but I try to deal with it.[/FONT]

[FONT=Helvetica]I want/need to rebuild my system (old /home directory is backed up) and had thought of the following configuration:[/FONT]

[FONT=Helvetica]/dev/sdd > 120GB SSD > system disk, boot, swap, root[/FONT]
[FONT=Helvetica]/dev/sda > 500GB SSD > RAID 0 (zpool mirror) disk 1 for my /home directory[/FONT]
[FONT=Helvetica]/dev/sdb > 500GB SSD > RAID 0 (zpool mirror) disk 2 for my /home directory[/FONT]

[FONT=Helvetica]I want to additionally set up encryption of all disks.[/FONT]

[FONT=Helvetica]That way I can rebuilt the system on /dev/sda at any time and have my zpool home directory always there regardless and then reintegrate it.[/FONT]


[FONT=Helvetica]I have already done some more research.[/FONT]
[FONT=Helvetica]First I installed Ubuntu 22.04 LTS on the system disk /dev/sdd.[/FONT]
[FONT=Helvetica]In the options for the disk I have already selected ZFS and encryption.[/FONT][FONT=Helvetica]
[/FONT]
[FONT=Helvetica]After the installation I made the other two disks into a corresponding zpool with:[/FONT]
[FONT=Helvetica]```
sudo zpool create -o ashift=12 -o feature@encryption=enabled -O keylocation=prompt -O keyformat=passphrase homepool mirror /dev/sda /dev/sdb
```[/FONT]
[FONT=Helvetica]Now I have the ZFS system of the Ubtuntu installation ('bpool' & 'rpool') and my ZFS mirror 'homepool'.[/FONT]
[FONT=Helvetica]
[/FONT][FONT=Helvetica]Then I tried with 'zfs set mountpoint' to mount the 'homepool' to my home directory.[/FONT]
[FONT=Helvetica]Without success, I could not boot at all and had to redo the installation directly.[/FONT]

[FONT=Helvetica]Before I waste so much time again, I wanted to ask for help here.[/FONT]
[FONT=Helvetica]How can I implement my plan? How exactly do I continue after creating the 'homepool'?[/FONT]
[FONT=Helvetica]
[/FONT][FONT=Helvetica]Thanks for the help.[/FONT]
[FONT=Helvetica]Many greetings.[/FONT]

---

### Post by justthenextuser on 2022-08-29
Hello,

I have now already done it.

After mounting with 'zfs set mountpoint' it went on with
```

sudo touch /etc/zfs/zfs-list.cache/homepool
sudo zfs set canmount=on homepool

```
The system works with the appropriate zfs pool

Source:
[https://blog.lifealgorithmic.com/2021/11/adding-new-zfs-encrypted-disk-on-ubuntu.html](https://blog.lifealgorithmic.com/2021/11/adding-new-zfs-encrypted-disk-on-ubuntu.html)

Thanks anyway

---

