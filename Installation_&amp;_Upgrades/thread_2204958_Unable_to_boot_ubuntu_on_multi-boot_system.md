---
title: "Unable to boot ubuntu on multi-boot system"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2014-02-11
I am unable to boot my multi-OS computer using ubuntu.
I initially set up my computer with 1 ssd and 1 hdd.  I installed ubuntu on the ssd.
Due to a software incompatability (long story), I wanted to try Centos6, so I bought a second ssd and installed Centos6 on it.
I was then able to choose which OS to use by selecting the correct hard drive in the BIOS.
This worked correctly.
I discovered that the software didn't run under Centos6 either, so I tried to downgrade to Centos5 (I know the program in question runs properly under
Centos5).
The installation hung.

Unfortunately, I can now longer boot under Ubuntu.  The system now uses grub to boot, and I cannot just select in BIOS the ssd with ubuntu and boot from there.  I unplugged the ssd containing Centos6 and tried to boot.  The machine still tries to boot Centos6 (but obviously fails).  From Centos6, I can still access the other directories on the ssd that I initially loaded Ubuntu on, so I think the problem is grub.  Any ideas?

Thanks.

---

### Post by sudodus on 2014-02-11
Connect all SSDs and boot the computer (into Centos6). I don't know the details of Centos, but try with superuser privileges (as root or with sudo)

```
update-grub
``` and reboot. Then I hope that you get Ubuntu as one alternative.

---

### Post by oldfred on 2014-02-11
It seems like you did not install grub to the same drive as the install?

May be best to see details. Do not run auto repair as that just installs one grub to all MBRs. You want each MBR to have the grub for the system installed in that drive. You can use advanced and choose install and drive to install boot loader into.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by asb3 on 2014-02-11
I ran boot-repair.  The link is http:/paste.ubuntu.com/6918005.
Now what?
Thanks for your help.

---

### Post by oldfred on 2014-02-12
Does your Centos use grub legacy?
Ubuntu modified its version of grub legacy in 9.04 to work with ext4 partitions, but standard 0.97 did not. And Ubuntu converted to grub2 with 9.10.

You show grub2 in the MBR of sdc, does that boot?

Do not know much about LVM, is system also encrypted?

Some old systems may not work with newer LVM or gpt partitioning.

---

### Post by asb3 on 2014-02-13
Update-grub is not installed on my machine:
[asb@cavu ~]$ sudo update-grub
sudo: update-grub: command not found

yumex was unable to find it.

---

### Post by asb3 on 2014-02-13
> **oldfred said:**
> Does your Centos use grub legacy?

I don't know.  How do I find out?

> **oldfred said:**
> Do not know much about LVM, is system also encrypted?

My system is not encrypted.

---

### Post by asb3 on 2014-02-13
> **oldfred said:**
> It seems like you did not install grub to the same drive as the install?
I didn't want to install grub at all.

> **oldfred said:**
> May be best to see details. Do not run auto repair as that just installs one grub to all MBRs. You want each MBR to have the grub for the system installed in that drive. You can use advanced and choose install and drive to install boot loader into.
I wouldn't mind installing the one grub on all MBRs as long as I can choose the operating system I want.  The way I originally set it up, I chose the OS by changing the boot order in BIOS.

       > **oldfred said:**
> Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I tried boot-repair.  I made a boot disk containing boot-repair and I tried to run it.  When I clicked on the "Repair" button, a dialog box appeared with instructions to cut and paste some shell commands  into a terminal, but I was unable to find a terminal to open.

I then rebooted from the ubuntu CD and downloaded and ran boot-repair again.  Here are the commands I was asked to execute:

sudo chroot /mnt/boot-sav/mapper/ubuntu-root dpkg --configure -a
sudo chroot /mnt/boot-sav/mapper/ubuntu-root apt-get install -fy
sudo chroot /mnt/boot-sav/mapper/ubuntu-root apt-get install -y --force-yes dmraid
sudo chroot /mnt/boot-sav/mapper/ubuntu-root dmraid -ay
sudo chroot /mnt/boot-sav/mapper/ubuntu-root apt-get install -y --force-yes lvm2
sudo chroot /mnt/boot-sav/mapper/ubuntu-root apt-get purge -y --force-yes grub* shim-signed linux-signed*

I tried the first command and it failed:
>sudo chroot /mnt/boot-sav/mapper/ubuntu-root dpkg --configure -a

Setting up dictionaries-common (1.12.11) ...
update-default-wordlist: Question empty but elements installed for class "wordlist"
  dictionaries-common/default-wordlist: return code: "0", value: ""
  Choices: , Manual symlink setting
  shared/packages-wordlist: return code: "10" owners/error: "shared/packages-wordlist doesn't exist"
  Installed elements: american (American English), british (British English)

  Please see "/usr/share/doc/dictionaries-common/README.problems", section
  "Debconf database corruption" for recovery info.

update-default-wordlist: Selected wordlist "" 
does not correspond to any installed package in the system
and no alternative wordlist could be selected.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 dictionaries-common

Now what?

---

### Post by oldfred on 2014-02-13
Where you running that on the Centos install? As those commands are to chroot into your LVM with Ubuntu. And it looks like it is trying to update dictionaries which are not related. That just is something you may not yet have updated before. 
But if it cannot mount LVM then it cannot run any grub updates.

I do not know enough about mounting and chrooting into LVM to know how to do it manually.

---

### Post by asb3 on 2014-02-13
> **oldfred said:**
> Where you running that on the Centos install? .
I was running while booted using the ubuntu installation disk.

---

