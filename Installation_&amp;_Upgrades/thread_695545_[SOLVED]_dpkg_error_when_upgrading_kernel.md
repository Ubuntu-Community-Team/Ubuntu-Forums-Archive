---
title: "[SOLVED] dpkg error when upgrading kernel"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by Creap on 2008-02-13
When upgrading the kernel something seems to go wrong with dpkg, I get "**Sub-process /usr/bin/dpkg returned an error code (1)**". These are the full results for *sudo apt-get install linux-image-2.6.22-14-generic*
```

Ställer in linux-image-2.6.22-14-386 (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-386 (--configure):
 underprocess post-installation script gav felkod 2
Ställer in linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-generic (--configure):
 underprocess post-installation script gav felkod 2
Ställer in linux-image-2.6.22-14-rt (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-rt (--configure):
 underprocess post-installation script gav felkod 2
Fel uppstod vid hantering:
 linux-image-2.6.22-14-386
 linux-image-2.6.22-14-generic
 linux-image-2.6.22-14-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
This happens every time I install or update *anything* with any of the apt-frontends, since the installers then also try to upgrade the kernel again. Any ideas?

---

### Post by jan quark on 2008-02-14
just a wild guess

try these commands and post any error messages

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

### Post by Creap on 2008-02-15
same :(
```
sudo apt-get install -f
<snip>
3 ej helt installerade eller borttagna.
Behöver hämta 0B arkiv.
Efter uppackning kommer ytterligare 0B utrymme användas på disken.
Ställer in linux-image-2.6.22-14-386 (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-386 (--configure):
 underprocess post-installation script gav felkod 2
Ställer in linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-generic (--configure):
 underprocess post-installation script gav felkod 2
Ställer in linux-image-2.6.22-14-rt (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-rt (--configure):
 underprocess post-installation script gav felkod 2
Fel uppstod vid hantering:
 linux-image-2.6.22-14-386
 linux-image-2.6.22-14-generic
 linux-image-2.6.22-14-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
```
sudo dpkg --configure -a
Ställer in linux-image-2.6.22-14-rt (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-rt (--configure):
 underprocess post-installation script gav felkod 2
Ställer in linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-generic (--configure):
 underprocess post-installation script gav felkod 2
Ställer in linux-image-2.6.22-14-386 (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: fel vid hantering av linux-image-2.6.22-14-386 (--configure):
 underprocess post-installation script gav felkod 2
Fel uppstod vid hantering:
 linux-image-2.6.22-14-rt
 linux-image-2.6.22-14-generic
 linux-image-2.6.22-14-386
```

---

### Post by Pumalite on 2008-02-15
Post:
uname -a

---

### Post by Creap on 2008-02-15
$ uname -a
Linux fenrir 2.6.22-14-386 #1 Fri Feb 1 04:32:03 UTC 2008 i686 GNU/Linux

---

### Post by Pumalite on 2008-02-15
What are you doing with an i386 kernel? Do you have an old computer?. Otherwise you should be running 14-generic-i686

---

### Post by Creap on 2008-02-15
> **Pumalite said:**
> What are you doing with an i386 kernel? Do you have an old computer?. Otherwise you should be running 14-generic-i686
No I have an Intel 1.8 GHz. 

I don't find any i686 to install though?

```
$ sudo apt-cache search i686
libgl1-mesa-swx11-i686 - Mesa OpenGL runtime [i686 optimized]
linux32 - Wrapper to set the execution domain
gogo - mp3 encoder
libc6-i686 - GNU C Library: Shared libraries [i686 optimized]
ardour-i686 - digital audio workstation (graphical gtk2 interface) [i686]

```

:(

---

### Post by Odrodzona-Sarmacja on 2008-02-15
> **Creap said:**
> 
```
sudo apt-get install -f
*
The provided postinst hook script [/sbin/update-grub] could not be run.
*
The provided postinst hook script [/sbin/update-grub] could not be run.
*
The provided postinst hook script [/sbin/update-grub] could not be run.
*
 underprocess post-installation script gav felkod 2
Fel uppstod vid hantering:
 linux-image-2.6.22-14-386
 linux-image-2.6.22-14-generic
 linux-image-2.6.22-14-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This looks interesting... It simply says that /sbin/update-grub ould not be run and it seems it is also installation sript and not program...

I would try the following:
-sudo mousepad /sbin/update-grub
and looks for whatever garbage maked into that script. Then I would copy the script to a safe place and tried to erase what i see as *garbage*. Then checking if it works as suppose to.

---

### Post by Creap on 2008-02-16
> **Odrodzona-Sarmacja said:**
> This looks interesting... It simply says that /sbin/update-grub ould not be run and it seems it is also installation sript and not program...

I would try the following:
-sudo mousepad /sbin/update-grub
and looks for whatever garbage maked into that script. Then I would copy the script to a safe place and tried to erase what i see as *garbage*. Then checking if it works as suppose to.
I actually don't have any files called *update-grub* on my system, anywhere, and nothing even with "grub" in the filename in sbin or bin folders...

---

### Post by Pumalite on 2008-02-16
Just upgraded my Feisty for fun. Other than reinstalling a driver everything went smooth.
pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
pumalite@pumalite-desktop:~$

---

### Post by Creap on 2008-02-21
I still have this problem, so I can't update anything automatically :( Did anyone find a solution yet or will there be a new kernel update any time soon which might solve my problems? Thanks.

---

### Post by Creap on 2008-02-21
OK, I simply installed grub and then reinstalled the kernel, **PROBLEM SOLVED!**

---

