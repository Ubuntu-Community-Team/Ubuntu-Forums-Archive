---
title: "[Mint 17]  Would like to add a partition: where to resize and how much?"
date: 2018-03-03
forum: MINT
---

### Post by tinker123 on 2018-03-03
I'm on Mint 17 Qiana.

My job has a secure telework setup that is only supported Red Hat.

So, I would like to create a new partition and put Fedora on it.

It has been so long since I have done this I am not sure how much room to give to another Linux OS, or even what I did years ago when I partitioned my home computer.

Attached is a screen shot of what is going on with my hard drive and partitions.  I know one partition is for boot.  Then there are two more and I don't know which is which or for what.

Which one should I resize for Fedora and how much room should I give it.

Thanks.

---

### Post by TheFu on 2018-03-03
You are using LVM.  That is good, since LVs can be grown and reduces as needed.  It is bad because gparted doesn't show what is really happening.  You'll need to use CLI tools for everything.  Start by posting **lsblk** output and please use "code tags" so things line up. Otherwise, it won't be understandable.

---

### Post by tinker123 on 2018-03-03
TheFu

Thank you, that was a nice command, here is the output

```

Mint17QianaCinnamonBIOSF10$ lsblk
NAME                       MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                          8:0    0 149.1G  0 disk 
&#9500;&#9472;sda1                       8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                       8:2    0     1K  0 part 
&#9492;&#9472;sda5                       8:5    0 148.8G  0 part 
  &#9500;&#9472;mint--vg-root (dm-0)   252:0    0 146.9G  0 lvm  /
  &#9492;&#9472;mint--vg-swap_1 (dm-1) 252:1    0     2G  0 lvm  [SWAP]
sdb                          8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1                       8:17   0 931.5G  0 part /media/steve/FreeAgent GoFl
sr0                         11:0    1  1024M  0 rom  
Mint17QianaCinnamonBIOSF10$
 
```

---

### Post by TheFu on 2018-03-04
So you have a standard, no encryption, LVM setup.
There are lots of opinions for how to proceed.  I'll only provide the broad strokes. You can google for specifics. LVM hasn't changed much in 15+ yrs, so almost any LVM/LVM2 guide you find that uses shell commands will work fine.  This assumes many things, like you are using "normal" file systems, have space to make it work and can get multi-boot working.  I haven't attempted this in a few years, so it might not work.

* Most linux distros are very happy in 15G of storage, provided you don't load every GUI programs there is and don't keep media local.
* You will definitely need to choose "do something else" and manually setup logical volumes for the new OS. If you pick any of the available choices, expect your current system to be wiped.  **MAKE a know-you-can-recover backup first.**  Expect to fail a few times and have to restore to start over.
* If you aren't scared, you should be.  Can I talk you into using a virtual machine to solve this instead?

If you want to continue. Post the command and output for:
* df -hT
* sudo lvs
* sudo vgs
* sudo pvs
* inxi -Fdpz
This will tell us about the LVM details and how much storage is available and the file system types being used. Some file systems can be reduced in size with minimal fuss. Others require a backup, wipe, restore method.  The last command will share some basic system info (z option removes MAC). 

BTW, if this is a desktop, then I think your swap is too small. 4.1G is my recommended swap size.

Using a virtual machine would really limit the risks. Does that make sense for your situation?

---

### Post by kerry_s on 2018-03-04
+1 go virtual

what are your specs, could your machine handle virtual?

i use fedora 27 & run other os's in gnome-boxes which is included in fedora, but can be installed in other os's, should be in the repo or app center.
example:
[ATTACH=CONFIG]278790[/ATTACH][ATTACH=CONFIG]278791[/ATTACH]

---

### Post by tinker123 on 2018-03-04
> **kerry_s said:**
> +1 go virtual

what are your specs, could your machine handle virtual?



Please see output of various commands below.  Does it look like my machine can handle it?

---

### Post by tinker123 on 2018-03-04
TheFU

I am open to the idea of a virtual machine, if it is fairly easy to do.

The whole reason I am looking to tangle with Fedora is to be able to VPN into my computer at work with a CAC.
It is a bit complicated to do and the system admins at my job only support Red Hat.

I don't plan on using Fedora for anything else.

The output from the command you asked me to execute:

```
Mint17QianaCinnamonBIOSF10$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  978M   12K  978M   1% /dev
tmpfs          tmpfs     199M  1.4M  198M   1% /run
/dev/dm-0      ext4      145G   25G  113G  19% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     993M   45M  948M   5% /run/shm
none           tmpfs     100M   24K  100M   1% /run/user
/dev/sda1      ext2      236M   46M  179M  21% /boot
/dev/sdb1      fuseblk   932G  143G  789G  16% /media/steve/FreeAgent GoFlex Drive
Mint17QianaCinnamonBIOSF10$ 
```



```
Mint17QianaCinnamonBIOSF10$ lvs
  LV     VG      Attr      LSize   Pool Origin Data%  Move Log Copy%  Convert
  root   mint-vg -wi-ao--- 146.83g                                           
  swap_1 mint-vg -wi-ao---   1.98g                                           
Mint17QianaCinnamonBIOSF10$ 
```


```
Mint17QianaCinnamonBIOSF10$ vgs
  VG      #PV #LV #SN Attr   VSize   VFree
  mint-vg   1   2   0 wz--n- 148.81g    0 
Mint17QianaCinnamonBIOSF10$ 

```


```
Mint17QianaCinnamonBIOSF10$ pvs
  PV         VG      Fmt  Attr PSize   PFree
  /dev/sda5  mint-vg lvm2 a--  148.81g    0 
Mint17QianaCinnamonBIOSF10$ 

```

```

Mint17QianaCinnamonBIOSF10$ inxi -Fdpz
System:    Host: steve-HP-Compaq-dc5800-Small-Form-Factor Kernel: 3.13.0-24-generic x86_64 (64 bit) 
           Desktop: N/A Distro: Linux Mint 17 Qiana
Machine:   System: Hewlett-Packard product: HP Compaq dc5800 Small Form Factor
           Mobo: Hewlett-Packard model: 2820h Bios: Hewlett-Packard version: 786F2 v01.53 date: 08/27/2008
CPU:       Dual core Intel Core2 Duo CPU E7400 (-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 ssse3) 
           Clock Speeds: 1: 1596.00 MHz 2: 1596.00 MHz
Graphics:  Card: NVIDIA Device 128b 
           X.org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) tty size: 123x27 Advanced Data: N/A for root 
Audio:     Card-1: NVIDIA GK208 HDMI/DP Audio Controller driver: snd_hda_intel Sound: ALSA ver: k3.13.0-24-generic
           Card-2: Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel
Network:   Card: Intel 82566DM-2 Gigabit Network Connection driver: e1000e 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1160.2GB (15.5% used) 1: id: /dev/sda model: ST3160318AS size: 160.0GB 
           2: id: /dev/sdb model: FreeAgent_GoFlex size: 1000.2GB 
           Optical: /dev/sr0 model: N/A dev-links: cdrom
           Features: speed: 48x multisession: yes audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram
Partition: ID: / size: 145G used: 25G (19%) fs: ext4 ID: /boot size: 236M used: 46M (21%) fs: ext2 
           ID: /media/steve/FreeAgent GoFlex Drive size: 932G used: 143G (16%) fs: fuseblk ID: swap-1 size: 2.12GB used: 0.47GB (22%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 33.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 177 Uptime: 19:46 Memory: 1554.4/1985.5MB Client: Shell inxi: 1.8.4 
Mint17QianaCinnamonBIOSF10$ 

```

---

### Post by TheFu on 2018-03-04
The CPU is fine (lower end, but shouldn't be bad if you avoid heavy DEs), but only having 2G of RAM will cause issues.  At least 4G would be minimal, IMHO. That way 2G for both systems could be allocated.

---

### Post by Dennis N on 2018-03-04
I have Fedora in an LVM multiboot setup. One of the other OS on my system happens to be Linux Mint 18.  So, this can be done. Look to shrink the root LV of Mint, and then create another LV for Fedora root. Then use the manual partitioning (not sure of the exact terminology Fedora uses) on Fedora's installer and you can do it. I did not use a separate boot partition when I did it. In fact none of the OSes required a separate boot partition. I do not have any encryption.

---

### Post by tinker123 on 2018-03-04
> **Dennis N said:**
> I have Fedora in an LVM multiboot setup. One of the other OS on my system happens to be Linux Mint 18.  So, this can be done. Look to shrink the root LV of Mint, and then create another LV for Fedora root. Then use the manual partitioning (not sure of the exact terminology Fedora uses) on Fedora's installer and you can do it. I did not use a separate boot partition when I did it. In fact none of the OSes required a separate boot partition. I do not have any encryption.

Thank you!

---

### Post by Dennis N on 2018-03-04
Some important advice on shrinking a logical volume:
[https://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/](https://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/)
[http://www.microhowto.info/howto/reduce_the_size_of_an_lvm_logical_volume.html](http://www.microhowto.info/howto/reduce_the_size_of_an_lvm_logical_volume.html)

I will add this too. The partitioning on the disk containing the LVM installs (also has two standard installs):

```
dmn@Sydney:~$ lsblk -o name,label,fstype
NAME                   LABEL            FSTYPE
sdb                                     
&#9500;&#9472;sdb1                                  vfat
&#9500;&#9472;sdb2                 Manjaro-XFCE     ext4
&#9500;&#9472;sdb3                 Manjaro-MATE     ext4
&#9500;&#9472;sdb4                                  vfat
&#9500;&#9472;sdb5                                  LVM2_member
&#9474; &#9500;&#9472;os_vg-mint_xfce    Mint-XFCE        ext4
&#9474; &#9500;&#9472;os_vg-mint_mate    Mint-MATE        ext4
&#9474; &#9500;&#9472;os_vg-fedora_gnome Fedora-GNOME     ext4
&#9474; &#9492;&#9472;os_vg-umate_1710   Ubuntu-Mate-1710 ext4
&#9500;&#9472;sdb6                                  vfat
&#9492;&#9472;sdb7                                  LVM2_member
  &#9492;&#9472;os_vg-ubuntu_1710  Ubuntu-1710      ext4

```

The 'vfat' partitions are EFI system partitions.

---

### Post by TheFu on 2018-03-04
Very nice Dennis!

Ubuntu's management of storage during install has been lacking compared to CentOS, RHEL and probably Fedora, especially when LVM is involved. 

Definitely make those backups before starting.

---

