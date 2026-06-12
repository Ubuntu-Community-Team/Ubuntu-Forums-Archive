---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by Durabys on 2014-02-20
I have  this problem that started this night. Every tine I install ANYTHING this happens.

```
durabys@durabys-TravelMate-B113:~$ sudo apt-get install synaptic
[sudo] password for durabys: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
The following packages were automatically installed and are no longer required:
  gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common libp11-kit-gnome-keyring:i386 libpeas-1.0-0
  libpeas-common linux-headers-3.8.0-19 linux-headers-3.8.0-19-generic
  linux-image-3.8.0-19-generic linux-image-extra-3.8.0-19-generic
  openjdk-7-jre-lib ttf-liberation ttf-umefont ttf-unfonts-core wine-gecko1.4
  wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up linux-image-extra-3.8.0-35-generic (3.8.0-35.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-35-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-35-generic.postinst line 1010.
dpkg: error processing linux-image-extra-3.8.0-35-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.8.0-35-generic; however:
  Package linux-image-extra-3.8.0-35-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.8.0.35.53); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.8.0-35-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And then I have to restart the notebook and hope the program is installed. Names of the programs and apps change in the text but otherwise it is identical.

---

### Post by Bashing-om on 2014-02-20
Durabys; Hi !

Maybe time for some house cleaning ?

This:
> 
gzip: stdout: No space left on device

Indicates the source of the problem. - space constraints ! -
Let's get specific and see what the system reports.
Post back the output of terminal commands:
```

df -h
df -i
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes.
I expect that our attention will focus on the /boot directory, but let the system tell us.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Durabys on 2014-02-21
I think I am doing it wrong..

```
durabys@durabys-TravelMate-B113:~$ gzip: stdout: No space left on device
No command 'gzip:' found, did you mean:
 Command 'gzip' from package 'gzip' (main)
gzip:: command not found
durabys@durabys-TravelMate-B113:~$ 


```

---

### Post by ian-weisser on 2014-02-21
> **Durabys said:**
> gzip: stdout: No space left on device

That's not a command to try - that's what your system told you.
Your disk is full.
Reread Bashing-om's instructions for the first steps to free up space.

---

### Post by Durabys on 2014-02-21
> **ian-weisser said:**
> That's not a command to try - that's what your system told you.
Your disk is full.
Reread Bashing-om's instructions for the first steps to free up space.

I feel *so* dumb. Sorry.

> **Bashing-om said:**
> Durabys; Hi !

Maybe time for some house cleaning ?

This:

Indicates the source of the problem. - space constraints ! -
Let's get specific and see what the system reports.
Post back the output of terminal commands:
```

df -h
df -i
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes.
I expect that our attention will focus on the /boot directory, but let the system tell us.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Thanks. Here it is..

```
durabys@durabys-TravelMate-B113:~$ df -h
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root  455G   27G  405G   7% /
none                          4,0K     0  4,0K   0% /sys/fs/cgroup
udev                          3,8G  4,0K  3,8G   1% /dev
tmpfs                         781M  896K  780M   1% /run
none                          5,0M     0  5,0M   0% /run/lock
none                          3,9G   80K  3,9G   1% /run/shm
none                          100M   12K  100M   1% /run/user
/dev/sda2                     229M  210M  7,5M  97% /boot
/dev/sda1                     188M  121K  187M   1% /boot/efi
durabys@durabys-TravelMate-B113:~$ df -i
Filesystem                     Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/xubuntu--vg-root 30244864 337374 29907490    2% /
none                           998535      1   998534    1% /sys/fs/cgroup
udev                           994132    540   993592    1% /dev
tmpfs                          998535    517   998018    1% /run
none                           998535      4   998531    1% /run/lock
none                           998535      5   998530    1% /run/shm
none                           998535     16   998519    1% /run/user
/dev/sda2                      124992    264   124728    1% /boot
/dev/sda1                           0      0        0     - /boot/efi
durabys@durabys-TravelMate-B113:~$ cd /
durabys@durabys-TravelMate-B113:/$ sudo du -sx * | sort -n
[sudo] password for durabys: 
du: cannot access ‘proc/2600/task/2600/fd/4’: No such file or directory
du: cannot access ‘proc/2600/task/2600/fdinfo/4’: No such file or directory
du: cannot access ‘proc/2600/fd/4’: No such file or directory
du: cannot access ‘proc/2600/fdinfo/4’: No such file or directory
0    initrd.img
0    initrd.img.old
0    proc
0    sys
0    vmlinuz
0    vmlinuz.old
4    cdrom
4    dev
4    lib64
4    mnt
4    opt
4    selinux
4    srv
8    media
16    lost+found
36    tmp
48    root
896    run
9500    bin
11472    sbin
13856    etc
214068    boot
500180    var
875632    lib
4633972    usr
22149180    home
durabys@durabys-TravelMate-B113:/$ 
durabys@durabys-TravelMate-B113:/$ ^C
durabys@durabys-TravelMate-B113:/$ 


```

---

### Post by ibjsb4 on 2014-02-21
> /dev/sda2                     229M  210M  7,5M  97% /boot

You need to clean out the old kernels.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Myself, I just use [synaptic]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") and manually remove them.

---

### Post by Durabys on 2014-02-21
> **ibjsb4 said:**
> You need to clean out the old kernels.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Myself, I just use [synaptic]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") and manually remove them.


Is this ok..

```
durabys@durabys-TravelMate-B113:~$ dpkg -l linux-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-doc-3.8. <none>                    (no description available)
ii  linux-firmware 1.106        all          Firmware for Linux kernel drivers
iU  linux-generic  3.8.0.35.53  amd64        Complete Generic Linux kernel and
un  linux-headers  <none>                    (no description available)
un  linux-headers- <none>                    (no description available)
ii  linux-headers- 3.8.0-19.30  all          Header files related to Linux ker
ii  linux-headers- 3.8.0-19.30  amd64        Linux kernel headers for version 
ii  linux-headers- 3.8.0-32.47  all          Header files related to Linux ker
ii  linux-headers- 3.8.0-32.47  amd64        Linux kernel headers for version 
ii  linux-headers- 3.8.0-33.48  all          Header files related to Linux ker
ii  linux-headers- 3.8.0-33.48  amd64        Linux kernel headers for version 
ii  linux-headers- 3.8.0-34.49  all          Header files related to Linux ker
ii  linux-headers- 3.8.0-34.49  amd64        Linux kernel headers for version 
ii  linux-headers- 3.8.0-35.50  all          Header files related to Linux ker
ii  linux-headers- 3.8.0-35.50  amd64        Linux kernel headers for version 
ii  linux-headers- 3.8.0.35.53  amd64        Generic Linux kernel headers
un  linux-image    <none>                    (no description available)
un  linux-image-3. <none>                    (no description available)
ii  linux-image-3. 3.8.0-19.30  amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.8.0-32.47  amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.8.0-33.48  amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.8.0-34.49  amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.8.0-35.50  amd64        Linux kernel image for version 3.
ii  linux-image-ex 3.8.0-19.30  amd64        Linux kernel image for version 3.
ii  linux-image-ex 3.8.0-32.47  amd64        Linux kernel image for version 3.
ii  linux-image-ex 3.8.0-33.48  amd64        Linux kernel image for version 3.
ii  linux-image-ex 3.8.0-34.49  amd64        Linux kernel image for version 3.
iF  linux-image-ex 3.8.0-35.50  amd64        Linux kernel image for version 3.
iU  linux-image-ge 3.8.0.35.53  amd64        Generic Linux kernel image
un  linux-initramf <none>                    (no description available)
un  linux-kernel-h <none>                    (no description available)
un  linux-kernel-l <none>                    (no description available)
ii  linux-libc-dev 3.8.0-35.50  amd64        Linux Kernel Headers for developm
un  linux-restrict <none>                    (no description available)
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
un  linux-source-3 <none>                    (no description available)
un  linux-tools    <none>                    (no description available)
durabys@durabys-TravelMate-B113:~$ dpkg -l linux-* | awk '/^ii/{ print $2 }'
linux-firmware
linux-headers-3.8.0-19
linux-headers-3.8.0-19-generic
linux-headers-3.8.0-32
linux-headers-3.8.0-32-generic
linux-headers-3.8.0-33
linux-headers-3.8.0-33-generic
linux-headers-3.8.0-34
linux-headers-3.8.0-34-generic
linux-headers-3.8.0-35
linux-headers-3.8.0-35-generic
linux-headers-generic
linux-image-3.8.0-19-generic
linux-image-3.8.0-32-generic
linux-image-3.8.0-33-generic
linux-image-3.8.0-34-generic
linux-image-3.8.0-35-generic
linux-image-extra-3.8.0-19-generic
linux-image-extra-3.8.0-32-generic
linux-image-extra-3.8.0-33-generic
linux-image-extra-3.8.0-34-generic
linux-libc-dev:amd64
linux-sound-base
durabys@durabys-TravelMate-B113:~$ uname -r | cut -f1,2 -d"-"
3.8.0-35
durabys@durabys-TravelMate-B113:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"`
linux-firmware
linux-headers-3.8.0-19
linux-headers-3.8.0-19-generic
linux-headers-3.8.0-32
linux-headers-3.8.0-32-generic
linux-headers-3.8.0-33
linux-headers-3.8.0-33-generic
linux-headers-3.8.0-34
linux-headers-3.8.0-34-generic
linux-headers-generic
linux-image-3.8.0-19-generic
linux-image-3.8.0-32-generic
linux-image-3.8.0-33-generic
linux-image-3.8.0-34-generic
linux-image-extra-3.8.0-19-generic
linux-image-extra-3.8.0-32-generic
linux-image-extra-3.8.0-33-generic
linux-image-extra-3.8.0-34-generic
linux-libc-dev:amd64
linux-sound-base
durabys@durabys-TravelMate-B113:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9]
linux-headers-3.8.0-19
linux-headers-3.8.0-19-generic
linux-headers-3.8.0-32
linux-headers-3.8.0-32-generic
linux-headers-3.8.0-33
linux-headers-3.8.0-33-generic
linux-headers-3.8.0-34
linux-headers-3.8.0-34-generic
linux-image-3.8.0-19-generic
linux-image-3.8.0-32-generic
linux-image-3.8.0-33-generic
linux-image-3.8.0-34-generic
linux-image-extra-3.8.0-19-generic
linux-image-extra-3.8.0-32-generic
linux-image-extra-3.8.0-33-generic
linux-image-extra-3.8.0-34-generic
linux-libc-dev:amd64
durabys@durabys-TravelMate-B113:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)"
linux-headers-3.8.0-19
linux-headers-3.8.0-19-generic
linux-headers-3.8.0-32
linux-headers-3.8.0-32-generic
linux-headers-3.8.0-33
linux-headers-3.8.0-33-generic
linux-headers-3.8.0-34
linux-headers-3.8.0-34-generic
linux-image-3.8.0-19-generic
linux-image-3.8.0-32-generic
linux-image-3.8.0-33-generic
linux-image-3.8.0-34-generic
linux-image-extra-3.8.0-19-generic
linux-image-extra-3.8.0-32-generic
linux-image-extra-3.8.0-33-generic
linux-image-extra-3.8.0-34-generic
durabys@durabys-TravelMate-B113:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove
[sudo] password for durabys: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common libp11-kit-gnome-keyring:i386 libpeas-1.0-0
  libpeas-common openjdk-7-jre-lib ttf-liberation ttf-umefont ttf-unfonts-core
  wine-gecko1.4 wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.8.0-19 linux-headers-3.8.0-19-generic linux-headers-3.8.0-32
  linux-headers-3.8.0-32-generic linux-headers-3.8.0-33
  linux-headers-3.8.0-33-generic linux-headers-3.8.0-34
  linux-headers-3.8.0-34-generic linux-image-3.8.0-19-generic
  linux-image-3.8.0-32-generic linux-image-3.8.0-33-generic
  linux-image-3.8.0-34-generic linux-image-extra-3.8.0-19-generic
  linux-image-extra-3.8.0-32-generic linux-image-extra-3.8.0-33-generic
  linux-image-extra-3.8.0-34-generic
0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
3 not fully installed or removed.
Remv linux-headers-3.8.0-19-generic [3.8.0-19.30]
Remv linux-headers-3.8.0-19 [3.8.0-19.30]
Remv linux-headers-3.8.0-32-generic [3.8.0-32.47]
Remv linux-headers-3.8.0-32 [3.8.0-32.47]
Remv linux-headers-3.8.0-33-generic [3.8.0-33.48]
Remv linux-headers-3.8.0-33 [3.8.0-33.48]
Remv linux-headers-3.8.0-34-generic [3.8.0-34.49]
Remv linux-headers-3.8.0-34 [3.8.0-34.49]
Remv linux-image-extra-3.8.0-19-generic [3.8.0-19.30]
Remv linux-image-3.8.0-19-generic [3.8.0-19.30]
Remv linux-image-extra-3.8.0-32-generic [3.8.0-32.47]
Remv linux-image-3.8.0-32-generic [3.8.0-32.47]
Remv linux-image-extra-3.8.0-33-generic [3.8.0-33.48]
Remv linux-image-3.8.0-33-generic [3.8.0-33.48]
Remv linux-image-extra-3.8.0-34-generic [3.8.0-34.49]
Remv linux-image-3.8.0-34-generic [3.8.0-34.49]
Conf linux-image-extra-3.8.0-35-generic (3.8.0-35.50 Ubuntu:13.04/raring-updates [amd64])
Conf linux-image-generic (3.8.0.35.53 Ubuntu:13.04/raring-updates [amd64])
Conf linux-generic (3.8.0.35.53 Ubuntu:13.04/raring-updates [amd64])
durabys@durabys-TravelMate-B113:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common libp11-kit-gnome-keyring:i386 libpeas-1.0-0
  libpeas-common openjdk-7-jre-lib ttf-liberation ttf-umefont ttf-unfonts-core
  wine-gecko1.4 wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.8.0-19* linux-headers-3.8.0-19-generic*
  linux-headers-3.8.0-32* linux-headers-3.8.0-32-generic*
  linux-headers-3.8.0-33* linux-headers-3.8.0-33-generic*
  linux-headers-3.8.0-34* linux-headers-3.8.0-34-generic*
  linux-image-3.8.0-19-generic* linux-image-3.8.0-32-generic*
  linux-image-3.8.0-33-generic* linux-image-3.8.0-34-generic*
  linux-image-extra-3.8.0-19-generic* linux-image-extra-3.8.0-32-generic*
  linux-image-extra-3.8.0-33-generic* linux-image-extra-3.8.0-34-generic*
0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 942 MB disk space will be freed.
(Reading database ... 285151 files and directories currently installed.)
Removing linux-headers-3.8.0-19-generic ...
Removing linux-headers-3.8.0-19 ...
Removing linux-headers-3.8.0-32-generic ...
Removing linux-headers-3.8.0-32 ...
Removing linux-headers-3.8.0-33-generic ...
Removing linux-headers-3.8.0-33 ...
Removing linux-headers-3.8.0-34-generic ...
Removing linux-headers-3.8.0-34 ...
Removing linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Removing linux-image-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Removing linux-image-extra-3.8.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-extra-3.8.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Removing linux-image-3.8.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.8.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Removing linux-image-extra-3.8.0-33-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-extra-3.8.0-33-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
Removing linux-image-3.8.0-33-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.8.0-33-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
Removing linux-image-extra-3.8.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-extra-3.8.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
Removing linux-image-3.8.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.8.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
Setting up linux-image-extra-3.8.0-35-generic (3.8.0-35.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-generic (3.8.0.35.53) ...
Setting up linux-generic (3.8.0.35.53) ...
durabys@durabys-TravelMate-B113:~$ 


```

---

### Post by ibjsb4 on 2014-02-21
Sorry, but your asking me for the go-a-head on something I have not used.  

With my disclaimer in place; I do not see anything destructive going on.  Looks to me that you will end up on 3.8.0.35.53.  

I like to keep the current running kernel as backup and I am not seeing it holding back the current kernel; maybe it is and I just am not seeing it.

---

### Post by Durabys on 2014-02-21
> **ibjsb4 said:**
> Sorry, but your asking me for the go-a-head on something I have not used.  

With my disclaimer in place; I do not see anything destructive going on.  Looks to me that you will end up on 3.8.0.35.53.  

I like to keep the current running kernel as backup and I am not seeing it holding back the current kernel; maybe it is and I just am not seeing it.

Ok. It seems this works now. Thanks for help. This is solved now.

---

