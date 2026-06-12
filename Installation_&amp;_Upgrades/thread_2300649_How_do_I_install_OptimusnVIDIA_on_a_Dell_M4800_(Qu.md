---
title: "How do I install Optimus/nVIDIA on a Dell M4800 (Quadro K1100M)"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2015-10-27
Hello,

  I am an experienced Ubuntu user, and just got a new Dell Precision Workstation M4800 with an nVIDIA K1100M Quadro card.  I've sucessfully installed the nVIDIA drivers and I'm using that (exclusively).

  I'd like to try and install the Optimus system and I need a step by step guide for Ubuntu 14.04.3 LTS AMD 64.

  I believe at this point that I'd need to (a) uninstall the nVIDIA drivers, (b) remove the xorg.conf file, (c) install the optimus system, (d) reboot and go into the BIOS and turn on the Optimus option.

  Should I be using the Xorg Edgers PPA?  Or should I just stick to the vanilla Ubuntu 14.04 nVIDIA repos?

  A link to a guide would be helpful.

Thanks,
Andor

---

### Post by Bashing-om on 2015-10-27
cement_head; Hello;

If you have the Nvidia proprietary driver installed; then it is 'nvidia-prime' that controls which graphics set to use.
```

dpkg -l | grep -i nvidia
sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo lshw -C display

```
Will show what you have and as well what you should have installed.

[INDENT][INDENT]ain't nothing now but a thing
[/INDENT][/INDENT]

---

### Post by frogotronic on 2015-10-27
That didn't help me AT ALL.

Pretend like I have no idea what I'm doing with Optimus

I need a STEP-BY-STEP guide

---

### Post by Bashing-om on 2015-10-27
> **cement_head said:**
> That didn't help me AT ALL.

Pretend like I have no idea what I'm doing with Optimus

I need a STEP-BY-STEP guide

A long time user of ubuntu, and been on this forum for a while .. requiring hand holding .

We do that too .
Provide the requested outputs - between code tags - so we have a foundation of communications.
Once we know what we are dealing with we have something to talk about.

There is no one-thing-fixes-everything guide.

[INDENT][INDENT]we do with 
[INDENT][INDENT][INDENT]what we have
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-10-27
Nvidia Optimus technology is a system where the motherboard has an Intel graphic adapter and an Nvidia graphic adapter. With Microsoft Windows installed the Intel adapter is used when low intensity graphic tasks are being performed. And then the system switches to the Nvidia adapter for high intensity graphic cards. This switching is done through the Nvidia driver and it is done automatically.

From the Dell web site it seems that your motherboard has built in Intel HD 4600 graphics and an Nvidia Quadro K1100M graphic adapter. So, in one sense there is nothing to install as you already have Nvidia Optimus techology.

Linux users have not had such a good deal from Nvidia. To start with, Nvidia waited many months after it released Nvidia Optimus technology before it even began working an Nvidia Linux driver that did anything with its Optimus technology. Ubuntu 14.04 was the first version of Ubuntu to get an Nvidia driver that did anything for Optimus. And even then the Nvidia driver did not and still does not provide automatic switching from the Intel adapter to the Nvidia adapter and back again.

During this period the only hope for Linux users with Optimus technology was a free and open source project called Bumblebee and the developers were working blind.

You have 2 choices. Install the latest Nvidia driver for your hardware and the use the Nvidia settings utility which is installed at the same time to switch between Intel and Nvidia. Or, install Bumblebee.

[http://bumblebee-project.org/](http://bumblebee-project.org/)

I have no idea if Bumblebee does automatic switching. If you choose to use the Nvidia driver then you might want to check out Prime Indicator. I do not know if this PPA is available for versions of Ubuntu later than 14.04.

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Regards.

---

### Post by frogotronic on 2015-10-27
Ok, hang on - WHHHOOOOAAAA HORSEY

I ONLY have an nVIDIA card showing up in the lspci | grep VGA

So...no optimus for me?

```
$ lspci |grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK107GLM [Quadro K1100M] (rev a1)
```

---

### Post by Bashing-om on 2015-10-27
cement_head; Mabe so ..

maybe not so .. what you see is what you asked to see " VGA" .. maybe the Intel is '3D' ?

what returns:
```

dpkg -l | grep -i nvidia
sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo lshw -C display

```

where " sudo ubuntu-drivers devices " will show all the devices requiring drivers .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by frogotronic on 2015-10-27
lspci

```
$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d4)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107GLM [Quadro K1100M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
11:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
```

lspci | grep VGA

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK107GLM [Quadro K1100M] (rev a1)
```

dpkg -l | grep -i nvidia

```
$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
ii  bumblebee                                             3.2.1-5                                                amd64        NVIDIA Optimus support for Linux
ii  bumblebee-nvidia                                      3.2.1-5                                                amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  libcuda1-346-updates                                  346.96-0ubuntu0.0.1                                    amd64        NVIDIA CUDA runtime library
ii  nvidia-346-updates                                    346.96-0ubuntu0.0.1                                    amd64        NVIDIA binary driver - version 346.96
ii  nvidia-common                                         1:0.2.91.11                                            amd64        transitional package for ubuntu-drivers-common
ii  nvidia-libopencl1-346-updates                         346.96-0ubuntu0.0.1                                    amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-346-updates                         346.96-0ubuntu0.0.1                                    amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                        amd64        Tool for configuring the NVIDIA graphics driver
ii  primus                                                0~20131127-2                                           amd64        client-side GPU offloading for NVIDIA Optimus

```

sudo ubuntu-drivers devices

```
$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:1c.7/0000:11:00.0 ==
modalias : pci:v00001217d00008520sv00001028sd000005CCbc08sc05i01
vendor   : O2 Micro, Inc.
driver   : oem-sdcard-o2micro-dkms - third-party free

== /sys/devices/virtual/dmi/id ==
modalias : dmi:bvnDellInc.:bvrA14:bd05/19/2015:svnDellInc.:pnPrecisionM4800:pvr01:rvnDellInc.:rn0V5GVY:rvrA00:cvnDellInc.:ct9:cvr:
driver   : config-remove-ubuntuone-precise-all - third-party free

== /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 ==
modalias : pci:v000014E4d000043B1sv00001028sd00000017bc02sc80i00
model    : BCM4352 802.11ac Wireless Network Adapter
vendor   : Broadcom Corporation
driver   : bcmwl-kernel-source - distro non-free

== /sys/devices/pci0000:00/0000:00:1b.0 ==
modalias : pci:v00008086d00008C20sv00001028sd000005CCbc04sc03i00
model    : Lynx Point High Definition Audio Controller
vendor   : Intel Corporation
driver   : oem-audio-hda-daily-lts-quantal-dkms - third-party free

== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000FF6sv00001028sd000005CCbc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-346 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-340 - distro non-free
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-346-updates - distro non-free
```

sudo ubuntu-drivers list

```
$ sudo ubuntu-drivers list
nvidia-340
oem-sdcard-o2micro-dkms
nvidia-346-updates
nvidia-340-updates
nvidia-346
bcmwl-kernel-source
oem-audio-hda-daily-lts-quantal-dkms
config-remove-ubuntuone-precise-all
```

sudo lshw -C display

```
$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GK107GLM [Quadro K1100M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:47 memory:f4000000-f4ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f5000000-f507ffff
```


Doesn't look as if there is an Intel VGA controller on the laptop...

---

### Post by Bashing-om on 2015-10-27
cement_head; Yep;

Agreed, I see no sign of Intel graphics, and a quick check on the specs also does not show this to be of 'optimus' technology .

You do show to have the Nvidia 346 version driver installed. Should be good to go !


A Good thing (?)
[INDENT][INDENT][INDENT]no optimus for you
[/INDENT][/INDENT][/INDENT]

---

### Post by frogotronic on 2015-11-06
Update:  If I go into the BIOS and check "Optimus" and boot, I see the Intel VGA adaptor.  So I do have the capacity.

So, now...how do I get it working?

---

### Post by Bashing-om on 2015-11-06
cement_head; Well ....

Does the system now see that there are 2 graphics sets ?
```

lspci | grep "VGA\|3D"
sudo ubuntu-drivers devices

```

If so, then:
```

dpkg -l | grep -i nvidia

``` see if 'nvidia-settings' is installed. If not see what results when it is installed.
It is 'nvidia-settings' that controls which graphic's set is active in a optimus situation.

[INDENT][INDENT]if it is, it is
[/INDENT][/INDENT]

---

### Post by frogotronic on 2015-11-09
Yes!  But one has to check it in the BIOS.  Using 12.04, the switching doesn't work.  Is there an updated NVIDIA-PRIME that I need to install?

---

### Post by Bashing-om on 2015-11-09
cement_head; Hummm ...

Beats me up too presently . If the Intel graphic's set is enabled in bios, and the system now sees both graphic's sets;
It is from within nvidia-settings that one chooses the graphic set to use upon next log in . yeah choose and logout/login .
As to a different version of nvidia-settings, nope; What we have in the repo is what we should be working with . Else one can get into all kinds of trouble with differing version libraries and support files . 

[INDENT][INDENT]the fight goes on
[/INDENT][/INDENT]

---

