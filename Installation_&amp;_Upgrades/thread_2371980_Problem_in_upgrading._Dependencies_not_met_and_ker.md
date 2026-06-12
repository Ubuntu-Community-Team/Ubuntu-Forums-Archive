---
title: "Problem in upgrading. Dependencies not met and kernel images"
date: 2017-09-20
forum: Installation &amp; Upgrades
---

### Post by Federico_Carta on 2017-09-20
Hi everyone. I am running Ubuntu 16.04 and I have a problem when updating.
When I run 
```

sudo apt-get upgrade

```

the output is the following (sorry for the fact it is in italian)

```

Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-image-extra-4.4.0-92-generic : Dipende: linux-image-4.4.0-92-generic ma non è installato
 linux-image-extra-4.4.0-94-generic : Dipende: linux-image-4.4.0-94-generic ma non è installato
 linux-image-extra-4.4.0-96-generic : Dipende: linux-image-4.4.0-96-generic ma non è installato
 linux-image-extra-4.4.0-97-generic : Dipende: linux-image-4.4.0-97-generic ma non è installato
 linux-image-generic : Dipende: linux-image-4.4.0-97-generic ma non è installato
 linux-signed-image-4.4.0-92-generic : Dipende: linux-image-4.4.0-92-generic (= 4.4.0-92.115) ma non è installato
 linux-signed-image-4.4.0-94-generic : Dipende: linux-image-4.4.0-94-generic (= 4.4.0-94.117) ma non è installato
 linux-signed-image-4.4.0-96-generic : Dipende: linux-image-4.4.0-96-generic (= 4.4.0-96.119) ma non è installato
 linux-signed-image-4.4.0-97-generic : Dipende: linux-image-4.4.0-97-generic (= 4.4.0-97.120) ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.

```

As far as I understand, there are some dependencies not met.
In particular, there look to be many packages not installed. It suggests retrying with -f. When I do 
```

sudo apt-get upgrade -f

```

I get the following output
```

Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Correzione delle dipendenze... Fatto
Calcolo dell'aggiornamento... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  libllvm3.8 libllvm3.8:i386 libmircommon5 linux-headers-4.4.0-70 linux-headers-4.4.0-70-generic linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-headers-4.4.0-75
  linux-headers-4.4.0-75-generic linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-image-4.4.0-70-generic linux-image-4.4.0-71-generic linux-image-4.4.0-72-generic
  linux-image-4.4.0-75-generic linux-image-4.4.0-78-generic linux-image-4.4.0-83-generic linux-image-extra-4.4.0-70-generic
  linux-image-extra-4.4.0-71-generic linux-image-extra-4.4.0-72-generic linux-image-extra-4.4.0-75-generic
  linux-image-extra-4.4.0-78-generic linux-image-extra-4.4.0-83-generic linux-image-extra-4.4.0-92-generic
  linux-image-extra-4.4.0-94-generic linux-image-extra-4.4.0-96-generic linux-signed-image-4.4.0-70-generic
  linux-signed-image-4.4.0-71-generic linux-signed-image-4.4.0-72-generic linux-signed-image-4.4.0-75-generic
  linux-signed-image-4.4.0-78-generic linux-signed-image-4.4.0-83-generic linux-signed-image-4.4.0-92-generic
  linux-signed-image-4.4.0-94-generic linux-signed-image-4.4.0-96-generic snap-confine
Usare "sudo apt autoremove" per rimuoverli.
I seguenti pacchetti NUOVI saranno installati:
  linux-image-4.4.0-92-generic linux-image-4.4.0-94-generic linux-image-4.4.0-96-generic linux-image-4.4.0-97-generic
0 aggiornati, 4 installati, 0 da rimuovere e 0 non aggiornati.
18 non completamente installati o rimossi.
È necessario scaricare 0 B/87,7 MB di archivi.
Dopo quest'operazione, verranno occupati 268 MB di spazio su disco.
Continuare? [S/n] S
(Lettura del database... 743736 file e directory attualmente installati.)
Preparativi per estrarre .../linux-image-4.4.0-97-generic_4.4.0-97.120_amd64.deb...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Done.
Estrazione di linux-image-4.4.0-97-generic (4.4.0-97.120)...
dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/linux-image-4.4.0-97-generic_4.4.0-97.120_amd64.deb (--unpack):
 impossibile copiare i dati estratti per "./boot/vmlinuz-4.4.0-97-generic" in "/boot/vmlinuz-4.4.0-97-generic.dpkg-new": scrittura non riuscita (Spazio esaurito sul device)
Segnalazione apport non scritta poiché il messaggio di errore indica un errore per disco pieno.
                                                                                               dpkg-deb: errore: il sottoprocesso paste è stato terminato dal segnale (Pipe interrotta)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Preparativi per estrarre .../linux-image-4.4.0-92-generic_4.4.0-92.115_amd64.deb...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-92-generic /boot/vmlinuz-4.4.0-92-generic
Done.
Estrazione di linux-image-4.4.0-92-generic (4.4.0-92.115)...
dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/linux-image-4.4.0-92-generic_4.4.0-92.115_amd64.deb (--unpack):
 impossibile copiare i dati estratti per "./boot/vmlinuz-4.4.0-92-generic" in "/boot/vmlinuz-4.4.0-92-generic.dpkg-new": scrittura non riuscita (Spazio esaurito sul device)
Segnalazione apport non scritta poiché il messaggio di errore indica un errore per disco pieno.
                                                                                               Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-92-generic /boot/vmlinuz-4.4.0-92-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-92-generic /boot/vmlinuz-4.4.0-92-generic
dpkg-deb: errore: il sottoprocesso paste è stato terminato dal segnale (Pipe interrotta)
Preparativi per estrarre .../linux-image-4.4.0-94-generic_4.4.0-94.117_amd64.deb...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-94-generic /boot/vmlinuz-4.4.0-94-generic
Done.
Estrazione di linux-image-4.4.0-94-generic (4.4.0-94.117)...
dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/linux-image-4.4.0-94-generic_4.4.0-94.117_amd64.deb (--unpack):
 impossibile copiare i dati estratti per "./boot/vmlinuz-4.4.0-94-generic" in "/boot/vmlinuz-4.4.0-94-generic.dpkg-new": scrittura non riuscita (Spazio esaurito sul device)
Segnalazione apport non scritta poiché il messaggio di errore indica un errore per disco pieno.
                                                                                               dpkg-deb: errore: il sottoprocesso paste è stato terminato dal segnale (Pipe interrotta)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-94-generic /boot/vmlinuz-4.4.0-94-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-94-generic /boot/vmlinuz-4.4.0-94-generic
Preparativi per estrarre .../linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Done.
Estrazione di linux-image-4.4.0-96-generic (4.4.0-96.119)...
dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb (--unpack):
 impossibile copiare i dati estratti per "./boot/vmlinuz-4.4.0-96-generic" in "/boot/vmlinuz-4.4.0-96-generic.dpkg-new": scrittura non riuscita (Spazio esaurito sul device)
Segnalazione apport non scritta poiché è stato raggiunto il valore massimo di MaxReports
                                                                                        Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
dpkg-deb: errore: il sottoprocesso paste è stato terminato dal segnale (Pipe interrotta)
Si sono verificati degli errori nell'elaborazione:
 /var/cache/apt/archives/linux-image-4.4.0-97-generic_4.4.0-97.120_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-92-generic_4.4.0-92.115_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-94-generic_4.4.0-94.117_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

In particular the last 5 lines of this output signal some errors in the elaboration of the command.

Does anybody know how to solve this?
It is quite important since it is preventing me to upgrade anything.
Thank you very much.

---

### Post by Impavidus on 2017-09-20
You have accumulated too many old kernels and now I think you have a full /boot partition. Run ```
df -h
``` to check. I don't think you have enough headroom for apt to work, but it should be possible to fix this using the lower-level tool dpkg directly. First find out which old kernel packages are installed. Run this (copy-paste into a terminal) and post the output:```
dpkg -l | grep linux
```

---

### Post by Federico_Carta on 2017-09-20
Thank you very much for answering. The output of

```

df -h

```

is the following:
```

File system               Dim. Usati Dispon. Uso% Montato su
udev                         7,8G     0    7,8G   0% /dev
tmpfs                        1,6G  9,3M    1,6G   1% /run
/dev/mapper/ubuntu--vg-root  218G   97G    110G  47% /
tmpfs                        7,8G   30M    7,8G   1% /dev/shm
tmpfs                        5,0M  4,0K    5,0M   1% /run/lock
tmpfs                        7,8G     0    7,8G   0% /sys/fs/cgroup
/dev/sda2                    473M  468M       0 100% /boot
/dev/sda1                    511M  3,4M    508M   1% /boot/efi
tmpfs                        1,6G   60K    1,6G   1% /run/user/1000
/home/federico/.Private      218G   97G    110G  47% /home/federico

```

So I think you are right, and I have no more space in the boot partition, which should be /dev/sda2 if I understand correctly.

Also, the output of 
```

dpkg -l | grep linux

```
is the following:

```

ii  console-setup-linux                           1.108ubuntu15.3                              all          Linux specific part of console-setup
ii  fonts-linuxlibertine                          5.3.0-2                                      all          Linux Libertine family of fonts
ii  libselinux1:amd64                             2.4-3build2                                  amd64        SELinux runtime shared libraries
ii  libselinux1:i386                              2.4-3build2                                  i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                1.10.0-1                                     amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                 1.10.0-1                                     i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                          1.10.0-1                                     amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                           1.10.0-1                                     i386         Video4linux frame format conversion library
ii  linux-base                                    4.0ubuntu1                                   all          Linux image base package
iF  linux-firmware                                1.157.12                                     all          Firmware for Linux kernel drivers
iU  linux-generic                                 4.4.0.97.102                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-70                        4.4.0-70.91                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-70-generic                4.4.0-70.91                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-71                        4.4.0-71.92                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-71-generic                4.4.0-71.92                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-72                        4.4.0-72.93                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-72-generic                4.4.0-72.93                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-75                        4.4.0-75.96                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-75-generic                4.4.0-75.96                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-78                        4.4.0-78.99                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-78-generic                4.4.0-78.99                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-83                        4.4.0-83.106                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-83-generic                4.4.0-83.106                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-87                        4.4.0-87.110                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-87-generic                4.4.0-87.110                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-89                        4.4.0-89.112                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-89-generic                4.4.0-89.112                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-92                        4.4.0-92.115                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-92-generic                4.4.0-92.115                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-94                        4.4.0-94.117                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-94-generic                4.4.0-94.117                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-96                        4.4.0-96.119                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-96-generic                4.4.0-96.119                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-97                        4.4.0-97.120                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-97-generic                4.4.0-97.120                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-040800                    4.8.0-040800.201610022031                    all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-040800-generic            4.8.0-040800.201610022031                    amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.4.0.97.102                                 amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-31-generic                  4.4.0-31.50                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic                  4.4.0-53.74                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-62-generic                  4.4.0-62.83                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-63-generic                  4.4.0-63.84                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic                  4.4.0-64.85                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic                  4.4.0-66.87                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-70-generic                  4.4.0-70.91                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-71-generic                  4.4.0-71.92                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-72-generic                  4.4.0-72.93                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-75-generic                  4.4.0-75.96                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-78-generic                  4.4.0-78.99                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-83-generic                  4.4.0-83.106                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-87-generic                  4.4.0-87.110                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-89-generic                  4.4.0-89.112                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-040800-generic              4.8.0-040800.201610022031                    amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic            4.4.0-31.50                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic            4.4.0-53.74                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic            4.4.0-62.83                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-63-generic            4.4.0-63.84                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic            4.4.0-64.85                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic            4.4.0-66.87                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-70-generic            4.4.0-70.91                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-71-generic            4.4.0-71.92                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-72-generic            4.4.0-72.93                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-75-generic            4.4.0-75.96                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic            4.4.0-78.99                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-83-generic            4.4.0-83.106                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-87-generic            4.4.0-87.110                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-89-generic            4.4.0-89.112                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-92-generic            4.4.0-92.115                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-94-generic            4.4.0-94.117                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-96-generic            4.4.0-96.119                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-97-generic            4.4.0-97.120                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                           4.4.0.97.102                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.4.0-97.120                                 amd64        Linux Kernel Headers for development
iU  linux-signed-generic                          4.4.0.97.102                                 amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-4.4.0-53-generic           4.4.0-53.74                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-62-generic           4.4.0-62.83                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-63-generic           4.4.0-63.84                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-64-generic           4.4.0-64.85                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-66-generic           4.4.0-66.87                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-70-generic           4.4.0-70.91                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-71-generic           4.4.0-71.92                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-72-generic           4.4.0-72.93                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-75-generic           4.4.0-75.96                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-78-generic           4.4.0-78.99                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-83-generic           4.4.0-83.106                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-87-generic           4.4.0-87.110                                 amd64        Signed kernel image generic
iU  linux-signed-image-4.4.0-89-generic           4.4.0-89.112                                 amd64        Signed kernel image generic
iU  linux-signed-image-4.4.0-92-generic           4.4.0-92.115                                 amd64        Signed kernel image generic
iU  linux-signed-image-4.4.0-94-generic           4.4.0-94.117                                 amd64        Signed kernel image generic
iU  linux-signed-image-4.4.0-96-generic           4.4.0-96.119                                 amd64        Signed kernel image generic
iU  linux-signed-image-4.4.0-97-generic           4.4.0-97.120                                 amd64        Signed kernel image generic
iU  linux-signed-image-generic                    4.4.0.97.102                                 amd64        Signed Generic Linux kernel image
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  playonlinux                                   4.2.11                                       all          This program is a front-end for wine.
ii  pptp-linux                                    1.8.0-1                                      amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                      3:6.03+dfsg-11ubuntu1                        amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                               3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                    2.27.1-6ubuntu3.3                            amd64        miscellaneous system utilities

```

I honestly don't understand well what this means, but I can see that there are many different kernel headers, some of newer versions than others. Is it possible to remove safely some of them?

Thank you very much again.

---

### Post by ian-weisser on 2017-09-20
Yes, it's possible to safely remove all older kernels.
Use dpkg for the first couple isn't working yet.

1) Use the following to determine your current kernel. DON'T UNINSTALL YOUR CURRENT KERNEL!
```
uname -r
```

2) Then use dpkg to remove the older kernels. Here's an example of removing one:
```
sudo dpkg --remove linux-signed-image-4.4.0-70-generic linux-image-extra-4.4.0-70-generic
```
Note that TWO packages need to be removed: -image and -image-extra.

3) You also have a bunch of *newer* kernels that are not installed yet: -89, -92, -94, -96, -97
You can uninstall all but the newest. Then install the newest, and reboot into it.

4) Everything on the list marked 'rc' is already removed. Those are merely listings in the database. Ignore them.

5) At this point, apt should work again, but still with a few errors. You have firmly broken your kernel metapackages (linux-signed-generic, linux-signed-image-generic), which will prevent future upgrades and creates error messages.
Uninstall both, use apt-clean on both to purge them from your local cache, then use apt to reinstall them.

---

### Post by Federico_Carta on 2017-09-20
Thanks for answering.

The output of 
```

uname -r

```
is the following:
```

4.8.0-040800-generic

```
so I guess this is the kernel I am using.

I then moved to point 2) in the list, trying to remove one old kernel. I runned
```

sudo dpkg --remove linux-signed-image-4.4.0-70-generic linux-image-extra-4.4.0-70-generic

```
as you suggested, and the output is the following:

```

dpkg: attenzione: viene ignorata la richiesta di rimuovere linux-signed-image-4.4.0-70-generic, solo i file
di configurazione sono presenti nel sistema: usare --purge per rimuoverli
(Lettura del database... 739308 file e directory attualmente installati.)
Rimozione di linux-image-extra-4.4.0-70-generic (4.4.0-70.91)...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-70-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-70-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: errore nell'elaborare il pacchetto linux-image-extra-4.4.0-70-generic (--remove):
 il sottoprocesso installato script di post-removal ha restituito lo stato di errore 1
Si sono verificati degli errori nell'elaborazione:
 linux-image-extra-4.4.0-70-generic

```

So some error happened. The first line says something like "the request of removing linux-signed-image-4.4.0-70-generic has been ignored, only configuration files are present in the system: use --purge to remove them.
Sorry if the question is very naive, but how do I use purge? Also, I have never installed, removed a kernel. How do install the new ones, as you suggest in part 3) ?

Thanks again

---

### Post by ian-weisser on 2017-09-20
Normally old kernels autoremove without any action by users.
I do not know how you defeated the kernel autoremoval...and not knowing will make it hard to restore.

> **Federico_Carta said:**
> 
```

4.8.0-040800-generic

```
so I guess this is the kernel I am using.

This is not a normal Ubuntu kernel. How and why did you install it? This may provide us clues as to how you broke your kernel autoremove.



> **Federico_Carta said:**
> Sorry if the question is very naive, but how do I use purge? 
Move on to the next kernel and try again. 'purge' is a distraction. 'purge' won't help your problem, as 1) kernel images don't have configuration files in /etc anyway and 2) /etc is not full - removing config files won't free any space in /boot.

---

### Post by Federico_Carta on 2017-09-21
> **ian-weisser said:**
> This is not a normal Ubuntu kernel. How and why did you install it? This may provide us clues as to how you broke your kernel autoremove.

I don't know how to install kernels or remove them, as I think I never did it before. I don't know why this one is the one in use, especially if it is a non-standard one...

---

### Post by Impavidus on 2017-09-21
Actually, you should remove 3 packages per kernel version```
sudo dpkg --remove linux-image-4.4.0-71-generic linux-image-extra-4.4.0-71-generic linux-signed-image-4.4.0-71-generic
```and similar for the other versions.

I don't know why you have a non-standard kernel. Sometimes you may need a more recent version for your hardware, but there's a simpler way to install kernel 4.10 on Ubuntu 16.04. Safest thing may be to get back to kernel 4.4.

When you boot the computer, you should be able to use the grub menu to start kernel 4.4.0-83, which is the last standard kernel that was succesfully installed.
Confirm using **uname -r** you're on 4.4.0-83 and that it works correctly. Running that kernel, you should be able to clean up. Try to remove kernels 4.4.0-{70,71,72,75,78,87,89,92,94,96}. Also remove your 4.8 kernel:```
sudo dpkg --remove linux-image-4.8.0-040800-generic
```That should give enough headroom for apt to work:```
sudo apt install -f
```Then let's see if things look better now:```
df -h
dpkg -l | grep linux
```

---

