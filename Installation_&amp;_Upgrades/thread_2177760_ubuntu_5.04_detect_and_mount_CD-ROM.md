---
title: "ubuntu 5.04 detect and mount CD-ROM"
date: 2013-09-30
forum: Installation &amp; Upgrades
---

### Post by daiyue2 on 2013-09-30
Hi, all, I am completely new to Ubuntu/Linux, and I tried to install Ubuntu 5.04 on my PC. I use VMware player on win7 pro x64, and insert the burned installation CD into my DVD drive. Now I stuck in the step for detect and mount CD-ROM. It gave me a list of modules: 

[COLOR=#000000]none[/COLOR]
[COLOR=#000000]aztcd[/COLOR]
[COLOR=#000000]cdrom[/COLOR]
[COLOR=#000000]cdu31a[/COLOR]
[COLOR=#000000]cm206[/COLOR]
[COLOR=#000000]gscd[/COLOR]
[COLOR=#000000]mcd[/COLOR]
[COLOR=#000000]mcdx[/COLOR]
[COLOR=#000000]optcd[/COLOR]
[COLOR=#000000]sbpcd[/COLOR]
[COLOR=#000000]sjcd[/COLOR]
[COLOR=#000000]sonycd535[/COLOR]

I also know that 5.04 is an old version of Ubuntu, it probably can not recognize SATA port, and I need to use the old gcc compiler there, that is why I want to install it. So anyone has any idea how to get around this issue?

cheers

---

### Post by Kirboosy on 2013-09-30
Welcome to the forums!

Rather than using a CD to install it you  could mount the ISO directly to the VM. This would also allow it to  install faster since it would be reading off the hard drive

[How to mount an ISO on VMWare Player]("http://linhost.info/2009/09/how-to-mount-an-iso-on-vmware-player/")

What version of GCC do you need?

~Caboose

---

### Post by sudodus on 2013-09-30
Welcome :-)

Ubuntu 5.04 passed end of life many years ago (October 2006). Please try an current version of Ubuntu!

I would recommend 12.04 LTS (long time support), and do not limit your choice to the standard Ubuntu version, try also Lubuntu, Xubuntu and Kubuntu, that have the same engine under the hood but different desktop environments (what it looks and feels like).

  ```

[SIZE=3]light

[B][FONT=courier new]^ Lubuntu |
| Xubuntu |
| Ubuntu  |
| Kubuntu v

          [/FONT][/B]fancy[/SIZE]

```

*Edit*: If you really want 5.04, try it in old hardware or an old version of a virtual machine.

---

### Post by Bucky Ball on 2013-09-30
> **sudodus said:**
> 

Ubuntu 5.04 passed end of life many years ago (October 2006). Please try an current version of Ubuntu!



Welcome.

5.04, don't go there. Not sure where you even found an ISO of it. We can't give you support with that as there's none to give. 

12.04 LTS is the current, stable long-term support release, supported until April 2017.

---

### Post by daiyue2 on 2013-09-30
> **Caboose885 said:**
> 

Rather than using a CD to install it you  could mount the ISO directly to the VM. This would also allow it to  install faster since it would be reading off the hard drive

[How to mount an ISO on VMWare Player]("http://linhost.info/2009/09/how-to-mount-an-iso-on-vmware-player/")

What version of GCC do you need?



Thx for reply, I have tried both ways (mount iso and installation CD), but ended up with the same results. I need gcc 2.95/3.3/3.4, so any idea how to get them work on windows platform (I did try cygwin, but with no luck, coz the gcc packages won't even be built)? like if I install 12.04 LTS instead of 5.04 using VMware, can I get the above gcc packages installed, and how to install them if the information is available.

cheers

---

### Post by Kirboosy on 2013-09-30
> **Bucky Ball said:**
> 5.04, don't go there. Not sure where you even found an ISO of it.7.

[Old Ubuntu Releases]("http://old-releases.ubuntu.com/releases/")

Yay for legacy!


> Thx for reply, I have tried both ways (mount iso and installation CD),  but ended up with the same results. I need gcc 2.95/3.3/3.4, so any idea  how to get them work on windows platform (I did try cygwin, but with no  luck, coz the gcc packages won't even be built)? like if I install  12.04 LTS instead of 5.04 using VMware, can I get the above gcc packages  installed, and how to install them if the information is available.

cheers 

Actually it looks like you can. I'm not sure if this PPA still works but you could try it.

[Old version of GCC for Newer Ubuntu]("http://askubuntu.com/questions/39628/old-version-of-gcc-for-new-ubuntu")

Alternatively you could find the source tar of the version you need and compile it. 

Hope that helps!
~Caboose
PS The PPA above and compiling tip is for newer versions of Ubuntu.

---

### Post by Bucky Ball on 2013-09-30
Not sure for what reason you are wanting to use 5.04 but if there isn't a specific one, you are going on a bit of a wild goose chase and wasting time. Ubuntu has come a looooong way in eight years. I doubt anyone (apart from Caboose885 and perhaps a few others) will have any idea of how to help with any issues you come up with. 

Bit like reinventing the wheel.

---

### Post by daiyue2 on 2013-09-30
> **Bucky Ball said:**
> Not sure for what reason you are wanting to use 5.04 but if there isn't a specific one, you are going on a bit of a wild goose chase and wasting time. Ubuntu has come a looooong way in eight years. I doubt anyone (apart from Caboose885 and perhaps a few others) will have any idea of how to help with any issues you come up with. 

Bit like reinventing the wheel.


Hi, I am trying Caboose's method now, but I need sometime to familiar with Ubuntu/Linux first, coz as been said I am really new to Linux, and don't know how to install software in general in Ubuntu. I am checking the commands/terms: su/sudo/apt etc. I hope there is a complete tutorial on how to install software in terms of both command mode and UI mode.

cheers

---

### Post by QIII on 2013-09-30
Hello!

You are more likely to become familiar with Linux using a supported version rather than spending much of your tme trying to track down unsupported, deprecated or discontinued components.

You would also avoid the risk of serious security problems.

---

### Post by Bucky Ball on 2013-10-01
You are not going to become familiar with Ubuntu using 5.04. It has changed radically. Like QIII says, use a supported release. 5.04 is ancient and we will not be able to help you with it (and like I said, no idea where you even found the ISO for it).

---

