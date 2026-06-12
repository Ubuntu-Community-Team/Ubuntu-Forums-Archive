---
title: "external usb install"
date: 2023-08-09
forum: Installation &amp; Upgrades
---

### Post by mcyber4 on 2023-08-09
booted with a rufus usb stick, selected install to what i thought to be my external hd. (not sda or sdb) I've 2 internal hd. Now I cannot boot form external hd and my windows drive D is not accessible (says i need to format to access) Important stuff on D:
that's with the latest lts...
so how to fix all this.
thanks

---

### Post by yancek on 2023-08-09
Boot the Ubuntu install USB and select the Try Ubuntu option.  You will need to connect to the internet and go to the site below and get boot repair.  Use the 2nd option described on the page adding the ppa.  When boot repair runs, select the Create BootInfo Summary option and post the link you get when it finishes here.  Do not try to make any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Questions needing to be answered:  which version of windows? is it UEFI or Legacy install?  can you boot the newly installed Ubuntu?  Which drive is set to first boot priority?

---

### Post by mcyber4 on 2023-08-09
Thanks. Silly me selected wrong HD, now all is fine. Haven't used Ubuntu for years. Any simple solution to not mount my Windows HDs? I'll find out... now on to reinstall stuff on Windows D:.

---

### Post by mcyber4 on 2023-08-09
Selected proprietary Nvidia driver (top from the list) and now it doesn't boot anymore. Why, what to do? I cannot access grub menu.

---

### Post by ubfan1 on 2023-08-09
Wait a bit at boot, letting grub (not showing) get past its timeout, then try to start a virtual terminal (ctrl+alt+Fn3), login, and see what modules are loaded (lsmod) (nvidia?) and maybe try startx.

---

### Post by mcyber4 on 2023-08-09
Waited 5 minutes or so. Then did a fresh install. So how to install Nvidia RTX 2080? Hopefully it's not a portable usb problem as I need 3D acceleration.

---

### Post by ubfan1 on 2023-08-09
I just use the Software & Updates/Additional drivers tab, select the driver I want...  Command line is possible via ubuntu-drivers, but I seldom use that. I use the 535.86.05, not the "...open" one, which seems to cause some problems with some scripts expecting the name to end in a version number.

---

### Post by TheFu on 2023-08-09
> **mcyber4 said:**
> Thanks. Silly me selected wrong HD, now all is fine. Haven't used Ubuntu for years. Any simple solution to not mount my Windows HDs? I'll find out... now on to reinstall stuff on Windows D:.

^^^^^^^^
THIS is why I don't ever recommend dual boot setups.  Use a virtual machine instead.  Then there's no confusion as to which OS controls booting.  Plus, the virtual machine won't need any funky drivers, since the VM will provide extremely well-know virtual hardware to the client machine.  Often, performance will be excellent, it is just gaming where it can become complex, since access to the real GPU hardware isn't normal.  There are ways to pass-thru a GPU to a VM for dedicated use, but that means it cannot be used by the host system, so you'll need 2 GPUs for this to work and one of them will need to be a more serious GPU - cheap GPUs need not apply.

If you don't need direct GPU access, like for typical server or office-productivity things, then the VM is definitely the way to go, until you don't need MS-Windows anymore or can switch out the host system from MS-Windows to Linux and run MS-Windows inside a VM, only when needed.  I'm down to 2 things that I need MS-Windows for and boot up a Windows VM for about 10 minutes, once a week.

---

### Post by mcyber4 on 2023-08-10
Virtual machine is not an option for me as I need it for Vulkan development. Tried X-Plane, works fine but didn't like 4k resolution. On Windows 4k is as fast as 2k probably because of Freesync. Need to test that further and is not important for me. I like my setup. No mess with Windows bootloader and simply unplug the HD when I don't need it for a while.

---

### Post by yancek on 2023-08-10
>  Any simple solution to not mount my Windows HDs? 

Check your /etc/fstab file to see if there is a line entry for any windows partition.  If so, uncomment it by placing a # at the beginning of the line.

---

### Post by TheFu on 2023-08-10
> **yancek said:**
> Check your /etc/fstab file to see if there is a line entry for any windows partition.  If so, uncomment it by placing a # at the beginning of the line.

Ubuntu/Linux desktops has a bad habit of udisks2 automatically mounting file system it recognizes even when those mounts aren't specifically requested by the sys admin. This is one of those "it is more convenient" decisions made for end-users, whether they ask for it or not.  Some File Managers have settings to do nothing, ask what to do, or automatically mount file systems.

The power to mount is the power to destroy, so I disable it.  Only a system admin should be allowed to mount storage, IMHO. Opinions about that differ.

Anyway, the simple way to prevent a storage device from being used is to unplug it from the computer.  However, since the UEFI standard really wants only 1 UEFI partition inside a computer, this can be problematic and prevent normal booting where a menu of possible OSes is displayed.  You'd need to use the BIOS to select a specific drive to boot from or use some efi-manager to choose. 

Whether any of this is "simple" or not is a judgement call.  It is certainly more hassle.  For my hassle-free life, I find it 100x easier to put the 2nd, 3rd, ... 10th OS into a virtual machine, so that no choice need be made at boot time.

---

### Post by mcyber4 on 2023-08-10
Checked again and no it doesn't mount automatically my Windows HDs so I'm fine. Thanks for all help.

---

