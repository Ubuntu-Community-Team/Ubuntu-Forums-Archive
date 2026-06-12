---
title: "Fix dependencies failed due to no space left on device"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by Macamba on 2013-07-08
Hi all,

I'm struggling with a problem, a bit.

While updating my software I got an error. I was asked to report it, but that failed too. In the end all I got was the following window:
> Problem in vhba-dkms
This problem cannot be reported
This is not an official ubuntu package. Please remove any third party package and try again.

Next I tried to fix the installation.

```

macamba@Hermod:~$ sudo apt-get install --fix-broken
...
Unpacking linux-headers-3.2.0-49 (from .../linux-headers-3.2.0-49_3.2.0-49.75_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-49/arch/s390/include/asm/segment.h.dpkg-new' 
(while processing `./usr/src/linux-headers-3.2.0-49/arch/s390/include/asm/segment.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

"No space left on device" eh?

So I tried to remove some old kernels automatically, failed, and tried to remove them manually.

But still the same problem. I have packages with unmet dependencies, linux-headers-3.2.0-49-generic. If I perform a sudo apt-get -f install I get:
```

The following extra packages will be installed:
  linux-headers-3.2.0-49
The following NEW packages will be installed:
  linux-headers-3.2.0-49
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 11.7 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.
```

So, 56.3 MB of additional disk space will be used. How much space do I have?
```

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda10      8.1G  6.6G  1.1G  87% /

```

So, that should work out, should it not? No, it should not. I still get the "No space left on device". And that while I have 1.1G available!

So, what are my options? Do I do a fresh install with a LiveCD? (I checked, what I burned last week, Ubuntu-12.04.2-desktop-amd64.iso is still the latest.

TIA,
Macamba

---

### Post by dino99 on 2013-07-08
the system, by default, will complaint if the free space is less than 10/15 % of the whole partition size. (it needs it for downloading updates and unflatting packages, and creating tmp files, ...)
and your sda10 is very narrow; usually a 10/12G is used at least. So uninstall some app(s) and/or meta-package(s) you does not really need/use (for example video-all & input-all from xserver)

---

### Post by dfayo on 2013-07-10
I had the same problem. This is what I did:

I used > rm -rfv /usr/src/(old kernels) to remove 5 previous versions leaving newest (linux-headers-3.2.0-49) and the two previous, then > apt-get install --fix-broken which fixed the problem. 

I'm relatively new to Ubuntu, so appologies if my Terminal commands are not formatted correctly.

---

### Post by Macamba on 2013-07-10
> **dfayo said:**
> I had the same problem. This is what I did:

I used  to remove 5 previous versions leaving newest (linux-headers-3.2.0-49) and the two previous, then  which fixed the problem. 

I'm relatively new to Ubuntu, so appologies if my Terminal commands are not formatted correctly.

Hi dfayo,

Thanks. That actually helped. I found out I had quite a few old kernels, beginning with linux-headers-3.2.0-33. I started with a listing of the diskdirectory, followed by a double check to find out the latest kernel
```

cd /usr/src/
ls -la
uname -r
```

Next I started to remove the directories that where superfluous (I quickly removed the fv from  your commands)
```

sudo rm -r /usr/src/linux-headers-3.2.0-37*

```
This removes both linux-headers-3.2.0-37 and linux-headers-3.2.0-37-generic 

And then some necessary housekeeping
```

apt-get install --fix-broken 

```

Then I updated my bootloader Grub2, and reordered its contents as I want to have Windows at the top.
```

sudo update-grub2
gksudo grub-customizer

```

Anyway, thanks.
Macamba

---

