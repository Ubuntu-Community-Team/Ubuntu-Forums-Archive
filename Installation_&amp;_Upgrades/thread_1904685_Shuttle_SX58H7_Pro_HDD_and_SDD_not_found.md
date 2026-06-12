---
title: "Shuttle SX58H7 Pro: HDD and SDD not found"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by janmartin on 2012-01-05
Hi all,

I have a new Shuttle SX58H7 Pro and try to install Ubuntu 10.04.3 LTS.

Problem is that at step 4 of 8 where one needs to create partitions nothing is displayed at all. The list is empty. Neither the SDD not the HDD are listed. I am stuck.

What to do?

Hardware list:
Intel Core i7 980 6x3,33GHz 12MB
16 GB Kingston HyperX 1600MHz (4x4GB), DDR3
SDD:Solid State Disk:120 GB OCZ Vertex3 SATA3
HDD: SATA 6Gb/s:500 GB SATA 6Gb/s Seagate Barracuda
22x DVD-Brenner Samsung SH-S223 SATA
NVIDIA geforce GTX 550Ti 1GB

---

### Post by darkod on 2012-01-05
Are the disks recognized in BIOS?
Also make sure the SATA mode is set to AHCI and on newer boards sometimes there is separate setting for the SATA3 ports, make sure this is AHCI too and enabled if they need to be enabled separately.

---

### Post by janmartin on 2012-01-05
I tried it with both IDE or AHCI settings in the BIOS, and it did not work at all!

Please find the output of

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ sudo sfdisk -l
ubuntu@ubuntu:~$ dmesg | grep sda
ubuntu@ubuntu:~$ dmesg | grep sdb
Just to clarify: No output at all so far.

ubuntu@ubuntu:~$ sudo lspci -v

output is a bit long, so I put it here:
[http://bit.ly/wX9hSM](http://bit.ly/wX9hSM)

Screenshots (photos) of the BIOS:
[http://bit.ly/yxQRNM](http://bit.ly/yxQRNM)

Any idea what's wrong?

Thanks.

---

### Post by darkod on 2012-01-05
Put it on AHCI, it should be AHCI.

Shut down the computer and try connecting the disks to different sata ports. Check that the cables are connected well.

In the list of the disks they are not shown, only the cd-rw is. The disks are not recognized.

---

### Post by janmartin on 2012-01-05
Darko,

I think you refer to this image:
[http://bit.ly/xtoUas](http://bit.ly/xtoUas)
Indeed the SDD and HDD are not shown.

However for booting they are listed:
[http://bit.ly/xLi6vg](http://bit.ly/xLi6vg)
[http://bit.ly/xuIcUx](http://bit.ly/xuIcUx)
[http://bit.ly/xLvb7P](http://bit.ly/xLvb7P)

Not sure what to think of this.

I had  a quick look, the HDD and SDD cables seem to be connected to the sockets labeled  "2x SATA 3.0 (6Gbps)" at the top left hand side as shown here:
[www.shuttle.eu/fileadmin/resources/download/docs/spec/barebones/SX58H7_Pro_e.pdf](www.shuttle.eu/fileadmin/resources/download/docs/spec/barebones/SX58H7_Pro_e.pdf)
(Last page.)

So what now?

---

### Post by janmartin on 2012-01-05
Just out of curiosity I burned iss to CDs and tried:
CentOS-6.2-x86_64-LiveCD.iso
Fedora-16-x86_64-Live-Desktop.iso

They both get stuck during booting.

Ubuntu USB sticks still don't find no HDD or SDD:
ubuntu-10.04.3-desktop-amd64.iso
ubuntu-11.10-desktop-amd64.iso

Ideas please?

---

### Post by darkod on 2012-01-05
I know the sata3 ports are faster, but just as a test try them in the sata2 ports to see what happens.

---

### Post by janmartin on 2012-01-06
I am not a hardware guy at all, so  changing is not an option unfortunately.

Shuttle support told the SATA 3 is controlled by ASM1061 and to check if it is supported by the OS.

I wonder how to do that?

---

### Post by darkod on 2012-01-06
Google doesn't show conclusive result whether it's supported or not.
One thing you could try, boot the cd in live mode and in terminal run:
lspci

Look carefully at the list of devices, look for SATA Controller, and see if the ASM1061 is reported. If it is, it should mean it's recognized. Note that you probably have two sata controllers, for sata2 and sata3.

---

### Post by janmartin on 2012-01-06
Darko,

already did:
sudo lspci -v
[http://bit.ly/wX9hSM](http://bit.ly/wX9hSM)

It seems it is not listed.
So what to do?

---

### Post by darkod on 2012-01-06
I'm running out of ideas. I still think there is something in BIOS because on one picture with the list of IDE devices there are no disks recognized. Plus on that picture there are only 4 ports and 2 external, the board seems to have 6 ports, or not?

You might need to touch something in BIOS to activate this controller.

Did you assemble this computer? You said you are not a hardware guy. If you bought it, can you ask for suppost at the shop?

Let me look in the manual if it says something about the bios but I'm not sure it can help.

---

### Post by darkod on 2012-01-06
OK, the 6 ports are the total, 4 internal sata and 2 external sata.
The 4 internal are 2 x sata2 and 2 x sata3.

Even though it detects the disks at boot, not showing them in BIOS is your problem. But not sure how to solve it. You have to take a good look in the BIOS and check all the options about using the sata3 controller. If the disks are not shown in BIOS it's like they don't exist for the machine.

This is not a problem with ubuntu or a driver. You have to make them show up in bios.

---

### Post by janmartin on 2012-01-06
I set up my video camera to capture the screens flashing by when booting.

What puzzles me is that SDD and HDD are in fact listed once:

Transcript from screen #3:
Asmedia 2106 SATA/PATA Controller Ver 0.83
Using PCIE Gen 2
SATA Channel 0 OCZ-VERTEX3 SATA 3
SATA Channel 1 ST3500413AS  SATA 3

So it seems the BIOS is aware of both drives?

But Ubuntu (and Debian, fedora and CentOS i tested) failed?
Ideas?

Frames:
[IMG]http://bit.ly/yoGuii[/IMG]

[IMG]http://bit.ly/yGY57J[/IMG]

[IMG]http://bit.ly/wQ6Yb2[/IMG]

[IMG]http://bit.ly/z6LMUE[/IMG]

[IMG]http://bit.ly/xGJ0F8[/IMG]

[IMG]http://bit.ly/wkO6K5[/IMG]

---

### Post by darkod on 2012-01-06
Not sure the Asmedia screen is part of bios or not. I understand that it detects the disks but that is still not proof bios works and communicates correctly with the Asmedia controller.

One thing is for sure, until you go into BIOS and see the disks listed there, they are not recognized.

Forget the screen showing them as detected. Why aren't they in the BIOS list?

You might have some type of setting you need to enable somewhere.

That's why I suggested temporarily moving them to the other sata2 ports. If they are detected in bios as I think they will be, that is telling you where the problem lies.

---

### Post by cioma on 2012-01-06
I'm pretty sure that connecting boot drives to SATA2 ports will solve the problem.

The thing is that Shuttle SX58H7 Pro is based on Intel X58 chipset (+ICH10R) with doesn't support SATA3 (it's SATA2 only). Instead, SATA3 support is implemented with a separate chip (Asmedia 2106 SATA/PATA Controller) which is connected over PCIe to the X58 chipset. So it's the same if you'd plugged in an add-on card with SATA3 controller into the PCIe slot. The problem is that either main BIOS, or bootloader (GRUB), or Linux kernel might have problems with booting from drives connected to this external (to chipset) controller.

This also explains why drives are not listed in BIOS setup - they are not supposed to. Asmedia 2106 has it's own firmware that is started after the main BIOS. By the way this firmware may have its own setup utility and to ender it you might need to press some key combination.

Well, in reality it's more complex than that but I simlify the description for the sake of clarity.

---

