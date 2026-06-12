---
title: "Graphics problem(?) upgrading to 16.04"
date: 2019-04-06
forum: Installation &amp; Upgrades
---

### Post by RegUB on 2019-04-06
I have been running 14.04 on my old Acer 5920 laptop for the last 3 years and all worked fine. I just tried to upgrade to 16.04. All seemed to be going well, until I got the following error -

```
Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself.
```

The system boots to a terminal prompt, but no GUI. Any help will be appreciated!

---

### Post by Bashing-om on 2019-04-06
RegUB; Hey - hey ..

Let's look and see what the hardware is and if a driver for graphics is loaded.
Post back:
```

sudo lshw -C display
cat /var/log/gpu-manager.log

```

[INDENT]maybe this
[INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT]

---

### Post by RegUB on 2019-04-07
> **Bashing-om said:**
> RegUB; Hey - hey ..

Let's look and see what the hardware is and if a driver for graphics is loaded.
Post back:
```

sudo lshw -C display
cat /var/log/gpu-manager.log

```

[INDENT]maybe this
[INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT]
I'm currently booting from a DVD but I guess the lshw output should be the same. It is -
```
ubuntu@ubuntu:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RV620/M82 [Mobility Radeon HD 3450/3470]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:d0000000-dfffffff memory:f0200000-f020ffff ioport:2000(size=256) memory:f0220000-f023ffff

```

The installation gpu-manager.log from the hard drive is as follows -
```
ubuntu@ubuntu:/media/ubuntu/f49ee143-3bec-431b-bb3b-b2decd131f87/var/log$ cat   gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/3.13.0-168-generic/updates/dkms
Looking for nvidia modules in /lib/modules/3.13.0-168-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? no
Is radeon loaded? yes
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Detected LTS < 14.04.5. Forcing Intel/SNA
Vendor/Device Id: 1002:95c4
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "radeon"
Found "/dev/dri/card0", driven by "radeon"
output 0:
	card0-LVDS-1
Number of connected outputs for /dev/dri/card0: 1
Skipping "/dev/dri/card0", driven by "radeon"
Skipping "/dev/dri/card0", driven by "radeon"
Does it require offloading? no
last cards number = 1
Has amd? yes
Has intel? no
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? no
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? no
Is prime egl available? no
Single card detected
Kernel Module is not loaded
Nothing to do
No change - nothing to do

```

---

### Post by Bashing-om on 2019-04-07
RegUB; Yukkie ouch !

Something in the upgrade did not go well:
14.04:
> 
trusty-updates (kernel): Generic Linux kernel image 
3.13.0.168.179: amd64 arm64 armhf i386 ppc64el

16.04:
> 
xenial-updates (kernel): Generic Linux kernel image 
4.4.0.145.153: amd64 arm64 armhf i386 ppc64el s390x


and as a consequence ->
> 
Kernel Module is not loaded

from the log file.

So .... What to do, oh what to do ??

When you boot the installed system what does "The system boots to a terminal prompt" mean ? Is this a grub prompt or a terminal interface to the system ?

If we can get to a true terminal interface, will make trouble shooting much easier.

---

### Post by RegUB on 2019-04-08
> **Bashing-om said:**
> 

When you boot the installed system what does "The system boots to a terminal prompt" mean ? Is this a grub prompt or a terminal interface to the system ?

If we can get to a true terminal interface, will make trouble shooting much easier.

It is a terminal interface - however, I can view all the contents of the installation hard drive when I boot from the 14.04 DVD. And I have just noticed that the timestamp on gpu-manager.log is from before I ran the upgrade.

---

### Post by Bashing-om on 2019-04-08
RegUB; Ho Kay -

Let's see what condition our condition is in.

From that terminal execute these commands:
```

uname -r
sudo apt autoclean
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudp dpkg -C

```
If that all comes back fine good and dandy, we see what is going on with the graphics.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by RegUB on 2019-04-10
> **Bashing-om said:**
> RegUB; Ho Kay -

From that terminal execute these commands:
```

uname -r
sudo apt autoclean
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudp dpkg -C

```

Thanks, I have made some progress.

uname -r initially gave 3.13.0-168-generic. The autoremove step then put out a message - can't remember it exactly - but it implied the update had not finished and said that "dpkg --configure -a" should be run. So I ran this. It ran for quite a while and finally got to a sequence where it was putting out lots of messages like the following -

update-initramfs: Generating /boot/initrd.img-3.13.0-168-generic
E: amd64-microcode: unsupported kernel version!
update-initramfs: Generating /boot/initrd.img-3.13.0-167-generic
E: amd64-microcode: unsupported kernel version!

Loads of new kernels appeared in /boot. It got as far as 3.13.0-129, at which point I CTL-C to stop it.

However the GUI problem appears to now be fixed. uname -r now gives 4.4.0-145-generic. But running the autoremove step again gets into the 'unsupported kernel' loop again. Can I just remove everything in /boot relating to 3.13?

I'm not convinced everything is totally fixed yet. I guess I still need to run the apt full-upgrade & apt install steps? - but wanted to check on what to do about the kernels first.

---

### Post by Bashing-om on 2019-04-10
RegUB; Yup - 
Let's check what is going on with the kernels.
Post back:
```

df -h
df -i
dpkg -l | grep linux-

```

See what we can do about getting rid of the cruft.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by RegUB on 2019-04-10
> **Bashing-om said:**
> RegUB; Yup - 
Let's check what is going on with the kernels.
Post back:
```

df -h
df -i
dpkg -l | grep linux-

```

See what we can do about getting rid of the cruft.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

```
reg@reg-Aspire-5920G:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.0G     0  2.0G   0% /dev
tmpfs           396M  6.6M  389M   2% /run
/dev/sda1       226G   37G  177G  18% /
tmpfs           2.0G  109M  1.9G   6% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           396M   84K  395M   1% /run/user/1000

reg@reg-Aspire-5920G:~$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             500332     518   499814    1% /dev
tmpfs            505647     805   504842    1% /run
/dev/sda1      15007744 1894461 13113283   13% /
tmpfs            505647     110   505537    1% /dev/shm
tmpfs            505647       6   505641    1% /run/lock
tmpfs            505647      18   505629    1% /sys/fs/cgroup
cgmfs            505647      14   505633    1% /run/cgmanager/fs
tmpfs            505647      42   505605    1% /run/user/1000

reg@reg-Aspire-5920G:~$ dpkg -l | grep linux-
ii  linux-base                                            4.5ubuntu1~16.04.1                            all          Linux image base package
iF  linux-firmware                                        1.157.21                                      all          Firmware for Linux kernel drivers
iU  linux-generic                                         4.4.0.145.153                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-100                              3.13.0-100.147                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-100-generic                      3.13.0-100.147                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-101                              3.13.0-101.148                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-101-generic                      3.13.0-101.148                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-103                              3.13.0-103.150                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-103-generic                      3.13.0-103.150                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-105                              3.13.0-105.152                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-105-generic                      3.13.0-105.152                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-106                              3.13.0-106.153                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-106-generic                      3.13.0-106.153                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-107                              3.13.0-107.154                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-107-generic                      3.13.0-107.154                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-108                              3.13.0-108.155                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-108-generic                      3.13.0-108.155                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-109                              3.13.0-109.156                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-109-generic                      3.13.0-109.156                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-110                              3.13.0-110.157                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-110-generic                      3.13.0-110.157                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-112                              3.13.0-112.159                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-112-generic                      3.13.0-112.159                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-115                              3.13.0-115.162                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-115-generic                      3.13.0-115.162                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-116                              3.13.0-116.163                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-116-generic                      3.13.0-116.163                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-117                              3.13.0-117.164                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-117-generic                      3.13.0-117.164                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-119                              3.13.0-119.166                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-119-generic                      3.13.0-119.166                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-121                              3.13.0-121.170                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-121-generic                      3.13.0-121.170                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-123                              3.13.0-123.172                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-123-generic                      3.13.0-123.172                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-125                              3.13.0-125.174                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-125-generic                      3.13.0-125.174                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-126                              3.13.0-126.175                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-126-generic                      3.13.0-126.175                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-128                              3.13.0-128.177                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-128-generic                      3.13.0-128.177                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-129                              3.13.0-129.178                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-129-generic                      3.13.0-129.178                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-132                              3.13.0-132.181                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-132-generic                      3.13.0-132.181                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-133                              3.13.0-133.182                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-133-generic                      3.13.0-133.182                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-135                              3.13.0-135.184                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-135-generic                      3.13.0-135.184                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-137                              3.13.0-137.186                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-137-generic                      3.13.0-137.186                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-139                              3.13.0-139.188                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-139-generic                      3.13.0-139.188                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-141                              3.13.0-141.190                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-141-generic                      3.13.0-141.190                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-142                              3.13.0-142.191                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-142-generic                      3.13.0-142.191                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-143                              3.13.0-143.192                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-143-generic                      3.13.0-143.192                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-144                              3.13.0-144.193                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-144-generic                      3.13.0-144.193                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-145                              3.13.0-145.194                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-145-generic                      3.13.0-145.194                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-147                              3.13.0-147.196                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-147-generic                      3.13.0-147.196                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-149                              3.13.0-149.199                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-149-generic                      3.13.0-149.199                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-151                              3.13.0-151.201                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-151-generic                      3.13.0-151.201                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-153                              3.13.0-153.203                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-153-generic                      3.13.0-153.203                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-155                              3.13.0-155.205                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-155-generic                      3.13.0-155.205                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-156                              3.13.0-156.206                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-156-generic                      3.13.0-156.206                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-157                              3.13.0-157.207                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-157-generic                      3.13.0-157.207                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-158                              3.13.0-158.208                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-158-generic                      3.13.0-158.208                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-160                              3.13.0-160.210                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-160-generic                      3.13.0-160.210                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-161                              3.13.0-161.211                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-161-generic                      3.13.0-161.211                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-162                              3.13.0-162.212                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-162-generic                      3.13.0-162.212                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-163                              3.13.0-163.213                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-163-generic                      3.13.0-163.213                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-164                              3.13.0-164.214                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-164-generic                      3.13.0-164.214                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-165                              3.13.0-165.215                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-165-generic                      3.13.0-165.215                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-166                              3.13.0-166.216                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-166-generic                      3.13.0-166.216                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-167                              3.13.0-167.217                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-167-generic                      3.13.0-167.217                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-168                              3.13.0-168.218                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-168-generic                      3.13.0-168.218                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-92                               3.13.0-92.139                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                       3.13.0-92.139                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-95                               3.13.0-95.142                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-95-generic                       3.13.0-95.142                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-96                               3.13.0-96.143                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic                       3.13.0-96.143                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-98                               3.13.0-98.145                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-98-generic                       3.13.0-98.145                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-145                               4.4.0-145.171                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-145-generic                       4.4.0-145.171                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.4.0.145.153                                 amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-100-generic                        3.13.0-100.147                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-101-generic                        3.13.0-101.148                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-103-generic                        3.13.0-103.150                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-105-generic                        3.13.0-105.152                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-106-generic                        3.13.0-106.153                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-107-generic                        3.13.0-107.154                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-108-generic                        3.13.0-108.155                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-109-generic                        3.13.0-109.156                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-110-generic                        3.13.0-110.157                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-112-generic                        3.13.0-112.159                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-113-generic                        3.13.0-113.160                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-115-generic                        3.13.0-115.162                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-116-generic                        3.13.0-116.163                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-117-generic                        3.13.0-117.164                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-119-generic                        3.13.0-119.166                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-121-generic                        3.13.0-121.170                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-123-generic                        3.13.0-123.172                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-125-generic                        3.13.0-125.174                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-126-generic                        3.13.0-126.175                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-128-generic                        3.13.0-128.177                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-129-generic                        3.13.0-129.178                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-132-generic                        3.13.0-132.181                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-133-generic                        3.13.0-133.182                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-135-generic                        3.13.0-135.184                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-137-generic                        3.13.0-137.186                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-139-generic                        3.13.0-139.188                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-141-generic                        3.13.0-141.190                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-142-generic                        3.13.0-142.191                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-143-generic                        3.13.0-143.192                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-144-generic                        3.13.0-144.193                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-145-generic                        3.13.0-145.194                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-147-generic                        3.13.0-147.196                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-149-generic                        3.13.0-149.199                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-151-generic                        3.13.0-151.201                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-153-generic                        3.13.0-153.203                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-155-generic                        3.13.0-155.205                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-156-generic                        3.13.0-156.206                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-157-generic                        3.13.0-157.207                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-158-generic                        3.13.0-158.208                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-160-generic                        3.13.0-160.210                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-161-generic                        3.13.0-161.211                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-162-generic                        3.13.0-162.212                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-163-generic                        3.13.0-163.213                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-164-generic                        3.13.0-164.214                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-165-generic                        3.13.0-165.215                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-166-generic                        3.13.0-166.216                                amd64        Signed kernel image generic
ii  linux-image-3.13.0-167-generic                        3.13.0-167.217                                amd64        Signed kernel image generic
ii  linux-image-3.13.0-168-generic                        3.13.0-168.218                                amd64        Signed kernel image generic
rc  linux-image-3.13.0-32-generic                         3.13.0-32.57                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-92-generic                         3.13.0-92.139                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-93-generic                         3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-95-generic                         3.13.0-95.142                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-96-generic                         3.13.0-96.143                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-98-generic                         3.13.0-98.145                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-145-generic                         4.4.0-145.171                                 amd64        Signed kernel image generic
ii  linux-image-extra-3.13.0-100-generic                  3.13.0-100.147                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-101-generic                  3.13.0-101.148                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-103-generic                  3.13.0-103.150                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-105-generic                  3.13.0-105.152                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-106-generic                  3.13.0-106.153                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-107-generic                  3.13.0-107.154                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-108-generic                  3.13.0-108.155                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-109-generic                  3.13.0-109.156                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-110-generic                  3.13.0-110.157                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-112-generic                  3.13.0-112.159                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-113-generic                  3.13.0-113.160                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-115-generic                  3.13.0-115.162                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-116-generic                  3.13.0-116.163                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-117-generic                  3.13.0-117.164                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-119-generic                  3.13.0-119.166                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-121-generic                  3.13.0-121.170                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-123-generic                  3.13.0-123.172                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-125-generic                  3.13.0-125.174                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-126-generic                  3.13.0-126.175                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-128-generic                  3.13.0-128.177                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-129-generic                  3.13.0-129.178                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-132-generic                  3.13.0-132.181                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-133-generic                  3.13.0-133.182                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-135-generic                  3.13.0-135.184                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-137-generic                  3.13.0-137.186                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-139-generic                  3.13.0-139.188                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-141-generic                  3.13.0-141.190                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-142-generic                  3.13.0-142.191                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-143-generic                  3.13.0-143.192                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-144-generic                  3.13.0-144.193                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-145-generic                  3.13.0-145.194                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-147-generic                  3.13.0-147.196                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-149-generic                  3.13.0-149.199                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-151-generic                  3.13.0-151.201                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-153-generic                  3.13.0-153.203                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-155-generic                  3.13.0-155.205                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-156-generic                  3.13.0-156.206                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-157-generic                  3.13.0-157.207                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-158-generic                  3.13.0-158.208                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-160-generic                  3.13.0-160.210                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-161-generic                  3.13.0-161.211                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-162-generic                  3.13.0-162.212                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-163-generic                  3.13.0-163.213                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-164-generic                  3.13.0-164.214                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-165-generic                  3.13.0-165.215                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-92-generic                   3.13.0-92.139                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-95-generic                   3.13.0-95.142                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-96-generic                   3.13.0-96.143                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-98-generic                   3.13.0-98.145                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   4.4.0.145.153                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  4.4.0-145.171                                 amd64        Linux Kernel Headers for development
ii  linux-modules-3.13.0-166-generic                      3.13.0-166.216                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-3.13.0-167-generic                      3.13.0-167.217                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-3.13.0-168-generic                      3.13.0-168.218                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-145-generic                       4.4.0-145.171                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-3.13.0-166-generic                3.13.0-166.216                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-3.13.0-167-generic                3.13.0-167.217                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-3.13.0-168-generic                3.13.0-168.218                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-145-generic                 4.4.0-145.171                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

---

### Post by Bashing-om on 2019-04-10
RegUB; Hey - hey :)

Let's try the easy way 1st.
The root of the issue is here:
```

iU  linux-generic

```
where the "iU" means the desired state is (i)nstalled but only (U)npacked - so not fully installed. This meta package controls installing the kernels.
so - what results:
```

sudo apt install --reinstall linux-generic

```

If and only if the above completes with no errors ... Let's have the package manager remove those obsolete packages (kernels)
```

sudo apt autoremove

```

[INDENT][INDENT]easy does it - I hope[/INDENT][/INDENT]

---

### Post by RegUB on 2019-04-10
> **Bashing-om said:**
> RegUB; Hey - hey :)

```

sudo apt install --reinstall linux-generic

```


```
reg@reg-Aspire-5920G:~$ sudo apt install --reinstall linux-generic
[sudo] password for reg: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```
This is the same message that I got when I ran autoremove, as mentioned previously, after which the dpkg --configure produced the "unsupported kernel version" messages. Should I run dpkg --configure again?

---

### Post by Bashing-om on 2019-04-10
RegUB; Hummm ...

Try this:
```

sudo dpkg --configure --pending

```

[INDENT]maybe
[/INDENT]

---

### Post by RegUB on 2019-04-10
> **Bashing-om said:**
> RegUB; Hummm ...

Try this:
```

sudo dpkg --configure --pending

```

[INDENT]maybe
[/INDENT]

I hit CTL-C after it started on initrd.img-3.13.0-166-generic so I don't know how relevant are the messages following that?
```
reg@reg-Aspire-5920G:~$ sudo dpkg --configure --pending
Setting up linux-firmware (1.157.21) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-145-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-168-generic
E: amd64-microcode: unsupported kernel version!
update-initramfs: Generating /boot/initrd.img-3.13.0-167-generic
E: amd64-microcode: unsupported kernel version!
update-initramfs: Generating /boot/initrd.img-3.13.0-166-generic
^Cdpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script was interrupted
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.145.153); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-firmware
 linux-image-generic
 linux-generic

```

---

### Post by Bashing-om on 2019-04-10
RegUB; Well -

All I can suggest is to allow dpkg to complete. The package management system must be in a consistent state, You have plenty of disk space so what gets installed in the healing process can not hurt.

Once consistent then remove the cruft,

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by RegUB on 2019-04-11
> **Bashing-om said:**
> RegUB; Well -

All I can suggest is to allow dpkg to complete. The package management system must be in a consistent state, You have plenty of disk space so what gets installed in the healing process can not hurt.

Once consistent then remove the cruft,

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]
OK, done that, and then ran the following without problems-
```
sudo apt install --reinstall linux-generic
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudp dpkg -C
```
All seems to be working OK. Still have all the old 3.13 kernel files in /boot which I guess can just be deleted - there is a script called purge-old-kernels which looks like it will do the trick (unless you can suggest a better way). Thanks for your help.

---

### Post by Bashing-om on 2019-04-11
RegUB; Geat !

Let's do the better way and have the package manager - if the system is now in a consistent state- take care of those old kernels.
```

sudo apt autoremove

```
which is supposed to also remove all old kernels less ONE. Should leave the present booting kernel and one other version under the current. Try again - and if it does not we need to find out the why not,
Else, sure, we can have apt do the dirty work or even drop down to the dpkg level to effect the removal. But we must not go behind the package manager's back to effect the removal as that creates additional issues we  then have to deal with.

[INDENT]good when a plan works out :)
[/INDENT]

---

