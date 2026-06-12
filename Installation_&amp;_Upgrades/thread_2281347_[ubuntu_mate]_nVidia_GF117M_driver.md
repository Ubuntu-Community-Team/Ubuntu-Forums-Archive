---
title: "[ubuntu mate] nVidia GF117M driver"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by efonde on 2015-06-06
[HR][/HR]Hi,
I'm using Ubuntu Mate for almost 2 weeks now. My laptop is Dell Inspiron 14 3458 with Intel + nVidia GF117M listed.

> *-display
             description: VGA compatible controller
             product: Broadwell-U Integrated Graphics
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:63 memory:f5000000-f5ffffff memory:d0000000-dfffffff

> *-display
                description: 3D controller
                product: GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:65 memory:f6000000-f6ffffff memory:e0000000-effff

Since software & updates displayed "no additional drivers available", I wonder if anyone know if there is proprietary driver available for nVidia GF117M in Ubuntu Mate? 


I saw this 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1362098](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1362098) and I thought if it's available (fixed) in Ubuntu then maybe the driver also available in Ubuntu Mate? Correct me if I'm wrong.

---

### Post by v3.xx on 2015-06-06
Yep, also ran across this one.
[https://bugs.launchpad.net/jockey/+bug/1262539](https://bugs.launchpad.net/jockey/+bug/1262539)

Mate is now official Ubuntu Mate and will have all packages that Ubuntu has to offer.

---

### Post by efonde on 2015-06-06
> **v3.xx said:**
> Yep, also ran across this one.
[https://bugs.launchpad.net/jockey/+bug/1262539](https://bugs.launchpad.net/jockey/+bug/1262539)

Mate is now official Ubuntu Mate and will have all packages that Ubuntu has to offer.

I saw that too but since the post  was around 2012, I wasn't sure (with Mate just officially Ubuntu). 

I guess I'll just wait for unknown time.

---

### Post by v3.xx on 2015-06-06
I have found that when all else fails, a manual driver install from the site is a good option.  You already have dkms installed (mate default package). I can offer assistance as will others :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=manually+install+graphic+driver&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=manually+install+graphic+driver&sa=Search&cof=FORID:9)

---

### Post by grahammechanical on 2015-06-06
Ubuntu Mate will have the same drivers available as Ubuntu has because they are accessing the same software archive. What version of Ubuntu Mate are you using? Is it 15.04 or 14.04.2? With Ubuntu and the Ubuntu family members we get the latest drivers with the latest version of Ubuntu.

Regards.

---

### Post by v3.xx on 2015-06-06
An after-thought

You did use the option to install restricted packages during the mate install?

---

### Post by efonde on 2015-06-06
> **grahammechanical said:**
> Ubuntu Mate will have the same drivers available as Ubuntu has because they are accessing the same software archive. What version of Ubuntu Mate are you using? Is it 15.04 or 14.04.2? With Ubuntu and the Ubuntu family members we get the latest drivers with the latest version of Ubuntu
Regards.

Ubuntu 14.04 the LTS one.

> **v3.xx said:**
> An after-thought
You did use the option to install restricted packages during the mate install?

yes, I did install the restricted packages.
I tried installing nvidia driver but none worked so far. The nvidia-340 and nvidia-331 resulted in black screen after ubuntu logo (probably the xorg configuration which I don't know ). The nvidia-304 was able to at least get the display but the nvidia-setting errored when I changed from Intel to Nvidia (with big minus thing).

---

### Post by grahammechanical on 2015-06-06
> when I changed from Intel to Nvidia

Ah. Hybrid graphics. If we are running on Intel graphics and open Additional Drivers then I guess that it would show "no additional drivers available." Ubuntu comes with an open source video driver for Nvidia adapters called Nouveau. If we do not have an Nvidia driver installed and we load with the Nvidia adapter then Ubuuntu should load using Nouveau and then Additional Drivers might show some available proprietary video drivers. We do need to be connected to the internet and we do need to allow the utility time to do the search.

What does this command show?

```
ubuntu-drivers devices
```

It should show video adapters and video drivers available.

Regards.

---

### Post by efonde on 2015-06-06
> **grahammechanical said:**
> Ah. Hybrid graphics. If we are running on Intel graphics and open Additional Drivers then I guess that it would show "no additional drivers available." Ubuntu comes with an open source video driver for Nvidia adapters called Nouveau. If we do not have an Nvidia driver installed and we load with the Nvidia adapter then Ubuuntu should load using Nouveau and then Additional Drivers might show some available proprietary video drivers. We do need to be connected to the internet and we do need to allow the utility time to do the search.

What does this command show?

```
ubuntu-drivers devices
```

It should show video adapters and video drivers available.

Regards.

the command returned nothing?


> 
~$ lspci -k
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
    Subsystem: Dell Device 06b0
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
    Subsystem: Dell Device 06b0
    Kernel driver in use: i915
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
    Subsystem: Dell Device 06b0
    Kernel driver in use: snd_hda_intel
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
    Subsystem: Dell Device 06b0
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
    Subsystem: Dell Device 06b0
    Kernel driver in use: mei_me
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
    Subsystem: Dell Device 06b0
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
    Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
    Subsystem: Dell Device 06b0
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
    Subsystem: Dell Device 06b0
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
    Subsystem: Dell Device 06b0
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
    Subsystem: Dell Device 06b0
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
    Subsystem: Dell Device 020e
    Kernel driver in use: ath9k
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
    Subsystem: Dell Device 06b0
    Kernel driver in use: r8169
08:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1)
    Subsystem: Dell Device 06b0
    Kernel driver in use: nouveau


I guess this means the nVidia card is a new hardware?

---

### Post by efonde on 2015-06-06
this laptop came with prinstalled ubuntu with working nvidia driver but i deleted and replaced it with mate since ubuntu hang from memory hog. i have 8GB ram. i still have the drivers from the previous preinstalled ubuntu. I wonder if there's anway I can use that drivers deb? 
> 
[COLOR=#333333][FONT=Trebuchet MS]bbswitch-dkms_0.7-2ubuntu1_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]bt-dw1708-firmware_1.2_all.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]config-prime-select-intel-all_0.4_all.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]dell-eula_1.02_all.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]dell-recovery_1.32~somerville6_all.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]fist_0.04_all.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]libcuda1-340_340.46-0somerville1_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]libvdpau1_0.7-1_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]linux-firmware_1.127.8_all.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]nvidia-340_340.46-0somerville1_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]nvidia-libopencl1-340_340.46-0somerville1_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]nvidia-opencl-icd-340_340.46-0somerville1_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]nvidia-prime_0.6.2_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]nvidia-settings_331.20-0ubuntu8_amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]oem-audio-hda-daily-dkms_0.201410112046~ubuntu14.04.1_all.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]screen-resolution-extra_0.17.1_all.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]ubuntu-drivers-common_0.2.91.7_amd64.deb[/FONT][/COLOR]


---

### Post by Bashing-om on 2015-06-06
efonde; Hello;

We can see:
> 
08:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1)
Subsystem: Dell Device 06b0
Kernel driver in use: nouveau

That the Nvidia card is using the open source driver 'nouveau'. To the best of my knowledge nouveau does not support switching.

Confirm please this is a notebook system we are working with.
If so, I find from Nvidia that they recommend the 346 driver . Now this driver is not available in the 14.04 ubuntu software repository. We must obtain the 346 driver elsewhere . I do suggest from the xorg-edgers PPA.

Before proceeding to install a different driver. let us make sure the system has no other Nvidia proprietary drivers installed:
What returns from terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
dpkg -l | grep -i nvidia

```
To see that there is no conflict of interest .
[INDENT][INDENT]installing an Nvidia driver is
[INDENT][INDENT][INDENT]no longer a step for a stepper -> can do !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2015-06-06
Hybrid graphics

I'm out of my pay grade here.  Glad grahamm and bashing came along, but did find others running the same card.

[http://www.ubuntu.com/certification/catalog/component/pci/10de%3A1140/](http://www.ubuntu.com/certification/catalog/component/pci/10de%3A1140/)

---

### Post by efonde on 2015-06-06
> **Bashing-om said:**
> efonde; Hello;

We can see:

That the Nvidia card is using the open source driver 'nouveau'. To the best of my knowledge nouveau does not support switching.

Confirm please this is a notebook system we are working with.
If so, I find from Nvidia that they recommend the 346 driver . Now this driver is not available in the 14.04 ubuntu software repository. We must obtain the 346 driver elsewhere . I do suggest from the xorg-edgers PPA.

Before proceeding to install a different driver. let us make sure the system has no other Nvidia proprietary drivers installed:
What returns from terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
dpkg -l | grep -i nvidia

```
To see that there is no conflict of interest .[INDENT][INDENT]installing an Nvidia driver is[INDENT][INDENT][INDENT]no longer a step for a stepper -> can do !
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Here you go:
> 
cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu MATE 14.04.2 _Trusty Tahr_ - LTS amd64 (20150323)]/ trusty main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
     6	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    17	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    18	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    27	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    28	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    37	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    38	
    39	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted
    40	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted
    41	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security universe
    42	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security universe
    43	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security multiverse
    44	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main


> 
cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu MATE 14.04.2 _Trusty Tahr_ - LTS amd64 (20150323)]/ trusty main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
     6	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    17	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    18	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    27	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    28	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    37	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    38	
    39	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted
    40	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted
    41	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security universe
    42	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security universe
    43	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security multiverse
    44	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
athlon@athlon-mate:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/extra-ppas.list <==
deb [http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate-hwe-2/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate-hwe-2/ubuntu) trusty main
deb [http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu) trusty main
deb [http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu) trusty main
deb [http://ppa.launchpad.net/accessibility-dev/ppa/ubuntu](http://ppa.launchpad.net/accessibility-dev/ppa/ubuntu) trusty main
deb [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu) trusty main


==> /etc/apt/sources.list.d/extra-ppas.list.save <==
deb [http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate-hwe-2/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate-hwe-2/ubuntu) trusty main
deb [http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu) trusty main
deb [http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu) trusty main
deb [http://ppa.launchpad.net/accessibility-dev/ppa/ubuntu](http://ppa.launchpad.net/accessibility-dev/ppa/ubuntu) trusty main
deb [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu) trusty main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/nomacs-stable-trusty.list <==
deb [http://ppa.launchpad.net/nomacs/stable/ubuntu](http://ppa.launchpad.net/nomacs/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/nomacs/stable/ubuntu](http://ppa.launchpad.net/nomacs/stable/ubuntu) trusty main


==> /etc/apt/sources.list.d/nomacs-stable-trusty.list.save <==
deb [http://ppa.launchpad.net/nomacs/stable/ubuntu](http://ppa.launchpad.net/nomacs/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/nomacs/stable/ubuntu](http://ppa.launchpad.net/nomacs/stable/ubuntu) trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/webupd8team-mate-trusty.list <==
deb [http://ppa.launchpad.net/webupd8team/mate/ubuntu](http://ppa.launchpad.net/webupd8team/mate/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/mate/ubuntu](http://ppa.launchpad.net/webupd8team/mate/ubuntu) trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main


> 
dpkg -l | grep -i nvidia
rc  libcuda1-304                                304.125-0ubuntu1~xedgers14.04.1                        amd64        NVIDIA CUDA runtime library
rc  libcuda1-304-updates                        304.125-0ubuntu0.0.1                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-331                                331.113-0ubuntu1~xedgers14.04.1                        amd64        NVIDIA CUDA runtime library
rc  libcuda1-331-updates                        331.113-0ubuntu0.0.4                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                340.76-0ubuntu1~xedgers14.04.4                         amd64        NVIDIA CUDA runtime library


---

### Post by Bashing-om on 2015-06-06
efonde; making progress.

Ok, we do have the xorg-edgers/ppa installed, and no others.
Let's remove the conflicting 304 / 331 drivers :
From the login screen key combo ctl+alt+F1 to gain a console interface.
Execute:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get purge nvidia*

```
which will remove all Nvidia drivers.

Now to install the 346 driver:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-346

```

Recently, installing the 346 driver also installs 'nvidia-settings' ; but now check and make sure that the tool is installed:
```

dpkg -l nvidia-settings

```

Reboot and let's see the effect. It is from within 'nvidia-settings' that the graphics sets are switched.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-07
> **Bashing-om said:**
> efonde; making progress.

Ok, we do have the xorg-edgers/ppa installed, and no others.
Let's remove the conflicting 304 / 331 drivers :
From the login screen key combo ctl+alt+F1 to gain a console interface.
Execute:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get purge nvidia*

```
which will remove all Nvidia drivers.

Now to install the 346 driver:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-346

```

Recently, installing the 346 driver also installs 'nvidia-settings' ; but now check and make sure that the tool is installed:
```

dpkg -l nvidia-settings

```

Reboot and let's see the effect. It is from within 'nvidia-settings' that the graphics sets are switched.
[INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]


done. after reboot I got black screen. Do you need to look at my bios settings? since there are lots of settings there that I don't even know what those are for.

---

### Post by Bashing-om on 2015-06-07
efonde; Humm ....

Strange that you still have no driver.
Speaking of bios ( which I would have no familiarity with) is the discreet graphics set disabled in bios such that the operating system is un-aware of it's existence ?

We also take a look and see what is installed:
```

dpkg -l | grep -i nvidia
sudo lshw -C display
cat /var/log/Xorg.0.log

```

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-08
> **Bashing-om said:**
> efonde; Humm ....

Strange that you still have no driver.
Speaking of bios ( which I would have no familiarity with) is the discreet graphics set disabled in bios such that the operating system is un-aware of it's existence ?

We also take a look and see what is installed:
```

dpkg -l | grep -i nvidia
sudo lshw -C display
cat /var/log/Xorg.0.log

```[INDENT][INDENT]gotta be a reason
[/INDENT]
[/INDENT]


> dpkg -l | grep -i nvidia
rc  libcuda1-304                                304.125-0ubuntu1~xedgers14.04.1                        amd64        NVIDIA CUDA runtime library
rc  libcuda1-304-updates                        304.125-0ubuntu0.0.1                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-331                                331.113-0ubuntu1~xedgers14.04.1                        amd64        NVIDIA CUDA runtime library
rc  libcuda1-331-updates                        331.113-0ubuntu0.0.4                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                340.76-0ubuntu1~xedgers14.04.4                         amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                346.72-0ubuntu0~xedgers14.04.2                         amd64        NVIDIA CUDA runtime library


> sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:62 memory:f5000000-f5ffffff memory:d0000000-dfffffff ioport:f000(size=64)
  *-display
       description: 3D controller
       product: GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:65 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff



for the Xorg log since it's so long please visit: [http://pastebin.com/FC7ChZZQ](http://pastebin.com/FC7ChZZQ). I have purged nvidia since I cant work with black screen.. nomodeset option also didn't have any effect.

---

### Post by Bashing-om on 2015-06-08
efonde; Don't know;

But maybe the system does not like the 346 version of the driver ??
Let's look at our software repository and see what is available:
```

sudo ubuntu-drivers list

```

And we consider once more to purge (completely) the 304/331 - I see no evidence that the 346 driver was installed; but, wont hurt to explore our options to install a proprietary graphics driver.
I presently do not understand the why of it that both the 304 and 331 drivers - marked as rc ( (r)emoved but (c)onfig files remain - AND the 346 driver did not install.

Installing a driver
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by efonde on 2015-06-08
> **Bashing-om said:**
> efonde; Don't know;

But maybe the system does not like the 346 version of the driver ??
Let's look at our software repository and see what is available:
```

sudo ubuntu-drivers list

```

And we consider once more to purge (completely) the 304/331 - I see no evidence that the 346 driver was installed; but, wont hurt to explore our options to install a proprietary graphics driver.
I presently do not understand the why of it that both the 304 and 331 drivers - marked as rc ( (r)emoved but (c)onfig files remain - AND the 346 driver did not install.

Installing a driver[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]
[/INDENT]




The command returned nothing
I noticed in the pre-installed ubuntu since I still have the OS & DIAGS partition untouched, they have something like this: 

> #!/bin/shcat <<'EOF' >> /etc/default/grub.d/99-video.cfg
GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT video.use_native_backlight=1"
EOF


and then there's also:

> #!/bin/sh

. /usr/share/dell/scripts/fifuncs


if match_system_device "pci" "8086" "0f31"; then


MIN_BRIGHT=780
cat <<EOF > /etc/udev/rules.d/99-force-minimun-intel-backlight-brightness.rules
ACTION=="change", KERNEL=="intel_backlight", SUBSYSTEM=="backlight", ATTR{brightness}=="?", ATTR{brightness}="${MIN_BRIGHT}"
ACTION=="change", KERNEL=="intel_backlight", SUBSYSTEM=="backlight", ATTR{brightness}=="??", ATTR{brightness}="${MIN_BRIGHT}"
ACTION=="change", KERNEL=="intel_backlight", SUBSYSTEM=="backlight", ATTR{brightness}=="[1-6]??", ATTR{brightness}="${MIN_BRIGHT}"
ACTION=="change", KERNEL=="intel_backlight", SUBSYSTEM=="backlight", ATTR{brightness}=="7[0-7]?", ATTR{brightness}="${MIN_BRIGHT}"
EOF


else


MIN_BRIGHT=46
cat <<EOF > /etc/udev/rules.d/99-force-minimun-intel-backlight-brightness.rules
ACTION=="change", KERNEL=="intel_backlight", SUBSYSTEM=="backlight", ATTR{brightness}=="?", ATTR{brightness}="${MIN_BRIGHT}"
ACTION=="change", KERNEL=="intel_backlight", SUBSYSTEM=="backlight", ATTR{brightness}=="[1-3]?", ATTR{brightness}="${MIN_BRIGHT}"
ACTION=="change", KERNEL=="intel_backlight", SUBSYSTEM=="backlight", ATTR{brightness}=="4[0-5]", ATTR{brightness}="${MIN_BRIGHT}"
EOF


fi

> #!/bin/sh

sed -i 's/pcie_aspm=force//' /etc/default/grub.d/*


> #!/bin/sh

dpkg -i /cdrom/kernel/*.deb
apt-get purge --yes --force-yes linux-.*-3.13.0-24.* linux-signed-generic linux-signed-image-generic linux-signed-image-3.13.0-24-generic

---

### Post by Bashing-om on 2015-06-08
efonde; Humm ..

a no return from ' ubuntu-drivers list ' simply menas the repository does not have a proprietary driver.
And Yeah, you may have a thought that a boot parameter may be in conflict. We can look at what that command line is:
```

cat /proc/cmdline

```
Then we are back to purging current Nvidia files and try and install once more the recommended 346 driver.

[INDENT][INDENT]if at 1st you do not suceed
[INDENT][INDENT]try try again ( sky diving excepted ) 
 [/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by efonde on 2015-06-09
> **Bashing-om said:**
> efonde; Humm ..

a no return from ' ubuntu-drivers list ' simply menas the repository does not have a proprietary driver.
And Yeah, you may have a thought that a boot parameter may be in conflict. We can look at what that command line is:
```

cat /proc/cmdline

```
Then we are back to purging current Nvidia files and try and install once more the recommended 346 driver.[INDENT][INDENT]if at 1st you do not suceed[INDENT][INDENT]try try again ( sky diving excepted ) 
 [/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


> BOOT_IMAGE=/boot/vmlinuz-3.16.0-39-generic root=UUID=f5256046-5d04-4798-a290-3561cb85217a ro quiet splash vt.handoff=7

Do you think it would be possible to force use the available nvidia drivers from the previous preinstalled ubuntu unity? And use the same kernel header [COLOR=#000000]*3.13.0-24*[/COLOR]?

These are the files lists that's on the preinstalled ubuntu recovery partition:
> [COLOR=#333333]*[FONT=Trebuchet MS]bbswitch-dkms_0.7-2ubuntu1_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]bt-dw1708-firmware_1.2_all.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]config-prime-select-intel-all_0.4_all.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]dell-eula_1.02_all.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]dell-recovery_1.32~somerville6_all.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]fist_0.04_all.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]libcuda1-340_340.46-0somerville1_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]libvdpau1_0.7-1_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]linux-firmware_1.127.8_all.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]nvidia-340_340.46-0somerville1_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]nvidia-libopencl1-340_340.46-0somerville1_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]nvidia-opencl-icd-340_340.46-0somerville1_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]nvidia-prime_0.6.2_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]nvidia-settings_331.20-0ubuntu8_amd64.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]oem-audio-hda-daily-dkms_0.201410112046~ubuntu14.04.1_all.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]screen-resolution-extra_0.17.1_all.deb[/FONT]*[/COLOR]
[COLOR=#333333]*[FONT=Trebuchet MS]ubuntu-drivers-common_0.2.91.7_amd64.deb[/FONT]*[/COLOR]

---

### Post by Bashing-om on 2015-06-09
efonde; Well, well ........

Nothing in the boot parameters to conflict with the Nvidia graphics driver;
And
> 
Do you think it would be possible to force use the available nvidia drivers from the previous preinstalled ubuntu unity

Not a good idea . The required supporting libraries would be different versions between the old, and what is present on the system. I do not think it would be possible to resolve the dependency issues and still have a stable system.
Linux is not Windows, The thought processes do differ between the two operating systems.

I do suggest we work toward getting a current graphics driver installed. IF we can not for what ever reason, well, we have a problem. That is the problem then we need to address.
To that end:
```

sudo apt-get remove --purge nvidia*
sudo apt-get purge nvidia-\*
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

All traces of the Nvidia proprietary drivers should now be gone from the system.

Before we proceed verify that Nvidia drivers are no longer in existence:
```

dpkg -l | grep -i nvidia

```

We are looking for a null return ( the result of the command is a return to prompt and no output).
Pending this result is what we do next.

[INDENT][INDENT]this ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-10
> **Bashing-om said:**
> efonde; Well, well ........

Nothing in the boot parameters to conflict with the Nvidia graphics driver;
And

Not a good idea . The required supporting libraries would be different versions between the old, and what is present on the system. I do not think it would be possible to resolve the dependency issues and still have a stable system.
Linux is not Windows, The thought processes do differ between the two operating systems.

I do suggest we work toward getting a current graphics driver installed. IF we can not for what ever reason, well, we have a problem. That is the problem then we need to address.
To that end:
```

sudo apt-get remove --purge nvidia*
sudo apt-get purge nvidia-\*
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

All traces of the Nvidia proprietary drivers should now be gone from the system.

Before we proceed verify that Nvidia drivers are no longer in existence:
```

dpkg -l | grep -i nvidia

```

We are looking for a null return ( the result of the command is a return to prompt and no output).
Pending this result is what we do next.[INDENT][INDENT]this ain't nothing but a thing
[/INDENT]
[/INDENT]


ok. done too. the first and second command got nothing. 
the third command seemed to remove some of config files:

> dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge(Reading database ... 225214 files and directories currently installed.)
Removing fonts-wqy-microhei (0.2.0-beta-2) ...
Purging configuration files for fonts-wqy-microhei (0.2.0-beta-2) ...
Removing libasn1-8-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libasn1-8-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libcapi20-3:amd64 (1:3.25+dfsg1-3.3ubuntu2) ...
Purging configuration files for libcapi20-3:amd64 (1:3.25+dfsg1-3.3ubuntu2) ...
Removing libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2) ...
Purging configuration files for libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2) ...
Removing libcuda1-304 (304.125-0ubuntu1~xedgers14.04.1) ...
Purging configuration files for libcuda1-304 (304.125-0ubuntu1~xedgers14.04.1) ...
Removing libcuda1-304-updates (304.125-0ubuntu0.0.1) ...
Purging configuration files for libcuda1-304-updates (304.125-0ubuntu0.0.1) ...
Removing libcuda1-331 (331.113-0ubuntu1~xedgers14.04.1) ...
Purging configuration files for libcuda1-331 (331.113-0ubuntu1~xedgers14.04.1) ...
Removing libcuda1-331-updates (331.113-0ubuntu0.0.4) ...
Purging configuration files for libcuda1-331-updates (331.113-0ubuntu0.0.4) ...
Removing libcuda1-340 (340.76-0ubuntu1~xedgers14.04.4) ...
Purging configuration files for libcuda1-340 (340.76-0ubuntu1~xedgers14.04.4) ...
Removing libcuda1-346 (346.72-0ubuntu0~xedgers14.04.2) ...
Purging configuration files for libcuda1-346 (346.72-0ubuntu0~xedgers14.04.2) ...
Removing libexif12:i386 (0.6.21-1ubuntu1) ...
Purging configuration files for libexif12:i386 (0.6.21-1ubuntu1) ...
Removing libgd3:i386 (2.1.0-3) ...
Purging configuration files for libgd3:i386 (2.1.0-3) ...
Removing libgif4:amd64 (4.1.6-11) ...
Purging configuration files for libgif4:amd64 (4.1.6-11) ...
Removing libgif4:i386 (4.1.6-11) ...
Purging configuration files for libgif4:i386 (4.1.6-11) ...
Removing libglu1-mesa:i386 (9.0.0-2) ...
Purging configuration files for libglu1-mesa:i386 (9.0.0-2) ...
Removing libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) ...
Purging configuration files for libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Purging configuration files for libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgssapi3-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libgssapi3-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2) ...
Purging configuration files for libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2) ...
Removing libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3) ...
Purging configuration files for libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3) ...
Removing libhcrypto4-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libhcrypto4-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libheimbase1-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libheimbase1-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libheimntlm0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libheimntlm0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libhx509-5-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libhx509-5-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libieee1284-3:i386 (0.2.11-12) ...
Purging configuration files for libieee1284-3:i386 (0.2.11-12) ...
Removing libjansson4:amd64 (2.5-2) ...
Purging configuration files for libjansson4:amd64 (2.5-2) ...
Removing libkrb5-26-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libkrb5-26-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing liblcms2-2:i386 (2.6-3ubuntu1~trusty1) ...
Purging configuration files for liblcms2-2:i386 (2.6-3ubuntu1~trusty1) ...
Removing libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu8.1) ...
Purging configuration files for libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu8.1) ...
Removing libllvm3.4:amd64 (1:3.4.2-3ubuntu2~xedgers) ...
Purging configuration files for libllvm3.4:amd64 (1:3.4.2-3ubuntu2~xedgers) ...
Removing libltdl7:i386 (2.4.2-1.7ubuntu1) ...
Purging configuration files for libltdl7:i386 (2.4.2-1.7ubuntu1) ...
Removing libmpg123-0:i386 (1.16.0-1ubuntu1) ...
Purging configuration files for libmpg123-0:i386 (1.16.0-1ubuntu1) ...
Removing libodbc1:amd64 (2.2.14p2-5ubuntu5) ...
Purging configuration files for libodbc1:amd64 (2.2.14p2-5ubuntu5) ...
Removing libopenal1:i386 (1:1.14-4ubuntu1) ...
Purging configuration files for libopenal1:i386 (1:1.14-4ubuntu1) ...
Removing libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.4) ...
Purging configuration files for libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.4) ...
Removing libosmesa6:amd64 (10.6.0~git20150528+10.6.ffd133bd-0ubuntu0ricotz~trusty) ...
Purging configuration files for libosmesa6:amd64 (10.6.0~git20150528+10.6.ffd133bd-0ubuntu0ricotz~trusty) ...
Removing libosmesa6:i386 (10.6.0~git20150528+10.6.ffd133bd-0ubuntu0ricotz~trusty) ...
Purging configuration files for libosmesa6:i386 (10.6.0~git20150528+10.6.ffd133bd-0ubuntu0ricotz~trusty) ...
Removing libpcap0.8:i386 (1.5.3-2) ...
Purging configuration files for libpcap0.8:i386 (1.5.3-2) ...
Removing libroken18-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libroken18-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libsane:i386 (1.0.23-3ubuntu3.1) ...
Purging configuration files for libsane:i386 (1.0.23-3ubuntu3.1) ...
Removing directory /etc/sane.d/ ...
Removing libsasl2-2:i386 (2.1.25.dfsg1-17build1) ...
Purging configuration files for libsasl2-2:i386 (2.1.25.dfsg1-17build1) ...
Removing libusb-1.0-0:i386 (2:1.0.17-1ubuntu2) ...
Purging configuration files for libusb-1.0-0:i386 (2:1.0.17-1ubuntu2) ...
Removing libv4l-0:i386 (1.0.1-1) ...
Purging configuration files for libv4l-0:i386 (1.0.1-1) ...
Removing libv4lconvert0:i386 (1.0.1-1) ...
Purging configuration files for libv4lconvert0:i386 (1.0.1-1) ...
Removing libvpx1:i386 (1.3.0-2) ...
Purging configuration files for libvpx1:i386 (1.3.0-2) ...
Removing libwayland-egl1-mesa:amd64 (10.6.0~git20150528+10.6.ffd133bd-0ubuntu0ricotz~trusty) ...
Purging configuration files for libwayland-egl1-mesa:amd64 (10.6.0~git20150528+10.6.ffd133bd-0ubuntu0ricotz~trusty) ...
Removing libwind0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libwind0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libxcomposite1:i386 (1:0.4.4-1) ...
Purging configuration files for libxcomposite1:i386 (1:0.4.4-1) ...
Removing libxcursor1:i386 (1:1.1.14-1) ...
Purging configuration files for libxcursor1:i386 (1:1.1.14-1) ...
Removing libxinerama1:i386 (2:1.1.3-1) ...
Purging configuration files for libxinerama1:i386 (2:1.1.3-1) ...
Removing libxnvctrl0 (352.09-0ubuntu0~xedgers14.04.1) ...
Purging configuration files for libxnvctrl0 (352.09-0ubuntu0~xedgers14.04.1) ...
Removing libxpm4:i386 (1:3.5.10-1) ...
Purging configuration files for libxpm4:i386 (1:3.5.10-1) ...
Removing libxrandr2:i386 (2:1.4.2-1) ...
Purging configuration files for libxrandr2:i386 (2:1.4.2-1) ...
Removing linux-image-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Purging configuration files for linux-image-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-33-generic /boot/vmlinuz-3.16.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-33-generic /boot/vmlinuz-3.16.0-33-generic
Removing linux-image-extra-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Purging configuration files for linux-image-extra-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Removing linux-signed-image-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Purging configuration files for linux-signed-image-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Removing ocl-icd-libopencl1:i386 (2.1.3-4) ...
Purging configuration files for ocl-icd-libopencl1:i386 (2.1.3-4) ...
Removing odbcinst (2.2.14p2-5ubuntu5) ...
Purging configuration files for odbcinst (2.2.14p2-5ubuntu5) ...
Removing odbcinst1debian2:amd64 (2.2.14p2-5ubuntu5) ...
Purging configuration files for odbcinst1debian2:amd64 (2.2.14p2-5ubuntu5) ...
Removing screen-resolution-extra (0.17.1) ...
Purging configuration files for screen-resolution-extra (0.17.1) ...
Removing wine1.7 (1:1.7.38-0ubuntu1) ...
Purging configuration files for wine1.7 (1:1.7.38-0ubuntu1) ...
Removing wine1.7-amd64 (1:1.7.38-0ubuntu1) ...
Purging configuration files for wine1.7-amd64 (1:1.7.38-0ubuntu1) ...
Removing wine1.7-i386 (1:1.7.38-0ubuntu1) ...
Purging configuration files for wine1.7-i386 (1:1.7.38-0ubuntu1) ...


I wonder why nvidia driver have connection with wine so anything with removing nvidia driver would also remove wine. Which rather troublesome since I'd have to reinstall wine after all the nvidia installation tries and purge. Just so I can play windows game.

---

### Post by Bashing-om on 2015-06-10
efonde; Wow ;

Surprised at the amount that is left to clean up .
While we are here, let's finish the cleanup of the system as it looks as if it has been a while since the system was "cleaned"
Simply done:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

And now to verify the status of the package management system :
```

sudo apt-get -f install
sudo dpkg -C

```

AND, let's make sure we are up on the latest version of the kernel:
```

uname -r

```
As there was a kernel update this day .

As to wine .. well it is an emulation layer, and gets embedded deep into the operating system. Wine gets it's fingers in a lot of pies.
I would not be real surprised IF we had to RE-install wine after the graphics driver change over to a proprietary driver, however un-expected that might be.
Before we proceed with installing the proprietary driver, let's look at the status of wine:
```

dpkg -l | grep -i nvidia
dpkg -l wine
apt-cache policy wine 

```

[INDENT][INDENT]this time
[INDENT][INDENT][INDENT]we make a firm foundation
[INDENT][INDENT][INDENT][INDENT][INDENT]before we jump
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by efonde on 2015-06-10
> **Bashing-om said:**
> efonde; Wow ;

Surprised at the amount that is left to clean up .
While we are here, let's finish the cleanup of the system as it looks as if it has been a while since the system was "cleaned"
Simply done:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

And now to verify the status of the package management system :
```

sudo apt-get -f install
sudo dpkg -C

```

AND, let's make sure we are up on the latest version of the kernel:
```

uname -r

```
As there was a kernel update this day .

As to wine .. well it is an emulation layer, and gets embedded deep into the operating system. Wine gets it's fingers in a lot of pies.
I would not be real surprised IF we had to RE-install wine after the graphics driver change over to a proprietary driver, however un-expected that might be.
Before we proceed with installing the proprietary driver, let's look at the status of wine:
```

dpkg -l | grep -i nvidia
dpkg -l wine
apt-cache policy wine 

```


done. 
> 
:~$ sudo dpkg -C:~$ uname -r
3.16.0-39-generic
:~$ dpkg -l | grep -i nvidia
:~$ dpkg -l wine
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  wine           <none>       <none>       (no description available)
:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1:1.7.38-0ubuntu1
  Version table:
     1:1.7.38-0ubuntu1 0
        500 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) trusty/main amd64 Packages
     1:1.6.2-0ubuntu4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages


---

### Post by Bashing-om on 2015-06-10
efonde; Yuk;

UnGood , maybe:
> 
 uname -r >> 3.16.0-39-generic

What is the reason that you are running the 3.16 kernel series in 'trusty' ?
Did you enable HardWare Enablement (HWE) ?
```

hwe-support-status --verbose
ls -al /usr/bin/hwe-support-status

```

For reference my updated trusty kernel:
```

sysop@1404mini:~$ uname -r
3.13.0-54-generic
sysop@1404mini:~$

``` running the 3.13 kernel series.

Presently I do not know how running vivid's kernel will impact installing the proprietary driver. We will find out.

As to wine, is there a particular reason the version in the repository is not satisfactory ? Should we then refocus to revert wine to that of the repository ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-11
> **Bashing-om said:**
> efonde; Yuk;

UnGood , maybe:

What is the reason that you are running the 3.16 kernel series in 'trusty' ?
Did you enable HardWare Enablement (HWE) ?
```

hwe-support-status --verbose
ls -al /usr/bin/hwe-support-status

```

For reference my updated trusty kernel:
```

sysop@1404mini:~$ uname -r
3.13.0-54-generic
sysop@1404mini:~$

``` running the 3.13 kernel series.

Presently I do not know how running vivid's kernel will impact installing the proprietary driver. We will find out.

As to wine, is there a particular reason the version in the repository is not satisfactory ? Should we then refocus to revert wine to that of the repository ?[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


> 
hwe-support-status --verbose
hwe-support-status: command not found

ls -al /usr/bin/hwe-support-status
ls: cannot access /usr/bin/hwe-support-status: No such file or directory



could try get back to the old kernal 3.13 but I doubt it would have effect. I tried in previous old kernel but nvidia didn't work  (ended up with black screen)

i use the stable one version from wine ppa for support more games.

---

### Post by Bashing-om on 2015-06-11
efonde' Welp;

OK, Let's work with what we have to work with.
Trying to install the Nvidia graphics driver. Up front, I have not had the experience of trying to install with an out-of-release kernel; But, I do have a thought:
As we are presently attempting to build the driver and telling the installer we are using 'trusty';
```

deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu [color=red]trusty[/color] main

```
Let's try telling the system the truth, that we are in fact up on 'utopic' for the kernel. As the driver gets built against the currently installed kernel.
In /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list . Change the source get from 'trusty' to 'utopic'.
And now let's try:
```

sudo apt-get update
sudo apt-get install nvidia-346

```
And let's look at what took place:
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]hey, It Could happen
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-15
> **Bashing-om said:**
> efonde' Welp;

OK, Let's work with what we have to work with.
Trying to install the Nvidia graphics driver. Up front, I have not had the experience of trying to install with an out-of-release kernel; But, I do have a thought:
As we are presently attempting to build the driver and telling the installer we are using 'trusty';
```

deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu [COLOR=red]trusty[/COLOR] main

```
Let's try telling the system the truth, that we are in fact up on 'utopic' for the kernel. As the driver gets built against the currently installed kernel.
In /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list . Change the source get from 'trusty' to 'utopic'.
And now let's try:
```

sudo apt-get update
sudo apt-get install nvidia-346

```
And let's look at what took place:
```

cat /var/log/Xorg.0.log

```[INDENT][INDENT]hey, It Could happen
[/INDENT]
[/INDENT]


sorry for the wait. my internet died and just back today. Anyway here's the xorg.log : [http://pastebin.com/iydzc8y6](http://pastebin.com/iydzc8y6)

it seems to be have working module but still black screen (can't get the right display out? valid display device none?)

[https://devtalk.nvidia.com/default/topic/807721/346-35-valid-display-device-s-none-860m/](https://devtalk.nvidia.com/default/topic/807721/346-35-valid-display-device-s-none-860m/)

---

### Post by Bashing-om on 2015-06-15
efonde; Welp;

1st up is an apology, seems I have had my head in a real dark place in respect to the 3.16.0-39-generic kernel. That kernel is valid as HWE is enabled by default on 14.04 after the point release.

Going to reread the log file, when my mind is a bit clearer, and see then

For now, what returns:
```

xrandr -q
xrandr --verbose

```
to see what we have for monitors and resolutions.

[INDENT][INDENT]too soon to guess
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-16
> **Bashing-om said:**
> efonde; Welp;

1st up is an apology, seems I have had my head in a real dark place in respect to the 3.16.0-39-generic kernel. That kernel is valid as HWE is enabled by default on 14.04 after the point release.

Going to reread the log file, when my mind is a bit clearer, and see then

For now, what returns:
```

xrandr -q
xrandr --verbose

```
to see what we have for monitors and resolutions.[INDENT][INDENT]too soon to guess
[/INDENT]
[/INDENT]


I don't quite understand with kernel use. 

> $ xrandr -q
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 32767 x 32767
eDP1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1366x768       60.1*+   48.1  
   1360x768       59.8     60.0  
   1280x720       60.0  
   1024x768       60.0  
   1024x576       60.0  
   960x540        60.0  
   800x600        60.3     56.2  
   864x486        60.0  
   640x480        59.9  
   720x405        60.0  
   680x384        60.0  
   640x360        60.0  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



> $ xrandr --verbose
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 32767 x 32767
eDP1 connected 1366x768+0+0 (0x67) normal (normal left inverted right x axis y axis) 309mm x 173mm
    Identifier: 0x63
    Timestamp:  25750
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff0006af3c2d00000000
        00170104951f117802bbf59455549027
        23505400000001010101010101010101
        010101010101ec1d56e850001e302616
        360035ad1000001af01756e850001e30
        2616360035ad1000001a000000fe0030
        44434e35804231343058544e00000000
        00004121960111000009010a20200067
    BACKLIGHT: 656 
        range: (0, 937)
    Backlight: 656 
        range: (0, 937)
    scaling mode: Full aspect 
        supported: None, Full, Center, Full aspect
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
  1366x768 (0x67)   76.6MHz +HSync -VSync *current +preferred
        h: width  1366 start 1404 end 1426 total 1598 skew    0 clock   47.9KHz
        v: height  768 start  771 end  777 total  798           clock   60.1Hz
  1366x768 (0x127)   61.3MHz +HSync -VSync
        h: width  1366 start 1404 end 1426 total 1598 skew    0 clock   38.3KHz
        v: height  768 start  771 end  777 total  798           clock   48.1Hz
  1360x768 (0x128)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x129)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1280x720 (0x12a)   74.5MHz -HSync +VSync
        h: width  1280 start 1336 end 1472 total 1664 skew    0 clock   44.8KHz
        v: height  720 start  721 end  724 total  746           clock   60.0Hz
  1024x768 (0x12b)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1024x576 (0x12c)   47.0MHz -HSync +VSync
        h: width  1024 start 1064 end 1168 total 1312 skew    0 clock   35.8KHz
        v: height  576 start  577 end  580 total  597           clock   60.0Hz
  960x540 (0x12d)   40.8MHz -HSync +VSync
        h: width   960 start  992 end 1088 total 1216 skew    0 clock   33.5KHz
        v: height  540 start  541 end  544 total  559           clock   60.0Hz
  800x600 (0x12e)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x12f)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  864x486 (0x130)   32.9MHz -HSync +VSync
        h: width   864 start  888 end  976 total 1088 skew    0 clock   30.2KHz
        v: height  486 start  487 end  490 total  504           clock   60.0Hz
  640x480 (0x131)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x405 (0x132)   22.2MHz -HSync +VSync
        h: width   720 start  728 end  800 total  880 skew    0 clock   25.2KHz
        v: height  405 start  406 end  409 total  420           clock   60.0Hz
  680x384 (0x133)   19.7MHz -HSync +VSync
        h: width   680 start  688 end  752 total  824 skew    0 clock   23.9KHz
        v: height  384 start  385 end  388 total  398           clock   60.0Hz
  640x360 (0x134)   17.2MHz -HSync +VSync
        h: width   640 start  640 end  704 total  768 skew    0 clock   22.4KHz
        v: height  360 start  361 end  364 total  373           clock   60.0Hz
HDMI1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x64
    Timestamp:  25750
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x65
    Timestamp:  25750
    Subpixel:   no subpixels
    Clones:    
    CRTCs:      3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 


---

### Post by Bashing-om on 2015-06-16
efonde; Humm ..

I have been considering what might not be taking place here !

The Nvidia driver does build and Intel just works !
The Xorg.0.log shows:
> 
5.331] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    25.337] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    25.337] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
<snip>
25.374] (II) intel(G0): Output eDP1 has no monitor section
25.374] (II) intel(G0): Enabled output eDP1
25.374] (II) intel(G0): Enabled output HDMI1
  25.374] (II) intel(G0): Enabled output VIRTUAL1


This, I have no idea of what it means. or the impact:
> 
25.375] (II) Loading sub module "present"
[    25.375] (II) LoadModule: "present"
[    25.456] (WW) Warning, couldn't open module present
[    25.456] (II) UnloadModule: "present"
[    25.456] (II) Unloading present
[    25.456] (EE) intel: Failed to load module "present" (module does not exist, 0)


Changing the focus of attention to the "xrandr -q" output:
> 
eDP1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm

Thus display port should be in use.

So let us follow the hint and look at the config file " Xorg.conf " :
```

cat /etc/X11/Xorg.conf

``` and verify that the display 'eDP1' is configured .

Mind you, I do not know;
[INDENT][INDENT]all I do know is to look and see what we can find out
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-17
> **Bashing-om said:**
> efonde; Humm ..

I have been considering what might not be taking place here !

The Nvidia driver does build and Intel just works !
The Xorg.0.log shows:


This, I have no idea of what it means. or the impact:

Changing the focus of attention to the "xrandr -q" output:

Thus display port should be in use.

So let us follow the hint and look at the config file " Xorg.conf " :
```

cat /etc/X11/Xorg.conf

``` and verify that the display 'eDP1' is configured .

Mind you, I do not know;[INDENT][INDENT]all I do know is to look and see what we can find out
[/INDENT]
[/INDENT]


Umm... I'm not sure do you need the xorg.conf when the nvidia installed or when the nvidia not installed?
The xorg list I have is very weird :
> 
-rw-r--r-- 1 root root       85 Jun  1 17:56 xorg.conf.06012015.old
-rw-r--r-- 1 root root       85 Jun  2 06:31 xorg.conf.06022015.old
-rw-r--r-- 1 root root       85 Jun  3 23:43 xorg.conf.06032015.old
-rw-r--r-- 1 root root      593 Jun  4 11:29 xorg.conf.06042015.old
-rw-r--r-- 1 root root      593 Jun  4 23:52 xorg.conf.06052015.old
-rw-r--r-- 1 root root      593 Jun  7 11:21 xorg.conf.06072015
-rw-r--r-- 1 root root      593 Jun 16 07:18 xorg.conf.06162015


if i do cat to Xorg.conf (with no nvidia driver installed) it would say "no such file or directory".
Anyway here is the Xorg.conf :
```
Section "ServerLayout"    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:8@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection



```

---

### Post by Bashing-om on 2015-06-18
efonde; Well;

Treading water here, trying to keep our heads above water.
But, we know we must make the system aware that "eDP1 "  exists. To do that we make an edit to the Xorg.conf file.

In continued preparation let's clean up old files and make sure of what driver is installed:
```

sudo rm /etc/X11/Xorg.conf.06*

```
This gets rid of those old backup files that I see no use for.
Now what have we on the system for the config file(s) ?
```

ls -al /etc/X11/Xorg*

```

And what is presently installed for the Nvidia driver - make sure that "nvidia-settings" is installed ...?
```

dpkg -l | grep -i nvidia

```

And to see what we are to set up for the display in the Xorg.conf file ; 
What returns:
```

cvt 1366 768 60

```

And believe me, I am open to any suggestions to make correct edits to the file !!

can not hurt to try ->
[INDENT][INDENT][INDENT]see what happens
[/INDENT][/INDENT][/INDENT]

---

### Post by efonde on 2015-06-18
> **Bashing-om said:**
> efonde; Well;

Treading water here, trying to keep our heads above water.
But, we know we must make the system aware that "eDP1 "  exists. To do that we make an edit to the Xorg.conf file.

In continued preparation let's clean up old files and make sure of what driver is installed:
```

sudo rm /etc/X11/Xorg.conf.06*

```
This gets rid of those old backup files that I see no use for.
Now what have we on the system for the config file(s) ?
```

ls -al /etc/X11/Xorg*

```

And what is presently installed for the Nvidia driver - make sure that "nvidia-settings" is installed ...?
```

dpkg -l | grep -i nvidia

```

And to see what we are to set up for the display in the Xorg.conf file ; 
What returns:
```

cvt 1366 768 60

```

And believe me, I am open to any suggestions to make correct edits to the file !!

can not hurt to try ->[INDENT][INDENT][INDENT]see what happens
[/INDENT]
[/INDENT]
[/INDENT]


Here you go:
```
cvt 1366 768 60
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

```

So is it okay to delete all those Xorg.conf? or just delete the old configurations? If I delete all those Xorg configurations, won't I lost the xorg.conf? or the Xorg.conf gets created every reboot? 
I'm worried since if i do "sudo service lightdm stop" then "sudo Xorg -configure", I'd get error "segmentation fault at address 0x0". The Xorg log: [http://pastebin.com/wnDQMVjF](http://pastebin.com/wnDQMVjF)

Anyway, I have deleted all those xorg.conf. So.....
```
ls -al /etc/X11/Xorg*
ls: cannot access /etc/X11/Xorg*: No such file or directory

```

---

### Post by Bashing-om on 2015-06-18
efonde; Yuk,

Not at all known what is taking place here,
The command " sudo rm /etc/X11/Xorg.conf.06* ' would have only removed files that include the suffixes .06" Not the primary target file "/etc/X11/Xorg.conf" .

Yuk, so in any event let's make up a new one:
```

sudo nvidia-xconfig

```

And now what do we have to work with ?
Post back the output of :
```

cat /etc/X11/Xorg.conf

```

and we see about including the monitor and a modeline suitable in that file .

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-24
> **Bashing-om said:**
> efonde; Yuk,

Not at all known what is taking place here,
The command " sudo rm /etc/X11/Xorg.conf.06* ' would have only removed files that include the suffixes .06" Not the primary target file "/etc/X11/Xorg.conf" .

Yuk, so in any event let's make up a new one:
```

sudo nvidia-xconfig

```

And now what do we have to work with ?
Post back the output of :
```

cat /etc/X11/Xorg.conf

```

and we see about including the monitor and a modeline suitable in that file .
[INDENT][INDENT]hey, it could happen
[/INDENT]
[/INDENT]


I had problem with internet. Here the xorg looked with nvidia:
> Section "ServerLayout"    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:8@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection




---

### Post by Bashing-om on 2015-06-24
efonde; Hey hey ..

We doing good.

Gimme a bit of time to do the homework here as I do not recognize the options given to Nvidia in the /etc/X11/Xorg.conf file.
As soon as I know more, I will report .

[INDENT][INDENT]sometimes, it is not what you know
[INDENT][INDENT][INDENT]but knowing where to find info you need
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-06-25
efonde;Welp;

I do have some conclusions.
The options are valid for optimus technology.

OK, lets back up the present config file:
```

sudo cp /etc/X11/Xorg.conf /etc/X11/Xorg.conf-old

```
and edit the config file; adding a monitor section with the modeline:
```

Section "ServerLayout" ##should be as this 
    Identifier "layout" ##should be as this
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:8@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

```

Save the file and reboot, let's see how this now runs.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-06-29
efonde; Hey !

Inquiry to know your present situation.

[INDENT][INDENT]What are we going to do ?
[/INDENT][/INDENT]

---

### Post by efonde on 2015-06-30
> **Bashing-om said:**
> efonde; Hey !

Inquiry to know your present situation.[INDENT][INDENT]What are we going to do ?
[/INDENT]
[/INDENT]

Sorry ... here is the xorg.conf with nvidia-346 installed after the command sudo nvidia-xconfig:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig# nvidia-xconfig:  version 346.72  (buildmeister@swio-display-x64-rhel04-19)  Tue May  5 18:19:38 PDT 2015


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


Section "Files"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```

but after reboot the xorg.conf would always back to this setting:
```

Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:8@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection



```

---

### Post by Bashing-om on 2015-06-30
efonde; Yuk;

I honestly do not know
> 
but after reboot the xorg.conf would always back to this setting:

What could possibly be re-writing the " /etc/X11/Xorg.conf " file. I did think it took user intervention to change that file .

I am presently stuck, and  may take me a while to learn the otherwise.

[INDENT][INDENT]which way did he go George
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-07-02
efonde; Update.

Not, It is discouraged to post without something positive to add.
All I can do is tell you that you are not left or forgotten. I do continue to seek how the system can rewrite that config file !

[INDENT][INDENT]just do not know better
[/INDENT][/INDENT]

---

### Post by efonde on 2015-07-04
> **Bashing-om said:**
> efonde; Yuk;

I honestly do not know

What could possibly be re-writing the " /etc/X11/Xorg.conf " file. I did think it took user intervention to change that file .

I am presently stuck, and  may take me a while to learn the otherwise.
[INDENT][INDENT]which way did he go George
[/INDENT]
[/INDENT]


yeah I don't know either. Weird enough the xorg.conf returned to default. Was it perhaps caused by the kernel 3.16 trusty I used?

---

