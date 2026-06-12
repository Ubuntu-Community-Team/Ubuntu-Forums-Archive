---
title: "Blank screen after updating kernel from 4.10.0.33-generic to 4.10.0.35-generic."
date: 2017-09-26
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2017-09-26
A few days ago, I updated Ubuntu kernel from 4.10.0.33-generic to 4.10.0.35-generic. After this update, I now get a blank screen during boot-up.

Symptoms:
4.10.0.35-generic : Black screen after BIOS screen, hangs, does not go to login screen but can use Ctrl-Alt-Del to reboot computer
4.10.0.35-generic (upstart) : Black screen after BIOS screen, hangs, does not go to login screen but can use Ctrl-Alt-Del to reboot computer
4.10.0.35-generic (recovery mode) : Purple screen after BIOS screen, completely hangs, does not go to login screen and cannot use Ctrl-Alt-Del to reboot computer.

Questions:
1. How do I locate the exact issue(s) causing the boot failure of kernel 4.10.0.35-generic and how do I fix it? 
2. If I can't do (1), how do I revert to using kernel 4.10.0.33-generic as default for Ubuntu 16.04?

---

### Post by ajgreeny on 2017-09-27
You can boot into the previous kernel from the grub menu by choosing **Advanced** then highlight the 4.10.0-33 kernel from the list shown and hit **Enter**.  If you don't normally see the grub menu hold down Shift at power-on if your computer is using legacy BIOS, or if UEFI keep stabbing at Esc when you power-on.

Hopefully that will get you to your normal desktop from where you have several options to try and solve the problem with this latest kernel version.

It will probably help if we know the specs of your computer, in particular the graphics card, if it has a dedicated card.

---

### Post by sunbear-c22 on 2017-09-27
@ajgreeny, I have been doing that you have described to use Ubuntu 16.04. At the Grub menu, I have chosen to use [COLOR=#000000]the 4.10.0-33 kernel to boot Ubuntu 16.04 instead of 4.10.0.35[/COLOR][COLOR=#000000]. 

Q1. What should I do next to find out why [/COLOR][COLOR=#000000]the 4.10.0-35 kernel resulted in a blank screen at or after Grub?
[/COLOR][COLOR=#000000]Q2. If I want to revert to using [/COLOR][COLOR=#000000]the 4.10.0-33 kernel instead of the [/COLOR][COLOR=#000000]the 4.10.0-35 kernel to boot Ubuntu 16.04 as default, what should I do?[/COLOR][COLOR=#000000] 

I have a dedicated Nvidia card and has been using the nvidia 375.82[/COLOR][COLOR=#000000] long-lived driver with the 4.8 and 4.10 kernels without issue. I am now having blank screen and booting [/COLOR][COLOR=#000000]problems[/COLOR][COLOR=#000000] with 4.10.0.35.   [/COLOR]

---

### Post by ajgreeny on 2017-09-27
Check to see if you have the linux-headers packages installed for version 4.10.0-35 with ```
dpkg -s linux-headers-4.10.0-35-generic
``` as occasionally these header packages are missing when a new kernel appears and they are usually necessary to build the necessary nvidia kernel module in the new kernel.

You may even find that repeating your update command ```
sudo apt update
sudo apt full-upgrade
``` now pulls in any missing packages.

---

### Post by sunbear-c22 on 2017-09-27
I did the full-upgrade command. 

apt list --upgradable
Listing... Done
adapta-gtk-theme/xenial,xenial 3.91.2.198-0ubuntu1~xenial1 all [upgradable from: 3.91.2.195-0ubuntu1~xenial1]
gnome-software/xenial-updates 3.20.5-0ubuntu0.16.04.6 amd64 [upgradable from: 3.20.5-0ubuntu0.16.04.5]
gnome-software-common/xenial-updates,xenial-updates 3.20.5-0ubuntu0.16.04.6 all [upgradable from: 3.20.5-0ubuntu0.16.04.5]
libvulkan-dev/xenial 1.0.61.1+dfsg1-1~gpu16.04.1 amd64 [upgradable from: 1.0.54.0+dfsg1-1~gpu16.04.1]
libvulkan1/xenial 1.0.61.1+dfsg1-1~gpu16.04.1 amd64 [upgradable from: 1.0.54.0+dfsg1-1~gpu16.04.1]
libxnvctrl0/xenial 384.90-0ubuntu0~gpu16.04.1 amd64 [upgradable from: 384.69-0ubuntu0~gpu16.04.1]
numix-icon-theme/xenial,xenial 0.3+905~201709261926~ubuntu16.04.1 all [upgradable from: 0.3+905~201709241848~ubuntu16.04.1]
numix-icon-theme-circle/xenial,xenial 2.0.3+17~201709261930~ubuntu16.04.1 all [upgradable from: 2.0.3+17~201709131546~ubuntu16.04.1]
nvidia-settings/xenial 384.90-0ubuntu0~gpu16.04.1 amd64 [upgradable from: 384.69-0ubuntu0~gpu16.04.1]
ubuntu-software/xenial-updates 3.20.5-0ubuntu0.16.04.6 amd64 [upgradable from: 3.20.5-0ubuntu0.16.04.5]
vulkan-utils/xenial 1.0.61.1+dfsg1-1~gpu16.04.1 amd64 [upgradable from: 1.0.54.0+dfsg1-1~gpu16.04.1]


I noticed nvidia-settings (384.90-0ubuntu0~gpu16.04.1) is involved... 

During sudo apt full-upgrade, experienced core dump.
Setting up adapta-gtk-theme (3.91.2.198-0ubuntu1~xenial1) ...
Setting up gnome-software-common (3.20.5-0ubuntu0.16.04.6) ...
Setting up gnome-software (3.20.5-0ubuntu0.16.04.6) ...
Setting up ubuntu-software (3.20.5-0ubuntu0.16.04.6) ...
Setting up libvulkan1:amd64 (1.0.61.1+dfsg1-1~gpu16.04.1) ...
Setting up libvulkan-dev:amd64 (1.0.61.1+dfsg1-1~gpu16.04.1) ...
Setting up libxnvctrl0 (384.90-0ubuntu0~gpu16.04.1) ...
Setting up nvidia-settings (384.90-0ubuntu0~gpu16.04.1) ...
Setting up vulkan-utils (1.0.61.1+dfsg1-1~gpu16.04.1) ...
Setting up numix-icon-theme (0.3+905~201709261926~ubuntu16.04.1) ...
Setting up numix-icon-theme-circle (2.0.3+17~201709261930~ubuntu16.04.1) ...
gtk-update-icon-cache: Cache file created successfully.
Processing triggers for libc-bin (2.23-0ubuntu9) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Bus error (core dumped)





Going to try to reboot the system to see what happens.
Tested... 4.10.0.35-generic still result in blank screen. 
Should I remove 4.10.0.35-generic completely and try upgrading the kernel again? How do I remove 4.10.0.35?

---

