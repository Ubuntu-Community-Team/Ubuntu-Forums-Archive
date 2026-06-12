---
title: "Ubuntu 13.10 - no wifi after thawing from hibernation"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by Lammis on 2013-10-24
I now run Ubuntu 13.10 and latest updates on my HP EliteBook 6930p and it works just fine except for one thing. Each time my computer goes into hibernation it looses the ability to connect to my WiFi. After thawing I have to go through a complete reboot to make it work again. Does anyone have a solution for this glitch?

After running the ”sudo lshw -C network ”command in a terminal window I get the following information (sorry for the occasional Swedish):


   *-network INAKTIVERAD    
        beskrivning: Ethernet interface  
        produkt: 82567LM Gigabit Network Connection  
        tillverkare: Intel Corporation  

        physical id: 19  
        bus info: pci@0000:00:19.0  
        logiskt namn: eth0  
        version: 03  
        serienummer: 00:21:5a:f7:46:c4  
        kapacitet: 1Gbit/s  
        bredd: 32 bits  
        klocka: 33MHz  
        förmågor: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation  
        konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair  
        resurser: irq:47 memory:d8400000-d841ffff memory:d8424000-d8424fff ioport:80e0(storlek=32)  
   *-network INAKTIVERAD  
        beskrivning: Trådlöst gränssnitt  

        produkt: Ultimate N WiFi Link 5300  
        tillverkare: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logiskt namn: wlan0  
        version: 00  
        serienummer: 00:21:6a:09:8d:a4  
        bredd: 64 bits  
        klocka: 33MHz  
        förmågor: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        konfiguration: broadcast=yes driver=iwlwifi driverversion=3.11.0-12-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn  
        resurser: irq:48 memory:d8100000-d8101fff

---

### Post by Toz on 2013-10-24
With root privledges, try creating the file **/etc/pm/config.d/modules** with the following content:
```
SUSPEND_MODULES="iwlwifi"
```
...save the file and give it a try.

If it doesn't work, post back the contents of the file **/var/log/pm-suspend.log** and the results of:
```
cat /var/log/syslog | grep PM:
```

---

### Post by Lammis on 2013-10-24
Is the file named "modules" without any extension or did you forget to mention the filename?

---

### Post by Toz on 2013-10-24
The filename is "modules" without an extension.

---

### Post by Lammis on 2013-10-24
You have to excuse me but I am a rookie... I am not able to create such a file in that directory. How do I do it?

---

### Post by Lammis on 2013-10-24
I got it...
I had to type "sudo su" not just "su". I have created the modules file and am now trying out if it works.

---

### Post by Lammis on 2013-10-24
This is the result of cat /var/log/syslog | grep PM:
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000eefff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000ef000-0x000fffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae4c000-0xbae4dfff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbbc70000-0xbbc7ffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbe3d8000-0xbe5d7fff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfd93000-0xbfd9afff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfdbf000-0xbfdcefff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfdcf000-0xbfecefff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfecf000-0xbfefefff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xbfffffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffe7ffff]
Oct 24 13:25:40 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe80000-0xffffffff]
Oct 24 13:25:40 Xorbus kernel: [    0.084389] PM: Registering ACPI NVS region [mem 0xbbc70000-0xbbc7ffff] (65536 bytes)
Oct 24 13:25:40 Xorbus kernel: [    0.084389] PM: Registering ACPI NVS region [mem 0xbe3d8000-0xbe5d7fff] (2097152 bytes)
Oct 24 13:25:40 Xorbus kernel: [    0.084389] PM: Registering ACPI NVS region [mem 0xbfdcf000-0xbfecefff] (1048576 bytes)
Oct 24 13:25:40 Xorbus kernel: [    0.873945] PM: Hibernation image not present or could not be loaded.
Oct 24 16:03:33 Xorbus kernel: [ 9493.668071] PM: Syncing filesystems ... done.
Oct 24 16:03:33 Xorbus kernel: [ 9493.822870] PM: Preparing system for mem sleep
Oct 24 16:10:26 Xorbus kernel: [ 9494.144253] PM: Entering mem sleep
Oct 24 16:10:26 Xorbus kernel: [ 9495.788064] PM: suspend of devices complete after 1643.244 msecs
Oct 24 16:10:26 Xorbus kernel: [ 9495.788480] PM: late suspend of devices complete after 0.413 msecs
Oct 24 16:10:26 Xorbus kernel: [ 9495.868061] PM: noirq suspend of devices complete after 79.579 msecs
Oct 24 16:10:26 Xorbus kernel: [ 9495.876166] PM: Saving platform NVS memory
Oct 24 16:10:26 Xorbus kernel: [ 9495.988316] PM: Restoring platform NVS memory
Oct 24 16:10:26 Xorbus kernel: [ 9496.928056] PM: noirq resume of devices complete after 889.939 msecs
Oct 24 16:10:26 Xorbus kernel: [ 9496.928211] PM: early resume of devices complete after 0.121 msecs
Oct 24 16:10:26 Xorbus kernel: [ 9497.019179] PM: Device PNP0C0B:00 failed to resume: error -19
Oct 24 16:10:26 Xorbus kernel: [ 9507.144133] PM: resume of devices complete after 10215.918 msecs
Oct 24 16:10:26 Xorbus kernel: [ 9507.144568] PM: Finishing wakeup.
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000eefff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000ef000-0x000fffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae4c000-0xbae4dfff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbbc70000-0xbbc7ffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbe3d8000-0xbe5d7fff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfd93000-0xbfd9afff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfdbf000-0xbfdcefff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfdcf000-0xbfecefff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfecf000-0xbfefefff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xbfffffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffe7ffff]
Oct 24 16:11:33 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe80000-0xffffffff]
Oct 24 16:11:33 Xorbus kernel: [    0.084388] PM: Registering ACPI NVS region [mem 0xbbc70000-0xbbc7ffff] (65536 bytes)
Oct 24 16:11:33 Xorbus kernel: [    0.084388] PM: Registering ACPI NVS region [mem 0xbe3d8000-0xbe5d7fff] (2097152 bytes)
Oct 24 16:11:33 Xorbus kernel: [    0.084388] PM: Registering ACPI NVS region [mem 0xbfdcf000-0xbfecefff] (1048576 bytes)
Oct 24 16:11:33 Xorbus kernel: [    0.874080] PM: Hibernation image not present or could not be loaded.
Oct 24 19:16:49 Xorbus kernel: [11136.367583] PM: Syncing filesystems ... done.
Oct 24 19:16:49 Xorbus kernel: [11136.692875] PM: Preparing system for mem sleep
Oct 24 19:17:46 Xorbus kernel: [11137.007573] PM: Entering mem sleep
Oct 24 19:17:46 Xorbus kernel: [11138.548261] PM: suspend of devices complete after 1540.118 msecs
Oct 24 19:17:46 Xorbus kernel: [11138.548687] PM: late suspend of devices complete after 0.423 msecs
Oct 24 19:17:46 Xorbus kernel: [11138.612062] PM: noirq suspend of devices complete after 63.373 msecs
Oct 24 19:17:46 Xorbus kernel: [11138.620155] PM: Saving platform NVS memory
Oct 24 19:17:46 Xorbus kernel: [11138.732318] PM: Restoring platform NVS memory
Oct 24 19:17:46 Xorbus kernel: [11139.656060] PM: noirq resume of devices complete after 874.255 msecs
Oct 24 19:17:46 Xorbus kernel: [11139.656214] PM: early resume of devices complete after 0.121 msecs
Oct 24 19:17:46 Xorbus kernel: [11139.748976] PM: Device PNP0C0B:00 failed to resume: error -19
Oct 24 19:17:46 Xorbus kernel: [11149.844100] PM: resume of devices complete after 10187.883 msecs
Oct 24 19:17:46 Xorbus kernel: [11149.844531] PM: Finishing wakeup.
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000eefff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000ef000-0x000fffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae4c000-0xbae4dfff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbbc70000-0xbbc7ffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbe3d8000-0xbe5d7fff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfd93000-0xbfd9afff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfdbf000-0xbfdcefff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfdcf000-0xbfecefff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfecf000-0xbfefefff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xbfffffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffe7ffff]
Oct 24 19:25:13 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe80000-0xffffffff]
Oct 24 19:25:13 Xorbus kernel: [    0.084390] PM: Registering ACPI NVS region [mem 0xbbc70000-0xbbc7ffff] (65536 bytes)
Oct 24 19:25:13 Xorbus kernel: [    0.084390] PM: Registering ACPI NVS region [mem 0xbe3d8000-0xbe5d7fff] (2097152 bytes)
Oct 24 19:25:13 Xorbus kernel: [    0.084390] PM: Registering ACPI NVS region [mem 0xbfdcf000-0xbfecefff] (1048576 bytes)
Oct 24 19:25:13 Xorbus kernel: [    0.874037] PM: Hibernation image not present or could not be loaded.
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000eefff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000ef000-0x000fffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae4c000-0xbae4dfff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbbc70000-0xbbc7ffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbe3d8000-0xbe5d7fff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfd93000-0xbfd9afff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfdbf000-0xbfdcefff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfdcf000-0xbfecefff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfecf000-0xbfefefff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xbfffffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffe7ffff]
Oct 24 19:35:30 Xorbus kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe80000-0xffffffff]
Oct 24 19:35:30 Xorbus kernel: [    0.084389] PM: Registering ACPI NVS region [mem 0xbbc70000-0xbbc7ffff] (65536 bytes)
Oct 24 19:35:30 Xorbus kernel: [    0.084389] PM: Registering ACPI NVS region [mem 0xbe3d8000-0xbe5d7fff] (2097152 bytes)
Oct 24 19:35:30 Xorbus kernel: [    0.084389] PM: Registering ACPI NVS region [mem 0xbfdcf000-0xbfecefff] (1048576 bytes)
Oct 24 19:35:30 Xorbus kernel: [    0.873931] PM: Hibernation image not present or could not be loaded.

---

### Post by Lammis on 2013-10-24
It did not work creating the suggested file. I have deleted it. I am open for other suggestions if anyone knows what might be wrong.

---

### Post by Toz on 2013-10-24
> Oct 24 19:17:46 Xorbus kernel: [11139.748976] PM: Device PNP0C0B:00 failed to resume: error -19
What does the following return:
```
dmesg | grep PNP0C0B
```



Can you also try to unload the module manually:
```
sudo rmmod iwlwifi
```
...then manually suspend:
```
sudo pm-suspend
```
...then resume and reload the module:
```
sudo modprobe iwlwifi
```
...and check whether it works now. Post back all responses to those commands.



Afterwards, please post back again the results of all these commands:
```
cat /var/log/syslog | grep PM:
```
...and
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by David D. on 2013-10-24
There is a confirmed bug in Launchpad on this subject, but I cannot find the number right now.  Maybe someone else will know the number.

I am also affected by this bug, so if someone has a solution I am interested.

---

### Post by Toz on 2013-10-24
> **David D. said:**
> There is a confirmed bug in Launchpad on this subject, but I cannot find the number right now.  Maybe someone else will know the number.

I am also affected by this bug, so if someone has a solution I am interested.

Sometimes, unloading the module before suspend and reloading it afterwards helps. This has worked for this module in the past. Can you try the commands from my last post to see if it works for you?


Also found [this thread]("http://ubuntuforums.org/showthread.php?t=1840116"). It suggests creating **/etc/modprobe.d/iwlwifi.conf** nd adding the lines:
```
options iwlwifi bt_coex_active=0 
options iwlwifi 11n_disable=1
```
...to the file and rebooting.

---

### Post by David D. on 2013-10-24
That fix did the trick for me, thanks Toz.  Hopefully the OP will have similar luck.

---

### Post by Toz on 2013-10-24
> **David D. said:**
> That fix did the trick for me, thanks Toz.  Hopefully the OP will have similar luck.

I'm curious, which fix? The loading/unloading of modules or the parameters in /etc/modprobe.d/iwlwifi.conf?

---

### Post by David D. on 2013-10-24
The parameters in /etc/modprobe.d/iwlwifi.conf

---

### Post by Lammis on 2013-10-25
> **Toz said:**
> What does the following return:
```
dmesg | grep PNP0C0B
```

It returns nothing!

> **Toz said:**
> Can you also try to unload the module manually:
```
sudo rmmod iwlwifi
```
...then manually suspend:
```
sudo pm-suspend
```
...then resume and reload the module:
```
sudo modprobe iwlwifi
```
...and check whether it works now. Post back all responses to those commands.


 I could not unload the module. I got this error:
 ```
lars@Xorbus:~$ sudo rmmod iwlwifi 
 Error: Module iwlwifi is in use by: iwldvm 
```
 

 Furthermore, the manual modprobe command had no effect either.


> **Toz said:**
> Afterwards, please post back again the results of all these commands:
```
cat /var/log/syslog | grep PM:
```
...and
 

 cat /var/log/syslog | grep PM:  
 Oct 25 12:07:56 Xorbus kernel: [ 4797.781542] PM: Syncing filesystems ... done.  
 Oct 25 12:07:56 Xorbus kernel: [ 4798.112618] PM: Preparing system for mem sleep  
 Oct 25 13:08:30 Xorbus kernel: [ 4798.411744] PM: Entering mem sleep  
 Oct 25 13:08:30 Xorbus kernel: [ 4800.012255] PM: suspend of devices complete after 1599.906 msecs  
 Oct 25 13:08:30 Xorbus kernel: [ 4800.012690] PM: late suspend of devices complete after 0.432 msecs  
 Oct 25 13:08:30 Xorbus kernel: [ 4800.092062] PM: noirq suspend of devices complete after 79.369 msecs 
 Oct 25 13:08:30 Xorbus kernel: [ 4800.100162] PM: Saving platform NVS memory  
 Oct 25 13:08:30 Xorbus kernel: [ 4800.212351] PM: Restoring platform NVS memory  
 Oct 25 13:08:30 Xorbus kernel: [ 4801.152048] PM: noirq resume of devices complete after 890.254 msecs 
 Oct 25 13:08:30 Xorbus kernel: [ 4801.152208] PM: early resume of devices complete after 0.126 msecs  
 Oct 25 13:08:30 Xorbus kernel: [ 4801.244394] PM: Device PNP0C0B:00 failed to resume: error -19  
 Oct 25 13:08:30 Xorbus kernel: [ 4811.348134] PM: resume of devices complete after 10195.923 msecs  
 Oct 25 13:08:30 Xorbus kernel: [ 4811.348566] PM: Finishing wakeup.  
 
> **Toz said:**
> ```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

before actions above - [http://paste.ubuntu.com/6299626/](http://paste.ubuntu.com/6299626/)
 after actions above - [http://paste.ubuntu.com/6300121/](http://paste.ubuntu.com/6300121/)

---

### Post by Lammis on 2013-10-25
> **Toz said:**
> Sometimes, unloading the module before suspend and reloading it afterwards helps. This has worked for this module in the past. Can you try the commands from my last post to see if it works for you?


Also found [this thread]("http://ubuntuforums.org/showthread.php?t=1840116"). It suggests creating **/etc/modprobe.d/iwlwifi.conf** nd adding the lines:
```
options iwlwifi bt_coex_active=0 
options iwlwifi 11n_disable=1
```
...to the file and rebooting.

I already have this file and the current content is as follows:
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

But I added the two lines of code suggested above and put my PC to rest. Ta-da it instantly reconnected to wifi when thawed. :-)

Great thanks Toz!

---

### Post by Lammis on 2013-10-25
> But I added the two lines of code suggested above and put my PC to rest. Ta-da it instantly reconnected to wifi when thawed. [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

I am sorry, that was a wee bit premature...
As my PC fell into sleep again it did not reconnect to my internet on wake-up. The problem is still there although it worked when I tested twice before. Crap!

---

### Post by Toz on 2013-10-25
Can you post back the current contents of /etc/modprobe.d/iwlwifi.conf inbetween **[noparse]```
 
```[/noparse]** tags?

---

### Post by Lammis on 2013-10-27
> **Toz said:**
> Can you post back the current contents of /etc/modprobe.d/iwlwifi.conf inbetween **[noparse]```
 
```[/noparse]** tags?

```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi bt_coex_active=0 
options iwlwifi 11n_disable=1
```

---

### Post by Toz on 2013-10-27
Can you comment out the first section so that you have:
```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
#remove iwlwifi \
#(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
#&& /sbin/modprobe -r mac80211
options iwlwifi bt_coex_active=0 
options iwlwifi 11n_disable=1
```
...then reboot and try again.

---

### Post by marcinkowski on 2013-10-27
This worked for me:

[http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153](http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153)

Though I am still suffering from this issue:

[http://askubuntu.com/questions/366511/update-to-13-10-blank-screen-and-repeated-suspend-on-wake-from-suspend](http://askubuntu.com/questions/366511/update-to-13-10-blank-screen-and-repeated-suspend-on-wake-from-suspend)

---

### Post by Toz on 2013-10-27
> **marcinkowski said:**
> This worked for me:

[http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153](http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153)

Though I am still suffering from this issue:

[http://askubuntu.com/questions/366511/update-to-13-10-blank-screen-and-repeated-suspend-on-wake-from-suspend](http://askubuntu.com/questions/366511/update-to-13-10-blank-screen-and-repeated-suspend-on-wake-from-suspend)

deleted.

Continued here: [http://ubuntuforums.org/showthread.php?t=2184159]("http://ubuntuforums.org/showthread.php?t=2184159")

---

### Post by Lammis on 2013-10-28
> **Toz said:**
> Can you comment out the first section so that you have:
```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
#remove iwlwifi \
#(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
#&& /sbin/modprobe -r mac80211
options iwlwifi bt_coex_active=0 
options iwlwifi 11n_disable=1
```
...then reboot and try again.

No difference I'm afraid...
Furthermore I forgot to mention that each time this problem occurs I also loose the ability to reboot the machine through the menu system. I have to press the hardware button for several seconds.

---

### Post by Lammis on 2013-11-04
Yesterday I got an update via the system update manager and it seems to have solved the problem.
I am a happy man again!

---

### Post by Lammis on 2013-11-14
> **Lammis said:**
> Yesterday I got an update via the system update manager and it seems to have solved the problem.
I am a happy man again!

It seems my problem is dependent on how long the PC has been suspended. After the previous upgrade it worked fine a few times but then it fell back to the old habit of not reconnecting the wifi and being impossible to turn off unless I press the HW button for 6 sek.

---

