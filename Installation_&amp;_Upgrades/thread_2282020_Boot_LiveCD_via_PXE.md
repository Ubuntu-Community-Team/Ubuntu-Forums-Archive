---
title: "Boot LiveCD via PXE"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by xerox2 on 2015-06-11
Hello guys,
I've build my own LiveCD with the following guide: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

The ISO runs fine and boots to ubuntu. But I need this to be booted from a PXE Server.

I'm using the following boot parameters (syslinux):
```
 LABEL LNX
 MENU LABEL Linux Recovery System
 KERNEL Linux\Rescue\vmlinuz
 APPEND  initrd=Linux\Rescue\initrd.img boot=casper username=root  file=/cdrom/preseed/ubuntu.seed noeject nomodeset noswap  module.blacklist=vmwgfx  fetch=tftp://XXX.XXX.XXX.XXX/Linux/Rescue/filesystem.squashfs
#---
 LABEL GParted
 MENU LABEL GParted
 KERNEL Linux\GParted\vmlinuz
 APPEND  initrd=Linux\GParted\initrd.img boot=live config components  union=overlay username=user noswap noeject ip= nomodeset  fetch=tftp://XXX.XXX.XXX.XXX/Linux/GParted/filesystem.squashfs
#---
```

GParted runs fine but Ubuntu doesn't seem to support fetch parameter, it boots to initramfs and claims "Unable to find a medium containing a live system". What am I doing wrong?

Secondly, I created a tty1.conf with:
```
exec /sbin/rungetty --autologin root tty1
```

It does not work and the file seems to be changed after booting up the iso.

Can you help me with this?

Thank you!

---

### Post by tempusfugit2 on 2015-06-14
Hello xerox2,

I'm far from being an expert but I managed to do what you are trying so sharing my experience;
My understanding of how this works is that tftp protocol is used only to pass the kernel and initrd to the client, while the download of the splash file system 
would be advisable happens via nfs or cifs (but maybe I'm wrong); I successeded to have the splash deployed via cifs with lines something as the following:

asset    = Ubuntu LTS 12.04 Desktop Live
platform = amd64
kernel   = /Folder1/Folder2/casper/vmlinuz
append   = showmounts toram root=/dev/cifs initrd=/Folder1/Folder2/casper/initrd.gz boot=casper netboot=cifs nfsroot=//server/share nfsopts=-ouser=xxx,pass=***,ro

The path //server/share is where the splash is (share with restricted acees), anyway I had to add modules md4.ko and des_generic.ko to initrd first to make the cifs server accept the credentials (my PXE was a Windows Server 2008 R2), also I had to replace the option toram with todisk since I was playing with a virtual machine low on ram

Hope this helps somehow

---

### Post by xerox2 on 2015-06-15
Hello tempusfugit2,
thanks for your reply.

GParted and Clonezilla support tftp but it has a major disadvantage, it copies the files to you memory.

Ubuntu never worked with fetch/tftp so I tried NFS (Server 2012 R2) and it works like a charm! I changed GParted and Clonezilla to NFS too, works perfect.

Regarding the autologon, there can't be a tty1.conf as its been used by upstart and Ubuntu 15.04 changed to systemd.

For autologon with systemd I used the following:
[URL="https://wiki.archlinux.org/index.php/Automatic_login_to_virtual_console"]https://wiki.archlinux.org/index.php/Automatic_login_to_virtual_console

[ATTACH=CONFIG]262607[/ATTACH]
[/URL]

---

### Post by andy156 on 2015-11-20
> **xerox2 said:**
> Hello tempusfugit2,
thanks for your reply.

GParted and Clonezilla support tftp but it has a major disadvantage, it copies the files to you memory.

Ubuntu never worked with fetch/tftp so I tried NFS (Server 2012 R2) and it works like a charm! I changed GParted and Clonezilla to NFS too, works perfect.

Regarding the autologon, there can't be a tty1.conf as its been used by upstart and Ubuntu 15.04 changed to systemd.

For autologon with systemd I used the following:
[URL="https://wiki.archlinux.org/index.php/Automatic_login_to_virtual_console"]https://wiki.archlinux.org/index.php/Automatic_login_to_virtual_console

[ATTACH=CONFIG]262607[/ATTACH]
[/URL]





Hi,

I am rather new to Ubuntu but have been a Linux user for some time. I currently have a working PXE server and am trying to do exactly what you are doing (customizing Ubuntu and PXE booting). Would you be kind enough to let a noob know how you did this?


Thanks,
Andy

---

