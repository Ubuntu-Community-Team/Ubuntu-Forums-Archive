---
title: "LiveCD USB pendrive with Multiple partitions and Grub2 installed"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by Neill_R on 2014-04-30
Trying to make this USB stick dual purpose
    
    1 A working copy of Ubuntu 14.04 LTS 
    2 A Live CD (well DVD now) to install UBuntu 14.04 LTS on other     disks/computers
    
    What I did  was to partition drive as so then installed the LIVE CD     on sdb1.     
[LIST]
[*]tried to boot from the USB drive to install Ubuntu. Not         possible to do that the partition table is in use. 
[*]used VirtualBox reading from virtual CD iso file to try Ubuntu         and then install the system on the attached USB disk. 
[/LIST]
     
    [IMG]https://mail.google.com/mail/u/0/?ui=2&ik=ead6025a5b&view=att&th=145af78d46c297d1&attid=0.1&disp=emb&zw&atsh=1[/IMG]



      [LEFT]Mount running from the hard drive sda
      [/LEFT]
       
      ```
[INDENT]         [LEFT]neill@HPlt2UbuntuSvr:~$ 
          neill@HPlt2UbuntuSvr:~$ mount
          
          /dev/sda7 on / type ext4 (rw,errors=remount-ro)
          proc on /proc type proc (rw,noexec,nosuid,nodev)
          sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
          none on /sys/fs/fuse/connections type fusectl (rw)
          none on /sys/kernel/debug type debugfs (rw)
          none on /sys/kernel/security type securityfs (rw)
          udev on /dev type devtmpfs (rw,mode=0755)
          devpts on /dev/pts type devpts           (rw,noexec,nosuid,gid=5,mode=0620)
          tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
          none on /run/lock type tmpfs           (rw,noexec,nosuid,nodev,size=5242880)
          none on /run/shm type tmpfs (rw,nosuid,nodev)
          cgroup on /sys/fs/cgroup type tmpfs (rw,relatime,mode=755)
          cgroup on /sys/fs/cgroup/cpuset type cgroup           (rw,relatime,cpuset)
          cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu)
          cgroup on /sys/fs/cgroup/cpuacct type cgroup           (rw,relatime,cpuacct)
          cgroup on /sys/fs/cgroup/memory type cgroup           (rw,relatime,memory)
          cgroup on /sys/fs/cgroup/devices type cgroup           (rw,relatime,devices)
          cgroup on /sys/fs/cgroup/freezer type cgroup           (rw,relatime,freezer)
          cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio)
          cgroup on /sys/fs/cgroup/perf_event type cgroup           (rw,relatime,perf_event)
          /dev/sda8 on /home type ext4 (rw,nosuid,nodev)
          rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
          binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc           (rw,noexec,nosuid,nodev)
          nfsd on /proc/fs/nfsd type nfsd (rw)
          gvfs-fuse-daemon on /home/neill/.gvfs type           fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=neill)
          /dev/sdb3 on /media/Home type ext4           (rw,nosuid,nodev,uhelper=udisks)
          /dev/sdb4 on /media/Root type ext4           (rw,nosuid,nodev,uhelper=udisks)
          /dev/sdb1 on /media/7E20-B291 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
          
          neill@HPlt2UbuntuSvr:~$ 
          neill@HPlt2UbuntuSvr:~$ 
        [/LEFT]
       [/INDENT]

```

      [LEFT]How do i get this into the grub2 configuration         on sdb
      [/LEFT]
       [LEFT]
      [/LEFT]
       ```
[INDENT]         [LEFT]/**dev/sdb1 on /media/7E20-B291 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)**
        [/LEFT]
       [/INDENT]

```                

I tried grub-update but all that did was to add the OS on sda.         Wish i knew how to stop it searching the internal hard drive when i am         configuring a removable disk device? 

Now running(booting) 14.04 from the pendrive (USB stick) 

```


sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x12bf842d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   661841919   330716160    7  HPFS/NTFS/exFAT
/dev/sda3      1927114752  1953525167    13205208    7  HPFS/NTFS/exFAT
/dev/sda4       661841920  1894217727   616187904    5  Extended
/dev/sda5       675459072   696143871    10342400   82  Linux swap / Solaris
/dev/sda6       724178944   961085439   118453248   83  Linux
/dev/sda7      1157052416  1383878655   113413120   83  Linux
/dev/sda8      1383880704  1760509951   188314624   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 16.4 GB, 16358768640 bytes
64 heads, 32 sectors/track, 15600 cylinders, total 31950720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063f98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     5496831     2747392    b  W95 FAT32
/dev/sdb2         5496832     9730047     2116608   82  Linux swap / Solaris
/dev/sdb3         9735390    15454139     2859375   83  Linux
/dev/sdb4        15462400    31948799     8243200   83  Linux
chris@chris-usb:~$


```

```


chris@chris-usb:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="0C2CE3F82CE3DAAA" TYPE="ntfs" 
/dev/sda2: UUID="9A8665128664EFE5" TYPE="ntfs" 
/dev/sda3: LABEL="RECOVERY" UUID="9CB8910BB890E554" TYPE="ntfs" 
/dev/sda5: UUID="e5dc3b89-9fd9-497b-a218-03c7ad8803f0" TYPE="swap" 
/dev/sda6: LABEL="Desktop_12_04" UUID="150e6635-c92f-4ae9-ba53-21a1b5426758" TYPE="ext4" 
/dev/sda7: LABEL="12_04_Server" UUID="83d8ab27-7990-46c4-b59e-91891997c327" TYPE="ext4" 
/dev/sda8: LABEL="Home_64_Server" UUID="7f3006a7-a968-4b18-a99a-c951197bf4ba" TYPE="ext4" 
/dev/sdb1: UUID="7E20-B291" TYPE="vfat" 
/dev/sdb2: UUID="124e75df-4f09-4503-b6c8-481616782c5f" TYPE="swap" 
/dev/sdb3: LABEL="Home" UUID="943b55b4-39ad-484c-a859-68208cdc1546" TYPE="ext4" 
/dev/sdb4: LABEL="Root" UUID="306ba494-0f3a-4dc9-9684-35e1d4dd2fcf" TYPE="ext4" 
chris@chris-usb:~$ 


```


i have discovered 

[URL="http://ubuntuforums.org/showthread.php?t=1664134"]http://ubuntuforums.org/showthread.php?t=1664134
[/URL]

and on sdb1 under /boot/grub i saw the file loopback.cfg containing the lines 

```


menuentry "Try Ubuntu without installing" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Test memory" {
    linux16    /install/mt86plus
}


```

now I have what have to figure out is how to integrate those lines into the grub menu on sdb4 


I be back if i have success but if you can help teach me I would be grateful

---

### Post by oldfred on 2014-04-30
A syslinux configuration is different.

I have a full install of Ubuntu on my flash drive and in another partition copy the ISOs. Then from grub with loopmount I boot the ISO directly. I also boot ISO from an old hard drive partition to install on another drive.

Then you do not have to extract the ISO to use it as an installer. I also copy several repair ISO like gparted, parted magic, Supergrub, Boot-Repair and others onto flash drive. 

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition

I have not tried chainloading to syslinux, but it is like Windows in that you should be able to just chain to sdb1 and boot the syslinux install. Boot drive is always hd0.
      ```
 menuentry "Syslinux Chainboot" {
set root=(hd0,1)
chainloader +1
}

```

---

### Post by Neill_R on 2014-05-01
SOLVED

This is what i did

installed 

[CODE}

# the 'exec tail' line above.
menuentry "Gparted live" {
      set isofile="/boot/for_40_custom/gparted-live-0.18.0-2-i486.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga$
      initrd (loop)/live/initrd.img
    }
#
# will this work? YES it did!!!
#
menuentry "CloneZilla live" {
      set isofile="/boot/for_40_custom/clonezilla-live-20140415-saucy-i386.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga$
      initrd (loop)/live/initrd.img
    }
#
# and will this? yes it did too !!!
#

[/CODE]


thanks oldfred 

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) 

     sudo apt-get install gksu
      gksu gedit /etc/default/grub &

     sudo add-apt-repository ppa:danielrichter2007/grub-customizer
   sudo apt-get update
       sudo apt-get upgrade
  sudo apt-get install grub-customizer

     sudo nano /etc/apt/sources.list uncomment partner lines
     sudo apt-get update
     sudo apt-get install skype
     skype
     sudo grub-install /dev/sdb1
 
     sudo mount -o loop  /boot/grml/ubuntu-14.04-desktop-i386.iso   /mnt/iso
     ls /mnt/iso
     sudo umount /mnt/iso

     sudo apt-get install grml-rescueboot
     sudo mv ~/Downloads/u*.iso /boot/grml/
     sudo mount -o loop  /boot/grml/ubuntu-14.04-desktop-i386.iso   /mnt/iso
     ls /mnt/iso
     sudo umount /mnt/iso

     sudo mkdir /boot/for_40_custom 
     sudo mv ~/Downloads/*.iso /boot/for_40_custom/
       ls /boot/for_40_custom
        clonezilla-live-20140331-saucy-amd64.iso  
        gparted-live-0.18.0-2-i486.iso
        clonezilla-live-20140415-saucy-i386.iso

  133  sudo nano /etc/grub.d/40_custom

# the 'exec tail' line above.
menuentry "Gparted live" {
      set isofile="/boot/for_40_custom/gparted-live-0.18.0-2-i486.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
      initrd (loop)/live/initrd.img
    }
#
# will this work? YES it did!!!
#
menuentry "CloneZilla live" {
      set isofile="/boot/for_40_custom/clonezilla-live-20140415-saucy-i386.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
      initrd (loop)/live/initrd.img
    }
#
# and will this? Yess!!!
#


  134  gksu grub-customizer &

unselect the sda OS entries 

save and then reboot


save and reboot

---

