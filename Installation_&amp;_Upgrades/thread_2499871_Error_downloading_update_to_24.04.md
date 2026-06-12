---
title: "Error downloading update to 24.04"
date: 2024-08-13
forum: Installation &amp; Upgrades
---

### Post by lucas392 on 2024-08-13
Good day 
Update 24.04 has appeared 
I currently have version 22.04
When I click Download in the update window, a new window pops up and the update starts downloading the progress bar reaches about 40%, which is about 255Mb, the download stops, and after a while a download error message pops up with a hint to check the internet connection.
The error occurs on LAN and WiFi 
Disk space about 800Gb.

 What can I do to make it go further?

---

### Post by ubfan1 on 2024-08-13
The full ISO size is 5Gigabytes +, so 800 megabytes is too small for available disk space.

---

### Post by Rubi1200 on 2024-08-13
Open a terminal and show us the output of this command:

```
df -hT
```

I assume from your post that you are trying to update via the Software Updater, correct?

---

### Post by lucas392 on 2024-08-13
Sorry.
I mixed up the letters. There are 800Gb free

---

### Post by lucas392 on 2024-08-13
Yes, exactly.
> tomek@no7:~$ df -hT
System plików  Typ   rozm. u&#380;yte dost. %u&#380;. zamont. na
tmpfs          tmpfs  1,6G  3,2M  1,6G   1% /run
/dev/sda3      ext4   916G  198G  672G  23% /
tmpfs          tmpfs  7,8G   32M  7,8G   1% /dev/shm
tmpfs          tmpfs  5,0M  4,0K  5,0M   1% /run/lock
/dev/sda2      vfat   513M  6,1M  506M   2% /boot/efi
tmpfs          tmpfs  1,6G  100K  1,6G   1% /run/user/1000
tomek@no7:~$

---

### Post by lucas392 on 2024-08-13
Synaptic:
W: Cannot download [http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb](http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb)
     Error reading from server - read (104: Connection disconnected by the other party) [IP: 153.19.251.225 80]

---

### Post by #&amp;thj^% on 2024-08-13
The DL Size is "254.4*MiB (266,737,844 bytes)"
Try this:
```
wget http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb

```
Next to install it:
```
sudo apt install linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
```

---

### Post by lucas392 on 2024-08-13
tomek@no7:~$ sudo apt install linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
[sudo] has&#322;o u&#380;ytkownika tomek: 
Reading package lists... Done Building dependency tree... Done Reading status information... Done The package linux-firmware has no version available, but is referenced by another package.  This usually means that the package is missing, has been superseded by another package, or is not available using the currently configured sources.  However, the following packages replace it:
  firmware-sof-signed

E: Issue "linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb" dla "linux-firmware" was not found
tomek@no7:~$

---

### Post by #&amp;thj^% on 2024-08-13
You have problems, as seen with mine:
```
wget http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
--2024-08-13 10:41:42--  http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
Resolving pl.archive.ubuntu.com (pl.archive.ubuntu.com)... 153.19.251.225, 2001:4070:1:2::4
Connecting to pl.archive.ubuntu.com (pl.archive.ubuntu.com)|153.19.251.225|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 266737844 (254M) [application/octet-stream]
Saving to: &#8216;linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb&#8217;

linux-firmware_20220329.  68%[======================>            ] 173.20M  2.58MB/s    in 48s     

2024-08-13 10:42:31 (3.63 MB/s) - Read error at byte 181614804/266737844 (Connection reset by peer). Retrying.

--2024-08-13 10:42:32--  (try: 2)  http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
Connecting to pl.archive.ubuntu.com (pl.archive.ubuntu.com)|153.19.251.225|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 266737844 (254M), 85123040 (81M) remaining [application/octet-stream]
Saving to: &#8216;linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb&#8217;

linux-firmware_20220329. 100%[+++++++++++++++++++++++===========>] 254.38M  5.83MB/s    in 47s     

2024-08-13 10:43:20 (1.71 MB/s) - &#8216;linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb&#8217; saved [266737844/266737844]

```

Is there a proxy involved?

```
apt policy linux-firmware
linux-firmware:
  Installed: 20240808.gite131a437-0ubuntu1
  Candidate: 20240808.gite131a437-0ubuntu1
  Version table:
 *** 20240808.gite131a437-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by lucas392 on 2024-08-13
I don't have a proxy

```
Tomek@no7:~$ wget [http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb](http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb)
--2024-08-13 19:10:06--  [http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb](http://pl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb)
Translacja pl.archive.ubuntu.com (pl.archive.ubuntu.com)... 153.19.251.225, 2001:4070:1:2::4
&#321;&#261;czenie si&#281; z pl.archive.ubuntu.com (pl.archive.ubuntu.com)|153.19.251.225|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: 266737844 (254M) [application/octet-stream]
Zapis do: ‘linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb’

linux-firmware_2022 100%[===================>] 254,38M  10,7MB/s    w 25s      

2024-08-13 19:10:30 (10,4 MB/s) - zapisano ‘linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb’ [266737844/266737844]

```

---

### Post by lucas392 on 2024-08-13
uffff, I finally managed to save correctly. sorry for the previous entries

---

### Post by #&amp;thj^% on 2024-08-13
Ok then lets install it:
```
sudo apt install linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
```
Post back any errors please.

---

### Post by lucas392 on 2024-08-13
I don't know what's going on here.
it's still wrong.


Is it possible that it downloads but does not save to disk?
 In what directory should it be?

```
tomek@no7:~$ sudo apt install linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
[sudo] has&#322;o u&#380;ytkownika tomek: 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Odczyt informacji o stanie... Gotowe   
E: Nie uda&#322;o si&#281; odnale&#378;&#263; pakietu linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
tomek@no7:~$ 
```

---

### Post by #&amp;thj^% on 2024-08-13
Just do this please, run this and hit your space bar
```
sudo apt install ##space here 
```
before you hit enter drop the .deb in that terminal now hit enter

---

### Post by lucas392 on 2024-08-13
Result of the last ( ## )

```
[tomek@no7:~$ sudo apt install ## 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Odczyt informacji o stanie... Gotowe   
Nast&#281;puj&#261;ce pakiety zosta&#322;y zainstalowane automatycznie i nie s&#261; ju&#380; wi&#281;cej wymagane:
  libminizip1 libwpe-1.0-1 libwpebackend-fdo-1.0-1
  linux-headers-6.5.0-41-generic linux-hwe-6.5-headers-6.5.0-41
  linux-image-6.5.0-41-generic linux-modules-6.5.0-41-generic
  linux-modules-extra-6.5.0-41-generic
Aby je usun&#261;&#263; nale&#380;y u&#380;y&#263; "sudo apt autoremove".
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 5 nieaktualizowanych.
tomek@no7:~$ 

```

```
tomek@no7:~$ sudo apt install ## deb
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Odczyt informacji o stanie... Gotowe   
Nast&#281;puj&#261;ce pakiety zosta&#322;y zainstalowane automatycznie i nie s&#261; ju&#380; wi&#281;cej wymagane:
  libminizip1 libwpe-1.0-1 libwpebackend-fdo-1.0-1
  linux-headers-6.5.0-41-generic linux-hwe-6.5-headers-6.5.0-41
  linux-image-6.5.0-41-generic linux-modules-6.5.0-41-generic
  linux-modules-extra-6.5.0-41-generic
Aby je usun&#261;&#263; nale&#380;y u&#380;y&#263; "sudo apt autoremove".
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 5 nieaktualizowanych.
tomek@no7:~$ 

```

---

### Post by deadflowr on 2024-08-13
Doesn't local apt installs require either the full path or if inside the directory that has the deb require ./ before the package?
```
sudo apt install ./linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
```

---

### Post by #&amp;thj^% on 2024-08-13
It's hard for me to translate, but all looks good as near as I tell:
Now run :
```
sudo apt autoremove --purge
##And
sudo apt upgrade
```

---

### Post by #&amp;thj^% on 2024-08-13
> **deadflowr said:**
> Doesn't local apt installs require either the full path or if inside the directory that has the deb require ./ before the package?
```
sudo apt install ./linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
```
Yes it dose.

---

### Post by lucas392 on 2024-08-13
> **deadflowr said:**
> Doesn't local apt installs require either the full path or if inside the directory that has the deb require ./ before the package?
```
sudo apt install ./linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
```

```
tomek@no7:~$ sudo apt install ./linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
[sudo] has&#322;o u&#380;ytkownika tomek: 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Odczyt informacji o stanie... Gotowe   
Uwaga, wybieranie "linux-firmware" zamiast "./linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb"
Nast&#281;puj&#261;ce pakiety zosta&#322;y zainstalowane automatycznie i nie s&#261; ju&#380; wi&#281;cej wymagane:
  libminizip1 libwpe-1.0-1 libwpebackend-fdo-1.0-1
  linux-headers-6.5.0-41-generic linux-hwe-6.5-headers-6.5.0-41
  linux-image-6.5.0-41-generic linux-modules-6.5.0-41-generic
  linux-modules-extra-6.5.0-41-generic
Aby je usun&#261;&#263; nale&#380;y u&#380;y&#263; "sudo apt autoremove".
Nast&#281;puj&#261;ce pakiety zostan&#261; zaktualizowane:
  linux-firmware
1 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 4 nieaktualizowanych.
Konieczne pobranie 267 MB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 1&#8239;549 kB miejsca na dysku.
Pobieranie:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31 [267 MB]
Ign.:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31
Pobieranie:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31 [267 MB]
Ign.:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31
Pobieranie:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31 [267 MB]
Ign.:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31
Pobieranie:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31 [267 MB]
Ign.:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31
Pobieranie:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31 [267 MB]
Ign.:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31
Pobieranie:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31 [267 MB]
B&#322;&#261;d:1 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-firmware all 20220329.git681281e4-0ubuntu3.31
  Nie odnaleziono pliku - /home/tomek/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb (13: Brak dost&#281;pu)
E: Nie uda&#322;o si&#281; pobra&#263; file:/home/tomek/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb  Nie odnaleziono pliku - /home/tomek/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb (13: Brak dost&#281;pu)
E: Nie uda&#322;o si&#281; pobra&#263; niektórych archiwów, prosz&#281; spróbowa&#263; uruchomi&#263; apt-get update lub u&#380;y&#263; opcji --fix-missing.
tomek@no7:~$ 

```

---

### Post by lucas392 on 2024-08-13
I changed the permissions to FULL access and now it works

---

### Post by #&amp;thj^% on 2024-08-13
I see now, I wish you would translate a bit better:
Please show this:
```
cd && ls
```
Mine:
```
ls
 balenaEtcher-1.18.11-x64.AppImage                         Music
 balenaEtcher-1.9.0-x64.AppImage                           nohup.out
 cachyos-repo                                              nvidia-bug-report.log.gz
 dead.letter                                               Pictures
 Desktop                                                   Public
 Documents                                                'resolve removal log'
 Downloads                                                 surfshark-install.sh
 Dropbox                                                   temp.file
 ExtremeCooling4Linux-v0.3-x86_64.AppImage                 Templates
 fpinstalled.txt                                           Videos
 installed.txt                                             zc-master
 linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb

```
install:
```
sudo apt install '/home/<your user name here>/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb'
```
```
ls -al '/home/me/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb' 
-rw-rw-r-- 1 me me 266737844 May  6 09:23 /home/me/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb

```

---

### Post by lucas392 on 2024-08-13
after changing permissions what installation went through. 
But 24 ubuntu is not.


```
tomek@no7:~$ sudo apt install /home/tomek/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Odczyt informacji o stanie... Gotowe   
Uwaga, wybieranie "linux-firmware" zamiast "/home/tomek/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb"
linux-firmware is already the newest version (20220329.git681281e4-0ubuntu3.31).
linux-firmware zaznaczony jako zainstalowany r&#281;cznie.
Nast&#281;puj&#261;ce pakiety zosta&#322;y zainstalowane automatycznie i nie s&#261; ju&#380; wi&#281;cej wymagane:
  libminizip1 libwpe-1.0-1 libwpebackend-fdo-1.0-1
Aby je usun&#261;&#263; nale&#380;y u&#380;y&#263; "sudo apt autoremove".
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 4 nieaktualizowanych.
tomek@no7:~$ 


```

---

### Post by #&amp;thj^% on 2024-08-13
What???
Please see your return:
in english:
```
Note, choosing "linux-firmware" instead of "/home/tom/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb" linux-firmware is already the newest version 
```
View with:
```
apt policy linux-firmware
linux-firmware:
  Installed: 20240808.gite131a437-0ubuntu1
  Candidate: 20240808.gite131a437-0ubuntu1
  Version table:
 *** 20240808.gite131a437-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```
Mine will show different than yours, I'm on 24.10  oracular

---

### Post by lucas392 on 2024-08-13
```
tomek@no7:~$ hostnamectl
 Static hostname: no7
       Icon name: computer-laptop
         Chassis: laptop
      Machine ID: 3f08fc0f6003439ca9e152bcb0325528
         Boot ID: 1944c30621b24502929211be2cc06cfb
Operating System: Ubuntu 22.04.4 LTS              
          Kernel: Linux 6.5.0-45-generic
    Architecture: x86-64
 Hardware Vendor: Lenovo
  Hardware Model: Lenovo G780
tomek@no7:~$ 

```

I wanted 24.04.

I changed the File Permissions to 777 linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb.  
The installation started and this is the result:

```
tomek@no7:~$ sudo apt install /home/tomek/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb
Reading package lists... Done
Building a dependency tree... Done
Reading status information... Done  
Note, selecting "linux-firmware" instead of "/home/tomek/linux-firmware_20220329.git681281e4-0ubuntu3.31_all.deb"
linux-firmware is already the newest version (20220329.git681281e4-0ubuntu3.31).
linux-firmware marked as manually installed.
The following packages were automatically installed and are no longer required:
  libminizip1 libwpe-1.0-1 libwpebackend-fdo-1.0-1
To remove them, use "sudo apt autoremove".
 0 updated, 0 newly installed, 0 removed and 4 not updated.
tomek@no7
```

---

### Post by #&amp;thj^% on 2024-08-13
> **lucas392 said:**
> ```


I wanted 24.04.



So really you want to go from 22.04 to 24.04, and nothing to do with "linux-firmware"
That will come in automatically with 24.04, now I understand your problem, and if it were me I'd wait another week.

But if your not afraid of the risks, have a look here: https://linuxconfig.org/ubuntu-upgrade-to-24-04-noble-numbat-a-step-by-step-howto-guide
Be very sure you have a good back-up in place before doing that. Good Luck
[code]hostnamectl
 Static hostname: Legion-5-15ACH6-zfs
       Icon name: computer-laptop
         Chassis: laptop &#55357;&#56507;
      Machine ID: 1a06a17ac41d493fbf1181d1659da4d2
         Boot ID: 7e81937b826b4642a6f1c3c7a173b9fb
Operating System: Ubuntu Oracular Oriole (development branch)
          Kernel: Linux 6.10.0-15-generic
    Architecture: x86-64
 Hardware Vendor: Lenovo
  Hardware Model: Legion 5 15ACH6
Firmware Version: HHCN36WW
   Firmware Date: Thu 2023-12-07
    Firmware Age: 8month 1w

```

---

### Post by lucas392 on 2024-08-13
Okay. I'll wait a week and see what happens. 
Thanks VERY much for helping me update.
A big BEER for you!!

---

### Post by #&amp;thj^% on 2024-08-13
> **lucas392 said:**
> 
A big BEER for you!!
Cheers ;)

---

