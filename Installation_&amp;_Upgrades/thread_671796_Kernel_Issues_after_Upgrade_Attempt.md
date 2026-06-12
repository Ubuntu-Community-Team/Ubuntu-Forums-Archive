---
title: "Kernel Issues after Upgrade Attempt"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by dissillus on 2008-01-18
Hi there,

I've got (I had?) a machine running Ubuntu 7.04 Server up for a while, and I decided to try and upgrade to 7.10. I changed the apt/sources.list to reflect the new codename, and then did an apt-get dist-upgrade.

Everythign went swimmingly, except at the very end, I was told the new kernel couldn't be installed. The following is the error message I initially got after the first upgrade attempt...

```

...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.20-15-server
Errors were encountered while processing:
 linux-image-2.6.22-14-server
 linux-ubuntu-modules-2.6.22-14-server
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried an apt-get dist-upgrade again, only to get the following:

```

root@fox:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.22-14-server (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
/usr/bin/perl: symbol lookup error: /usr/local/lib/perl/5.8.8/auto/Cwd/Cwd.so: undefined symbol: strlcpy
dpkg: error processing linux-image-2.6.22-14-server (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-server:
 linux-ubuntu-modules-2.6.22-14-server depends on linux-image-2.6.22-14-server; however:
  Package linux-image-2.6.22-14-server is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.22-14-server; however:
  Package linux-image-2.6.22-14-server is not configured yet.
 linux-image-server depends on linux-ubuntu-modules-2.6.22-14-server; however:
  Package linux-ubuntu-modules-2.6.22-14-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.22.14.21); however:
  Package linux-image-server is not configured yet.
dpkg: E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems I'm in some sort of looping dependency hell...can anyone shed some light on what's going on here, or ever better...perhaps suggest how to fix it? :-)

---

### Post by Craigus on 2008-01-18
Can you boot with the old kernel and install the new kernel with apt or synaptic ?

---

### Post by dissillus on 2008-01-21
Nope, and as a matter of fact, when I reboot into 2.6.22-14, I get a kernel panic. It is listed in the bootloader menu though, and booting into the old kernel works just fine. Still Can't dist-upgrade, because it says the same 4 packages are busted...

```
tduff@fox:/etc$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.22-14-server (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
/usr/bin/perl: symbol lookup error: /usr/local/lib/perl/5.8.8/auto/Cwd/Cwd.so: undefined symbol: strlcpy
dpkg: error processing linux-image-2.6.22-14-server (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-server:
 linux-ubuntu-modules-2.6.22-14-server depends on linux-image-2.6.22-14-server; however:
  Package linux-image-2.6.22-14-server is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.22-14-server; however:
  Package linux-image-2.6.22-14-server is not configured yet.
 linux-image-server depends on linux-ubuntu-modules-2.6.22-14-server; however:
  Package linux-ubuntu-modules-2.6.22-14-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.22.14.21); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-server
 linux-ubuntu-modules-2.6.22-14-server
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by PmDematagoda on 2008-01-21
Boot into an old kernel and post the outputs of:-
```
sudo dpkg --configure -a
```
and
```
sudo apt-get install -f
```

---

### Post by dissillus on 2008-01-27
```
root@fox:/etc/apt# sudo dpkg --configure -a
```

Gives...

```
Setting up linux-image-2.6.22-14-server (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
/usr/bin/perl: symbol lookup error: /usr/local/lib/perl/5.8.8/auto/Cwd/Cwd.so: undefined symbol: strlcpy
dpkg: error processing linux-image-2.6.22-14-server (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.22-14-server

```

and 
```

root@fox:/etc/apt# sudo apt-get install -f

```

gives


```

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-server (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
find: /lib/firmware/2.6.22-14-server: No such file or directory
/usr/bin/perl: symbol lookup error: /usr/local/lib/perl/5.8.8/auto/Cwd/Cwd.so: undefined symbol: strlcpy
dpkg: error processing linux-image-2.6.22-14-server (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.22-14-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by galamud on 2008-04-25
Run the following:

```

$ sudo perl5.8.8 `which cpan`
CPAN: File::HomeDir loaded ok (v0.66)

cpan shell -- CPAN exploration and modules installation (v1.9205)
ReadLine support enabled

cpan[1]> install K/KW/KWILLIAMS/PathTools-3.2701.tar.gz

```

Then

```

$ sudo apt-get install linux

```

And you should be good to go.

---

