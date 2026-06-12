---
title: "Upgrading from Ubuntu 16.04 to 18.04"
date: 2018-07-16
forum: Installation &amp; Upgrades
---

### Post by ordak on 2018-07-16
Hi,

I have an ASUS laptop. After some* sound card* problems I decided to upgrade from Ubuntu 16.04 to 18.04 . *Without *the following command:

**$ sudo  apt autoremove**

I tried: 

[B]$ sudo do-release-upgrade -d

[/B]Now for about a day I saw some upper text quickly appearing and disappearing. After that for about three days I am seeing five circles in the center of screen. One by one they become orange, then white and reverse of it.

What can I do now ?

---

### Post by akhilgeothom on 2018-07-16
Are you sure it is not a hardware fault?

Try connecting to another display or boot from another OS.

---

### Post by ordak on 2018-07-16
> **akhilgeothom said:**
> Are you sure it is not a hardware fault?

Try connecting to another display or boot from another OS.

On the left side of the laptop's touch-pad a place has come up, maybe it is battery's area, should I get someone to remove battery ? this is un-trivial for me.

---

### Post by oldfred on 2018-07-16
You did do a good backup before starting upgrade?

Generally upgrades work, but only with systems that already work well and have no proprietary drivers or ppa. Those have to be un-installed or upgrade may not work.
I just prefer new clean install & restore all data and maybe some settings from backup.

This may not work:
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key) 
    
Download 18.04 and create live installer. Even if you still want to try to repair and finish upgrade.
        Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Direct link to downloads page, most want  ubuntu-18.04-desktop-amd64.iso
[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

---

### Post by ordak on 2018-07-18
> **oldfred said:**
> You did do a good backup before starting upgrade?

Generally upgrades work, but only with systems that already work well and have no proprietary drivers or ppa. Those have to be un-installed or upgrade may not work.
I just prefer new clean install & restore all data and maybe some settings from backup.

This may not work:
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key) 
    
Download 18.04 and create live installer. Even if you still want to try to repair and finish upgrade.
        Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Direct link to downloads page, most want  ubuntu-18.04-desktop-amd64.iso
[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

Thanks, I tried "live installer" Ubuntu 18.04 and installed it over unfinished one. Things seem to be going rather well despite some Wi-Fi problems.

---

