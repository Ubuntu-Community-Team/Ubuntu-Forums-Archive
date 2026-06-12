---
title: "Wont install from CD"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by Tobes1000 on 2013-07-01
Hey, today I have been trying to install Ubuntu Linux from a cd. Now I was told I should install it from a dvd, but this is the second time I have ever installed linux on a machine, and the first time I installed using a cd rom. I still have the same cd rom and I am trying to get ubuntu to install by rebooting the computer. I have shrunk enough space on my hard drive and the cd operates correctly, but when I reboot the pc, it just starts up with windows. Any help please? :D

EDIT: I have finally gotten it to install using some sort of help manager, but now it will not let me to connect to my wifi (the option to search for a connection is blocked out) and when I click on the dash home button it freezes my computer and I have to hard shut it down. Can I get some help please? I really hate using windows :(

---

### Post by Tobes1000 on 2013-07-01
support please? or is this the wrong place to post :P

---

### Post by VMC on 2013-07-01
We need more info. What version of Ubuntu, and what hardware do you have?

---

### Post by oldfred on 2013-07-01
New versions are oversize and do not fit on CDs, you need DVD or flash drive.
What version did you install?
Do you have a wired Ethernet connection?

From liveCD you can install this, or download the repair version tha tis a liveCD that includes Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Tobes1000 on 2013-07-01
Well I actually have the program installed from a cd, but the current problems I am having now is that it will not find my wifi, and when I click dash home it freezes the computer. I have installed the same linux distribution from the same disc on a previous computer and ubuntu worked great on that. It is Ubuntu 12.04 LTS

My computer specs

HP Pavillion G6

x64

Graphics card: Intel HD 3000 (I know :l)

if theres any other information you need let me know thanks!

and my internet is wireless

---

### Post by VMC on 2013-07-01
What's the output of this command:

```
ifconfig
```

---

### Post by oldfred on 2013-07-01
Intel is updating its drivers for the very new systems, but that supposedly is helping some of the older models.

 Force Intel Video mode as boot parameter in grub menu but change to your screen size.
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

   Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)
Intel HD4000
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
[http://ubuntuforums.org/showthread.php?t=2089640](http://ubuntuforums.org/showthread.php?t=2089640)
[http://ubuntuforums.org/showthread.php?t=2126191](http://ubuntuforums.org/showthread.php?t=2126191)
Also one used nolapic.
[http://ubuntuforums.org/showthread.php?t=2133816](http://ubuntuforums.org/showthread.php?t=2133816)
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"
Needs Raring & new kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175029](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175029)

---

