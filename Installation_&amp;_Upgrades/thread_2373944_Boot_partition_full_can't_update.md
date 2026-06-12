---
title: "Boot partition full: can't update"
date: 2017-10-11
forum: Installation &amp; Upgrades
---

### Post by strixtux on 2017-10-11
Dear Foristi,

I am a complete newbie to Linux, although i am catching up rapidly after installing it on three different PCs within two weeks.

Just today I ran into a mess I am not used to. I tried to update as prescribed and ran into the error message that my HD was full. As apparently the partition "boot" is the only part affected, I tried to clean it, but no avail, it sill claims the partition is full.

ANY real help will be thoroughly appreciated. Under Win X I used to use Advanced System Cleaner, but that ain't gonna play with Linux.

What brought me to Linux was the fact that Win X keeps on crashing over and over. <snip>

Thanxalot for your patience!

---

### Post by The Cog on 2017-10-11
Please don't be rude with name calling like that. It is against the code of conduct.

Try 
```
sudo apt autoremove
``` and see if that is successful.

---

### Post by ajgreeny on 2017-10-11
So we can see the exact state of things at the moment please show us the output of the following commands, one at a time.
```
df -h
sudo blkid
mount
sudo fdisk -l
dpkg -l linux-image*
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by strixtux on 2017-10-11
```
Dateisystem                         Größe Benutzt Verf. Verw% Eingehängt auf
udev                                 2,0G       0  2,0G    0% /dev
tmpfs                                404M    6,4M  397M    2% /run
/dev/mapper/ubuntu--studio--vg-root  289G     37G  239G   14% /
tmpfs                                2,0G     24M  2,0G    2% /dev/shm
tmpfs                                5,0M    4,0K  5,0M    1% /run/lock
tmpfs                                2,0G       0  2,0G    0% /sys/fs/cgroup
/dev/sda1                            472M    466M     0  100% /boot
tmpfs                                404M     52K  404M    1% /run/user/1000
```

Sounds a trifle complicated....

```
/dev/sda1: UUID="f5776107-f4df-4e2c-8eaf-c55be514c748" TYPE="ext2" PARTUUID="6c0ac3da-01"
/dev/sda5: UUID="lDn00c-ZbAR-98NK-yTm5-6Ejm-HcPG-cPSQcG" TYPE="LVM2_member" PARTUUID="6c0ac3da-05"
/dev/mapper/ubuntu--studio--vg-root: UUID="dc73df80-90c6-47a8-bd69-ad9645ce9da2" TYPE="ext4"
/dev/mapper/ubuntu--studio--vg-swap_1: UUID="1ba96088-5692-4d19-928f-f9d5cd349518" TYPE="swap"
```

---

### Post by vasa1 on 2017-10-11
Your operating system seems to be German. If you preface commands you run in the terminal with **LANG=C**, the output will be in English. Try it with```
LANG=C df -h
```

I've modified two of your posts to incorporate code tags. Please use them in future posts.

---

### Post by ajgreeny on 2017-10-11
In order to clear some of the unneeded kernels that are filling /boot we do need the output of ```
LANG=C dpkg -l linux-image*
``` which will list all of the current kernels, some of which could be only half installed or perhaps unconfigured at the moment.

Once we know that we can give you some dpkg commands to remove kernel packages and make space in /boot.

---

### Post by strixtux on 2017-10-12
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
ii  linux-image-4. 4.10.0-30.34 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-32.36 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-33.37 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-35.39 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-37.41 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-92.115 i386         Linux kernel image for version 4.
ic  linux-image-4. 4.4.0-93.116 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-96.119 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.8.0-36.36~ i386         Linux kernel image for version 4.
ii  linux-image-lo 4.4.0.97.102 i386         lowlatency Linux kernel image
ii  linux-image-lo 4.10.0.37.39 i386         lowlatency Linux kernel image
```

---

### Post by ajgreeny on 2017-10-12
That's an interesting output as you appear to have the most recent versions of both the 4.4.0 and the 4.10.0 kernel series.
What kernel are you currently booting to; show us the output of **uname -a** in terminal.
It could also help to extend that dpkg command you ran to show other packages with linux at the start of their name as it may avoid dependency errors when we remove packages to make room, so let's see the output of ```
dpkg -l linux-image* linux-signed* linux-generic*
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by strixtux on 2017-10-13
```
rick@Angor:~$ dpkg -l linux-image* linux-signed* linux-generic*
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Vollständig Löschen/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/halb konFiguriert/
         Halb installiert/Trigger erWartet/Trigger anhängig
|/ Fehler?=(kein)/R=Neuinstallation notwendig (Status, Fehler: GROSS=schlecht)
||/ Name           Version      Architektur  Beschreibung
+++-==============-============-============-=================================
un  linux-generic- <keine>      <keine>      (keine Beschreibung vorhanden)
un  linux-image    <keine>      <keine>      (keine Beschreibung vorhanden)
ii  linux-image-4. 4.10.0-35.39 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-37.41 i386         Linux kernel image for version 4.
ic  linux-image-4. 4.4.0-93.116 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 i386         Linux kernel image for version 4.
ii  linux-image-lo 4.4.0.97.102 i386         lowlatency Linux kernel image
ii  linux-image-lo 4.10.0.37.39 i386         lowlatency Linux kernel image
dpkg-query: Kein Paket gefunden, das auf linux-signed* passt
```

---

### Post by ajgreeny on 2017-10-13
Was that the full output as it is very different and shows fewer kernels than showed in your post #8?

It will also help if you maximise the terminal before running the command.

And please use code tags as I requested last time.
I also forgot to ask you to use the prefix **LANG=C** with that last command; it will help us a lot more as this is an English language forum.

---

### Post by strixtux on 2017-10-15
```

Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Vollständig Löschen/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/halb konFiguriert/
         Halb installiert/Trigger erWartet/Trigger anhängig
|/ Fehler?=(kein)/R=Neuinstallation notwendig (Status, Fehler: GROSS=schlecht)
||/ Name                                    Version                  Architektur              Beschreibung
+++-=======================================-========================-========================-==================================================    =================================
un  linux-generic-hwe-16.04                 <keine>                    <keine>                  (keine Beschreibung vorhanden)
un  linux-image                             <keine>                    <keine>                  (keine Beschreibung vorhanden)
ii  linux-image-4.10.0-35-lowlatency        4.10.0-35.39~16.04.1       i386                     Linux kernel image for version 4.10.0 on 32 bit   x86 SMP
ii  linux-image-4.10.0-37-lowlatency        4.10.0-37.41~16.04.1       i386                     Linux kernel image for version 4.10.0 on 32 bit   x86 SMP
ic  linux-image-4.4.0-93-lowlatency         4.4.0-93.116               i386                     Linux kernel image for version 4.4.0 on 32 bit   x86 SMP
ii  linux-image-4.4.0-97-lowlatency         4.4.0-97.120               i386                     Linux kernel image for version 4.4.0 on 32 bit   x86 SMP
ii  linux-image-lowlatency                  4.4.0.97.102             i386                     lowlatency Linux kernel image
ii  linux-image-lowlatency-hwe-16.04        4.10.0.37.39             i386                     lowlatency Linux kernel image
dpkg-query: Kein Paket gefunden, das auf linux-signed* passt [\code]
Sill no substantial difference (in my eyes) But a difference there is. 				

```

---

### Post by ajgreeny on 2017-10-15
You now show only the six kernels shown as installed though the one marked ic is not configured or usable.
```
ii  linux-image-4.10.0-35-lowlatency        4.10.0-35.39~16.04.1      
ii  linux-image-4.10.0-37-lowlatency        4.10.0-37.41~16.04.1 
ic  linux-image-4.4.0-93-lowlatency         4.4.0-93.116   
ii  linux-image-4.4.0-97-lowlatency         4.4.0-97.120
ii  linux-image-lowlatency                  4.4.0.97.102
ii  linux-image-lowlatency-hwe-16.04        4.10.0.37.39
```
Previously in post #7 you had these
```
ii  linux-image-4. 4.10.0-30.34 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-32.36 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-33.37 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-35.39 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-37.41 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-92.115 i386         Linux kernel image for version 4.
ic  linux-image-4. 4.4.0-93.116 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-96.119 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.8.0-36.36~ i386         Linux kernel image for version 4.
ii  linux-image-lo 4.4.0.97.102 i386         lowlatency Linux kernel image
ii  linux-image-lo 4.10.0.37.39 i386         lowlatency Linux kernel image
```
so several have already gone.
Do you know how they have disappeared?

Have you tried using```
sudo apt-get autoremove
```
Did it work or show errors?
We can still clear up some of these unneeded kernels if it did not work for you, but need to know which kernel you are booted to now so please show us the output of ```
uname -a
```and please, please, please, use code tags for terminal output.

---

### Post by strixtux on 2017-10-16
```

[COLOR=#000080]ick@Angor:~$ dpkg -l linux-image* linux-signed* linux-generic*
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Vollständig Löschen/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/halb konFiguriert/
         Halb installiert/Trigger erWartet/Trigger anhängig
|/ Fehler?=(kein)/R=Neuinstallation notwendig (Status, Fehler: GROSS=schlecht)
||/ Name                                    Version                  Architektur              Beschreibung
+++-=======================================-========================-========================-===================================================================================
un  linux-generic-hwe-16.04                 <keine>                  <keine>                  (keine Beschreibung vorhanden)
un  linux-image                             <keine>                  <keine>                  (keine Beschreibung vorhanden)
ii  linux-image-4.10.0-35-lowlatency        4.10.0-35.39~16.04.1     i386                     Linux kernel image for version 4.10.0 on 32 bit x86 SMP
ii  linux-image-4.10.0-37-lowlatency        4.10.0-37.41~16.04.1     i386                     Linux kernel image for version 4.10.0 on 32 bit x86 SMP
ic  linux-image-4.4.0-93-lowlatency         4.4.0-93.116             i386                     Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-97-lowlatency         4.4.0-97.120             i386                     Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-lowlatency                  4.4.0.97.102             i386                     lowlatency Linux kernel image
ii  linux-image-lowlatency-hwe-16.04        4.10.0.37.39             i386                     lowlatency Linux kernel image
[/COLOR]

```

sudo apt-get autoremove just gave me the most confusing answer: everything OK, nothing to do.

I'm getting sore points on the back of my head ;-)

rescinded due to redundancy

---

### Post by strixtux on 2017-10-18
I put an end to the misery by upgrading to 17.04 which is working like a charm on this device. Wreaked havoc on my Compaq but that is a different can of worms, most probably due to my patty fingers. Thank you all a lot!

---

