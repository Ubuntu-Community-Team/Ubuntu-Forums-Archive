---
title: "Boot working only in recovery mode or with login"
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by larry90 on 2019-06-17
Hello everyone, as the title suggested i have a problem booting in my Ubuntu.
 I have dual boot with windows, which i can boot without problems, but when i try to login in Ubuntu i get a never ending loading screen; I noticed that the only way i can boot is if i disable automatic login or if enter recovery mode and than normal start.... 
can anyone help me?
 have a nice day!

---

### Post by larry90 on 2019-06-18
noone knows how to fix my problem? ](*,)
everything else looks like is working fine!

---

### Post by Rubi1200 on 2019-06-18
Which version are you on?

Post some specs. please especially RAM, graphics card etc.

Any recent updates that might have caused this?

Output of following commands would also help:

```
sudo fdisk -l
```

```
cat /etc/apt/sources.list
```

```
systemd-analyze blame
```

Please post using code tags.

Thanks.

---

### Post by larry90 on 2019-06-18
I m using Ubuntu 18.04 LTS version.
 My specs are:
 -RAM 16GB,  
 - graphic card NVIDIA GeForce RTX 2060
 Hard Drive: 2 native hard drive (m.2 SSD of 256GM and HDD 1TB ) but i later added one more m.2 via PCIE adaptor. This last drive is where I installed Ubuntu.
 
 Regarding recent updates that might cause this… u could be on to something, because at first it was working smoothly and than after I was still personalizing my ubuntu and making updates the problem started…
 
 Here is the output of sources.list
  ```
deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted
 
 
 # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to

 # newer versions of the distribution.
 deb http://ch.archive.ubuntu.com/ubuntu/ bionic main restricted
 # deb-src http://ch.archive.ubuntu.com/ubuntu/ bionic main restricted
 
 
 ## Major bug fix updates produced after the final release of the
 ## distribution.
 deb http://ch.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
 # deb-src http://ch.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
 
 
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team. Also, please note that software in universe WILL NOT receive any
 ## review or updates from the Ubuntu security team.
 deb http://ch.archive.ubuntu.com/ubuntu/ bionic universe
 # deb-src http://ch.archive.ubuntu.com/ubuntu/ bionic universe
 deb http://ch.archive.ubuntu.com/ubuntu/ bionic-updates universe
 # deb-src http://ch.archive.ubuntu.com/ubuntu/ bionic-updates universe
 
 
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu
 ## security team.
 # deb-src http://ch.archive.ubuntu.com/ubuntu/ bionic multiverse
 # deb-src http://ch.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
 
 
 ## N.B. software from this repository may not have been tested as
 ## extensively as that contained in the main release, although it includes
 ## newer versions of some applications which may provide useful features.
 ## Also, please note that software in backports WILL NOT receive any review
 ## or updates from the Ubuntu security team.
 # deb-src http://ch.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
 
 
 ## Uncomment the following two lines to add software from Canonical's
 ## 'partner' repository.
 ## This software is not part of Ubuntu, but is offered by Canonical and the
 ## respective vendors as a service to Ubuntu users.
 # deb http://archive.canonical.com/ubuntu bionic partner
 # deb-src http://archive.canonical.com/ubuntu bionic partner
 
 
 deb http://security.ubuntu.com/ubuntu bionic-security main restricted
 # deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
 deb http://security.ubuntu.com/ubuntu bionic-security universe
 # deb-src http://security.ubuntu.com/ubuntu bionic-security universe
 # deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```

Systemd seems to be working just fine.

```
$ systemd-analyze
Startup finished in 3.456s (kernel) + 12.417s (userspace) = 15.873s
graphical.target reached after 10.482s in userspace
```

I hope now my problem is a bit better explained, thanks for your help!

---

### Post by Rubi1200 on 2019-06-18
Maybe an update got messed up?

What do these commands show?

```
sudo dpkg --configure -a
```

```
sudo apt update
```

Please post the full output.

Thanks.

---

### Post by larry90 on 2019-06-18
first command there is no output, just asked my sudo psw; from sudo apt update it seems everything fine
```
Trovato:1 http://ch.archive.ubuntu.com/ubuntu bionic InRelease
Trovato:2 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease
Trovato:3 http://security.ubuntu.com/ubuntu bionic-security InRelease          
Trovato:4 http://ch.archive.ubuntu.com/ubuntu bionic-updates InRelease         
Trovato:5 http://ppa.launchpad.net/system76/pop/ubuntu bionic InRelease        
Scaricamento di:6 https://mega.nz/linux/MEGAsync/xUbuntu_18.04 ./ InRelease [1'484 B]
Recuperati 1'484 B in 1s (2'446 B/s)                              
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Tutti i pacchetti sono aggiornati.
```
All packages are updated (last sentence :P)

I was thinking maybe it could be something related to secure boot and the password to login that enable NVIDIA driver? Could it be something like that?

---

### Post by Rubi1200 on 2019-06-18
I don't dual boot with Windows but I know that if secure boot was disabled and there was a Windows update it is enabled again. Would be good to check the settings (also for fast startup).

Don't use NVIDIA, but yes could be. Try starting without the NVIDIA driver perhaps?

---

### Post by larry90 on 2019-06-19
> **Rubi1200 said:**
> I don't dual boot with Windows but I know that if secure boot was disabled and there was a Windows update it is enabled again. Would be good to check the settings (also for fast startup).

Don't use NVIDIA, but yes could be. Try starting without the NVIDIA driver perhaps?

I tried with or without secure boot, with or without NVIDIA drivers;  nothing works, I can only boot without an automatic login....after many days and tries I just give up with my problem. Ubuntu seems to be working fine so I can live with just entering my password at the beginning .. anyway thanks for trying to help me!

---

### Post by Rubi1200 on 2019-06-19
With automatic login disabled can you boot Ubuntu normally without any delays (other than entering the password)?

And you can reach the desktop and everything functions normally?

---

### Post by larry90 on 2019-06-20
yes, everything seems to be working fine

---

### Post by Rubi1200 on 2019-06-20
Good to hear.

Please mark Solved using Thread Tools at the top of the page.

Good luck and feel free to post if there is anything else we can help with.

---

