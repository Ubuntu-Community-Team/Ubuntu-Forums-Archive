---
title: "Ubuntu 20.04 LVM usr filesystem name"
date: 2020-06-05
forum: Installation &amp; Upgrades
---

### Post by yungdelta on 2020-06-05
I've created a volume group named 'OSVG' with a few logical volumes underneath and when running the 'df -h' command, the /usr partition outputs the long UUID name and not /dev/mapper/OSVG-usr_lv

This is from a fresh install with the Ubuntu 20.04 server ISO image. Has anyone ran into this issue? I've used the same schema before for Xenial and Bionic and never had an issue.

df -h
```

Filesystem                                                                                    Size  Used Avail Use% Mounted on
udev                                                                                          700M     0  700M   0% /dev
tmpfs                                                                                         149M  1.2M  148M   1% /run
/dev/sda3                                                                                     2.4G   13M  2.3G   1% /
/dev/disk/by-id/dm-uuid-LVM-jYkvnAp4wuH8aeneXeyPhf2tmRoDGscVJJIsYB8RB5ZArIggpnDptLuGTZCmqZ2n  3.9G  1.7G  2.1G  44% /usr
tmpfs                                                                                         742M     0  742M   0% /dev/shm
tmpfs                                                                                         5.0M     0  5.0M   0% /run/lock
tmpfs                                                                                         742M     0  742M   0% /sys/fs/cgroup
/dev/sda2                                                                                     976M  103M  806M  12% /boot
/dev/mapper/OSVG-home_lv                                                                      976M  2.6M  907M   1% /home
/dev/mapper/OSVG-tmp_lv                                                                       976M  2.6M  907M   1% /tmp
/dev/mapper/OSVG-var_lv                                                                       2.9G  443M  2.3G  16% /var
/dev/loop0                                                                                     55M   55M     0 100% /snap/core18/1705
/dev/loop1                                                                                     28M   28M     0 100% /snap/snapd/7264
/dev/loop2                                                                                     69M   69M     0 100% /snap/lxd/14804
tmpfs                                                                                         149M     0  149M   0% /run/user/1000

```

pvs
```

 PV         VG   Fmt  Attr PSize   PFree
 /dev/sdb   OSVG lvm2 a--  <10.00g    0 

```

lvs
```

 LV      VG   Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
 home_lv OSVG -wi-ao----    1.00g                                                    
 swap_lv OSVG -wi-ao---- 1020.00m                                                    
 tmp_lv  OSVG -wi-ao----    1.00g                                                    
 usr_lv  OSVG -wi-ao----    4.00g                                                    
 var_lv  OSVG -wi-ao----    3.00g                                                    

```

vgs
```

 VG   #PV #LV #SN Attr   VSize   VFree
 OSVG   1   5   0 wz--n- <10.00g    0 

```

lsblk -e 7 -o name,size,type,fstype,mountpoint
```

NAME            SIZE TYPE FSTYPE      MOUNTPOINT
sda             3.5G disk             
&#9500;&#9472;sda1            1M part             
&#9500;&#9472;sda2            1G part ext4        /boot
&#9492;&#9472;sda3          2.5G part ext4        /
sdb              10G disk LVM2_member 
&#9500;&#9472;OSVG-usr_lv     4G lvm  ext4        /usr
&#9500;&#9472;OSVG-var_lv     3G lvm  ext4        /var
&#9500;&#9472;OSVG-home_lv    1G lvm  ext4        /home
&#9500;&#9472;OSVG-tmp_lv     1G lvm  ext4        /tmp
&#9492;&#9472;OSVG-swap_lv 1020M lvm  swap        [SWAP]
sr0            1024M rom              

```

---

### Post by TheFu on 2020-06-05
Please don't set any fonts when using code tags. That defeats the main purpose of code tags - so that everything looks like it would in a terminal.  It isn't lined up now.

I'm not seeing anything like what is being shown above here on a 20.04 desktop:
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   12G   11G  188M  99% /
/dev/mapper/vgubuntu--mate-home ext4   12G  5.9G  5.4G  53% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
```

```
$ lsblka 
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sr0                       1024M rom              
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     12G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home

```

And the fstab:
```
/dev/vgubuntu-mate/root /       ext4    errors=remount-ro 0 1
/dev/vgubuntu-mate/home /home   ext4    errors=remount-ro 0 1

UUID=9CE4-930A  /boot/efi       vfat    umask=0077      0       1
/dev/vgubuntu-mate/swap_1 none  swap    sw      0       0
```

Looks like LVM was added post-install. Mine was part of the install. It would be nice if the dft output used the device links from the fstab, but that's what we get when systemd takes over mounting stuff.  They do what they want.

See how my code tags line up?

---

### Post by DuckHook on 2020-06-05
> **TheFu said:**
> Please don't set any fonts when using code tags. That defeats the main purpose of code tags - so that everything looks like it would in a terminal.  It isn't lined up now…
&#8593;+1

@yungdelta

Please refrain from nonstandard formatting when posting to the forums. This makes your post hard to read for people on small screens or who have impaired vision.

---

### Post by yungdelta on 2020-06-08
Apologize for using formatting inside the code tags! Thanks @DuckHook for editing my post!

@TheFu I created the LVM during the install NOT during post-install. Also, your output doesn't have the /usr LVM partition, so I can't compare your outputs to mine. If it helps, here is my fstab file:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during curtin installation
/dev/disk/by-uuid/a47cea98-e6c2-4fe0-ab7b-9e8773e38164 / ext4 defaults 0 0
# /usr was on /dev/OSVG/usr_lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-jYkvnAp4wuH8aeneXeyPhf2tmRoDGscVJJIsYB8RB5ZArIggpnDptLuGTZCmqZ2n /usr ext4 defaults 0 0
# /var was on /dev/OSVG/var_lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-jYkvnAp4wuH8aeneXeyPhf2tmRoDGscVFLXdCR4ozEdVgHIazI3rGGAU4g6oOyfL /var ext4 defaults 0 0
# /home was on /dev/OSVG/home_lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-jYkvnAp4wuH8aeneXeyPhf2tmRoDGscVj1o920kGd5g6TcAR20q1UCBaeSWrKuuN /home ext4 defaults 0 0
# /tmp was on /dev/OSVG/tmp_lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-jYkvnAp4wuH8aeneXeyPhf2tmRoDGscVuMWUD55sLwjgY9IYfBS00fPJI86ZiiKt /tmp ext4 defaults 0 0
/dev/disk/by-id/dm-uuid-LVM-jYkvnAp4wuH8aeneXeyPhf2tmRoDGscVcUNp026CHKBbkqm7BupZMTVgk72lYj0c none swap sw 0 0
# /boot was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/55b8be2d-cbf1-4ecc-a0b6-bbaccfbc7c4b /boot ext4 defaults 0 0


```

---

### Post by TheFu on 2020-06-08
which installer?
i used the ubuntu-mate 20.04, selected "Minimal" and "LVM".  The fstab never had uuids for LVM mounts in mine.  i would hope that the mounts shown by df would match what the fstab shows for all of them.

First thing i would do is change the fstab to use the /dev/{VG}/{LV} links and see if that fixes it. Those long paths aren't exactly useful unless someone on the plex server team is working on the ubuntu installer team now. Plex uses:
*/var/lib/plexmediaserver/Library/Application Support/Plex Media Server*  before anything interesting happens. Long paths just to be long are stupid.  _/var/lib/plexms_ provides just as much useful information, yes?

What's the point of having lots of small LVs in 2020?  if there were different mount options, i could see it being useful, but there aren't. Why?

I&#8217;d check the systemd documentation for mounting if changing to shorter names in the fstab doesn't fix it.

---

