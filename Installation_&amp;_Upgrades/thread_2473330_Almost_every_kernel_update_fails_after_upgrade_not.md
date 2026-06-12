---
title: "Almost every kernel update fails after upgrade: not enough space on /boot"
date: 2022-04-01
forum: Installation &amp; Upgrades
---

### Post by fisch3r on 2022-04-01
Hi,

I upgraded Ubuntu 18.04 to 20.04. Everything worked out so far except the software updates for the kernel. Almost every time I get the error "Not enough disk space on /boot".
I then checked my partitions with df -h and looked for /boot:
[HTML]
/dev/nvme0n1p2               705M    329M  325M   51% /boot
/dev/nvme0n1p1               511M     38M  474M    8% /boot/efi
[/HTML]

I also checked the current kernel with uname -r
[HTML]
5.13.0-30-generic[/HTML]

I then checked the installed kernels with: dpkg --list 'linux-image*' | grep ^ii
[HTML]
ii  linux-image-5.13.0-30-generic           5.13.0-30.33~20.04.1 amd64        Signed kernel image generic
ii  linux-image-5.4.0-105-generic           5.4.0-105.119        amd64        Signed kernel image generic
ii  linux-image-generic                     5.4.0.105.109        amd64        Generic Linux kernel image
[/HTML]

On 18.04 I never experienced this error. I found the solution to manually remove the installed kernels which are not in use but I think this does not really solve the problem.
It looks like the /boot is just way to small but I did just use the defaults for the installation of 18.04.
Do you have recommendations on how to solve this?

---

### Post by ActionParsnip on 2022-04-01
With a 700Mb /boot you will need to manage the file system a lot

What is the output of
```

dpkg -l | grep linux-image

```

Thanks

---

### Post by fisch3r on 2022-04-01
Here is the output:

[HTML]
rc  linux-image-4.15.0-167-generic             4.15.0-167.175                                amd64        Signed kernel image generic
rc  linux-image-5.0.0-23-generic               5.0.0-23.24~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.0.0-37-generic               5.0.0-37.40~18.04.1                           amd64        Signed kernel image generic
ii  linux-image-5.13.0-30-generic              5.13.0-30.33~20.04.1                          amd64        Signed kernel image generic
rc  linux-image-5.3.0-26-generic               5.3.0-26.28~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-28-generic               5.3.0-28.30~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-40-generic               5.3.0-40.32~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-42-generic               5.3.0-42.34~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-45-generic               5.3.0-45.37~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-46-generic               5.3.0-46.38~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-51-generic               5.3.0-51.44~18.04.2                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-53-generic               5.3.0-53.47~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-59-generic               5.3.0-59.53~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-61-generic               5.3.0-61.55~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.3.0-62-generic               5.3.0-62.56~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-104-generic              5.4.0-104.118                                 amd64        Signed kernel image generic
ii  linux-image-5.4.0-105-generic              5.4.0-105.119                                 amd64        Signed kernel image generic
rc  linux-image-5.4.0-42-generic               5.4.0-42.46~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-45-generic               5.4.0-45.49~18.04.2                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-47-generic               5.4.0-47.51~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-48-generic               5.4.0-48.52~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-51-generic               5.4.0-51.56~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic               5.4.0-52.57~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic               5.4.0-53.59~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-54-generic               5.4.0-54.60~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic               5.4.0-56.62~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic               5.4.0-58.64~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic               5.4.0-59.65~18.04.1                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-62-generic               5.4.0-62.70                                   amd64        Signed kernel image generic
ii  linux-image-generic                        5.4.0.105.109                                 amd64        Generic Linux kernel image
[/HTML]

---

### Post by ActionParsnip on 2022-04-01
OK you can clear up with:
```

sudo dpkg -P `dpkg -l grep linux-image | grep ^rc | awk {'print $2'}`

```

---

### Post by fisch3r on 2022-04-01
Thank you! I cleaned it up, there was a pipe missing in your command, so I executed: 
[HTML]sudo dpkg -P `dpkg -l | grep linux-image | grep ^rc | awk {'print $2'}`[/HTML]
So now it is cleaned up but /boot is still at 51%. So what should I do next? Add more space to /boot?

---

### Post by ubfan1 on 2022-04-01
Look at the ls /boot and see if you have any old pieces (particularly initrd... which are large), left around.  Those may be using space.  I thought the free space you have shown would be sufficient for an update.

---

### Post by fisch3r on 2022-04-01
There is not really much lying around to delete:
[HTML]
-rw-r--r-- 1 root root    257734 Feb  7 15:01 config-5.13.0-30-generic
-rw-r--r-- 1 root root    237973 Mär  7 17:07 config-5.4.0-105-generic
drwx------ 3 root root      4096 Jan  1  1970 efi
drwxr-xr-x 5 root root      4096 Mär 22 14:34 grub
lrwxrwxrwx 1 root root        28 Mär 22 14:32 initrd.img -> initrd.img-5.4.0-105-generic
-rw-r--r-- 1 root root 160958515 Mär 18 06:57 initrd.img-5.13.0-30-generic
-rw-r--r-- 1 root root 137953616 Mär 22 14:32 initrd.img-5.4.0-105-generic
lrwxrwxrwx 1 root root        28 Mär 22 14:33 initrd.img.old -> initrd.img-5.13.0-30-generic
drwx------ 2 root root     16384 Dez 22  2019 lost+found
-rw-r--r-- 1 root root    182704 Aug 18  2020 memtest86+.bin
-rw-r--r-- 1 root root    184380 Aug 18  2020 memtest86+.elf
-rw-r--r-- 1 root root    184884 Aug 18  2020 memtest86+_multiboot.bin
-rw------- 1 root root   5960334 Feb  7 15:01 System.map-5.13.0-30-generic
-rw------- 1 root root   4759409 Mär  7 17:07 System.map-5.4.0-105-generic
lrwxrwxrwx 1 root root        25 Mär 22 14:32 vmlinuz -> vmlinuz-5.4.0-105-generic
-rw------- 1 root root  10171040 Feb  7 15:03 vmlinuz-5.13.0-30-generic
-rw------- 1 root root  13664512 Mär  7 17:20 vmlinuz-5.4.0-105-generic
lrwxrwxrwx 1 root root        25 Mär 22 14:33 vmlinuz.old -> vmlinuz-5.13.0-30-generic[/HTML]

Right now there is an update and I cannot update since 15MB free space are missing. So I cannot even 3 kernels have. I think there is something deeply broken. Maybe something did not clean up after the upgrade?

---

### Post by ActionParsnip on 2022-04-01
What is the new output of
```

dpkg -l | grep linux-image; echo; uname -a

```
Thanks

---

### Post by fisch3r on 2022-04-01
[HTML]
ii  linux-image-5.13.0-30-generic              5.13.0-30.33~20.04.1                          amd64        Signed kernel image generic
ii  linux-image-5.4.0-105-generic              5.4.0-105.119                                 amd64        Signed kernel image generic
ii  linux-image-generic                        5.4.0.105.109                                 amd64        Generic Linux kernel image

Linux LIN3442 5.13.0-30-generic #33~20.04.1-Ubuntu SMP Mon Feb 7 14:25:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux[/HTML]

---

### Post by ubfan1 on 2022-04-01
Just noticed the sizes of your initrd files are much larger than mine, 137MB vs 52MB.  That would explain why there's not enough room, when normally there would be.  So, do you really need a separate /boot (Logical encrypted root etc.)?  If not, rather than expand /boot, consider just use the root's /boot directory.

---

### Post by deadflowr on 2022-04-01
Your initrd.XXX files are huge.
What compression is being used
```
grep COMPRESS /etc/initramfs-tools/initramfs.conf
```


Edit: I notice ubfan1 posted the same general query.

---

### Post by Impavidus on 2022-04-01
The default size of the /boot partition was already a bit small-ish in 18.04. On 20.04, you need more.

---

### Post by TheFu on 2022-04-04
700MB should be enough for 6+ kernels.
You had a number of failures that left junk around and manually removing some of the files wasn't helping.
Also, having 2 kernel lines (v5.4.x and something else) will mean that APT tries to maintain both sets of updates - taking 2x the space. If you are happy with the HWE kernel, then remove all the 5.4.x kernels, headers, modules, etc ... from the system.

NEVER manually remove files that are part of a package. Always use the package manager to do that. If one of the files is missing, the package manager will error out, causing issues, like you've seen.

On a 20.04 system, 220M is needed to have 2 kernels installed. This is the default.

```
$ du -sh /boot
219M    /boot
```
700MB should be fine. No need to waste more space, unless you just want to waste more space.  

On an 18.04 system, 
```
$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       720M  168M  516M  25% /boot
```
Less room is needed.
And anther 18.04 system:
```
$ df /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       237M  195M   30M  87% /boot
```
This one is tight and I've had issues with /boot getting full a few times. I have new storage installed, but need to move the OS onto that new storage. Already have the new storage partitioned and ready ... 
```
nvme0n1                    465.8G disk                     
&#9500;&#9472;nvme0n1p1                   50M part vfat     EFI        
&#9500;&#9472;nvme0n1p2                  600M part ext2     BOOT-A     
&#9492;&#9472;nvme0n1p3                  465G part LVM2_mem            
  &#9500;&#9472;vg00-swap                4.1G lvm  swap                
  &#9500;&#9472;vg00-root                 35G lvm  ext4     root       
  &#9500;&#9472;vg00-var                  35G lvm  ext4     var        
  &#9500;&#9472;vg00-home                 25G lvm  ext4     home
  &#9500;&#9472;vg00-t2004--lvm           10G lvm                      
  &#9492;&#9472;vg00-t2004--r2            10G lvm                      

```
As you can see, I think 600M is sufficient for /boot and 50M is sufficient for a single boot (no dual/tri/quad booting here!), for an Ubuntu /boot/efi area.  You'll also note that I'm leaving most of the storage (500G) unallocated, but managed by LVM2.

---

### Post by fisch3r on 2022-04-05
> **deadflowr said:**
> Your initrd.XXX files are huge.
What compression is being used
```
grep COMPRESS /etc/initramfs-tools/initramfs.conf
```


Edit: I notice ubfan1 posted the same general query.

Result of the command:

[HTML]
# COMPRESS: [ gzip | bzip2 | lz4 | lzma | lzop | xz ]
COMPRESS=lz4[/HTML]

---

### Post by ubfan1 on 2022-04-05
lz4 is the normal compression (it's what I have).  I have Nvidia hardware, (third party driver), and don't have huge initrds.  Seems your initrd builds include something big.  I don't know much about building the initrds or examining them, but others might.

---

### Post by TheFu on 2022-04-05
> **ubfan1 said:**
> lz4 is the normal compression (it's what I have).  I have Nvidia hardware, (third party driver), and don't have huge initrds.  Seems your initrd builds include something big.  I don't know much about building the initrds or examining them, but others might.

**mkinitramfs** is the command. Whenever I've needed to know more (perhaps 3 times since 2006), I'd delve into the manpage for that command.  **update-grub** calls it, so for the most general needs, end-users don't need to use mkinitramfs directly.

---

