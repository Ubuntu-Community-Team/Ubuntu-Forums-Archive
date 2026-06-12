---
title: "Ubuntu 18 won't install on Dell XPS 15 9570"
date: 2019-02-21
forum: Installation &amp; Upgrades
---

### Post by dean.w.schulze on 2019-02-21
I have a new Dell XPS 15 9570 with Windows 10.  I want to install Ubuntu (replace Win10 completely and run it in a VM on Ubuntu).  I have a bootable USB memory stick with Ubuntu 18 that I've used successfully to install Ubuntu 18 on an older desktop.

I can boot from the USB stick via the boot menu (F12 on start up).  I get the Ubuntu 18 desktop with the install Ubuntu icon.  During the installation process when it gets to where I partition storage the [COLOR=#242729][FONT=Arial]"device for boot loader installation" drop list only contains [/FONT][/COLOR]/dev/sda which is the USB stick itself.  It doesn't recognize the internal SSD which is where I want to install Ubuntu 18.

I tried playing with BIOS options.  Turning RAID off and AHCI on results in not being able to boot from the USB stick.  The F12 boot menu shows the USB stick but selecting it just gives a black screen.  I also can't boot into Windows 10.  The secure boot does not seem to be a problem with Ubuntu 18 since it boots from the memory stick and gives me the install option.

What do I have to do to install Ubuntu 18 on the internal SSD?

---

### Post by nicholasarussell on 2019-02-21
I had the same issue with my HP Ohmen.

here are my cut down steps Q.Q:

1. Download Ubuntu LTS 14.04.
2. boot into bios, check that secure boot is disabled and legacy is enabled, then set boot order to your instalation medium. (I used a latop drive VIA USB-C install took 5 mins) 
3. reboot while pressing the boot device selection button.
4. choose your boot device containing LTS 14.04
5. Install Ubuntu if issues load without graphics driver (second option no=acpi)
6. connect to the internet and open terminal.
7. Type "sudo apt update" and click enter
8. once completed type "sudo apt upgrade"
9. then when that is completed type "sudo do-release-upgrade"
10. after upgrade repeat steps 6-9 until you have your desired version XD.

Hope this helps XD, Enjoy!

P.S. Steams Proton is amazing running Flatout 4 and AOE2HD great!

-- ubuntu 18.04 LTS, Core i7-7700HQ, 16gb DDR4, GeForce GTX 1050/PCIe/SSE2 64bit

---

### Post by CatKiller on 2019-02-21
> **dean.w.schulze said:**
>  It doesn't recognize the internal SSD which is where I want to install Ubuntu 18.

Windows doesn't shut down: it simply hibernates, leaving the drive in a state that Linux won't touch. They call it fast boot. You'll need to turn that off.

Should you wish to boot into Windows, you'll also need to install an AHCI driver before you set the drive to AHCI in the BIOS. You don't want the drive to be set to RAID.

You'll also want to be using UEFI rather than Legacy, and you'll probably want to turn off Secure Boot.

---

### Post by ajgreeny on 2019-02-21
And don't forget that you will need a new license from Microsoft to be able to use Win 10 as a VM; unfair as it may seem you can not use the same install disk, if you had one from Dell, to install to VM as the hardware will be seen as different so far as the Windows OS is concerned.

---

### Post by dean.w.schulze on 2019-02-21
The fast boot option was under the POST menu item.  The options were Minimal (checked by default), Thorough, and Auto.  It sounds  like Thorough was the option that would disable fast boot, but it failed.

Now I can't even boot from the USB drive.  I tried restoring the default bios settings, and then the factory default settings but still can't boot from the USB.  Windows still boots, so maybe my USB stick has gone bad.

Dell tech support said that the issue might be trying to install Ubuntu on an M2 SSD and they provided these links in case they might help others:

[https://www.dell.com/support/article/us/en/19/sln308883/how-to-resolve-an-pcie-nvme-m2-ssd-ubuntu-kabuntu-installation-problem-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/19/sln308883/how-to-resolve-an-pcie-nvme-m2-ssd-ubuntu-kabuntu-installation-problem-on-your-dell-pc?lang=en)
[https://www.dell.com/support/article/us/en/19/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/19/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)
Loading Ubuntu on Systems Using PCIe M2 Drives
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

I have an Dell XPS 15 9560 that I've been running Ubuntu 16 on for 2 years and had no problems installing it.  It seems that the model 9570 had introduced some incompatibility with Linux.

---

### Post by oldfred on 2019-02-21
Many have installed to that Dell:

       Dell XPS 16 9570 Personal experience of installing Ubuntu 18.04 LTS
[https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe](https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe)
[https://ubuntuforums.org/showthread.php?t=2408749](https://ubuntuforums.org/showthread.php?t=2408749)
[https://ubuntuforums.org/showthread.php?t=2408585](https://ubuntuforums.org/showthread.php?t=2408585)
Dell 9570  Dell XPS 15 (9570), TB16 dock, and mixed DPI dual monitors
[https://askubuntu.com/questions/1092690/dell-xps-15-9570-tb16-dock-and-mixed-dpi-dual-monitors](https://askubuntu.com/questions/1092690/dell-xps-15-9570-tb16-dock-and-mixed-dpi-dual-monitors)
 Dell 9570 No nvidia Driver working - only one kernel version seems to work?
[https://ubuntuforums.org/showthread.php?t=2392938](https://ubuntuforums.org/showthread.php?t=2392938)
[https://askubuntu.com/questions/1042414/trying-to-install-ubuntu-on-dell-xps-15-9570](https://askubuntu.com/questions/1042414/trying-to-install-ubuntu-on-dell-xps-15-9570)
[https://askubuntu.com/questions/1046263/dell-xps-15-9570-2018-disable-nvidia-gpu](https://askubuntu.com/questions/1046263/dell-xps-15-9570-2018-disable-nvidia-gpu)

---

### Post by CatKiller on 2019-02-21
> **dean.w.schulze said:**
> The fast boot option was under the POST menu item.  The options were Minimal (checked by default), Thorough, and Auto.  It sounds  like Thorough was the option that would disable fast boot, but it failed.

It's Windows' own Fast Boot setting that you need to disable to have it shutdown properly and relinquish control of the drive. The BIOS *also* has a setting called Fast Boot, but that does something else entirely. 

> Now I can't even boot from the USB drive.  I tried restoring the default bios settings, and then the factory default settings but still can't boot from the USB.  Windows still boots, so maybe my USB stick has gone bad.

I have no idea about your on-again-off-again USB stick. 

> Dell tech support said that the issue might be trying to install Ubuntu on an M2 SSD

I've had zero issues with installing Ubuntu onto an M.2 drive.

---

### Post by CatKiller on 2019-02-21
> **dean.w.schulze said:**
> Turning RAID off and AHCI on results in not being able to boot from the USB stick.  The F12 boot menu shows the USB stick but selecting it just gives a black screen. 
If your configuration of the laptop has Nvidia graphics, you may need to use the nomodeset kernel parameter for the installation, and subsequent boots until you've installed the proprietary driver.

---

### Post by dean.w.schulze on 2019-02-21
Got Ubuntu installed on the XPS 15 9570.  Here's what worked.

I created a new bootable USB stick with Ubuntu 18.04.2.  Version 18.04 didn't work.  This seems to be the biggest factor.

The bios settings that had to be changed:

    SATA:  AHCI
    POST FastBoot:  Minimal

Hope this helps someone else.

---

