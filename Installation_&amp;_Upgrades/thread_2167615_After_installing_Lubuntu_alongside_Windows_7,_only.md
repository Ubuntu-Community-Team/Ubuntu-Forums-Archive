---
title: "After installing Lubuntu alongside Windows 7, only Win7 boots.  No boot menu"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by Falen on 2013-08-14
I recently installed Lubuntu 13.04 alongside Win7 but after I reboot, the computer boots directly into Win7 as if I didn't even install Lubuntu. I tried this a couple of time.  What the heck is going on?  I have installed Lubuntu with Windows before but that was using older motherboards (pre-UEFI).  I am currently trying to installing Lubuntu on a system using the "Gigabyte GA-Z87X-D3H" motherboard.  Is there some kind of settings I need to set to get this to work?

Thanks in advance.

---

### Post by GwL3eNC on 2013-08-14
Hi,

it's possible that the bootloader grub was not installed correct. Do you have more than one drive?

---

### Post by Falen on 2013-08-14
Yes, there a multiple drives.

Windows on one and Lubuntu on the other and a third drive.

---

### Post by Boab1993 on 2013-08-14
Hi there Falen,

A quick easy user friendly fix is download the PLOP boot manager: [http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)

If you don't like it i can suggest other solutions.

Hope this helps.

---

### Post by GwL3eNC on 2013-08-14
Hi,

the easiest thing i can think about is that you install grub (for example lubuntu is on hd2) in the master boot sector of hd2
then your bios dont know if you want to start it. Then you must select in your bios the second hd as first boot drive. 
I cant tell you exactly what you should do, because if i tell you something wrong without a boot cd nothing will work.
Normally grub must be placed in the master boot sector of your first harddrive. In ubuntu you can use grub-customiser
which simplifys things. There is also an option to install grub in master boot. You can boot from ubunru cd and install it
with

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
 sudo apt-get update
sudo apt-get install grub-customizer

Hopfully it can autodetect you windows installation.  Also the Idea von Boab sounds good. Evtl. it better to go
his way.

Ps: Many people here suggest a thing called boot-repair. Dont know that.

---

### Post by Falen on 2013-08-14
When I installed Lubuntu, it did detect Windows and auto-selected the drive(master boot) to install grub but I will try again when I get home.

I will also read up on boot-repair later.

---

### Post by Falen on 2013-08-14
> **Boab1993 said:**
> Hi there Falen,

A quick easy user friendly fix is download the PLOP boot manager: [http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)

If you don't like it i can suggest other solutions.

Hope this helps.

I try this when I get home later.  Thanks.

---

### Post by oldfred on 2013-08-15
Plop is good for systems that will not boot a USB flash drive.

Your issue is the new UEFI. Did you install all systems on every drive in UEFI mode? And have you gone into UEFI to select to boot ubuntu UEFI entry. All systems must be installed in the same boot mode either all UEFI or all BIOS/CSM/Legacy.

Best to see details.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Link in my signature has a lot of useful UEFI info, including multiple drive UEFI installs. Several users have posted how to do it.

---

### Post by Falen on 2013-08-15
I tried using boot-repair and afterwards, I no longer have a boot partition.

---

### Post by oldfred on 2013-08-16
Boot-Repair does not delete partitions.

Post the link to the BootInfo report it creates.

---

