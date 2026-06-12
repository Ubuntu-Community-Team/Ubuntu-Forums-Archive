---
title: "Make GRUB boot USB if present"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by ugh_bough on 2011-10-01
Hi,

I hope this is the right place to ask my question. I would like to know about the capabilites of GRUB (Note: I have browsed the GRUB 2 Guide in the forum but could not find an answer there).

Scenario: I would like to setup a NAS with the OS (ubuntu server of course) on a dedicated harddisk H. I'd like to have another partition on H to store an image of the boot partition so that I can go back to a working version when problems occur while customizing the server. For backup/restore I'd like to boot from a USB drive that has the right environment installed to do the job remotely (note: there is no monitor on the server).

Now the problem: I have a ASUS E35M1-I DELUXE mainboard (feature-rich but bad bios) that will not allow me to setup a static boot order that prefers a bootable USB drive if present (instead it always prefers the drive that was last booted and you have to enter the bios to prefer another one).

Now the funny part: When I installed debian 6.02 I got a funny problem. The installer installed the system fine on the hdd but it installed the bootloader on the USB-drive it was booted from. So I could not boot the PC when the USB drive was unplugged ("No bootable device found...") but everything worked well when it was plugged: the installed system booted from the hdd.

Now my question: Is it possible to turn the whole thing around, i.e. can I install GRUB on the hdd's mbr and make it boot the OS installed on the first partition if no other bootable device is present and make it boot e.g. a plugged USB-drive if present? This way I could circumvent the problem with the poor bios.

Thanks in advance for any suggestions (and of course for reading all the bla bla ;)),
ugh_bough

---

### Post by Lampi on 2011-10-01
Can you enter a boot order menu if you press f11 or f12? Check the mainboard manual if you don't know what f-key it is.

---

### Post by oldfred on 2011-10-01
Related to Lampi post.

Most even poor BIOS let you choose boot device priority. So if USB is first and it does not exist then it should boot hard drive.

To reinstall grub to hard drive, change sdb to your drive:


#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by ugh_bough on 2011-10-01
Hi,

@all: yes I can edit the boot order, but only when several bootable devices are plugged in. On the next boot, when only one drive is plugged, i.e. the hdd, the order is lost. The order has to be _restored by hand_ the next time more than one bootable drives are plugged in :(

@ oldfred: Thanx for the instructions. The problem was not to install the boot loader to another drive (Now that I have ubuntu server installed, the problem with the wrong boot loader location in the _debian_ installation is gone). I would like to exploit this behavior (boot loader on USB boots HDD installation) and turn the thing around: HDD-installed boot loader boots USB drive (if present).

I'll keep on trying and will report if I find a solution or not. In the meantime if some of you guys know if this is possible and how to do this, please let me know.

Thanks again,
ugh_bough

---

### Post by ugh_bough on 2011-10-01
so far: [http://www.linuxquestions.org/questions/linux-general-1/boot-from-usb-if-not-detected-by-bios-650312/](http://www.linuxquestions.org/questions/linux-general-1/boot-from-usb-if-not-detected-by-bios-650312/)

did not investigate it further, yet.

---

### Post by brc816 on 2011-10-02
Make sure that the USB drive you're attempting to boot from has 512 byte sectors, not 4096 byte, and is partitioned with MBR if you're trying to use a BIOS boot without EFI capability. I've been beating my head bloody trying to boot a 4096 byte sector 3TB Seagate USB drive and it's just not working, either with MBR or GPT partitioning.

That said, I have a 512byte sector 250GB Western Digital "Book" drive that I've been using for a couple of years now, and it works beautifully. It was partitioned with MBR and when I plug it in, the legacy GRUB (0.97) bits on it boot nicely because the BIOS thinks it's the second drive. (My laptop has TWO internal hard drives, but the second one becomes /dev/sdc instead of /dev/sdb when the USB drive is seen at power-up).

---

