---
title: "funny boot in 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Pablo W on 2012-04-27
Hi, forum.
After running the beta for some time, I have just made a fresh install of the official release of Ubuntu 12.04. I installed from a usb drive.

Everything went well, except for the following issue at boot:
The first problem I had was that the PC would only boot if I had the usb plugged, even if prompted to start from the hard drive. 

I ran boot-repair and got the following:
[http://paste.ubuntu.com/950911](http://paste.ubuntu.com/950911)

The situation now is: I don't need to plug the usb stick at boot, but the boot process is very slow. It gives me a black screen a couple of times and then a get a menu page (reading "Debian, the Universal Operating System") for me to choose out of different boot options. I cannot find a way to ensure a smooth boot.

For the rest, Ubuntu 12.04 seems to be working fine.

I'll appreciate your help.

Cheers.

---

### Post by Rubi1200 on 2012-04-28
Hi,
please post the full specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by Pablo W on 2012-05-02
> **Rubi1200 said:**
> Hi,
please post the full specifications for the computer, especially RAM and graphics card.

Thanks.

Thanks for your answer, Rubi. And sorry for a late reply (the funny-boot PC is at the office and I only returned to work this morning).
Here is a list of the hardware

```
ruta H/W           Dispositivo  Clase          Descripción
===========================================================
                                system         HP Compaq dc7700 Small Form Facto
/0                              bus            0A54h
/0/1                            memory         128KiB BIOS
/0/5                            processor      Intel(R) Pentium(R) D CPU 3.00GHz
/0/5/7                          memory         28KiB L1 caché
/0/5/8                          memory         2MiB L2 caché
/0/5/0.1                        processor      CPU lógica
/0/5/0.2                        processor      CPU lógica
/0/6                            processor      CPU [vacío]
/0/37                           memory         Memoria de sistema
/0/37/0                         memory         512MiB DIMM DDR2 Síncrono 667 MH
/0/37/1                         memory         512MiB DIMM DDR2 Síncrono 667 MH
/0/37/2                         memory         1GiB DIMM DDR2 Síncrono 667 MHz 
/0/37/3                         memory         DIMM DDR2 Síncrono [vacío]
/0/38                           memory         Memoria flash
/0/38/0                         memory         1MiB Chip FLASH No volátil
/0/0                            processor      
/0/0/0.1                        processor      CPU lógica
/0/0/0.2                        processor      CPU lógica
/0/2                            memory         
/0/3                            memory         
/0/100                          bridge         82Q963/Q965 Memory Controller Hub
/0/100/2                        display        82Q963/Q965 Integrated Graphics C
/0/100/3                        communication  82Q963/Q965 HECI Controller
/0/100/19          eth0         network        82566DM Gigabit Network Connectio
/0/100/1a                       bus            82801H (ICH8 Family) USB UHCI Con
/0/100/1a.1                     bus            82801H (ICH8 Family) USB UHCI Con
/0/100/1a.7                     bus            82801H (ICH8 Family) USB2 EHCI Co
/0/100/1b                       multimedia     82801H (ICH8 Family) HD Audio Con
/0/100/1c                       bridge         82801H (ICH8 Family) PCI Express 
/0/100/1d                       bus            82801H (ICH8 Family) USB UHCI Con
/0/100/1d.1                     bus            82801H (ICH8 Family) USB UHCI Con
/0/100/1d.7                     bus            82801H (ICH8 Family) USB2 EHCI Co
/0/100/1e                       bridge         82801 PCI Bridge
/0/100/1e/9                     bus            USB
/0/100/1e/9.1                   bus            USB
/0/100/1e/9.2                   bus            USB 2.0
/0/100/1f                       bridge         82801HO (ICH8DO) LPC Interface Co
/0/100/1f.2        scsi0        storage        82801H (ICH8 Family) 4 port SATA 
/0/100/1f.2/0      /dev/sda     disk           80GB WDC WD800JD-60LS
/0/100/1f.2/0/1    /dev/sda1    volume         72GiB partición EXT4
/0/100/1f.2/0/2    /dev/sda2    volume         2022MiB Extended partition
/0/100/1f.2/0/2/5  /dev/sda5    volume         2022MiB Linux swap / Solaris part
/0/100/1f.2/1      /dev/cdrom   disk           COMBO SHC-48S7K
/1                 scsi3        storage  
``` 

Thanks,
Pablo.

---

### Post by Pablo W on 2012-05-02
In my previous post I forgot to include the following info on the graphic card. I hope this helps:
```

  *-display               
       descripción: VGA compatible controller
       producto: 82Q963/Q965 Integrated Graphics Controller
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       versión: 02
       anchura: 64 bits
       reloj: 33MHz
       capacidades: msi pm vga_controller bus_master cap_list rom
       configuración: driver=i915 latency=0
       recursos: irq:43 memoria:f0400000-f04fffff memoria:e0000000-efffffff ioport:1100(size=8)
pablo@pablo-HP-Compaq-dc7700-Small-Form-Factor:~$ 
```

Thanks.

---

### Post by Pablo W on 2012-05-04
Dear forum members,
I'm still trying to figure out how to sort this out. My Ubuntu-knowledge is pretty limited, though. Could anybody assist me with this question?
Thank you!

---

### Post by grahammechanical on 2012-05-04
Hi Pablo W

How many different operating systems do you have on this machine? Have you installed Debian?

Ubuntu is based on Debian but we do not usually see any reference to Debian in the Grub menu. No references to Ubuntu either. Just to Linux.

May I suggest that when you are in Ubuntu you run the command:

```
sudo update-grub
```

Then enter your password when asked to.

That command will refresh the Grub menu. That may improve things.

Regards.

---

### Post by Pablo W on 2012-05-04
> **grahammechanical said:**
> Hi Pablo W

How many different operating systems do you have on this machine? Have you installed Debian?

Ubuntu is based on Debian but we do not usually see any reference to Debian in the Grub menu. No references to Ubuntu either. Just to Linux.

May I suggest that when you are in Ubuntu you run the command:

```
sudo update-grub
```

Then enter your password when asked to.

That command will refresh the Grub menu. That may improve things.

Regards.

Thanks, Grahammechanical.

I have only the brand new Ubuntu 12.04 installed, no other operating systems. It is a fresh install from a USB drive. I had previously used 12.04 beta and, following the forum broad preference for fresh installs, I decided to install the official 12.04 LTS from scratch (which now I think was a mistake). The reference to Debian appeared after I install boot-repair (see post #1). 

Regarding the sudo update-grub command, this is the outcome:

```
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
pablo@pablo-HP-Compaq-dc7700-Small-Form-Factor:~$ 
```

Regards.

---

### Post by grahammechanical on 2012-05-04
Those messages seem normal to me.

There was a kernel update recently so you should have both the 3.2.0-23 and the 3.2.0-24 kernels and Grub should know about them. Keeping an older kernel is done so that if we have problems we can boot into the older kernel and get to a desktop.

You might what to consider this utiltity

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

I use Grub Customizer to keep control over the Grub menu.

As you only have one OS you should not see the Grub menu unless you press Shift during the first part of the boot process.

There is something that I do not understand. I see this:

> Found background image: /usr/share/images/desktop-base/desktop-grub.png

I have used Grub Customizer to set a background image to my Grub boot menu and it is found at /usr/share/images/grub

I do not have a /usr/share/images/desktop-base folder and I am using a 12.04 that I installed just a few hours ago.


Regards.

---

### Post by Pablo W on 2012-05-04
> **grahammechanical said:**
> Those messages seem normal to me.

There was a kernel update recently so you should have both the 3.2.0-23 and the 3.2.0-24 kernels and Grub should know about them. Keeping an older kernel is done so that if we have problems we can boot into the older kernel and get to a desktop.

You might what to consider this utiltity

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

I use Grub Customizer to keep control over the Grub menu.

As you only have one OS you should not see the Grub menu unless you press Shift during the first part of the boot process.

There is something that I do not understand. I see this:



I have used Grub Customizer to set a background image to my Grub boot menu and it is found at /usr/share/images/grub

I do not have a /usr/share/images/desktop-base folder and I am using a 12.04 that I installed just a few hours ago.


Regards.


Thanks, grahammechanical.
I've tried to install the Grub Customizer and I think I've made a mistake. I added the repositories as suggested in the thread you posted, but something went wrong. As a consequence, now I have an additional problem: Grub Customizer has not installed and the added lines to the repositories seem to be creating some trouble: I cannot make the software manager nor the updates manager work anymore. I have tried to delete the added repositories through nautilus (etc/apt/sources.list.d). Although I manage to find two files related to Grub Customizer, I get a message saying that I don't have the required permission to delete them (even though I am the only user and have administrator rights). Plus: I still get the funny-boot thing. Any clues?

---

### Post by Pablo W on 2012-05-04
Update: I managed to delete the faulty repositories through sudo nautilus. So the software manager is up and running again :)

I still face the situation described in post #1. I wonder if that could be fixed with grub-customizer. I have now correctly added its repositories. Nevertheless, I cannot find how to run grub-customizer, since it is not in the applications menu. I guess this is something very basic for the experts?
:confused:

---

### Post by Pablo W on 2012-05-07
HI again, forum.
I think I've found where the problem is. I went to a terminal and did

sudo fdisk -l

to see where my full install was. Since it was in sda, I did


sudo grub-install /dev/sda

and... look at the outcome: 

```
Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048   152158207    76078080   83  Linux
/dev/sda2       152160254   156301311     2070529    5  Extendida
/dev/sda5       152160256   156301311     2070528   82  Linux swap / Solaris
pablo@pablo-HP-Compaq-dc7700-Small-Form-Factor:~$ sudo grub-install /dev/sda
/usr/sbin/grub-setup: aviso: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

```

So it seems to me that the delayed boot comes from something related to Flexnet. This is as far as i could go. At this point, I cannot go further without expert advice. Is there any expert happy to lend a willing hand?

---

### Post by Pablo W on 2012-05-09
This issue was solved in a different thread. In case you are interested to see the details, please look at: [http://ubuntuforums.org/showthread.php?t=1976158](http://ubuntuforums.org/showthread.php?t=1976158)

Thanks.

---

