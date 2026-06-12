---
title: "ubuntu 13.04 USB bootable on Dell Latitue not properly working"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by rajTech on 2013-07-11
Hi, 

I am totaly new to Ubuntu and linux as well.  I just want try out ubuntu on my Dell laptop.
So I am using USB stick to boot and to try Ubuntu.  Having said that I haven't installed Ubuntu at all.
I just wants to tryout the Ubuntu and for that I don't want to touch the existing setup on my laptop.
But trying Ubuntu by bootable USB drive is not giving me the result which I can dare to install it on my loptop in dual mode along with my existing windows installation.
I tried Ubuntu 11, 12 and 13 as well but in the cases the same issues I found -
1. Firefox not work properly and it crashes now every and then.
2. Ubnutu gives unexpected error and stops responding, finally I had to have hard shutdown.
3. It does not shutdown properly when I tend to do it .  It show ubuntu logo in the middle of the screen and never progress further to shutdown.

Please suggest me whether I should go for Ubuntu on my machine or not?.

Thanks

---

### Post by praseodym on 2013-07-11
Does your laptop boot via BIOS or (U)EFI?

---

### Post by rajTech on 2013-07-12
Hi, I realy don't know about it(BIOS / UEFI) and searched on the net for how to know that BIOS/UEFI boot is using in a machine. 
But my laptop is having 64 bit support and currently Windows 7(64 bit) is  installed on it.
When I wants to run Ubuntu, I need to press F12 to get the options to boot from devices.
I will let you know about BIOS/UEFI boot after doing detailed analysis of my laptop.
But just wants to know how it affects on trying/installing Ubuntu (11 / 12 / 13.04)?

Thanks for the quick reply.
Raj

---

### Post by praseodym on 2013-07-12
Check here

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by rajTech on 2013-07-12
Thanks for the link.  This is a very good link considering installations in dual mode.
Really I didn't know the concept of UEFI boot, and thanks for intementing about it before I jump for the installation.
Will try  installation(USB boot) again as per the link.  Also I am facing Mobile broadband network issues on both Ubuntu and Mint (will post this on other thread).

Thanks,
Raj

---

### Post by rajTech on 2013-07-12
Hi,
I checked my laptop and it has option to boot with Leagacy(BIOS)  and UEFI option.  Current setting is BIOS and with this Windows7 is  installed.
I tried "ubuntu-11.10-desktop-i386" and  "ubuntu-13.04-desktop-i386" but both are giving me the same problem.   When I tried to download 64 bit version (12.04 / 13.04) it downloads  ubuntu-13/12.04-desktop-amd64.  I am concern with "...amd64".  My  motherboard is "intel", and I am doubt that this installation is for AMD  processors and that is why I am getting problem with it.
Please clarify my doubt and guide me which installation I can try.

Thanks,
Raj

---

### Post by praseodym on 2013-07-12
"amd64" also works with intel chips

---

### Post by oldfred on 2013-07-12
It is important to know if Windows is UEFI or BIOS. Ubuntu must be installed in the some mode and it installs in the mode you boot live installer. 

Post this, if it says msdos(MBR) then you have BIOS, if it says gpt(GUID) and you have an efi partition then it is UEFI.

sudo parted -l

Only use Windows to shrink Windows partition. Also check if you have used all 4 primary partitions as then you will have to back one up and convert it to the extended partition.

---

