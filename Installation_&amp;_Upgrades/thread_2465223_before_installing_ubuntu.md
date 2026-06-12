---
title: "before installing ubuntu"
date: 2021-07-26
forum: Installation &amp; Upgrades
---

### Post by hpezelj on 2021-07-26
[COLOR=#22231F][FONT=&quot]I'm interested in what I need to do in UEFI (BIOS) before installing ubuntu. The configuration is Lenovo IdeaPad UltraSlim 3 **Intel Core i5 1135G7** 2.40GHz 12GB 512GB **SSD** FreeDOS 15.6 "IPS Full HD Intel Iris Xe Graphics? Which is the recommended version of ubuntu 20.04TLS or ubuntu 21.04 thanks[/FONT][/COLOR]

---

### Post by guiverc on 2021-07-26
I don't know anything about your device, so this is *generic* advice.

I'd boot the systems and try them out on your actual hardware; compare for yourself to decide which you prefer. (*this applies to flavors too*)

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install](https://ubuntu.com/tutorials/try-ubuntu-before-you-install)

I'd usually decide between the LTS or non-LTS more by other things than hardware; ie. do you want the latest software and are willing to *release-upgrade* your system every 6-9 months, instead of doing it on a every-second/third/etc year period. 

The LTS releases are available using two kernel stacks, ie. the GA (original kernel) or HWE (*a stack that upgrades over the first two years of it's life*), thus many of the stack advantages of the non-LTS are available for LTS too; the LTS just gets it later.

The 21.04 kernel stack (5.11) is available for 20.04 when it reaches 20.04.3 (*it's still on 20.04.2 currently and using the 5.8 stack from 20.10*).  If you cannot wait - then the non-LTS is where you need to go.

But either way; you can **try the system on your actual hardware **before installing, so I'd do that and come to your own conclusions.  If you want to confirm those, or have questions, then I'd ask here.

---

### Post by CatKiller on 2021-07-26
> **guiverc said:**
> The 21.04 kernel stack (5.11) is available for 20.04 when it reaches 20.04.3 (*it's still on 20.04.2 currently and using the 5.8 stack from 20.10*).  If you cannot wait - then the non-LTS is where you need to go.
Informational rather than correctional; hwe-edge gets the updates (for further testing) before hwe. My 20.04 is already on 5.11.

---

### Post by tea for one on 2021-07-26
Are you dual booting with Windows 10?

If so, please read this first [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

There are also other settings (Windows and UEFI) to double check but please confirm if you intend to dual boot before we continue.

---

### Post by tea for one on 2021-07-26
Does your device have 11th Generation Intel Processor?

If so, you will probably need the kernel in Ubuntu 21.04.

---

### Post by hpezelj on 2021-07-26
No dual booting, i want only ubuntu.  yes, this is 11th generation intel processor. so the choice is ubuntu 21.04. do i need to change something in uefi because of ssd (for example raid to ahci)?
do something else settings in uefi need to be changed or disable?
thanks everyone

---

### Post by tea for one on 2021-07-26
_Checklist for[COLOR="#0000FF"] UEFI[/COLOR] settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

_Ubuntu checklist_

Boot into a live session in UEFI mode (how you boot determines the installation mode)
Check that you are in UEFI mode:-
Open a terminal and enter
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Check wifi, sound, graphics, mouse, keypad etc
Use gparted to create a GPT (GUID Partition Table)
Install Ubuntu using your own partition scheme (e.g. possibly a separate root and home)

---

### Post by hpezelj on 2021-07-26
> **tea for one said:**
> _Checklist for[COLOR=#0000FF] UEFI[/COLOR] settings_

1.Disable Secure Boot(solve)
2.Disable Fast boot(solve=Intel(R) Hyper-Threading Technology)
3.Disable Legacy mode(cant find)
4.Check that Legacy USB Support is enabled(cant find)
5.Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)(cant find)
6.Disable TPM(cant find)

can not find 3,4,5 and 6, attached images, thanks for helping

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288876&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=288877&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=288878&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=288879&stc=1[/IMG]

---

### Post by tea for one on 2021-07-26
No. 6 is Intel Platform Trust Technology (probably)

The checklist I mentioned is not [COLOR="#0000FF"]set in stone[/COLOR].

It is a general guide gleaned from previous difficulties encountered by various users with alternative hardware/UEFI/bios configurations.

You do not yet have an OS installed, therefore bite the bullet and install based on your own experience.

Everything can be fixed even if it means a re-installation.

Alternatively, send me your laptop by DHL and I'll sort it for you  ;)

---

### Post by oldfred on 2021-07-26
You probably need to update UEFI & SSD firmware first.

There seem to be some issues on kernels & Xe graphics. A flag needs to be set when compiling kernel and many do not yet have that.
Or you need most current version of any distribution and may still need to update to a newer or different kernel.

Squeezing More Performance Out Of Intel Tiger Lake Xe Graphics By Using Mesa Git 21.04 
[https://www.phoronix.com/scan.php?page=news_item&px=TGL-Xe-Graphics-More-Mesa-Git](https://www.phoronix.com/scan.php?page=news_item&px=TGL-Xe-Graphics-More-Mesa-Git)
Gen12 Xe Graphics might not be working out-of-the-box depending upon your kernel. 
Install OEM kernel
[https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372](https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372)

Similar generation Intel, but Dell & i7. May discuss issues.
ttps://www.phoronix.com/scan.php?page=news_item&px=Linux-5.10-Mesa-21.0-Xe-Compare

---

