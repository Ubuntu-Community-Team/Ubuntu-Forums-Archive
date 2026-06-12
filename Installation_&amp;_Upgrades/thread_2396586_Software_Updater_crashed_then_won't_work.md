---
title: "Software Updater crashed then won't work"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by Nina_W on 2018-07-18
Software Updater crashed whilst doing an update. Now it won't open at all. I've tried sudo apt-get dist-upgrade in the termimal window and it gives segmentation faulty tree... 50%

Any suggestions?
Is there any way to re-install the Software Updater without having to install the whole operating system?
Also, is there any way to get the operating system to check itself for errors in case any other bits have got corrupted.

I should add that I have had an ongoing problem with the internet crashing intermittently, fine some days, unuseable on others, seems worse if there are videos, animated adverts etc. It often does this after updating then seems to sort itself out after a few days.

---

### Post by Frogs Hair on 2018-07-18
Can you post the entire output from the following? ```
sudo apt update
```

---

### Post by Nina_W on 2018-07-19
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]    
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [186 kB]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [204 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [37.5 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [37.4 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [138 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [31.4 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [53.7 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en [21.7 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [2,452 B]
Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [130 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [129 kB]
Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [58.1 kB]
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [125 kB]
Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [122 kB]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [219 kB]
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Fetched 1,670 kB in 2s (768 kB/s)                                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
28 packages can be upgraded. Run 'apt list --upgradable' to see them.

---

### Post by Nina_W on 2018-07-19
Software Updater is now working.
However, I'm still getting errors when rebooting.
There's a segmentation fault shown in the screenshot below.
Also, it says I have obsolete packages "apt, apt-utils, libapt-inst2.0, libapt-pkg5.0" and need to upgrade them, but I don't know how to do that.

---

### Post by Frogs Hair on 2018-07-19
Where does it say you need to upgrade obsolete packages ?

---

### Post by Nina_W on 2018-07-19
A window pops up saying Ubuntu has experienced and internal error, then there's a load of text listing things like operating system.

---

### Post by Bashing-om on 2018-07-19
Nina_W; Hello -

None of us are have extreme clairvoyant powers. We do need to see what you see and we can not look over your shoulder . crystal balls just no longer work/
From the above paste:
> 
28 packages can be upgraded. 


so, show now the result:
```

sudo apt full-upgrade

```

see where that leads to .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Nina_W on 2018-08-01
Well the sudo apt full-upgrade did do some upgrades.

However, even if I set the preferences to not look for updates I was still getting system errors a short time after boot up. Looking at all errors, they were different each time. Errors appearing mid-session randomly as well. So it looks like a hardware problem that seems to be getting steadily worse. 

So I have now bought a newer computer and am currently trying to get dual boot to work.

---

