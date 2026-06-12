---
title: "Feisty upgrade; INIT_WORK error; ppscsi"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by annemarie on 2007-05-12
Dear Ubuntu users!

I've recently upgraded my Ubuntu to the latest Feisty version, using the Update Manager. All went well, but now I ran into problems while trying to make Xsane detect my parallel port HP scanner (Scanjet 5200C).

In Edgy, I had already installed the PPSCSI drivers, and managed to get Xsane to scan, but since the upgrade, Xsane doesn't anymore detect the scanner, so I tried to reinstall ppSCSI using the "module-assistant" lines found in this thread:

[http://ubuntuforums.org/showthread.php?t=29885&page=3](http://ubuntuforums.org/showthread.php?t=29885&page=3)

However, I run into the same problems as in the last post of that thread, i.e. "module-assistant build" stops with that "INIT_WORK undeclared" error.

Googling around, I see that so many users run into that error, while trying to install so many different applications, wireless devices, TV cards, scanners etc etc.

So I just wanted to know if someone is working on this, if anybody has an idea why this error occurs, and if there is any hope that the problem will be solved in the near future?

Thanks a lot!!

Anne-Marie

---

### Post by haydnc on 2007-06-02
I have managed to get ppscsi to work properly in feisty. I'm posting the full instructions I've typed up here for anyone else who stumbles across them. The individual parts of this all exist out there on the net, but I've not found anywhere that puts the whole lot together, so here goes:

**How to make a HP ScanJet 5100/5200C work with Ubuntu Feisty (Kernel 2.6.20)**

1. Make sure that you have the kernel headers installed: 

```
sudo apt-get install linux-headers-`uname -r`
```

2. Download the latest(?) version of ppscsi from [http://penguin-breeder.org/kernel/download/](http://penguin-breeder.org/kernel/download/) : ppscsi-beta2-20060424.tar.gz

3. Once downloaded extract the file:
tar zxvf ppscsi-beta2-20060424.tar.gz

This next bit is from translated instructions on the spanish Ubuntu website: 

> When extracted and running make we get two significant errors as per the above website:

… /ppscsi-beta2/ppscsi.h: 16: 26: error: linux/config.h: The directory file does not exist or

… /ppscsi-beta2/ppscsi.c: 1148: 39: error: macro “INIT_WORK” received 3 arguments, but it only took 2

Analysis:

The file linux/config.h this obsolete and macro “INIT_WORK” at the moment receives two arguments.

That is to say, the file config.h is replaced at the moment by the file autoconf.h

**Solution:**

4. Open ppscsi.h in the editing program of your choice. 
Change the where it says **#include <linux/config.h>** to read **#include <linux/autoconf.h>**
*This is on line 16 of the copy of ppscsi.h that I'm working with.*

5. Save and close ppscsi.h and open ppscsi.c

Change the following lines:
**static void ppsc_tq_int (void *data) **
change to 
**static void ppsc_tq_int (struct work_struct *data)**
*(Note: This is line 191 in the copy of ppscsi.c I'm working with)*
[B]
INIT_WORK (&pha->wq, ppsc_tq_int, pha);[/B]
change to
**INIT_WORK (&pha->wq, ppsc_tq_int);**
*(Note: This is line 1148 in the copy of ppscsi.c I'm working with)*

6. Save and close ppscsi.c and run make. This should produce a set of .ko files, including the all important (to us anyway) ppscsi.ko and epst.ko.

7. Since the Makefile for ppscsi has no instructions for installing these files we need to copy them to their new location manually:
```
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
```

8. Next we need to tell the kernel that they exist:
```
sudo depmod
```

9. Lastly we need to load the modules:
```
sudo modprobe ppscsi
sudo modprobe epst
```

This will make the scanner useable until next time the computer is rebooted. 

In order to make sure that the scanner is recognised from the moment you boot up it is necessary to edit **/etc/modules** and add the following two lines to the end of the file:
```
ppscsi
epst

```

My apologies if this seems a little cluttered, but hopefully it should work as well for you as it did for me.

---

### Post by Garyu on 2007-06-12
Thank you so much for posting this. Saved me quite some time to go back to the Dapper thread and figure things out again. This solution was very smooth too. And directions easy to follow. Great job! :D

---

### Post by CheeseEatingBulldog on 2007-07-22
I can't get the epst.ko to insert. it gives :

root@ifrit:~# sudo modprobe epst
FATAL: Error inserting epst (/lib/modules/2.6.20-16-generic/kernel/drivers/parport/epst.ko): No such device

I have tried changing bios options (EPP) and a got dmesg:

root@ifrit:~# dmesg | grep par
[   52.918266] Booting paravirtualized kernel on bare hardware
[   31.616000] parport: PnPBIOS parport detected.
[   31.616000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   32.908000] lp0: using parport0 (interrupt-driven).
[   47.920000] ppdev: user-space parallel port driver
[  100.768000] ppdev0: registered pardevice
[  100.816000] ppdev0: unregistered pardevice

Why won't it insert the kernel module?

---

### Post by Labyrinth on 2007-08-19
Hello!

I have exactly the same problem, as CheeseEatingBulldog.

The lines:

 ppdev0: registered pardevice
 ppdev0: unregistered pardevice

repeat many times in dmesg.

Greetings,
Labyrinth

---

### Post by stevenwscott on 2008-01-31
TO haydnc:

      Bless you, kind sir!  I've been looking for a working ppscsi since 2.4.........

SWS

---

