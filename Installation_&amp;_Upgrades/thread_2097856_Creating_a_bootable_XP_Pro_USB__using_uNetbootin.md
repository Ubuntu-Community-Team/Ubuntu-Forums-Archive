---
title: "Creating a bootable XP Pro USB  using uNetbootin"
date: 2012-12-24
forum: Installation &amp; Upgrades
---

### Post by WiReIs on 2012-12-24
Hey Folks,  as the title states i am currently trying to create a bootable Windows XP Professional USB using the uNetbootin software available on my Ubuntu machine, i have purchased the XP & licence from my cousin which he made available for me to download the xp.iso image from Dropbox.

I have formatted my USB as FAT32 and wiped all memory on the USB.

i have ran uNetBootin and directed the .iso to the USB location on my machine

uNetBootin has the run through its normal proceedings of extracting and copying files etc..

Once the installation is complete i then EXIT the application (i am not rebooting as the machine i am on is not the machine i wish to install XP)

the machine i DO wish to install XP Professional on is an old E-System EI3102 system which is currently running Debian 6 however before Debian it was Win Vista installed (slow as you can imagine with only 512mb RAM installed)

I have upgraded to 2x 1 GB RAM cards to boost performance on the old machine.

Now.. 

whats happening when i set my BIOS in order of boot first i have:

1: USB Key
2: IDE CD
3: IDE HDD
4:USB FDC
5:USB CDROM
6: PCI BEV

Excluded from my boot loader are;

PCI SCSI
Other USB
PCI

when i plug in the USB to the machine and reboot, i press f12 and boot from USB Key: Verbatim4gb i get the following information;

No DEFAULT or UI configuration directive found!
boot:_

if i press "y"

boot: y_

and enter i get the following;

Could not find kernel image


Any ideas were i am going wrong?

Any help would be much appreciated :)

---

### Post by snowpine on 2012-12-24
Have your cousin mail you the install DVD, problem solved. :)

---

### Post by WiReIs on 2012-12-24
that would probably be the best thing to do but we thought we were being smart :P

..not smart enough though

just thought it would save time creating a bootable USB, i dont understand why it wont work as i have created many bootable USBs for linux distros before in the past, i used this method for installing ubuntu on the machine im using now

---

### Post by C.S.Cameron on 2012-12-25
I have installed Windows XP Pro on flash using the instructions on this site:

[http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf](http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf)

I use it for my Atom powered home entertainment center as Ubuntu does not see the S-Video.

It plays AVI's and MPG4's ok but is otherwise very slow.
The flash drive only works on the computer it was made on, like normal XP.

UNetbootin does not work for installing XP to flash.

---

