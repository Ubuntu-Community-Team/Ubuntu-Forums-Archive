---
title: "UEFI Installation Problems"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by physicistus on 2014-12-15
I am new to linux. I tried to install the latest version of Ubunto 14.04.1 LTS from a USB stick. During the installation proccess, I chose the replace current OS with Ubuntu option. Upon reboot, my computer doesn't detect any OS and gives me the message to "insert an OS and reboot, press any key to continue". Pressing any key just makes the message reappear. I can only boot up from my USB. This computer came with Windows 8.1 preinstalled. Windows had fast boot. The only way I was able to get to the CMOS was through Windows. I did not know I was suppose to disable the UEFI before installation, Now I can't access the cmos, because windows has been wiped from my hard drive. From the sidebar I can see that hard drive partitions were made. I downloaded the grub-booter fixer thing. I choose the recommended option and it seamed to work without fault. It gave me the url: [http://paste.ubuntu.com/9524809/](http://paste.ubuntu.com/9524809/) as in the title of this post. However, I still get no OS error message as described before. I did use the terminal to do updates, but those didn't work. What can I do?

Edit: When I type in  

sudo fdisk -l

into my terminal I get

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

EDIT: I was able to access CMOS without Windows 8.1 by repeatedly tapping F1 and delete at the same time. From there I turned off the secure boot and disabled UEFI. Then I reinstalled.
After booting up a second time, Ubuntu booted up with out the USB connected.

---

