---
title: "unable to do fresh install on Lenovo X220 with SSD"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by globalgoat on 2016-06-02
Hi, been having some trouble installing 16.04 on one of my old Lenovo X220. Symptoms are these:

Boot in live mode from USB
select to erase everything for fresh install
install appears to work ok without error
when reboots throws error VFS: unable to mount root fs on unknown block(0,0)

I've been through other threads with this error. Troubleshooting I've done so far:

1. confirmed install media is OK - have installed on another machine with this usb media
2. confirmed machine is OK - have re-installed windows 10 successfully after ubuntu failure, wiping the disk (it was a windows 10 machine originally)
3. have tried manual partition selection - delete everything with install wizard and configure partitions manually
4. have tried wiping and formatting disk with various utilities before installing (from windows 10 boot disk, and from gparted live disk)
5. If i try recovery mode boot I get the same thing

if i go into grub command line I get the following (following fresh install from live usb stick, with default options from wizard to erase everything)

following thoughts from this article

I've also tried following the advice here
[https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux)

ls
(hd0) (hd0,msdos5) (hd0, msdos1)

cat (hd0,1)/etc/issue

Ubuntu 16.04 LTS \n \1

(replacing the kernel with the relevant one using tab key to find it)

grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1
grub> initrd /boot/initrd.img-3.13.0-29-generic
grub> boot
and now the message is same error at kernel panic, but against block(8,1).

I have no data to save or recover or any such, I just want to do a fresh clean install.

Any thoughts appreciated.

---

### Post by QIII on 2016-06-02
Hello!

If this is an SSD, then I would highly recommend following the instructions [here]("https://wiki.archlinux.org/index.php/SSD_memory_cell_clearing") to restore your SSD to factory default.  SSDs operate differently than mechanical drives.  You cannot simply overwrite sectors on an SSD as you can with a mechanical drive and formatting does not remove data written there, so what was there before is still there, leaving you with less space -- and perhaps something where you would rather it not be.

You'll probably need to set your BIOS to allow hot-swapping of drives and follow the instructions in a Live session.

Otherwise, you may have to do this on a different machine.

This will give us a chance to start with everything fresh and eliminate a lot of possible problems.

---

### Post by globalgoat on 2016-06-02
Hi, Thanks for the reply. That was interesting reading. I did the security erase successfully on the SSD, and then did a default install from the media again, selecting erase options. The end error is the same. The ls and cat commands from grub return the same as well.

---

### Post by QIII on 2016-06-03
OK.  Let's get some information then.

From a Live session, take a look at [this]("https://help.ubuntu.com/community/Boot-Repair").  Install Boot-Repair, but **don't** choose "Recommended Repair" for now. 

Instead, click "Create a Boot info summary" and post back the link to the output.

---

### Post by globalgoat on 2016-06-04
Thanks for your help - edited: pasting link not text [http://paste2.org/Fw4ZVnC2](http://paste2.org/Fw4ZVnC2)

---

### Post by globalgoat on 2016-06-08
anyone have any thoughts on the boot-repair output?

---

### Post by gsahli on 2016-06-08
I'm not an expert here, but...
Looks like grub put the latest config onto sdb, but you want it on sda to boot from the SSD.

---

### Post by oldfred on 2016-06-08
I think it is just showing the installers boot files on sdb.

It looks like a standard BIOS/MBR install. Was Windows 10 UEFI/gpt install?

But Boot-Repair says it cannot find any system at all. 
But it mentions that Secure boot may be enabled.

Not sure that you were able to install in BIOS mode with Secure boot on as BIOS is not Secure Boot.
If you have Secure boot on in UEFI, turn it off. And turn on CSM/Legacy boot mode.

There are three ways to boot new systems - UEFI with Secure Boot, standard UEFI and BIOS/CSM/Legacy. Last two are not Secure boot.
How you boot installer is how it installs but that may not be the default boot setting in system for the install.

---

