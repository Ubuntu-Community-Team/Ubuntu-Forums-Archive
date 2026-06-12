---
title: "Update Issue (Not Enough Disk Space in Boot?)"
date: 2019-04-21
forum: Installation &amp; Upgrades
---

### Post by linux.user on 2019-04-21
I've tried all the advices of the forum without results on the follow message had after running the update
"The upgrade needs a total of 127 M free space on disk '/boot'. Please  free at least an additional 25 M of disk space on '/boot'. You can  remove old kernels using 'sudo apt autoremove', and you could also set  COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of  your initramfs."

```
fabrizio@fabrizio-laptop:~$ sudo apt-get autoremove
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 149 non aggiornati.
fabrizio@fabrizio-laptop:~$ dpkg-query -W -f '${binary:Package}\n' | grep -P '^linux'
linux-base
linux-firmware
linux-generic
linux-headers-4.15.0-47
linux-headers-4.15.0-47-generic
linux-headers-generic
linux-image-4.15.0-47-generic
linux-image-4.4.0-141-generic
linux-image-4.4.0-142-generic
linux-image-4.4.0-144-generic
linux-image-4.4.0-31-generic
linux-image-extra-4.4.0-141-generic
linux-image-extra-4.4.0-31-generic
linux-image-generic
linux-libc-dev:i386
linux-modules-4.15.0-47-generic
linux-modules-4.4.0-144-generic
linux-modules-extra-4.15.0-47-generic
linux-modules-extra-4.4.0-144-generic
linux-sound-base
fabrizio@fabrizio-laptop:~$ dpkg --list 'linux-*'
Voluto=U (non noto)/I (installato)/R (rimosso)/P (rimosso totale)/H (in attesa)
| Stato=Non/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(nessuno)/R (reinstallazione richiesta) (Stato,Err: maiuscolo=grave)
||/ Nome           Versione     Architettura Descrizione
+++-==============-============-============-=================================
ii  linux-base     4.5ubuntu1   all          Linux image base package
un  linux-doc-4.15 <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-doc-4.4. <nessuna>    <nessuna>    (nessuna descrizione disponibile)
ii  linux-firmware 1.173.3      all          Firmware for Linux kernel drivers
un  linux-firmware <nessuna>    <nessuna>    (nessuna descrizione disponibile)
ii  linux-generic  4.15.0.47.49 i386         Complete Generic Linux kernel and
un  linux-headers  <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-headers- <nessuna>    <nessuna>    (nessuna descrizione disponibile)
ii  linux-headers- 4.15.0-47.50 all          Header files related to Linux ker
ii  linux-headers- 4.15.0-47.50 i386         Linux kernel headers for version 
un  linux-headers- <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-headers- <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-headers- <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-headers- <nessuna>    <nessuna>    (nessuna descrizione disponibile)
ii  linux-headers- 4.15.0.47.49 i386         Generic Linux kernel headers
un  linux-image    <nessuna>    <nessuna>    (nessuna descrizione disponibile)
ii  linux-image-4. 4.15.0-47.50 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-141.16 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-142.16 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-144.17 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-31.50  i386         Linux kernel image for version 4.
rc  linux-image-ex 4.4.0-141.16 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-31.50  i386         Linux kernel extra modules for ve
ii  linux-image-ge 4.15.0.47.49 i386         Generic Linux kernel image
un  linux-image-un <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-image-un <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-initramf <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-kernel-h <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-kernel-l <nessuna>    <nessuna>    (nessuna descrizione disponibile)
ii  linux-libc-dev 4.15.0-47.50 i386         Linux Kernel Headers for developm
ii  linux-modules- 4.15.0-47.50 i386         Linux kernel extra modules for ve
ii  linux-modules- 4.4.0-144.17 i386         Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-47.50 i386         Linux kernel extra modules for ve
ii  linux-modules- 4.4.0-144.17 i386         Linux kernel extra modules for ve
un  linux-restrict <nessuna>    <nessuna>    (nessuna descrizione disponibile)
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
un  linux-source-4 <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-source-4 <nessuna>    <nessuna>    (nessuna descrizione disponibile)
un  linux-tools    <nessuna>    <nessuna>    (nessuna descrizione disponibile)
fabrizio@fabrizio-laptop:~$ ^C
fabrizio@fabrizio-laptop:~$ uname -r
4.15.0-47-generic
fabrizio@fabrizio-laptop:~$ df -h
File system                    Dim. Usati Dispon. Uso% Montato su
udev                           946M     0    946M   0% /dev
tmpfs                          195M  1,9M    193M   1% /run
/dev/mapper/edubuntu--vg-root  145G   45G     93G  33% /
tmpfs                          972M   51M    922M   6% /dev/shm
tmpfs                          5,0M  4,0K    5,0M   1% /run/lock
tmpfs                          972M     0    972M   0% /sys/fs/cgroup
/dev/loop0                      86M   86M       0 100% /snap/core/6675
/dev/loop1                      86M   86M       0 100% /snap/core/6530
/dev/loop2                      36M   36M       0 100% /snap/gtk-common-themes/1198
/dev/sda1                      236M  126M     98M  57% /boot
tmpfs                          195M   16K    195M   1% /run/user/124
tmpfs                          195M   32K    195M   1% /run/user/1000
fabrizio@fabrizio-laptop:~$ sudo apt autoremove --purge
[sudo] password di fabrizio: 
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 149 non aggiornati.
```

Do you have any advice, please?

---

### Post by Dennis N on 2019-04-21
You have more kernels than you need. I suggest you delete the packages of all but 2 or 3 most recent kernel versions with Synaptic Package Manager. Each kernel version has several related packages.

In Synaptic Package Manager, search for "linux-"
Order results by "Installed Version". (Click on the column header to order them)
Select the packages of same version(s) number that you want to remove > Right-click on the selected group  > Mark for complete removal > Apply
Attached image: I selected the packages of kernel **4.15.0-46** for removal.

---

### Post by SeijiSensei on 2019-04-21
Try manually removing the deprecated packages with dpkg. For instance,

```
sudo dpkg -r linux-image-extra-4.4.0-31-generic
```

then working up the list.

I've bumped my /boot partitions up to 512 MB in new installs.  Even with just three kernels installed there, I'm using 231 MB.

---

### Post by Impavidus on 2019-04-22
The autoremove command tries to remove old kernels, keeping just 2 of them. However, your /boot partition is so small that even 2 is too many, as there's no room to install a third (the new one). Remove kernel 4.4.0-144. Use the terminal or synaptic. The package names on your dpkg --list output were truncated, so I can't give you the exact commands. When using dpkg --list, it's best to make sure the terminal window is the full width of your screen.

Some other old kernels are listed as "removed, remaining configuration files" (status rc). You can purge them if you like. They don't take any disk space in /boot, but purging will remove some clutter.

---

