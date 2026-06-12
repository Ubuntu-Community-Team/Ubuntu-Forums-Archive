---
title: "Plustek 9630P (parallel port scanner) worked in 5.10 / not working in 6.06"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by forlau on 2006-06-13
My scanner worked with Kubuntu 5.10 like a charm.

Now i installed Kubuntu 6.06 and i can't get it working. Its connected to the EPP parallel port as before.

I configured the well known files
[LIST]
[*]dll.conf to plustek_pp
[*]plustek_pp.conf file to device parport0
[/LIST]

**"lsmod |grep pp"**
```

ppdev                  9220  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc 
```

seems to me, that all needed modules are correctly loaded.

**"export SANE_DEBUG_DLL=20" **and **"sudo scanimage -L":**

```
[sanei_debug] Setting debug level of dll to 20.
[dll] sane_init: SANE dll backend version 1.0.11 from sane-backends 1.0.17
[dll] sane_init/read_dlld: processing /etc/sane.d/dll.d ...
[dll] sane_init/read_dlld: considering /etc/sane.d/dll.d/hplip
[dll] sane_init/read_config: reading dll.d/hplip
[dll] add_backend: adding backend `hpaio'
[dll] sane_init/read_dlld: done.
[dll] sane_init/read_config: reading dll.conf
[dll] add_backend: adding backend `plustek'
[dll] add_backend: adding backend `plustek_pp'
[dll] sane_get_devices
[dll] load: searching backend `plustek_pp' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-plustek_pp.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-plustek_pp.so.1'
[dll] init: initializing backend `plustek_pp' 
```

but nothing happens. Scanner is not scanning or making any noise.

**"ls -l /dev/parport0"**
```
crw-rw---- 1 root lp 99, 0 2006-06-03 10:17 /dev/parport0 
```

**"dmesg"** shows:

```
[ 1817.698050] ppdev0: registered pardevice
[ 1817.698245] ppdev0: unregistered pardevice
[ 1817.698692] ppdev0: registered pardevice
[ 1817.698962] ppdev0: unregistered pardevice
[ 1817.699044] ppdev0: registered pardevice
[ 1817.700298] ppdev0: unregistered pardevice
``` 

I don't know how to understand this pardevice message.

Any ideas?

Had anybody succes with (K)ubuntu and parallelport scanner?

What has changed from Kubuntu 5.10 regarding parallel port devices?

---

### Post by forlau on 2006-06-20
Solution:

It is necessary to enable apm and acpi!

in /boot/grub/menu.lst add **apm=on acpi=force** to the line that it looks like the following line:

```
kernel      /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda8 ro quiet splash vga=775 apm=on acpi=force
```

ACPI has to be enabled in BIOS and also parallel port set to EPP.

Maybe its enough to set **acpi=on**, depends on the machine.

---

### Post by skunkpit on 2006-06-22
iv been having the same issue
well probably a little worse

sudo modprobe plustek_pp
FATAL: Module plustek_pp not found.

---

### Post by forlau on 2006-06-23
@skunkpit
"sudo modprobe plustek_pp" cannot work, because its a not a module, its a Sane backend.

To see if all your needed modules are loaded try
```
sudo lsmod |grep pp
```

as i wrote in my first message.

Try also
```
export SANE_DEBUG_DLL=128
sudo scanimage -L
```

```
export SANE_DEBUG_PLUSTEK_PP=128
sudo scanimage -L
```

```
export SANE_DEBUG_SANEI_PP=128
sudo scanimage -L
```

Be sure that your ACPI is working.

---

### Post by skunkpit on 2006-06-24
forlau

cool thanks for reply

i tried seting kernel load option to force acpi

[dll] sane_get_devices: found 0 devices
scanimage: no SANE devices found

im suspecting my parallel port cable is damaged its pretty old like 10 years or so im going to get a more trust worthy one and try a bit more ill post again if i have any confusions

many thanks & greets

---

### Post by fabertawe on 2006-07-14
Hi folks,

I've been trying to get my parallel port Plustek OpticPro 4830P working for sometime now and I've tried everything I could find. I got it working (almost) as a '[direct]' device with the plustek_pp backend but only xscanimage recognised it as a device and then only as root. I say almost as it couldn't communicate with the scanner anyway.

So I thought I'd try compiling the module and using that. I changed plustek_pp.conf to use '[kernel]' and added pt_drv to '/etc/modules'. I've tried booting with 'apm=on acpi=force' added to the relevant '/boot/grub/menu.lst' entry and I've tried adding 
```
alias char-major-40 pt_drv
options  pt_drv  lampoff=180  warmup=15  port=0x378 lOffonEnd=0  mov=0 slowIO=1 forceMode=0
```
to '/etc/modprobe.conf'.

pt_drv is loading...
```
paul@ubuntu:~$ lsmod | grep pt_drv
pt_drv                126120  0
parport                43532  4 ppdev,pt_drv,lp,parport_pc
```

but is failing to open...
```
paul@ubuntu:~$ sudo scanimage -L
[sanei_debug] Setting debug level of plustek_pp to 128.
[sanei_debug] Setting debug level of sanei_pp to 128.
[sanei_pp] pp_init: called for the first time
[sanei_pp] pp_init: initializing libieee1284
[sanei_pp] pp_init: 1 ports reported by IEEE 1284 library
[sanei_pp] pp_init: port 0 is `parport0`
[sanei_pp] pp_init: initialized successfully
[sanei_pp] pp_calibrate_delay: Delay expected: 1000, real 1016, pp_thresh=0
[plustek_pp] PlustekPP backend V0.43-10, part of sane-backends 1.0.18
[plustek_pp] ># Plustek-PP SANE Backend configuration file<
[plustek_pp] ># For use with Plustek parallel-port scanners<
[plustek_pp] >#<
[plustek_pp] ><
[plustek_pp] >#<
[plustek_pp] ># user either [direct] or [kernel] to access the scanner<
[plustek_pp] ># when using [kernel], device specifies the device-node, which is created<
[plustek_pp] ># by the kernel-module loader (applies only to Linux)<
[plustek_pp] ># when using [direct], device is used to set the parallel-port base address<
[plustek_pp] ># or a device-name suitable for libieee1284, i.e. parport0<
[plustek_pp] >#<
[plustek_pp] >#[direct]<
[plustek_pp] >#device 0x378<
[plustek_pp] ><
[plustek_pp] >#<
[plustek_pp] ># example for accessing the scanner via libieee1284<
[plustek_pp] >#<
[plustek_pp] >#[direct]<
[plustek_pp] >#device parport0<
[plustek_pp] ><
[plustek_pp] >#<
[plustek_pp] ># leave the default values as specified in /etc/modules.conf<
[plustek_pp] >#<
[plustek_pp] >#option warmup    -1<
[plustek_pp] >#option lOffOnEnd -1<
[plustek_pp] >#option lampOff   -1<
[plustek_pp] ><
[plustek_pp] ># model override switch, mostly for cosmetic changes, if the autodetection<
[plustek_pp] ># does not work or could not work correctly<
[plustek_pp] >#option mov 7<
[plustek_pp] ><
[plustek_pp] >#<
[plustek_pp] ># example for accessing the scanner via the kernel module<
[plustek_pp] >#<
[plustek_pp] >[kernel]<
[plustek_pp] >device /dev/pt_drv<
[plustek_pp] Decoding device name >/dev/pt_drv<
[plustek_pp] >#<
[plustek_pp] >option warmup    -1<
[plustek_pp] Decoding option >warmup<
[plustek_pp] >option lOffOnEnd -1<
[plustek_pp] Decoding option >lOffOnEnd<
[plustek_pp] >option lampOff   -1<
[plustek_pp] Decoding option >lampOff<
[plustek_pp] attach (/dev/pt_drv, 0x7fffffaa12e0, (nil))
[plustek_pp] Device configuration:
[plustek_pp] device name   : >/dev/pt_drv<
[plustek_pp] direct I/O    : no
[plustek_pp] warmup        : -1s
[plustek_pp] lampOff       : -1
[plustek_pp] lampOffOnEnd  : yes
[plustek_pp] model override: 0
[plustek_pp] ---------------------
[plustek_pp] drvopen()
[plustek_pp] open: can't open /dev/pt_drv as a device
[plustek_pp] open failed: -1
[plustek_pp] sane_get_devices (0x7fffffaa33e0, 0)
device `v4l:/dev/video1' is a Noname OV511+ USB Camera virtual device
device `v4l:/dev/video0' is a Noname BT878 video (Pinnacle PCTV Stud virtual device
[plustek_pp] sane_exit
```

I would be immensely grateful if anyone has any suggestions as to my next course of action as this is driving me potty!

Cheers ... Paul

---

### Post by forlau on 2006-07-17
Same as you is tried before the pt_drv, but also with no success. I think its really the best to use the device parport0.

Maybe it helps to set the rights for parport0:
chmod 660 /dev/parport0
(I hope its the right syntax)

**Very important:**
If you comiled the backend by yourself, you maybe have to configure the files not in /etc/... but in /usr/...! See the sane homepage for more information.

---

### Post by fabertawe on 2006-07-17
> **forlau said:**
> Same as you is tried before the pt_drv, but also with no success. I think its really the best to use the device parport0.

Maybe it helps to set the rights for parport0:
chmod 660 /dev/parport0
(I hope its the right syntax)

**Very important:**
If you comiled the backend by yourself, you maybe have to configure the files not in /etc/... but in /usr/...! See the sane homepage for more information.

Thanks for replying forlau. I will go back to trying to get the backend working. I only compiled the module myself but may give the backend a go also.

Paul

---

