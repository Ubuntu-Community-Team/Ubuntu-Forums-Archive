---
title: "Xen PV Guest won't boot latest kernel- OSError: [Errno 28] No space left on device"
date: 2018-01-11
forum: Installation &amp; Upgrades
---

### Post by mabarkdoll on 2018-01-11
Hello, I have an Ubuntu 14.04 run Xen and the VM that I'm having issues with it an Ubuntu 16.04 LTS server that wouldn't boot when I upgraded it to the newest kernel with:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

The following is the xen log upon reboot:
```
$ tailf /var/log/xen/servername.log
Domain 24 needs to be cleaned up: destroying the domain
Done. Rebooting now
libxl: error: libxl_bootloader.c:628:bootloader_finished: bootloader failed - consult logfile /var/log/xen/bootloader.27.log
libxl: error: libxl_exec.c:118:libxl_report_child_exitstatus: bootloader [-1] exited with error status 1
libxl: error: libxl_create.c:1024:domcreate_rebuild_done: cannot (re-)build domain: -3
```

```
cat /var/log/xen/bootloader.27.log
```

```
Using <class 'grub.GrubConf.Grub2ConfigFile'> to parse /grub/grub.cfg    pyGRUB  version 0.6
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; Ubuntu                                                                 &#9474;
 &#9474; Ubuntu, with Linux 4.4.0-109-generic                                   &#9474;
 &#9474; Ubuntu, with Linux 4.4.0-109-generic (recovery mode)                   &#9474;
 &#9474; Ubuntu, with Linux 4.4.0-108-generic                                   &#9474;
 &#9474; Ubuntu, with Linux 4.4.0-108-generic (recovery mode)                   &#9474;
 &#9474; Ubuntu, with Linux 4.4.0-104-generic                                   &#9474;
 &#9474; Ubuntu, with Linux 4.4.0-104-generic (recovery mode)                   &#9474;
 &#9474; Ubuntu, with Linux 4.4.0-15-generic                                    &#9474;
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Use the ^ and &#9524; keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the
commands before booting, 'a' to modify the kernel arguments
before booting, or 'c' for a command line.














Traceback (most recent call last):
  File "/usr/lib/xen-4.4/bin/pygrub", line 905, in <module>
    os.write(fd, ostring)
OSError: [Errno 28] No space left on device
```

I was able to get the vm to boot only by rapidly attempt to access the menu options and boot the old kernel (4.4.0-15-generic).  Disk space and inodes seems fine on the host Ubuntu 14.04LTS and Ubuntu 16.04LTS Guest.

Ubuntu 14.04 Host:
```
root@host:/var/log/xen# df -hFilesystem      Size  Used Avail Use% Mounted on
udev            197M   12K  197M   1% /dev
tmpfs            42M  1.1M   41M   3% /run
/dev/dm-0       104G   49G   50G  50% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            208M     0  208M   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda1       236M   40M  184M  18% /boot
root@host:/var/log/xen# df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
udev              50K   721   49K    2% /dev
tmpfs             52K   849   52K    2% /run
/dev/dm-0        6.6M   86K  6.5M    2% /
none              52K     2   52K    1% /sys/fs/cgroup
none              52K     5   52K    1% /run/lock
none              52K     1   52K    1% /run/shm
none              52K     2   52K    1% /run/user
/dev/sda1         61K   298   61K    1% /boot
root@host:/var/log/xen# 
```


Ubuntu 16.04 PV Guest:
```
root@guest:~# df -hFilesystem                            Size  Used Avail Use% Mounted on
udev                                  950M     0  950M   0% /dev
tmpfs                                 200M  3.1M  197M   2% /run
/dev/mapper/guest--vg-root              47G  4.3G   40G  10% /
tmpfs                                 997M     0  997M   0% /dev/shm
tmpfs                                 5.0M     0  5.0M   0% /run/lock
tmpfs                                 997M     0  997M   0% /sys/fs/cgroup
/dev/xvda1                            472M  192M  256M  43% /boot
tmpfs                                 200M     0  200M   0% /run/user/1000
root@www2:~# df -hi
Filesystem                           Inodes IUsed IFree IUse% Mounted on
udev                                   238K   406  237K    1% /dev
tmpfs                                  250K   491  249K    1% /run
/dev/mapper/guest--vg-root              3.0M  177K  2.8M    6% /
tmpfs                                  250K     1  250K    1% /dev/shm
tmpfs                                  250K     7  250K    1% /run/lock
tmpfs                                  250K    16  250K    1% /sys/fs/cgroup
/dev/xvda1                             122K   315  122K    1% /boot
tmpfs                                  250K     4  250K    1% /run/user/1000
root@guest:~# 

```

Here is the guest OS kernels:
```
root@guest:~# dpkg -l | grep linux-image-
ii  linux-image-4.4.0-104-generic       4.4.0-104.127                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-108-generic       4.4.0-108.131                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-109-generic       4.4.0-109.132                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-15-generic        4.4.0-15.31                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-104-generic 4.4.0-104.127                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-108-generic 4.4.0-108.131                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-109-generic 4.4.0-109.132                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-15-generic  4.4.0-15.31                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                 4.4.0.109.114                              amd64        Generic Linux kernel image
root@guest:~#
```

I'm currently able to boot to 4.4.0-15.31

Here is my xen config file that I use to start the vm:
```
# cat /etc/xen/guest.cfg
# /var/lib/xen/images/ubuntu-netboot/xenial16LTS


name = "guest"


#kernel = "/var/lib/xen/images/ubuntu-netboot/xenial16LTS/vmlinuz"
#ramdisk = "/var/lib/xen/images/ubuntu-netboot/xenial16LTS/initrd.gz"
bootloader = "/usr/lib/xen-4.4/bin/pygrub"


memory = 2048
vcpus = 1




disk = [ '/dev/host-disk2-vg/guest-disk,raw,xvda,rw' ]




#
#  Networking
#
vif         = [ 'ip=xxx.xxx.xxx.xxx ,mac=AA:BB:CC:DD:EE:FF' ]


#
#  Behaviour
#
on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'

```

I also tried launching the vm with strace output is here:  [https://pastebin.com/8ctS3TQh](https://pastebin.com/8ctS3TQh)

I'm a bit lost as to the cause of this... I was hoping to just upgrade the kernel for meltdown and spetre, but this issue I've never faced before.  I think it might be related to pygrub and the new kernel?  I don't know for sure though anything I can check to figure this out better?  Thanks.

---

### Post by DuckHook on 2018-01-11
I would highly suspect the new kernel as the culprit. Meltdown and Spectre have forced the kernel devs into playing a high stakes game of whack-a-mole for now. I expect a flurry of kernel upgrades over the next few weeks. I'm afraid you will have decide whether covering off Meltdown is worth the loss of your Xen functionality. If not, then sit tight for a kernel fix. In either case, please help the devs by reporting the breakage as a bug on launchpad. Include your trace data in your report.

---

### Post by mabarkdoll on 2018-01-11
I tried to report it but it failed to report...

# ubuntu-bug linux


*** Collecting problem information


The collected information can be sent to the developers to improve the
application. This might take a few minutes.
...............


*** Problem in linux-image-4.4.0-15-generic


The problem cannot be reported:


This is not an official Ubuntu package. Please remove any third party package and try again.


Press any key to continue... 


No pending crash reports. Try --help for more information.

---

