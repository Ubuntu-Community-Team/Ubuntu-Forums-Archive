---
title: "Dual boot Windows 8.1 &amp; Ubuntu on a System with AMD Radeon HD 8600M series"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by bsr1100 on 2016-08-16
Hi there,

As the subject states, I am looking for dual boot setup on my system and currently have Windows 8.1. The system configuration is as follows,
[U][I]
Config[/I][/U]
i5-6200U, 8GB DDR4 RAM, 1TB HDD, 2GB AMD Radeon HD 8600 M series (not sure about the precise model)

Searching the interwebs, I find that there is no support for the AMD Radeon series on the latest Ubuntu release 16.04 LTS. ([http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)) Although this is old news, I didn't find any fix for the issue in the recent posts either. Mostly people are told to revert back to the older 14.04.x releases to peruse fglrx OR use AMDGPU with 16.04 with not the best performance. If I'm wrong and there is indeed a fix pls point me in the right direction.

If not, what is the best course of action. Which is the best Ubuntu release that helps leverage the GPU functionality? I would request precise answers for the versions suggested.

PS: Not sure if this info is useful but, 
1) I ran CPU-Z to find the exact GPU model but unfortunately it lists my GPU as Intel HD graphics 520. However, the Device Manager lists both of them under the "Display Adapters".
2) Windows is booted under BIOS and not UEFI. As evidenced by the string value "Callback_BootEnvironmentDetect: Detected boot environment: BIOS" @ C:\\Windows\Panther\setupact.log

PPS: I don't do any gaming. I'll be running Matlab, Eclipse, Visual Studio and Android Studio frequently. Maybe a year down the lane I'll frequently run Adobe Photoshop. I'll use Hadoop, after the Ubuntu setup. So, based on **PS 1) **the CPU-Z output, it seems like the (AMD) GPU is not enabled/active. Could I just install 16.04 and use the default open source drivers for Intel HD Graphics 520 and proceed without any display issues?

Please let me know, if any more info is needed.

---

