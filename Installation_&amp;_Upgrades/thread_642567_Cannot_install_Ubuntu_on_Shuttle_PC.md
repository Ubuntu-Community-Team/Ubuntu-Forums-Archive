---
title: "Cannot install Ubuntu on Shuttle PC"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by pacerhill on 2007-12-16
I'm a newbie to Linux and I'm having great trouble trying to install Ubuntu 7.10 Server edition on my New Shuttle PC 64-bit AMD.

First of all I have bought 2 500GB SATAII disks that I would like to RAID mirror, but Ubuntu sees them as 2 individual disks. I have selected RAID-1 array in my BIOS setup. If I proceed to install Ubuntu, selecting one of the disks, I get a 'GRUB Loading stage 1.5' repeat itself down the screen after rebooting at the end of installation. Therfore I decided to proceed with just 1 disk to install Ubuntu.

After, removing the RAID configuration in the BIOS, I proceed to install Ubuntu without errors. However, after rebooting at the end of the installation, I was expecting some kind of gui login like in 'Windows'.

 I have a built in NVIDIA 7050PV graphics card and when I try to run startx I get a 'Fatal server error: 'No valid FontPath could be found' XIO: fatal IO error (Connection reset by peer) on X server.

I've been on the NVIDIA site and have tried to install their latest Linux drivers and failed. I've been hunting around on these fourums for days and I cannot find a solution to get my screen working. I've even installed the LinuxMCE and still have this error.

Can someone first of all tell me if I am wasting my time trying to get RAID-1 setup on the NVIDIA BIOS before installing Ubuntu/Kubuntu?

Secondly, I cannot get a gui after installing the OS. Do I need to apt-get packages? I am using a Dell 1594FP digital monitor that has a max resolution of 1024x768@60Hz.
How do I install the lastest NVIDIA drivers so that Ubuntu/Kubuntu recognises it?

My shuttle model is SN68PTG6.

Thanks,

Pacerhill

---

### Post by Pumalite on 2007-12-16
[http://ubuntuforums.org/archive/index.php/t-105372.html](http://ubuntuforums.org/archive/index.php/t-105372.html)

---

### Post by pacerhill on 2007-12-17
Thanks for the link on installing the desktop enviroment.

Can anyone answer my question on RAID-1 array mirroring support and if it is supported on ubuntu?

Many thanks

---

### Post by Pumalite on 2007-12-17
> **pacerhill said:**
> Thanks for the link on installing the desktop enviroment.

Can anyone answer my question on RAID-1 array mirroring support and if it is supported on ubuntu?

Many thanks

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by pacerhill on 2007-12-17
> **Pumalite said:**
> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Thanks Pumalight,

I think this is what is was looking for. I'll follow the instructions and let the readers know how I got on with the RAID

---

### Post by Pumalite on 2007-12-17
> **pacerhill said:**
> Thanks Pumalight,

I think this is what is was looking for. I'll follow the instructions and let the readers know how I got on with the RAID

Good luck!

---

### Post by pacerhill on 2007-12-19
I'm still having issues with my graphics card. I cannot get a gui displayed. I get the following error if I run Startx:

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server":0.0"
after 0 requests(0 known processed) with 0 events remaining.

I then proceeded to install the latest drivers from NVIDIA's website with the command 'sudo sh NVIDIA-Linux-x86_64-169.04-pkg1.run', but it asked for 'libc' to be installed which I managed to do with an apt-get. After this I ran the command again, but this time the NVIDIA driver installer said the following:

No precompiled kernel interface was found to match your kernel.....

..it then said the installer will try to compile the kernel but then i got the following error:

ERROR: Unable to find the kernel source tree for the currently running kernel. please make sure you have installed the kernel source files for your kernel abd that they are properly configured...

Basically I have searched around these forums for a solution, but I am a bit lost as to what I should do next. Therefore, please can I have some assistance to get my NVIDIA driver configured?

Many thnaks :)

---

### Post by Pumalite on 2007-12-19
sudo aptitude install build-essential
Then try again.

---

### Post by pacerhill on 2007-12-20
Hi,

I had already tried this command, but I have just tried it again and I still have the same error ()fatal IO error 104) when I try to install the NVIDIA drivers.

When running 'sudo aptitude install build-essential' there are errors such as:
Errors were encountered while processing:
acpid
ubuntu-desktop
acpi-support
powermanagement-interface
kubuntu-desktop

Further up these error messages, I see statments such as 'kubuntu-desktop depends on acpi-support; however: Package acpid is not configured yet'. To me it suggests the errors reported have not been configured.
Is there a way to configure acpid, ubuntu-desktop, acpi-support, powermanagement-interface and kubuntu-desktop from the command line?

Please can you suggest what I tackle next to get my gui working?

Thanks

---

### Post by pacerhill on 2007-12-20
[SOLUTION]

after searching many forums I found that running the following commands enabled my NVIDIA driver to be installed:

command 1: uname -r
response: 2.6.22-14-server

I then proceeded to enter the following commands specifiying my kernel version.

command 2: sudo apt-get install linux-image-2.6.22-14-server
command 3: sudo apt-get install linux-headers-2.6.22-14-server

I rebooted my shuttle PC

I then logged into the console

command 4: sudo killall kdm
(I think you can issue gdm instead of kdm if you are running gnome)

I then mounted my cdrom and installed the latest NVIDIA drivers and the install ran successfully without errors.

command 5: startx
response: GUI started finally!!!!!!!!!!!!

---

