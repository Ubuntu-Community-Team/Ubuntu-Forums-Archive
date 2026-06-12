---
title: "Installing ubuntu on old laptop (help)"
date: 2019-09-08
forum: Installation &amp; Upgrades
---

### Post by mvpcurtis on 2019-09-08
Hello. I purchased an old cheap laptop yesterday and I wanted to wipe it clean from windows 7 and install ubuntu onto it. The problem I'm having is that I'm unable to change the boot priority order in the bios on the laptop. I have both a bootable USB and DVD ready but whenever I enter the bios, I can't change anything except for the system time and date, let alone the boot priority order. I've added a couple of pics of the bios screen and some information about the laptop model below. If anyone can help me out as I'm eager to sink my teeth into this OS, that'd be amazing!

Information:[IMG]https://imgur.com/PCw6G1b[/IMG]
Model - Packard bell P5WS0
OS - Windows 7 home premium 

```
[https://imgur.com/PCw6G1b](https://imgur.com/PCw6G1b)
[https://imgur.com/hfvOTIT](https://imgur.com/hfvOTIT)
```
[COLOR=#FFFFFF][FONT=&amp]
[/FONT][/COLOR]

---

### Post by crip720 on 2019-09-08
Check the security tab and see if it is password protected.  F12 change to enable, if you can.  You use F5/F6 to move up/down.

---

### Post by crip720 on 2019-09-08
Would also try to keep Win 7 in smaller partition in case you need to update bios or something, saves having to install it after if you do need it.

---

### Post by GhX6GZMB on 2019-09-08
Try F9 to restore defaults. But if it's password protected, you have a problem.

---

### Post by oldfred on 2019-09-08
Flash drives are often under HDD entries.
It looks like an old BIOS only system.

You often do not have to change boot priority in BIOS, but use a one time boot key, often f10 or f12 check your manual. And that should show live installer under HDD(s).

Since only 2GB of RAM, you need a lighter weight version of Ubuntu.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu MATE, Budgie 
      
 [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors) 
    

If not ever network booting, I might turn that off, just so BIOS does not try to get to network to boot.

---

### Post by ubfan1 on 2019-09-08
In addition to the F12 boot menu change to enable on the main menu, you should probably change the Function Key Behavior from "Special Keys" to "Function Keys".

---

### Post by (kyT%0) on 2019-09-08
if the bios was password protected would the op be able to get to the screens posted in the images?

---

### Post by crip720 on 2019-09-08
If password protected, here is one link, many more if you google.  [https://www.howtogeek.com/186235/how-to-secure-your-computer-with-a-bios-or-uefi-password/](https://www.howtogeek.com/186235/how-to-secure-your-computer-with-a-bios-or-uefi-password/)

---

### Post by GhX6GZMB on 2019-09-08
> **u-n said:**
> if the bios was password protected would the op be able to get to the screens posted in the images?


Good question. Depends on the BIOS.

But I agree with other posters: Ubuntu is too heavy for an older laptop.
I use Lubuntu 19.04 on my 10 year old HP/Compaq 6910p myself. Ubuntu demanded too much, even though I installed 4 GB RAM.

---

### Post by Skaperen on 2019-09-08
i have seen a bios with user passwords and an admin password.  user can look in the bios but not change anything.

---

### Post by Skaperen on 2019-09-08
long ago my first Linux fit on a machine with 170 MB (Megabyte) hard drive and 4 MB RAM.  a friend of mine did it on less (120 MB and 2.5 MB).

---

### Post by (kyT%0) on 2019-09-08
admin password locks the bios | user password locks the boot process | hdd password locks the hard disk

if you can access the bios you can make changes.

---

