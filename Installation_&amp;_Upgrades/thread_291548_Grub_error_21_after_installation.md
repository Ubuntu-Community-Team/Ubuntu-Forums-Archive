---
title: "Grub error 21 after installation"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by rasmus_olsen on 2006-11-02
After a successful an easy installation, on a ASUS P5B motherboard with a jmicron PATA controller, I get a grub error 21 when i try to boot the system. I installed Ubuntu on my IDE harddisk and have windows installed on a SATA disk. I have tried to install grub to the MBR of both the IDE and SATA disk with out luck.

I tried to install grub on a usb-key and boot from that, but from the grub command line I can only find the usb-key which is mapped to hd0. When i try to map the disks i get error 15 and error 17.

Is there another way to boot the system?

---

### Post by bulldog on 2006-11-02
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system

Try to install Grub from the live cd on your boot disk [ubuntu]
Then you have to map your windows entry.
```
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


[code]sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.
[/code]

---

### Post by kapono12 on 2006-11-05
I have the same motherboard, I have the same problem.  Installing grub manually does nothing, you will get the error 21 on reboot.  Happens with Fedora Core 6 and my openSuSE 10.1 cannot find itself to install with the way the motherboard handles ide(jmicron).  I believe the problem lies there and if I had an extra sata hard drive I could tell you, but alas, im running a raid on my windows install with my only two sata drives(yes I need the windows partition because I have data I need to get off of there, yet I changed motherboards and now windows locks me out due to the "key being invalid" ](*,) ). Little frustrating..

---

