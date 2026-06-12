---
title: "Can I install Ubuntu 17.10 on AMD graphics card laptop?"
date: 2018-04-01
forum: Installation &amp; Upgrades
---

### Post by parag-93 on 2018-04-01
I want to install Ubuntu 17.10 on my laptop. It has AMD Radeon HD 8670M graphics. I've heard that latest versions of Ubuntu does not support graphics card drivers and during installation it doesn't boot. is there any way to install Ubuntu 17.10 in my laptop?

---

### Post by oldfred on 2018-04-01
Where are you getting that info?

 Linux 4.15 is what's tentatively slated as the default kernel for Ubuntu 18.04 LTS, among other distribution releases in H1'2018. 
Linux 4.15 Is A Huge Update For Both AMD CPU & Radeon GPU Owners
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-AMD-Mega](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-AMD-Mega) 
   [https://ubuntuforums.org/showthread.php?t=2372733](https://ubuntuforums.org/showthread.php?t=2372733)
If your card is supported by AMDGPU, it will be installed when you install Ubuntu. You can only install the AMDGPU-PRO overlay if AMDGPU is installed. If your card is not supported by AMDGPU, the Radeon driver will be installed.
It's automagic now. You don't need to do anything unless you have a need or pressing desire for the overlay-- for instance if you need Vulkan support. In that case, AMD has a script that will take care of it.  

If willing to recognize there may be issues which may even require reinstall, you can install 18.04 which will be final later this month. Generally best to only install current released versions and then LTS versions which 18.04 will be. 

There can be issues with any system with very new hardware. Vendors often do not directly support Linux like they do with Windows so Linux developers have to update & create drivers for that new hardware. That can take 6 month for kernel and even a year before in a standard distribution.


 The Fastest Linux Distribution For Ryzen: A 10-Way Linux OS Comparison On Ryzen 7 & Threadripper
[https://www.phoronix.com/scan.php?page=article&item=ryzen-linux-10way&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-linux-10way&num=1)

---

### Post by parag-93 on 2018-04-28
> **oldfred said:**
> Where are you getting that info?

 Linux 4.15 is what's tentatively slated as the default kernel for Ubuntu 18.04 LTS, among other distribution releases in H1'2018. 
Linux 4.15 Is A Huge Update For Both AMD CPU & Radeon GPU Owners
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-AMD-Mega](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-AMD-Mega) 
   [https://ubuntuforums.org/showthread.php?t=2372733](https://ubuntuforums.org/showthread.php?t=2372733)
If your card is supported by AMDGPU, it will be installed when you install Ubuntu. You can only install the AMDGPU-PRO overlay if AMDGPU is installed. If your card is not supported by AMDGPU, the Radeon driver will be installed.
It's automagic now. You don't need to do anything unless you have a need or pressing desire for the overlay-- for instance if you need Vulkan support. In that case, AMD has a script that will take care of it.  

If willing to recognize there may be issues which may even require reinstall, you can install 18.04 which will be final later this month. Generally best to only install current released versions and then LTS versions which 18.04 will be. 

There can be issues with any system with very new hardware. Vendors often do not directly support Linux like they do with Windows so Linux developers have to update & create drivers for that new hardware. That can take 6 month for kernel and even a year before in a standard distribution.


 The Fastest Linux Distribution For Ryzen: A 10-Way Linux OS Comparison On Ryzen 7 & Threadripper
[https://www.phoronix.com/scan.php?page=article&item=ryzen-linux-10way&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-linux-10way&num=1)

I've tried to install ubuntu 18.04 LTS after it finally released. But the same problem (black screen during boot) persists. My graphics card information is given below-

     ```
*-display UNCLAIMED       
       description: Display controller
       product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi cap_list
       configuration: latency=0
       resources: memory:a0000000-afffffff memory:c2000000-c203ffff ioport:4000(size=256) memory:c2040000-c205ffff

```
Is there any way to install any graphics driver?

---

### Post by oldfred on 2018-04-28
Have you tried nomodeset boot parameter?

Is this a Ryzen?
 ASUS PRIME B350M-E major issues 
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)

---

### Post by parag-93 on 2018-04-29
> **oldfred said:**
> Have you tried nomodeset boot parameter?

Is this a Ryzen?
 ASUS PRIME B350M-E major issues 
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)

Yes, I tried nomodeset and booted successfully. But after that I found no drivers for my graphics card. AMD GPU pro is also not installing. I have a AMD radeon HD 8670M graphics card. What can I do now?

---

### Post by oldfred on 2018-04-29
Have you updated the UEFI from the laptop vendor for your model?
Vendors have had to release new UEFI updates recently.

---

### Post by parag-93 on 2018-05-01
> **oldfred said:**
> Have you updated the UEFI from the laptop vendor for your model?
Vendors have had to release new UEFI updates recently.

Yes, I update the UEFI. But still it is not working.

---

### Post by oldfred on 2018-05-01
Is this what you have been doing?
[https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux)

---

### Post by parag-93 on 2018-05-04
[HR][/HR]> **oldfred said:**
> Is this what you have been doing?
[https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux)
Yes. I think I need a graphics driver. I've already tried the thing described in this link. But the problem is not solving.

---

### Post by the+phoenix on 2019-01-01
> **parag-93 said:**
> [HR][/HR]
Yes. I think I need a graphics driver. I've already tried the thing described in this link. But the problem is not solving.

Was your problem solved? Which version are you using finally? I am currently using Ubuntu 17.04. I have a R5 M430 video card and I am worried about graphic card compatibility if I upgrade to Ubuntu 18.04.

---

### Post by oldfred on 2019-01-01
Both 17.10 as in title & 17.04 are EOF - end of life. You get no new updates.

[https://en.wikipedia.org/wiki/Ubuntu_version_history](https://en.wikipedia.org/wiki/Ubuntu_version_history)

      ```

Version      Code name           Release date         Supported until       Kernel Version     
  
17.04       Zesty Zapus             April 2017              January 2018       4.10
17.10       Artful Aardvark        October 2017            Sept 2018          4.13
18.04LTS    Bionic Beaver           April 2018                April 2023          4.15
18.10        Cosmic Cuttlefish     2018-10-18               2019-07             4.18
19.04        Disco Dingo             2019-04-18               2020-01             TBA  


```

---

