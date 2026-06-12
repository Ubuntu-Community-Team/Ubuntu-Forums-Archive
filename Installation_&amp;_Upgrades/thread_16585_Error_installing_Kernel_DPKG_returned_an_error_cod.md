---
title: "Error installing Kernel DPKG returned an error code (1)"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by Robban59 on 2005-02-22
Hi everybody !

first post in the Ubuntu world unfortunately asking for help in order to be able to install Warty on my PC; I downloaded Warty and yes checked the MD then burned the CD with NERO.

Been using for 15 years DOS & Windows, now I long sooo much to try out Ubuntu, did I mention I'm a complete total newbie in Linux ?? 

My system : P4 2.4 GHz  1 GB RAM DDR  ABIT IT7 MAX 2 v.2  Geforce TI4200 2x60GB RAID-0 1x80GB SATA LiteOn LTR 48125S ( CD writer)  Pioneer 106-R (DVD writer) 

What happens is that during the Base Install phase, at around 87% the installation stops with a red screen beaming an error message : 

 An error was returned while trying to install the Kernel into the target system  
 Kernel package " Linux-386 "
 E: sub-process /usr/bin/dpkg returned an error code (1)

Switching to Alt-F3 I can read the following : 

Errors were encountered while processing : 
Linux-image-2.6.8.1-3-386
Linux-image-2.6-386
Linux-image-386
Linux-restricted-modules-2.6.8.1-3-386
Linux-restricted-modules-2.6-386
Linux-restricted-modules-386
Linux-386

Dependency problems - leaving unconfigured 

-User notice  base-installer: error : exiting on error
                     base-installer/kernel/failed-install

Got the installation logs written to floppy if they are needed.

What I tried, nothing worked :

0) Searched Ubuntu Installation Help forum :  didn't find similar problem 
1) Unplugged all UBS devices before booting the Ubuntu CD
2) Booting in expert mode and specified HDPARAM -E4 ( read somewhere it could help..) 
3) Booted with : linux pci=noapci  ( read somewhere...)
4) Booted with : linux noapic nolapic ( read somewhere...)

Have not tried yet :

1) Set BIOS HD parameters to LBA from AUTO ( read somewhere...)

Well gentlemen now I'm just going to make myself a drink and wait for a kind Ubuntu soul to start firing at me questions and suggestions that hopefully will help me turn into a happy Ubuntu user !

Have a nice day you all !

---

### Post by tkiesel on 2005-02-22
> **Robban59]Hi everybody !

first post in the Ubuntu world unfortunately asking for help in order to be able to install Warty on my PC said:**
> 

One thing I learned to do is to then rip an ISO image from the disk I've burned and check the MD5 of that.  That's an even further guarantee that the disc you've burned is perfect.  :) It took me several tries. In the end, I had four disks that were fit for coasters before I perfected my method.

[QUOTE=Robban59]Been using for 15 years DOS & Windows, now I long sooo much to try out Ubuntu, did I mention I'm a complete total newbie in Linux ?? 

I'm a complete and total newbie too. Just installed Ubuntu about two weeks ago, and I'm already to the point where booting back to Windows is a rare, non-daily occurance.   :grin: 

I don't have any other expertise to offer, just general support. Hang in there! You'll love this OS!

take care,
-T

---

### Post by Robban59 on 2005-02-23
Thanks Tkiesel,

I'll check again the MD of the ripped ISO from my burned Warty CD, it is a good tip !

Have a nice day/Rgds

---

### Post by Robban59 on 2005-02-23
Hi again everybody,

I checked again the  quality of the CD I burned with Warty : I recreated an ISO file with UltraISO and checked it with the MD code listed in the Ubuntu download section, and it matches OK !

So what I'm trying to install from my CD is OK !

Any other suggestions for my problem ??

Thnaks again in advance for any help..

---

### Post by sanjal on 2005-02-27
Hi!
I think for P-4 it is better to use kernels with SMP support+hyper threading. Therefore try with linux-686 <- 686 for P4. (of course there will be issues with APIC/ACPI and hotplugging.. 5 minutes of googling will help)

In my case my machine is rather old so I use linux-386 kernel
PII 300Mhz 90MB 32Gb

And I have the same problem with unresolved dependencies. The apt-get cries on
#apt-get install linux-386

and the output is the same as yours.
Something to do with unconfigured 
linux-modules-restricted-2.6.8
linux-modules-restricted-386
... dpkg error code (1)

Did anyone find the solution yet??? ](*,)

---

### Post by johnwind on 2005-03-03
Reading Package Lists... Done
Building Dependency Tree... Done
linux-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.8.1-5-686 (2.6.8.1-16.11) ...
mkcramfs: ROM image write failed (wrote 2195456 of 4464640 bytes): No space left on device?
Failed to create initrd image.
dpkg: error processing linux-image-2.6.8.1-5-686 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-2.6-686:
 linux-image-2.6-686 depends on linux-image-2.6.8.1-5-686; however:
  Package linux-image-2.6.8.1-5-686 is not configured yet.
dpkg: error processing linux-image-2.6-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-686:
 linux-image-686 depends on linux-image-2.6-686; however:
  Package linux-image-2.6-686 is not configured yet.
dpkg: error processing linux-image-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.8.1-5-686:
 linux-restricted-modules-2.6.8.1-5-686 depends on linux-image-2.6.8.1-5-686; however:
  Package linux-image-2.6.8.1-5-686 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.8.1-5-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6-686:
 linux-restricted-modules-2.6-686 depends on linux-restricted-modules-2.6.8.1-5-686; however:
  Package linux-restricted-modules-2.6.8.1-5-686 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-686:
 linux-restricted-modules-686 depends on linux-restricted-modules-2.6-686; however:
  Package linux-restricted-modules-2.6-686 is not configured yet.
dpkg: error processing linux-restricted-modules-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-686:
 linux-686 depends on linux-image-686; however:
  Package linux-image-686 is not configured yet.
 linux-686 depends on linux-restricted-modules-686; however:
  Package linux-restricted-modules-686 is not configured yet.
dpkg: error processing linux-686 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.8.1-5-686
 linux-image-2.6-686
 linux-image-686
 linux-restricted-modules-2.6.8.1-5-686
 linux-restricted-modules-2.6-686
 linux-restricted-modules-686
 linux-686
E: Sub-process /usr/bin/dpkg returned an error code (1)

Same thing i got here......any idea how to fix it ?  :confused:

---

### Post by az on 2005-03-03
"mkcramfs: ROM image write failed (wrote 2195456 of 4464640 bytes): No space left on device?"

Did you run out of disk space? How big did you make your partition?

try
sudo apt-get update
sudo apt-get -f install

---

### Post by cargo on 2005-03-05
Same problem while installing Ubuntu from CD:
```

An error was returned while trying to install the Kernel into the target system 
Kernel package " Linux-386 "
E: sub-process /usr/bin/dpkg returned an error code (1)

```

earlier also got messages about missing modules ide-***

ISO was downloaded a couple of days ago...

BTW after trying to install Ubuntu my WinXP partition appeared totally broken  #-o 

any suggestions?  :confused:

**hoary array 6 installed ok :D**

---

