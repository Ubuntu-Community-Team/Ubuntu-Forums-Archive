---
title: "Boot full, unmet dependencies when attempting to delete package"
date: 2015-08-09
forum: Installation &amp; Upgrades
---

### Post by Remowax on 2015-08-09
I can't update system or install anything trought Ubuntu Software Center. The upper toolbar has the red "dont drive" symbol and when I click it it says

> An error occured, please run Package Manager or apt-get in a terminal. The error message was 'Error: BrokenCount >0'. This usually means that your installed packages have unmet dependencies. 

Tried googling how to remove old kernels and tried different commands but everytime ran into "unmet dependencies".

uname-r:
```

3.13.0-39-generic

```

ls /boot:
```

abi-3.13.0-32-generic         initrd.img-3.13.0-39-generic
abi-3.13.0-34-generic         lost+found
abi-3.13.0-35-generic         memtest86+.bin
abi-3.13.0-36-generic         memtest86+.elf
abi-3.13.0-37-generic         memtest86+_multiboot.bin
abi-3.13.0-39-generic         System.map-3.13.0-32-generic
config-3.13.0-32-generic      System.map-3.13.0-34-generic
config-3.13.0-34-generic      System.map-3.13.0-35-generic
config-3.13.0-35-generic      System.map-3.13.0-36-generic
config-3.13.0-36-generic      System.map-3.13.0-37-generic
config-3.13.0-37-generic      System.map-3.13.0-39-generic
config-3.13.0-39-generic      vmlinuz-3.13.0-32-generic
grub                          vmlinuz-3.13.0-34-generic
initrd.img-3.13.0-32-generic  vmlinuz-3.13.0-35-generic
initrd.img-3.13.0-34-generic  vmlinuz-3.13.0-36-generic
initrd.img-3.13.0-35-generic  vmlinuz-3.13.0-37-generic
initrd.img-3.13.0-36-generic  vmlinuz-3.13.0-39-generic
initrd.img-3.13.0-37-generic

```

ls /boot | grep vmlinuz | cut -d'-' -f2,3
```

3.13.0-32
3.13.0-34
3.13.0-35
3.13.0-36
3.13.0-37
3.13.0-39

```

I tried to remove the oldest kernel first.

```

tekdino@dino:~$ dpkg -l | grep ^ii | grep 3.13.0-32 | awk -F' ' '{ print $2 }'
linux-headers-3.13.0-32
linux-headers-3.13.0-32-generic
linux-image-3.13.0-32-generic
linux-image-extra-3.13.0-32-generic
tekdino@dino:~$ sudo apt-get remove linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-40-generic : Depends: linux-image-3.13.0-40-generic but it is not going to be installed
 linux-image-extra-3.13.0-61-generic : Depends: linux-image-3.13.0-61-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-61-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




```


When I type sudo apt-get -f install:
```

tekdino@dino:~$ sudo apt-get -f install
[sudo] password for tekdino: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-40-generic linux-image-3.13.0-61-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-40-generic linux-image-3.13.0-61-generic
0 upgraded, 2 newly installed, 0 to remove and 525 not upgraded.
6 not fully installed or removed.
Need to get 0 B/30,3 MB of archives.
After this operation, 84,6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 373135 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-61-generic_3.13.0-61.100_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-61-generic (3.13.0-61.100) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-61-generic_3.13.0-61.100_amd64.deb (--unpack):
 cannot copy extracted data for './boot/config-3.13.0-61-generic' to '/boot/config-3.13.0-61-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
Preparing to unpack .../linux-image-3.13.0-40-generic_3.13.0-40.69_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-40-generic (3.13.0-40.69) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-40-generic_3.13.0-40.69_amd64.deb (--unpack):
 cannot copy extracted data for './boot/config-3.13.0-40-generic' to '/boot/config-3.13.0-40-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-61-generic_3.13.0-61.100_amd64.deb
 /var/cache/apt/archives/linux-image-3.13.0-40-generic_3.13.0-40.69_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

```

Thanks

---

### Post by v3.xx on 2015-08-09
If apt-get can't do it, I would remove with dpkg.  I have seen forum post on this with other options.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=boot+full&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=boot+full&sa=Search&cof=FORID:9)

---

### Post by Bashing-om on 2015-08-09
Remowaxl Hi !

Been a problem for a while, huh ?

Let's see what we can do !
As you are aware the main problem here is :
> 
(No space left on device)


Which is the 1st order of priority. Get some operating head room.
Let's see if the package manager can work to remove the old kernels:
```

sudo apt-get autoremove

```
Else we sic dpkg on the situation, see if dpkg at the lower level can work.


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-08-09
Hay Bashing :)  We haven't crossed path in a while :)

@OP
If you do go with dpkg, it should only be necessary to remove a couple of kernels from /boot and apt-get should start working again.

---

### Post by Remowax on 2015-08-09
Thanks for the replies everyone! Sudo apt-get autoremove didn't work (should have mentioned this in the first post, sorry) but dpkg did the trick. I succeed to delete them one by one (except the kernel in use and 1 before it just in case) and then succesfully ran update and also succeed installing a program trought Software Center. Also the red "no drive" sign is gone. The main problem is solved but just out of curiosity:

1. Is there a way to prevent this from happening again?

2. This was printed many times on the terminal, what does it mean: "Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported."

---

### Post by Bashing-om on 2015-08-09
Remowax; Well ...

The system will not second guess you:
> 
1. Is there a way to prevent this from happening again?

As to if/when/need/want to use an older kernel. The system leaves it to your discretion how to handle old kernels.

Grub has been re-written:
> 
2. This was printed many times on the terminal, what does it mean: "Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.

There is a minor edit one can do to the effected file to make things all better :
As an example my grub file with the recommended change:
```

sysop@1404mini:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
[color=green]GRUB_HIDDEN_TIMEOUT_QUIET=false[/color]
[color=green]GRUB_TIMEOUT=10[/color]
GRUB_DISTRIBUTOR="My-Work-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1600x900

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
sysop@1404mini:~$

```

@v3.xx ; Be assured , I am looking over your shoulder .

[INDENT][INDENT]together,
[INDENT][INDENT][INDENT]we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

