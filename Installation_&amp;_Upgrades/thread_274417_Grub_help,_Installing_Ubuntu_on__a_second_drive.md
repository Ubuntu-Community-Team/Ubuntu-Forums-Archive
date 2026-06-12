---
title: "Grub help, Installing Ubuntu on  a second drive"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by treck on 2006-10-09
I installed Dapper on my second drive and installed grub on hd1,0I did the comand: dd if=/dev/hdb of=/mnt/floppy/bootsect.lnx bs=12 count=1. I added the bootsect.lnx to my boot.ini in windows and and rebooted. I selected Ubuntu from the menu but then I just get a screen the says "Grub" and a flashing cursor. Any Ideas?

---

### Post by woob on 2006-10-09
Treck, I think you should have installed Grub to the MBR, (hd0,01). Grub will then pick-up anything on both drives and put it in your Grub menu.

---

### Post by treck on 2006-10-09
Well, the first install that's what I did. I put the ubuntu disk in and installed to the second drive and let ubuntu use the auto partioner. It screwed up my system and I could not boot to windows and I got an error 17 from Grub.

---

### Post by lha on 2006-10-10
Take a look at [BootPart]("http://www.winimage.com/bootpart.htm").

---

### Post by treck on 2006-10-10
I tried that too. When I select Ubuntu from the NTLOADER bootpart starts and then just hangs.

---

### Post by woob on 2006-10-11
Trek, if you are using the ntbootloader then you are not using Grub. Windows refuses to recognize other file systems other than FAT and NTFS. If you install Grub in the MBR(master boot record) then it will detect your Windows partition and add it to the Grub menu automatically. That way when you start your puter you will have a choice of Windows or Ubuntu. Also, if you decide to install other distros later on it is very easy to add them to the Grub menu. If you know all of this already I apologize.

---

### Post by PapaDocta on 2006-10-11
sorry i don't wanna hijack your post but i have a similar problem

i have SATA 260G and it's partitioned 4 parts... i used the last part for Ubuntu everything went ok (as for installation part) but when i restarted it just booted into windows i used bootpart (bootpart 11 C:\BOOTLINX.BIN Ubuntu) and added the partition where ubuntu is installed and rebooted windows XP and i got the boot menu with Ubuntu but when i select it nothing happens it says try using mdisk or something like that... i tried all of my partitions using bootpart and still the same can't boot into Ubuntu.. i used winimage and connected to the Ubuntu partition i can see a boot directory and has lots of files... meaning that grub is installed fine in that partition...........

please someone help me i wanted to boot into Ubuntu ... what to do?

i forgot to add ubuntu doesn't give any option to where install grub! and it would be nice if i can ntloader instead of grub


thanks

---

### Post by gn2 on 2006-10-11
Generally the usual way that is suggested to install a dual-boot system involves overwriting the Master Boot Record of the Windows hard drive.

On one hard drive this is pretty much unavoidable.

HOWEVER:

If you are dual-booting with TWO hard drives it is not necessary to write Grub over the MBR if you can access a "Boot Device Selection Menu" by pressing F8
(or whatever key depending on BIOS)

You can keep both installations entirely separate and avoid a host of problems later on.

To do it this way:

Disconnect the Windows drive and install Ubuntu and Grub on the second drive. Reconnect first drive after installing Ubuntu.

Windows on master, Ubuntu & Grub on slave if using two IDE drives.

(This method will also work on SATA drives, or a mix of SATA & IDE)

Press F8 (or whatever key depending on BIOS version) at boot time to bring up the Boot Device Selection Menu.

Choose OS by selecting which drive to boot from.

Select desired default OS by re-arranging boot order in BIOS.

Only need to press F8 to select non-default OS.

Re-boots are as quick as using traditional Grub-in-MBR option.

Always disconnect other OS's drive if re-installing.

This process will also work for adding Windows to a Ubuntu system

If you take this option you will never have any issues with Grub menu lists or MBR corruption.

Grub on my MBR was worse than any virus I ever had.

Access to files on either drive can be configured later on, once you've got a safe installation organised.


.

---

### Post by PapaDocta on 2006-10-11
thanks a lot for the fast respond.. i guess i will have to wait till i get a new hard drive to install ubuntu in it...

thanks

---

