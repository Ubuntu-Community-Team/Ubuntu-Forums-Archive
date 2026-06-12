---
title: "Kubuntu and xubuntu 20.04.3 LTS have different kernels"
date: 2022-02-15
forum: Installation &amp; Upgrades
---

### Post by nozombian on 2022-02-15
Hi, I have 2 ubuntu flavours on 2 PCs: kubuntu and xubuntu.
Kubuntu:
```
[FONT=monospace][COLOR=#000000]Static hostname: kubuntu [/COLOR]
         Icon name: computer-desktop 
           Chassis: desktop 
        Machine ID: 8619bf4587d346889bb1677a218f689d 
           Boot ID: b52ccf7bda1c49388dded2536748c293 
  Operating System: Ubuntu 20.04.3 LTS 
            Kernel: Linux 5.4.0-99-generic 
      Architecture: x86-64
[/FONT]
[FONT=monospace][FONT=monospace][COLOR=#54ff54]**me@kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt update [/COLOR]
Mám:1 http://cz.archive.ubuntu.com/ubuntu focal InRelease 
Mám:2 http://cz.archive.ubuntu.com/ubuntu focal-updates InRelease 
Mám:3 http://cz.archive.ubuntu.com/ubuntu focal-backports InRelease 
Stahuje se:4 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB] 
Sta&#382;eno 114 kB za 1s (154 kB/s)
Na&#269;ítají se seznamy balík&#367;&#8230; Hotovo 
Vytvá&#345;í se strom závislostí        
Na&#269;ítají se stavové informace&#8230; Hotovo 
V&#353;echny balíky jsou aktuální.
[/FONT][/FONT]
```

Xubuntu:
```
[FONT=monospace][COLOR=#000000]   Static hostname: xubuntu [/COLOR]
         Icon name: computer-desktop 
           Chassis: desktop 
        Machine ID: d3c6a94a2b174c5181a5f80a823b49de 
           Boot ID: 9fb31fd8e89c4df38dbdc0f0c219ccb1 
  Operating System: Ubuntu 20.04.3 LTS 
            Kernel: Linux 5.13.0-28-generic 
      Architecture: x86-64
[/FONT]
[FONT=monospace][FONT=monospace][COLOR=#54ff54]**me@xubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt update [/COLOR]
Mám:1 http://cz.archive.ubuntu.com/ubuntu focal InRelease 
Stahuje se:2 http://cz.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]                            
Mám:3 http://ppa.launchpad.net/x2go/stable/ubuntu focal InRelease                
Stahuje se:4 http://cz.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB] 
Stahuje se:5 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Stahuje se:6 http://cz.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1&#8239;572 kB] 
Stahuje se:7 http://cz.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [602 kB] 
Stahuje se:8 http://cz.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [282 kB] 
Stahuje se:9 http://cz.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [904 kB]
Stahuje se:10 http://cz.archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [667 kB] 
Stahuje se:11 http://cz.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [391 kB] 
Stahuje se:12 http://cz.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [940 B] 
Stahuje se:13 http://cz.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata [7&#8239;996 B] 
Stahuje se:14 http://cz.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [23,7 kB] 
Stahuje se:15 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [40,5 kB] 
Stahuje se:16 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66,4 kB] 
Stahuje se:17 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B] 
Sta&#382;eno 4&#8239;896 kB za 1s (4&#8239;567 kB/s)
Na&#269;ítají se seznamy balík&#367;&#8230; Hotovo 
Vytvá&#345;í se strom závislostí        
Na&#269;ítají se stavové informace&#8230; Hotovo 
V&#353;echny balíky jsou aktuální.
[/FONT][/FONT]
```

Both have same repos, both are ubuntu 20.04.3 LTS, but different kernels, both are updated and rebooted. What am I missing? Why does my kubuntu have an older kernel? Thank you.

---

### Post by Impavidus on 2022-02-15
20.04, like all LTS releases, has two kernels series available. You can use the original, 5.4, or the HWE kernel, which is upgraded every 6 months and now at 5.13. Try```
dpkg --list "linux-image*"
```
That will show the kernel (meta-)packages installed on your systems. On your Xubuntu system it will be the HWE kernel. Which one you get depends on the live disk .iso you used for installation. 20.04 and 20.04.1 can give the original kernel series (depending on flavour), 20.04.2 and later give the HWE series. You can switch, if you like, but there's rarely a reason to.

---

### Post by nozombian on 2022-02-15
I see, that is interesting. I took a look on my another kubuntu and it is also 5.13.0-28, it must indeed depend on date (and iso of that time) when I have installed it. I had no idea about this, thank you.

---

