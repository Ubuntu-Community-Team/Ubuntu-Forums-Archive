---
title: "too fast fan speed, and no ATI temp detected"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xmflsct on 2010-03-18
hi all,

i am running Ubuntu 10.04 on my HP dv6-1122tx laptop. i have tried hard to make lm-sensors work, and it can detect now the temperature of my hard disk and CPU. BUT lm-sensors couldn't find my ATI diode temperature sensor. any idea how to fix it? i am using ATI Mobility HD 4650.

and, the average temp of CPU is around 65 Celsius, and the temp of hard disk is around 50 Celsius, which are the SAME as in the WIndows platform. BUT the fan runs much faster than in the Windows platform. any idea how i can deal with this?

thanks a lot for your attention!! :popcorn:

---

### Post by donfilipo on 2010-04-13
> **xmflsct said:**
> hi all,

i am running Ubuntu 10.04 on my HP dv6-1122tx laptop. i have tried hard to make lm-sensors work, and it can detect now the temperature of my hard disk and CPU. BUT lm-sensors couldn't find my ATI diode temperature sensor. any idea how to fix it? i am using ATI Mobility HD 4650.

and, the average temp of CPU is around 65 Celsius, and the temp of hard disk is around 50 Celsius, which are the SAME as in the WIndows platform. BUT the fan runs much faster than in the Windows platform. any idea how i can deal with this?

thanks a lot for your attention!! :popcorn:

Same Here... my comp always starts with high revs (fan) and after it's in OS (Windows 7, or Ubuntu 9.10) it lowers the revs on fans and runs quieter. Not so in ubuntu 10.04. Seems to me, cause i have a completely different machine it's a major fault. I tried with 'thinkfan' but it stays the same. It seems to me, the 10.04 just do not recognizes the temperatures on machine, so it leaves running the fans on max....and that is somehow disturbing....believe me. Nobody likes to here his comp ventilating for nothing:(

---

### Post by TrueJournals on 2010-04-13
Are you using the proprietary ATI driver (fglrx)?  The open-source ATI video driver doesn't have support for power saving on the graphics card, so the fan will run full-speed all the time...

---

### Post by dino99 on 2010-04-13
you need to run : sudo sensors-detect then tweak the conf file to add these sensors

---

### Post by donfilipo on 2010-04-20
> **dino99 said:**
> you need to run : sudo sensors-detect then tweak the conf file to add these sensors

Well i did that:) No change at all. And i forgot to tell i don't have ATI graphics. It's NVIDIA. To be clear:
-some have an option of somekind of a smart fan BIOS 
-i  do not....and i am sure i am not the only one:)
-when computer starts, fans are running on max rev
-when computer comes to login screen (example 9.04 or 9.10) it's fan revs drop, and the machine run's reasonably quiet...until you put some difficult task on it, and it starts gaining on temperature. That means: the sensors are communicating trough some kind of logic in OS with fans. In Ubuntu 9.04 and also 9.10.
-not so in 10.04 beta 2 (updated). The fans are on max rev all the time..and machine is too loud....that alone makes impression of it somehow suffering:) I knopw it's silly...but believe that kind of bug is truelly annoying
-i have tried averything i could find. Detect sensors? It detects them, but does not imply the 'logic of OS with fans'

---

### Post by BrokeMahPC on 2010-04-20
OK, this is what I know so far.......
There is a problem with the open source driver for ATI that installs by default with 10.04 that makes the newer HD Radeon graphics cards run hot, therefore the fans whirl like crazy and the system crashes. A bug has been reported and they are looking at it but the advice is you must use the ATI proprietary FGLRX driver. This has worked in my case with a desktop machine and ATI Radeon HD4670.
Activate the driver with System->Admin.->Hardware Drivers
then run:
```
sudo aticonfig --initial -f
```to configure the driver in xorg

To get a specific ATI Temperature run:
```
aticonfig --odgt
```which should give you something like this:

> Default Adapter - ATI Radeon HD 4600 Series
                  Sensor 0: Temperature - 32.50 C(I found this on the web but type the following to see the options in  the help file: 
```
aticonfig -h
```lm-sensors (should be installed by default, if not use synaptic to get it)
then run:
```
sudo sensors-detect
```and answer yes to every question.
Then REBOOT

To get the temperatures run:
```
sensors
```which gives me:
> atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.12 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:      +3.33 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.14 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.15 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     2057 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:1117 RPM  (min =  600 RPM)
POWER FAN Speed:   1140 RPM  (min =  600 RPM)
CPU Temperature:    +19.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:     +31.0°C  (high = +45.0°C, crit = +95.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +76.0°C, crit = +100.0°C)  You can make extra additions to the /etc/modules file but I have no experience of that.
Anyone know a better way of accessing this data? I tried installing computertemp from synaptic but I need to get some updates before it will run.

---

### Post by dino99 on 2010-04-20
> **donfilipo said:**
>  And i forgot to tell i don't have ATI graphics. It's NVIDIA. T


So change the title if you want usefull answers

---

### Post by andrek on 2010-04-20
He's not the OP. This thread is 4 weeks old.

---

### Post by BrokeMahPC on 2010-04-20
I'm answering the original question thoroughly as no one has - if you would like info on Nvidia (sorry can't help - I'm an ATI man) - start a new thread?

---

### Post by Sepiraph on 2010-04-25
> **BrokeMahPC said:**
> You can make extra additions to the /etc/modules file but I have no experience of that.
Anyone know a better way of accessing this data? I tried installing computertemp from synaptic but I need to get some updates before it will run.

Well what you can do is just add the driver name manually in the /etc/modules file at the end.  I have to do this since for some bizarre reason it couldn't detect my i7 930 ... so I just added (driver name) at the end:
coretemp   

You can see the supported driver list on [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

---

### Post by Sepiraph on 2010-04-25
> **BrokeMahPC said:**
> I'm answering the original question thoroughly as no one has - if you would like info on Nvidia (sorry can't help - I'm an ATI man) - start a new thread?

Hey can you post the result of cat /etc/modules

Since you are running the ATI it will narrow down the possible ATI driver. :)

---

### Post by BrokeMahPC on 2010-04-25
```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Tue Apr 20 09:27:15 2010
# Chip drivers
coretemp
w83627ehf
```

lmdetect drivers: [http://dl.lm-sensors.org/lm-sensors/files/sensors-detect](http://dl.lm-sensors.org/lm-sensors/files/sensors-detect)
Drivers in use are:[FONT=monospace]
[/FONT]"Intel Core family thermal sensor",[FONT=monospace]
[/FONT]driver => "coretemp",[FONT=monospace]
[/FONT]detect => sub { coretemp_detect(0); },
[FONT=monospace]
[/FONT]"Winbond W83627EHF",
driver => "use-isa-instead",[FONT=monospace]
[/FONT]i2c_addrs => [0x28..0x2f],[FONT=monospace]
[/FONT]i2c_detect => sub { w83781d_detect(@_, 9); },

---

### Post by andrewthomas on 2010-04-25
If you want the sensors-applet to detect your GPU temp then you need to compile it yourself. 
The latest sensors-applet from sourceforge

[http://sensors-applet.sourceforge.net/index.php?content=source](http://sensors-applet.sourceforge.net/index.php?content=source)

Make sure that you have the development files for lm-sensors from synaptic before compiling.

---

### Post by BrokeMahPC on 2010-04-25
Had a go and compiled it - screenshots of it working in fglrx - now to try radeon!

---

