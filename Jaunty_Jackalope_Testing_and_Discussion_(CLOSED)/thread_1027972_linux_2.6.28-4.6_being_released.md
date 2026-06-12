---
title: "linux 2.6.28-4.6 being released"
date: 2009-01-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-01
Hi all, 
 Highlights of this new kernel release. 
> 

linux (2.6.28-4.6) jaunty; urgency=low

  [ Tim Gardner ]

  * Enable CONFIG_X86_E_POWERSAVER=m for i386 generic
    - LP: #237405
  * Build i386 AGP drivers as modules
    - LP: #312721
  * Build i386 DRM as a module
    - LP: #312721

  [ Upstream Kernel Changes ]

  * drm/i915: Add missing userland definitions for gem init/execbuffer.

    - LP: #308387


Although nothing for making ipv6 as a module or something because no bug filed I guess. 


Please file a bug on the same using the following 2 steps in Jaunty :-

First do a search using the exact image version with 

 ```
$ sudo aptitude search linux-image 
```

Then do 
```

$ apport-cli -f -p  linux-image-2.6.28- ?-generic

```

whatever the exact version so people may get ipv6 as an optional module and not built-in.

---

### Post by Slug71 on 2009-01-02
This Kernel just came through Update Manager.

---

### Post by autocrosser on 2009-01-02
I'm D/L it right now.....Anyone bugged the ipv6 yet?

Got it--rebooting------

---

### Post by autocrosser on 2009-01-02
Bootchart showed about 2~3 sec faster to GDM with this one.....Still about 7 sec or so slower that I was getting with Intrepid.......

---

### Post by plun on 2009-01-02
Well... the first boot froze for me directly after networking was initiated.

A power button freeze:^o...  magic Alt-SysRq-b also failed.

Rebooted again and it works...

- Boot time, nearly the same for me.

- No problem with IPv6, this must be a ISP specific bug.

Both behind a router and also directly to the ADSL line tested.

---

### Post by ronacc on 2009-01-02
it could be either router or ISP I only see it when I am behind my router (belkin f5d7230-4 ) not directly connected to my cable modem .

---

### Post by plun on 2009-01-02
> **ronacc said:**
> it could be either router or ISP I only see it when I am behind my router (belkin f5d7230-4 ) not directly connected to my cable modem .

OK...just some thoughts 

- Latest firmware for the router ?

- DNS issue ??  >>  the same with **OpenDNS** ?

[https://www.opendns.com/smb/start](https://www.opendns.com/smb/start)


- Clues with Wireshark...  upper "nerd-division" maybe...:D

Package info
[http://packages.ubuntu.com/jaunty/wireshark](http://packages.ubuntu.com/jaunty/wireshark)

Minimize the amout of running Internet apps > check for clues...

It can flood your logs...):P

---

### Post by vishalrao on 2009-01-02
why do we suspect ipv6 is causing slowdown for some people? i also feel that since kernel .28 came in with ipv6 built-in my downloads from archives (main and mirrors) are slow. earlier korean and japanese mirrors were full speed for me.

is there some way to disable ipv6 for now? i know we should file bugs and help fix the issue rather than avoiding it, but for the time being. i've tried editing /etc/modprobe.d/aliases and also setting some sysctl variables (searched for all with disable_ipv6)... but ifconfig still lists ipv6 enabled and my downloads are still slow...

(im currently updating, want to try out kvm/virt-manager)

EDIT: nevermind, downloading package lists directly via firefox are slow for me even on intrepid and vista from main and mirror archives... so its an ISP slowness issue :( but i'd still be interested to know if i was trying the correct way to set sysctl variables to turn off ipv6...

---

### Post by ronacc on 2009-01-02
entered bug# 313218 .

---

### Post by ccw on 2009-01-02
> **vishalrao said:**
> why do we suspect ipv6 is causing slowdown for some people? i also feel that since kernel .28 came in with ipv6 built-in my downloads from archives (main and mirrors) are slow. earlier korean and japanese mirrors were full speed for me.

is there some way to disable ipv6 for now? i know we should file bugs and help fix the issue rather than avoiding it, but for the time being. i've tried editing /etc/modprobe.d/aliases and also setting some sysctl variables (searched for all with disable_ipv6)... but ifconfig still lists ipv6 enabled and my downloads are still slow...

(im currently updating, want to try out kvm/virt-manager)

EDIT: nevermind, downloading package lists directly via firefox are slow for me even on intrepid and vista from main and mirror archives... so its an ISP slowness issue :( but i'd still be interested to know if i was trying the correct way to set sysctl variables to turn off ipv6...

alias net-pf-10 off

in /etc/modprobe.d/aliases works for me

---

### Post by ronacc on 2009-01-02
> **ccw said:**
> alias net-pf-10 off

in /etc/modprobe.d/aliases works for me

that worked PRIOR to 2.6.28-4 it no longer does due to ipv6 being built in and not a module .

---

### Post by vishalrao on 2009-01-02
right, thot that alias wouldnt work, nor blacklisting ipv6.

@shirish: saw your post to devel-discuss, now i dont belive it (ipv6) is affecting me, downloads on BSNL were going at full speed for me just now :) let me revert any alias/sysctl settings and check again...

---

### Post by ccw on 2009-01-02
> **ronacc said:**
> that worked PRIOR to 2.6.28-4 it no longer does due to ipv6 being built in and not a module .

Yeah, I see that now. ssh is listening in ipv6

---

### Post by ShirishAg75 on 2009-01-12
2.6.28-4.10 being uploaded.

There are no changelogs in jaunty-changes but can find the same on the source page. 

> 

linux (2.6.28-4.10) jaunty; urgency=low

  [ Andy Whitcroft ]

  * update kernel bootloader recommends: to prefer grub
    - LP: [#314004]("https://edge.launchpad.net/bugs/314004")
  * SAUCE: don't use buggy _BCL/_BCM/_BQC for backlight control
    - LP: [#311716]("https://edge.launchpad.net/bugs/311716")
  * SAUCE: test-suspend -- add the suspend test scripts
    - LP: [#316419]("https://edge.launchpad.net/bugs/316419")

  [ Colin Watson ]

  * Enable udebs for armel

  [ Tim Gardner ]

  * SAUCE: Dell laptop digital mic does not work, PCI 1028:0271
    - LP: [#309508]("https://edge.launchpad.net/bugs/309508")
  * Enable CIFS_XATTR=y and CONFIG_CIFS_POSIX=y
    - LP: [#220658]("https://edge.launchpad.net/bugs/220658")


[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

---

