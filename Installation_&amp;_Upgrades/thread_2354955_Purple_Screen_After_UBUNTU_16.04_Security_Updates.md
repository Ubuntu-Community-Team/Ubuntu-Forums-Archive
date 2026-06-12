---
title: "Purple Screen After UBUNTU 16.04 Security Updates"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2017-03-08
I am using Ubuntu 16.04. 
After agreeing to latest security updates today, which required a reboot, my system only reboots to a purple screen with no mouse pointer and no GUI. 
Alt+Ctl+ F1 upto F7 does not work. That is, I can't get to any non graphical terminal to check the issue.
 It am guessing the system is running behind the purple screen but I can't see anything. 
I am using NVIDA proprietary driver.
Prior to this, everything was working fine.

Any advice on how I can recover from this issue w/o reinstalling the entire system?

---

### Post by Perfect Storm on 2017-03-08
This might be helpful: [http://askubuntu.com/questions/737189/purple-screen-on-boot-nvidia-960-and-no-acces-to-recovery-mode](http://askubuntu.com/questions/737189/purple-screen-on-boot-nvidia-960-and-no-acces-to-recovery-mode)

---

### Post by sunbear-c22 on 2017-03-08
> **Artificial Intelligence said:**
> This might be helpful: [http://askubuntu.com/questions/737189/purple-screen-on-boot-nvidia-960-and-no-acces-to-recovery-mode](http://askubuntu.com/questions/737189/purple-screen-on-boot-nvidia-960-and-no-acces-to-recovery-mode)


I tried [COLOR=#000000]boot by removing splash on boot line: hold "shift" key down at end of bios process if grub menu is hidden.


[/COLOR]I can't get GRUB by pressing shift. It just proceed with booting into a purple screen. Any suggestion?

---

### Post by Perfect Storm on 2017-03-08
try [esc]

---

### Post by sunbear-c22 on 2017-03-08
Esc key works.
Get Minimal BASH-like line editing is supported.
Press TAB get a list of commands that is supported.
What do I do next?
[IMG]afc://1bedd8fea3b674fafc51b0aca4a7ddd78f824dc1/DCIM/114APPLE/IMG_4792.JPG[/IMG]

---

### Post by Perfect Storm on 2017-03-08
enter:
```
nouveau.modeset=0
```

then press <f10> to boot

---

### Post by sunbear-c22 on 2017-03-08
Before I type this cmd, may I know if nouveau packages are required? 
I ask because my NVidia driver installation previously had removed and purged nouveau drivers.

What does [COLOR=#000000][FONT=&quot]nouveau.modeset=0 means/do?[/FONT][/COLOR]

---

### Post by Perfect Storm on 2017-03-08
you can also use **nomodeset** which means it won't read the driver and uses BIOS modes instead until X is loaded. When you reboot it will be set back to normal so no harm done.

But if nv is unistalled I would go with **nomodeset**

---

### Post by sunbear-c22 on 2017-03-08
Clarification. So I should type:

"nomodeset" (no need to press <Enter>) 
press <f10>

---

### Post by Perfect Storm on 2017-03-08
aye. I'm not sure if you have to press enter or not. Can't recall.

---

### Post by sunbear-c22 on 2017-03-08
I typed "nomodeset" pressed <Enter> and got "error: can't find command 'nomodeset'. "
I typed "nomodeset" pressed <F10> and nothing happened.

Pressed <Tab>. 
Possible commands are:

. [ acpi all_functional_test appleloader authenticate background_color background_image backtrace badram blocklist boot break cl at cbmemc chainloader clear cmp configfile continue coreboot_boottime cpuid crc cryptmount cutmem data distrust dump echo eval exit export extract_entries_configfile extract_entries_source extract_legacy_entries_configfile extract_legacy_entries_source extract_syslinux_entries_configfile extract_syslinux_entries_source fakebios false file fix_video functional_test fwsetup gettext gptsync halt hashsum hdparam hello help hexdump inb initrd initrd16 initrdefi inl insmod inw keymap keystatus kfreebsd_loadenv kfreebsd_module kfreebsd_module_elf knetbsd knetbsd_module knetbsd_module_elf kopenbsd kopenbsd_ramdisk legacy_check_password legacy_configfile legacy_initrd legacy_initrd_nounzip legacy_kernel legacy_password legacy_source linux linux16 linuxefi list_env list_trusted load_env loadbios loadfront loopback ls lsacpi lscoreboot lsefi lsefimmap lsefisysta b lsfonts lsmmap lsmod lspci lssal macppcbless mactelbless md5sum menuentry module module2 multiboot multiboot2 nativedisk net_add_addr net_add_dns net_add_route net_bootp net_bootp6 net_del_addr net_del_dns net_del_route net_get_dhcp_option net_ipv6_autoconf net_ls_addr net_ls_cards net_ls_dns net_ls_routes net_nslookup normal normal_exit outb outl outw parttool password password_pbkdf2 pcidump play probe read read_byte read_dword read_word reboot regexp return rmmod save_env search search.file search.fs_label search.fs_uuid serial set setparam setpci sha1sum sha256sum sha512sum shift sleep source submenu syslinux_configfile syslinux_source terminal_input terminal_output terminfo test test_blockarg testload testspeed time tr true trust unset usb verify_detached videoinfo videotest write_byte write_dword xnu_devprop_load xnu_kernel xnu_kernel164 xnu_kext xnu_kextdir xnu_mkext xnu_ramdisk xnu_resume xnu_splash xnu_uuid zfs_bootfs zfsinfo zfskey 

Clarification. It is GRUB2.

Question. How do I exit from GRUB2 and reboot to BIOS?

---

### Post by Perfect Storm on 2017-03-08
type **normal**

---

### Post by Perfect Storm on 2017-03-08
you should be able to press <shift> and <e> before it boot up. Works on mine.

Then find the line that says linux and add the following nomodeset (right after quiet splash).

---

### Post by sunbear-c22 on 2017-03-08
I used "help" "GRUB2_cmd" to see the use of each command. 
I found the "reboot" cmd. Rebooted system. I could hear some sound from my speaker after the boot, common to a warning or error toggle sound from my desktop. I suspect the system is running behind the purple screen. 

I read from tommcd (the link you gave) that "*[COLOR=#000000]If you used the driver from nvidia.com, you should know that you need to reinstall the driver whenever there is a kernel [/COLOR][COLOR=#417394]update[/COLOR]*[COLOR=#000000]* for Ubuntu.*" 
I had not done this. Did not know I had to do this. Is this why I am getting the purple screen....?[/COLOR]

---

### Post by Perfect Storm on 2017-03-08
That's very likely if you installed the drivers manually.

---

### Post by sunbear-c22 on 2017-03-08
I tried "normal" <Enter>.
It immediately boot up back to  the purple screen. I tried <shift> <e> while it was booting up but nothing happened.

I rebooted my system. This time during the BIOS page or near the end of it, instead of holding the <Esc> for a long time, pressed it once or twice, I got to a GRUB2 menu. I chose "Advance...." (I think), and got a list/history of the kernels of my system, from the most recent to when it was installed. I selected the kernel version prior to the updated kernel that caused the purple screen. **HURRAY, EVERYTHING IS BACK TO NORMAL**. 

Questions. 
1. What do I do next to prevent the purple screen from re-occurring? I suspect when I reboot, normal boot will mean booting into the new kernel that gave me a purple screen. Working linux kernel is 4.4.0-64-generic. The update kernel with problem is  4.4.0-66-generic.
2. How do I reinstall my NVidia driver to the new kernel version, if it is causing the purple screen with the new kernel? The reason why I need this driver version is because it is compatible with CUDA 8.

---

### Post by Perfect Storm on 2017-03-08
You need to install the nvidia driver against the newer kernel, that's why you need to boot into the new kernel and install the driver there. 

Instead of hitting advance you hit "e" to get to the grubs kernel parameters.

---

### Post by sunbear-c22 on 2017-03-08
> **Artificial Intelligence said:**
> You need to install the nvidia driver against the newer kernel, that's why you need to boot into the new kernel and install the driver there. 

Instead of hitting advance you hit "e" to get to the grubs kernel parameters.

What do you mean "[COLOR=#000000]Instead of hitting advance you hit "e" to get to the grubs kernel parameters.[/COLOR]" What is advance?

[COLOR=#000000]Earlier your wrote "you should be able to press <shift> and <e> before it boot up. Works on mine." Is <e> same as pressing the e key?[/COLOR]

---

### Post by Perfect Storm on 2017-03-08
aye

---

### Post by sunbear-c22 on 2017-03-08
I did reboot to reattempt the procedure, reboot, during BIOS page press <Esc>, holding the <Esc> down long will skip GRUB2 menu and go into the purple screen with  [COLOR=#000000]Minimal BASH-like line editing is supported. At the GRUB prompt, I typed normal and <Enter> and I immediately hold down <Shift> + <e> all the way. The system still continue to boot up to the "purple screen".  I have not found a way to implement your instruction on:

[/COLOR][COLOR=#000000]> [INDENT]you should be able to press <shift> and <e> before it boot up. Works on mine.

Then find the line that says linux and add the following nomodeset (right after quiet splash).[/INDENT]

[/COLOR]

I am very glad to have your help and appreciate it. I would not have gone so far and learned so much if not for your help. I am just stuck at this step.

If I can't figure this out, another approach I am thinking is whether it is possible to 
1. safely remove the latest kernel so that it will reboot using [COLOR=#000000]4.4.0-64-generic.
2. uninstall NVIDIA driver and reinstall the same version driver using 
[/COLOR][COLOR=#333333]    sudo add-apt-repository ppa:graphics-drivers/ppa[/COLOR]
[COLOR=#333333]    sudo apt-get update
3. Then let Ubuntu update to upgrade my kernel. 
Do you thing it could work too? [/COLOR]

---

### Post by Perfect Storm on 2017-03-08
That's a good idea. Boot into the previous kernel uninstall the driver. then reboot into the new kernel and install the driver.

---

### Post by sunbear-c22 on 2017-03-08
I tried <Ctrl>+<Alt>+<F1>. However, I find that tty1 is obstructed by a black screen. There is no way to see the command prompt to login, stop lightdm, and uninstall Nvidia driver. Bummer...  

Is there a way to safely remove the new kernel so that for the moment it will only boot up using the driver before update? This is to allow me to pursue updating to the Linux new kernel later.

---

### Post by Perfect Storm on 2017-03-08
Use synaptic to remove newer kernels:
linux-headers-x.x.x
linux-image-x.x.x

where x is number of the version you want to remove.

---

### Post by sunbear-c22 on 2017-03-08
Clarification: Do I just do removal or complete removal of these 2 files?

---

### Post by Perfect Storm on 2017-03-08
In synaptic you can lock your preferred kernel. Find your kernel and select 'Package' ---> 'Lock Version'

---

### Post by Perfect Storm on 2017-03-08
> **sunbear-c22 said:**
> Clarification: Do I just do removal or complete removal of these 2 files?

Complete removal.

---

### Post by sunbear-c22 on 2017-03-08
Synaptic is also requesting the complete removal of linux-image-extra-4.4.0-66-generic and linux-image-generic. 
I think removing the formal is ok since it is part of 4.4.0-66 but do I agree to the latter?

---

### Post by Perfect Storm on 2017-03-08
yeah it's fine.

---

### Post by sunbear-c22 on 2017-03-08
Synaptic recommended the following

Complete removal of: 
linux-headers-4.4.0-66
linux-image-4.4.0-66

Removal of:
linux-generic
linux-headers-4.4.0-66-generic
linux-headers-generic
linux-image-extra-4.4.0-66-generic
linux-image-generic
linux-signed-generic
linux-signed-image-4.4.0-66-generic
linux-signed-image-generic

I also locked the kernel. Rebooted successfully using 4.4.0-64.
I did try to <Ctrl><Alt><F1> but tty1 is still obstructed by a black screen. This leaves me no way to uninstall the Nvidia proprietary driver.

---

### Post by Perfect Storm on 2017-03-08
Try and see if you can do it in tty2
<Ctrl><Alt><F2>

---

### Post by sunbear-c22 on 2017-03-08
Same issue with tty 2,3,4,5,6.

---

### Post by Perfect Storm on 2017-03-08
I don't know the answer to that problem. I guess it's a driver issue(nvidia). Perhaps starting a new thread about it.

---

### Post by sunbear-c22 on 2017-03-08
Sure. Grateful for your help. :) 
I regard my question answered/solved. Is there anything I should do?

---

