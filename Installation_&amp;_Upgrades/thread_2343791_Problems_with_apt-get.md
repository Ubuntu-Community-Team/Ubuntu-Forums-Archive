---
title: "Problems with apt-get"
date: 2016-11-19
forum: Installation &amp; Upgrades
---

### Post by dam034 on 2016-11-19
Dear users,

from several days I have problems with apt-get on my ubuntu desktop 14.04, I can't update the programs.

In the ubuntu toolbar I see an access prohibition signal, as in attached screenshot:
[ATTACH=CONFIG]272235[/ATTACH]

Then, I run these commands in terminal:
```
root@giocopc:~# apt-get autoremove
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-headers-3.13.0-101-generic : Dipende: linux-headers-3.13.0-101 ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.

root@giocopc:~# apt-get -f install
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Correzione delle dipendenze... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  kde-l10n-engb kde-l10n-it
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti saranno inoltre installati:
  linux-headers-3.13.0-101
I seguenti pacchetti NUOVI saranno installati:
  linux-headers-3.13.0-101
0 aggiornati, 1 installati, 0 da rimuovere e 14 non aggiornati.
3 non completamente installati o rimossi.
È necessario scaricare 0 B/8.867 kB di archivi.
Dopo quest'operazione, verranno occupati 63,5 MB di spazio su disco.
Continuare? [S/n] s
(Lettura del database... 1061416 file e directory attualmente installati.)
Preparativi per estrarre .../linux-headers-3.13.0-101_3.13.0-101.148_all.deb...
Estrazione di linux-headers-3.13.0-101 (3.13.0-101.148)...
Segnalazione apport non scritta poiché il messaggio di errore indica un errore per disco pieno.
               dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/linux-headers-3.13.0-101_3.13.0-101.148_all.deb (--unpack):
 impossibile creare "/usr/src/linux-headers-3.13.0-101/arch/powerpc/include/asm/mmu-hash32.h.dpkg-new" (durante l'elaborazione di "./usr/src/linux-headers-3.13.0-101/arch/powerpc/include/asm/mmu-hash32.h"): Spazio esaurito sul device
dpkg-deb: errore: il sottoprocesso paste è stato terminato dal segnale (Pipe interrotta)
Si sono verificati degli errori nell'elaborazione:
 /var/cache/apt/archives/linux-headers-3.13.0-101_3.13.0-101.148_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

root@giocopc:~# df -h
File system     Dim. Usati Dispon. Uso% Montato su
udev            4,0G  4,0K    4,0G   1% /dev
tmpfs           810M  1,1M    809M   1% /run
/dev/sda7        18G   15G    2,0G  89% /
none            4,0K     0    4,0K   0% /sys/fs/cgroup
none            5,0M     0    5,0M   0% /run/lock
none            4,0G  152K    4,0G   1% /run/shm
none            100M   36K    100M   1% /run/user
```

I don't understand why I can't update programs, the error is "out of space", but the partition is filled at 89%.


How can I fix this issue?


Thanks,
dam034

---

### Post by Bucky Ball on 2016-11-19
Try this in a terminal.

```
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

The last command will not upgrade your release to a newer one.

You need the 'sudo' as you need to be root temporarily to run the command you are trying to run (sudo=superuser do). ;)

If it throws any errors from any of those commands, post them back. You will be asked for your password after a sudo command. It will be invisible when you type it and that is normal.

---

### Post by ian-weisser on 2016-11-19
Try 'df -i' to check your inodes.
Kernel headers consume lots of inodes.

If your inodes are near 100% then try 'dpkg -l | grep linux-headers' to get a list of all header packages.
Uninstall all numbered header packages that are installed (ii), except of course for the currently running kernel's headers.

---

### Post by dam034 on 2016-11-19
> **Bucky Ball said:**
> You need the 'sudo' as you need to be root temporarily to run the command you are trying to run (sudo=superuser do). ;)
[..]
You will be asked for your password after a sudo command. It will be invisible when you type it and that is normal.
I know how sudo works, in fact I always enter "sudo su" to be root, and to not write "sudo" to every command.

> **Bucky Ball said:**
> Try this in a terminal.

```
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```
These are the results:
```
root@giocopc:~# apt-get autoremove
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-headers-3.13.0-101-generic : Dipende: linux-headers-3.13.0-101 ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.

root@giocopc:~# apt-get -f install
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Correzione delle dipendenze... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  kde-l10n-engb kde-l10n-it
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti saranno inoltre installati:
  linux-headers-3.13.0-101
I seguenti pacchetti NUOVI saranno installati:
  linux-headers-3.13.0-101
0 aggiornati, 1 installati, 0 da rimuovere e 15 non aggiornati.
3 non completamente installati o rimossi.
È necessario scaricare 0 B/8.867 kB di archivi.
Dopo quest'operazione, verranno occupati 63,5 MB di spazio su disco.
Continuare? [S/n] s
(Lettura del database... 1061416 file e directory attualmente installati.)
Preparativi per estrarre .../linux-headers-3.13.0-101_3.13.0-101.148_all.deb...
Estrazione di linux-headers-3.13.0-101 (3.13.0-101.148)...
dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/linux-headers-3.13.0-101_3.13.0-101.148_all.deb (--unpack):
 impossibile creare "/usr/src/linux-headers-3.13.0-101/arch/m68k/include/asm/zorro.h.dpkg-new" (durante l'elaborazione di "./usr/src/linux-headers-3.13.0-101/arch/m68k/include/asm/zorro.h"): Spazio esaurito sul device
Segnalazione apport non scritta poiché il messaggio di errore indica un errore per disco pieno.
               dpkg-deb: errore: il sottoprocesso paste è stato terminato dal segnale (Pipe interrotta)
Si sono verificati degli errori nell'elaborazione:
 /var/cache/apt/archives/linux-headers-3.13.0-101_3.13.0-101.148_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

root@giocopc:~# apt-get update
Scaricamento di:1 http://security.ubuntu.com trusty-security InRelease [65,9 kB]
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://it.archive.ubuntu.com trusty InRelease                              
Trovato http://extras.ubuntu.com trusty Release.gpg           
Scaricamento di:2 http://it.archive.ubuntu.com trusty-updates InRelease [65,9 kB]
Trovato http://extras.ubuntu.com trusty Release                                
Scaricamento di:3 http://security.ubuntu.com trusty-security/main Sources [120 kB]
Trovato http://it.archive.ubuntu.com trusty-backports InRelease                
Trovato http://it.archive.ubuntu.com trusty Release.gpg                        
Scaricamento di:4 http://it.archive.ubuntu.com trusty-updates/main Sources [384 kB]
Scaricamento di:5 http://security.ubuntu.com trusty-security/restricted Sources [4.613 B]
Trovato http://extras.ubuntu.com trusty/main Sources                           
Scaricamento di:6 http://security.ubuntu.com trusty-security/universe Sources [45,8 kB]
Trovato http://extras.ubuntu.com trusty/main i386 Packages                     
Scaricamento di:7 http://security.ubuntu.com trusty-security/multiverse Sources [3.207 B]
Scaricamento di:8 http://security.ubuntu.com trusty-security/main i386 Packages [507 kB]
Scaricamento di:9 http://it.archive.ubuntu.com trusty-updates/restricted Sources [5.888 B]
Scaricamento di:10 http://security.ubuntu.com trusty-security/restricted i386 Packages [13,1 kB]
Scaricamento di:11 http://it.archive.ubuntu.com trusty-updates/universe Sources [169 kB]
Scaricamento di:12 http://security.ubuntu.com trusty-security/universe i386 Packages [144 kB]
Ign http://extras.ubuntu.com trusty/main Translation-it_IT                     
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Scaricamento di:13 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4.289 B]
Trovato http://security.ubuntu.com trusty-security/main Translation-en         
Trovato http://security.ubuntu.com trusty-security/multiverse Translation-en   
Scaricamento di:14 http://it.archive.ubuntu.com trusty-updates/multiverse Sources [7.522 B]
Trovato http://security.ubuntu.com trusty-security/restricted Translation-en   
Scaricamento di:15 http://it.archive.ubuntu.com trusty-updates/main i386 Packages [876 kB]
Trovato http://security.ubuntu.com trusty-security/universe Translation-en     
Scaricamento di:16 http://it.archive.ubuntu.com trusty-updates/restricted i386 Packages [16,2 kB]
Scaricamento di:17 http://it.archive.ubuntu.com trusty-updates/universe i386 Packages [389 kB]
Scaricamento di:18 http://it.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14,5 kB]
Scaricamento di:19 http://it.archive.ubuntu.com trusty-updates/main Translation-en [445 kB]
Scaricamento di:20 http://it.archive.ubuntu.com trusty-updates/multiverse Translation-en [7.340 B]
Scaricamento di:21 http://it.archive.ubuntu.com trusty-updates/restricted Translation-en [3.842 B]
Scaricamento di:22 http://it.archive.ubuntu.com trusty-updates/universe Translation-en [205 kB]
Trovato http://it.archive.ubuntu.com trusty-backports/main Sources             
Trovato http://it.archive.ubuntu.com trusty-backports/restricted Sources       
Trovato http://it.archive.ubuntu.com trusty-backports/universe Sources         
Trovato http://it.archive.ubuntu.com trusty-backports/multiverse Sources       
Trovato http://it.archive.ubuntu.com trusty-backports/main i386 Packages       
Trovato http://it.archive.ubuntu.com trusty-backports/restricted i386 Packages 
Trovato http://it.archive.ubuntu.com trusty-backports/universe i386 Packages   
Trovato http://it.archive.ubuntu.com trusty-backports/multiverse i386 Packages 
Trovato http://it.archive.ubuntu.com trusty-backports/main Translation-en      
Trovato http://it.archive.ubuntu.com trusty-backports/multiverse Translation-en
Trovato http://it.archive.ubuntu.com trusty-backports/restricted Translation-en
Trovato http://it.archive.ubuntu.com trusty-backports/universe Translation-en  
Trovato http://it.archive.ubuntu.com trusty Release                            
Trovato http://it.archive.ubuntu.com trusty/main Sources                       
Trovato http://it.archive.ubuntu.com trusty/restricted Sources                 
Trovato http://it.archive.ubuntu.com trusty/universe Sources                   
Trovato http://it.archive.ubuntu.com trusty/multiverse Sources                 
Trovato http://it.archive.ubuntu.com trusty/main i386 Packages                 
Trovato http://it.archive.ubuntu.com trusty/restricted i386 Packages           
Trovato http://it.archive.ubuntu.com trusty/universe i386 Packages             
Trovato http://it.archive.ubuntu.com trusty/multiverse i386 Packages           
Trovato http://it.archive.ubuntu.com trusty/main Translation-it                
Trovato http://it.archive.ubuntu.com trusty/main Translation-en                
Trovato http://it.archive.ubuntu.com trusty/multiverse Translation-it          
Trovato http://it.archive.ubuntu.com trusty/multiverse Translation-en          
Trovato http://it.archive.ubuntu.com trusty/restricted Translation-it          
Trovato http://it.archive.ubuntu.com trusty/restricted Translation-en          
Trovato http://it.archive.ubuntu.com trusty/universe Translation-it            
Trovato http://it.archive.ubuntu.com trusty/universe Translation-en            
Ign http://it.archive.ubuntu.com trusty/main Translation-it_IT                 
Ign http://it.archive.ubuntu.com trusty/multiverse Translation-it_IT           
Ign http://it.archive.ubuntu.com trusty/restricted Translation-it_IT           
Ign http://it.archive.ubuntu.com trusty/universe Translation-it_IT             
Recuperati 3.498 kB in 13s (257 kB/s)                                          
Lettura elenco dei pacchetti... Fatto

root@giocopc:~# apt-get dist-upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-headers-3.13.0-101-generic : Dipende: linux-headers-3.13.0-101 ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.

```




> **ian-weisser said:**
> Try 'df -i' to check your inodes.
Kernel headers consume lots of inodes.

If your inodes are near 100% then try 'dpkg -l | grep linux-headers' to get a list of all header packages.
Uninstall all numbered header packages that are installed (ii), except of course for the currently running kernel's headers.
This is the result of the two commands you have written:
```
root@giocopc:~# df -i
File system      Inode  IUsati ILiberi IUso% Montato su
udev            198635     488  198147    1% /dev
tmpfs           203446     488  202958    1% /run
/dev/sda7      1172736 1170232    2504  100% /
none            203446       2  203444    1% /sys/fs/cgroup
none            203446       3  203443    1% /run/lock
none            203446      35  203411    1% /run/shm
none            203446      26  203420    1% /run/user

root@giocopc:~# dpkg -l | grep linux-headers
ii  linux-headers-3.13.0-100                              3.13.0-100.147                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-100-generic                      3.13.0-100.147                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
iU  linux-headers-3.13.0-101-generic                      3.13.0-101.148                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-27                               3.13.0-27.50                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-27-generic                       3.13.0-27.50                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-35                               3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                       3.13.0-35.62                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-71                               3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic                       3.13.0-71.114                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-85                               3.13.0-85.129                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                       3.13.0-85.129                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-88                               3.13.0-88.135                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                       3.13.0-88.135                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-91                               3.13.0-91.138                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic                       3.13.0-91.138                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-92                               3.13.0-92.139                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                       3.13.0-92.139                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-96                               3.13.0-96.143                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic                       3.13.0-96.143                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-98                               3.13.0-98.145                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-98-generic                       3.13.0-98.145                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
iU  linux-headers-generic                                 3.13.0.101.109                                      i386         Generic Linux kernel headers

```

I don't know how to unistall the headers.


How can I do?


Thanks,
dam034

---

### Post by ian-weisser on 2016-11-19
> **dam034 said:**
> I don't know how to unistall the headers.

How can I do?

They are packages, so use apt.
Example:
```
sudo apt remove linux-headers-3.13.0-27 linux-headers-3.13.0-27-generic
```
 Repeat for each set of kernel header packages until you reach the currently-running kernel.

---

### Post by dam034 on 2016-11-19
I tried, but it returns the same error:

```
root@giocopc:~# apt-get remove linux-headers-3.13.0-27 linux-headers-3.13.0-27-generic
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-headers-3.13.0-101-generic : Dipende: linux-headers-3.13.0-101 ma non sta per essere installato
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).
```

How can I continue?


Thanks,
dam034

---

### Post by Bashing-om on 2016-11-19
dam034; Hello;

We got any operational headroom to this time ?
```

df -i
df -h

```

Maybe just maybe - IF there is no headroom, we can drop down to a lower level of package management and see if we can get that needed headroom.

[INDENT][INDENT]if push comes to shove
[INDENT][INDENT][INDENT]we force
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dam034 on 2016-11-19
I executed the two commands and these are the results:

```
root@giocopc:~# df -i
File system      Inode  IUsati ILiberi IUso% Montato su
udev            198635     488  198147    1% /dev
tmpfs           203446     487  202959    1% /run
/dev/sda7      1172736 1170391    2345  100% /
none            203446       2  203444    1% /sys/fs/cgroup
none            203446       3  203443    1% /run/lock
none            203446      26  203420    1% /run/shm
none            203446      26  203420    1% /run/user

root@giocopc:~# df -h
File system     Dim. Usati Dispon. Uso% Montato su
udev            4,0G  4,0K    4,0G   1% /dev
tmpfs           810M  1,1M    809M   1% /run
/dev/sda7        18G   15G    2,0G  89% /
none            4,0K     0    4,0K   0% /sys/fs/cgroup
none            5,0M     0    5,0M   0% /run/lock
none            4,0G  5,3M    4,0G   1% /run/shm
none            100M   40K    100M   1% /run/user
```

I don't know how to repair this issue.


dam034

---

### Post by Bashing-om on 2016-11-19
dam034; Welp ...

Still at 100% capacity .....
Let us try that lower level .
what results:
```

sudo dpkg -P linux-image-extra-3.13.0-27-generic
sudo dpkg -P linux-image-3.13.0-27-generic
sudo dpkg -P linux-headers-3.13.0-27-generic
sudo dpkg -P linux-headers-3.13.0-27

```

Now if that runs, we want to see what other to be purged. 
Show :
```

dpkg -l | grep linux-

```

[INDENT][INDENT]we got to get some elbow room;
[INDENT][INDENT][INDENT]somehow
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dam034 on 2016-11-20
I executed your commands and these are the results:

```
root@giocopc:~# dpkg -P linux-image-extra-3.13.0-27-generic
(Lettura del database... 1061415 file e directory attualmente installati.)
Rimozione di linux-image-extra-3.13.0-27-generic (3.13.0-27.50)...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
Generating grub configuration file ...
Trovata immagine linux: /boot/vmlinuz-3.13.0-101-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-101-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-100-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-100-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-98-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-98-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-96-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-96-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-93-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-93-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-92-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-92-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-91-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-91-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-88-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-88-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-86-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-86-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-85-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-85-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-74-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-74-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-71-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-71-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-65-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-65-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-63-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-63-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-62-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-62-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-61-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-61-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-57-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-57-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-55-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-55-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-54-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-54-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-53-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-53-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-52-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-52-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-49-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-49-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-48-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-48-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-46-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-46-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-45-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-45-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-44-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-44-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-43-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-43-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-35-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-35-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-29-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-29-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-27-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Trovato Windows 7 (loader) su /dev/sda1
fatto
Eliminazione dei file di configurazione di linux-image-extra-3.13.0-27-generic (3.13.0-27.50)...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic

root@giocopc:~# dpkg -P linux-image-3.13.0-27-generic
(Lettura del database... 1057321 file e directory attualmente installati.)
Rimozione di linux-image-3.13.0-27-generic (3.13.0-27.50)...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
Generating grub configuration file ...
Trovata immagine linux: /boot/vmlinuz-3.13.0-101-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-101-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-100-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-100-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-98-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-98-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-96-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-96-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-93-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-93-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-92-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-92-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-91-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-91-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-88-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-88-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-86-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-86-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-85-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-85-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-74-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-74-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-71-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-71-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-65-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-65-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-63-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-63-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-62-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-62-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-61-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-61-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-57-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-57-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-55-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-55-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-54-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-54-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-53-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-53-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-52-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-52-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-49-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-49-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-48-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-48-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-46-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-46-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-45-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-45-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-44-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-44-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-43-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-43-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-35-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-35-generic
Trovata immagine linux: /boot/vmlinuz-3.13.0-29-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-29-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Trovato Windows 7 (loader) su /dev/sda1
fatto
Eliminazione dei file di configurazione di linux-image-3.13.0-27-generic (3.13.0-27.50)...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic

root@giocopc:~# dpkg -P linux-headers-3.13.0-27-generic
(Lettura del database... 1056443 file e directory attualmente installati.)
Rimozione di linux-headers-3.13.0-27-generic (3.13.0-27.50)...

root@giocopc:~# dpkg -P linux-headers-3.13.0-27
(Lettura del database... 1046789 file e directory attualmente installati.)
Rimozione di linux-headers-3.13.0-27 (3.13.0-27.50)...

root@giocopc:~# dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
iU  linux-generic                                         3.13.0.101.109                                      i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-100                              3.13.0-100.147                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-100-generic                      3.13.0-100.147                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
iU  linux-headers-3.13.0-101-generic                      3.13.0-101.148                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-35                               3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                       3.13.0-35.62                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-71                               3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic                       3.13.0-71.114                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-85                               3.13.0-85.129                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                       3.13.0-85.129                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-88                               3.13.0-88.135                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                       3.13.0-88.135                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-91                               3.13.0-91.138                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic                       3.13.0-91.138                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-92                               3.13.0-92.139                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                       3.13.0-92.139                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-96                               3.13.0-96.143                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic                       3.13.0-96.143                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-98                               3.13.0-98.145                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-98-generic                       3.13.0-98.145                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
iU  linux-headers-generic                                 3.13.0.101.109                                      i386         Generic Linux kernel headers
ii  linux-image-3.13.0-100-generic                        3.13.0-100.147                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-101-generic                        3.13.0-101.148                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-71-generic                         3.13.0-71.114                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-74-generic                         3.13.0-74.118                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-85-generic                         3.13.0-85.129                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-86-generic                         3.13.0-86.131                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-88-generic                         3.13.0-88.135                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-91-generic                         3.13.0-91.138                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-92-generic                         3.13.0-92.139                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-93-generic                         3.13.0-93.140                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-96-generic                         3.13.0-96.143                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-98-generic                         3.13.0-98.145                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-100-generic                  3.13.0-100.147                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-101-generic                  3.13.0-101.148                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-71-generic                   3.13.0-71.114                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                   3.13.0-74.118                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic                   3.13.0-85.129                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                   3.13.0-86.131                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic                   3.13.0-88.135                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-91-generic                   3.13.0-91.138                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-92-generic                   3.13.0-92.139                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-96-generic                   3.13.0-96.143                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-98-generic                   3.13.0-98.145                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.101.109                                      i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-101.148                                      i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
```

And I tried my own way to run these additional commands:
```
root@giocopc:~# dpkg -P linux-headers-3.13.0-29-generic
(Lettura del database... 1031541 file e directory attualmente installati.)
Rimozione di linux-headers-3.13.0-29-generic (3.13.0-29.53)...

root@giocopc:~# dpkg -P linux-headers-3.13.0-29
(Lettura del database... 1021887 file e directory attualmente installati.)
Rimozione di linux-headers-3.13.0-29 (3.13.0-29.53)...
```

After, I executed these commands:
```
root@giocopc:~# df -h
File system     Dim. Usati Dispon. Uso% Montato su
udev            4,0G   12K    4,0G   1% /dev
tmpfs           810M  1,1M    809M   1% /run
/dev/sda7        18G   15G    2,4G  86% /
none            4,0K     0    4,0K   0% /sys/fs/cgroup
none            5,0M     0    5,0M   0% /run/lock
none            4,0G  9,7M    4,0G   1% /run/shm
none            100M   40K    100M   1% /run/user

root@giocopc:~# df -i
File system      Inode  IUsati ILiberi IUso% Montato su
udev            198635     491  198144    1% /dev
tmpfs           203446     488  202958    1% /run
/dev/sda7      1172736 1115600   57136   96% /
none            203446       2  203444    1% /sys/fs/cgroup
none            203446       3  203443    1% /run/lock
none            203446      32  203414    1% /run/shm
none            203446      26  203420    1% /run/user
```

And it shows me 96%, but now I want to know if in the future it is possible that it reaches again the 100% and how can I proceed to reduce that percentage.

This is "apt-get -f install":

```
root@giocopc:~# apt-get -f install
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Correzione delle dipendenze... Fatto
I seguenti pacchetti saranno inoltre installati:
  linux-headers-3.13.0-101
I seguenti pacchetti NUOVI saranno installati:
  linux-headers-3.13.0-101
0 aggiornati, 1 installati, 0 da rimuovere e 15 non aggiornati.
3 non completamente installati o rimossi.
È necessario scaricare 0 B/8.867 kB di archivi.
Dopo quest'operazione, verranno occupati 63,5 MB di spazio su disco.
Continuare? [S/n] s
(Lettura del database... 1006639 file e directory attualmente installati.)
Preparativi per estrarre .../linux-headers-3.13.0-101_3.13.0-101.148_all.deb...
Estrazione di linux-headers-3.13.0-101 (3.13.0-101.148)...
Configurazione di linux-headers-3.13.0-101 (3.13.0-101.148)...
Configurazione di linux-headers-3.13.0-101-generic (3.13.0-101.148)...
Configurazione di linux-headers-generic (3.13.0.101.109)...
Configurazione di linux-generic (3.13.0.101.109)...

```

It works!


dam034

---

### Post by ian-weisser on 2016-11-20
Your system is NOT fixed yet,
Keep using apt or dpkg. Clean out ALL those obsolete kernel and header packages.
It's easier using apt. However, apt fails when your inodes or space reach 100%, which is why you initially used dpkg.

If you fail to clean out all those old packages, you will quickly reach 100% again. As you can see, new kernel and header packages are installed regularly.
Reminder: DO NOT remove the currently running kernel. That would be very bad.

---

