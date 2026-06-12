---
title: "Installing Ubuntu Server 22.04 on LVM RAID 1"
date: 2023-03-02
forum: Installation &amp; Upgrades
---

### Post by norsemangrey on 2023-03-02
[COLOR=#1A1A1A][FONT=&amp]How do I install Ubuntu Server 22.04 on an LVM mirror (RAID 1) using two SSDs? Can I do this using only the Installer? I found this [/FONT][/COLOR][guide]("https://askubuntu.com/questions/1299978/install-ubuntu-20-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios/")[COLOR=#1A1A1A][FONT=&amp] for Ubuntu Desktop 20.04, but seems convoluted and I'm thinking things might have changed a bit since then. (I'm noob so I might need a step-by-step explanation [/FONT][/COLOR]:KS[COLOR=#1A1A1A][FONT=&amp]).[/FONT][/COLOR]

---

### Post by TheFu on 2023-03-02
This isn't a task for noobs.  None of the Canonical installers provide an easy solution. Most of the experienced users setup storage outside the installer.

For LVM RAID1, I'd setup the system with the "Use LVM" standard install, then after that's all completed, come back with LVM tools and convert each LV I needed as RAID1 to be RAID1 using lvconvert.  Basically, ignore the 2nd SSD during the install, since you'll be wiping it later.

LVM RAID1 devices look funny in lsblk output.  Let me see if I can find a system here setup that way.

BTW, RAID never replaces the need for backups. In fact, when a RAID setup goes badly, sometimes the fastest, easiest fix is to wipe everything and start over with a new RAID array.

Found it:
```
$ lsblkt
NAME                       SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                         15G disk                   
&#9500;&#9472;vda1                       1M part                   
&#9500;&#9472;vda2                     768M part ext4              /boot
&#9492;&#9472;vda3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_0     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9500;&#9472;vg--00-lv--0_rimage_0   10G lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap          1G lvm  swap              [SWAP]
vdb                         15G disk                   
&#9500;&#9472;vdb1                       1M part                   
&#9500;&#9472;vdb2                     768M part                   
&#9492;&#9472;vdb3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_1     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--0_rimage_1   10G lvm                    
    &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
```
Sorta ugly with the rmeta and rimage objects.

Some more data, which will show more details:
```
$ sudo pvs
  PV         VG    Fmt  Attr PSize   PFree
  /dev/vda3  vg-00 lvm2 a--  <13.25g 2.24g
  /dev/vdb3  vg-00 lvm2 a--  <13.25g 3.24g

$ sudo vgs
  VG    #PV #LV #SN Attr   VSize  VFree
  vg-00   2   2   0 wz--n- 26.49g 5.48g

$ sudo lvs
  LV      VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0    vg-00 rwi-aor--- 10.00g                                    100.00          
  lv-swap vg-00 -wi-ao----  1.00g                    
```

As you can see, this is about the most trivial storage setup possible with LVM-RAID1.  If you are going to do this, you'll need to read the manpages for all the different LVM commands carefully.  That is beyond the skills for most non-experts, I'm afraid.

Backups.  Required.

---

