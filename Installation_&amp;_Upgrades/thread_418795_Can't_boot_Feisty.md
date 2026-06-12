---
title: "Can't boot Feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by krolben on 2007-04-22
I get the following error when booting into Feisty (Server):
Int 14: CR2 c1000000      err 0000002     EIP c03f3c3e     CD 00000060    flags 0010016
Stack: 373c0046 00000000 ffffffff c0490000 000013c0 00000080 003c0000 ffffff80

The system is:
Via Epia ME 6000 LVDS motherboard (mini-ITX)
1GB internal HDD (flash card mounted on IDE port)
320GB external HDD mounted via USB

The system crashes completely and the error is displayed at the bottom of the page.

What can be the course of this error? Any reply will be greatly appreciated!

---

### Post by jnusa on 2007-04-27
Get the same message on EPIA SP 800 with 7.04. No solution yet.

---

### Post by WeBToR on 2007-05-04
I experienced the same problem when trying to install Feisty on VirtualBox (winXP).
Tried both Server and Desktop. Server crashed as mentioned above, Destop hang before even installing.
The Alternate CD ISO installed correctly. [http://www.virtualbox.org/ticket/289](http://www.virtualbox.org/ticket/289).
This solved the issue for me.

---

### Post by rcrcomputing on 2007-05-19
On unbuntu Feisty server, it might be just as easy to chroot and install a new kernel
(The cd boots from the generic one)

alt+F2 after installation starts (Brings up another terminal)
mkdir /mnt/hd
# Change the hda??? below to your setup. fdisk -l /dev/hda will clue you in here...
mount -t ext3 -o rw /dev/hda1 /mnt/hd
chroot /mnt/hd

Do a uname -a to see what kernel your running now. (Might be helpfull)
apt-get install linux-image will bring you up a list or

apt-get install linux-image-2.6.20-15-generic

Note, when you boot, you may have to hit the esc key to choose the new kernel.


after you get the system going..

apt-get remove linux-image-2.6.20-15-server

---

### Post by AdeV on 2007-08-24
Excellent advice, thanks! This rescued my Feisty installation on a Tranquil T2 box!

Cheers,
Ade.

---

### Post by dkathrens77 on 2007-09-10
[COLOR="Blue"][B][SIZE="3"]:confused:

I have a similar problem. I have a Feisty Live CD that gives me Int 14 CR2 d0000000 etc boot error only on a particular machine: 

HP a614n   2.6 GHz P4, 256 Mb RAM 

Motherboard MS-6577 Ver 4.1

I am trying to install Feisty on this machine for a friend who "lost" his Win XP recovery CD

This same Live CD works fine in my HP Pavilion zd8000us laptop and other machines as well.

 

I tried instaling a different CD drive in my friend's machine to see if that might be causing this, but same behavior.

I notice a following post referring to an "alternate CD ISO" but in connection with VirtualBox.

I don't know what VirtualBox is, or if this solution might work for me. 

Any help appreciated. Thanks [/SIZE]


 [/B][/COLOR]

---

### Post by dkathrens77 on 2007-09-10
:confused:
[SIZE="3"][COLOR="Blue"]
I read the ticket #289 link.  I tried boot options ACPI=OFF noapic nolapic

Did I mention that my Live CD is for Feisty DESKTOP?  the posts here seem to be about SERVER

the boot process is currently hung at step 125.20540

last complete step: 125.205392: EIP" [<c011c706>] native_apic_write_atomic+0x6/0x10SS:ES 006:c3e2bdb0.

I have NO IDEA what any of this means. 

Please help? Thanks[/COLOR][/SIZE]

---

