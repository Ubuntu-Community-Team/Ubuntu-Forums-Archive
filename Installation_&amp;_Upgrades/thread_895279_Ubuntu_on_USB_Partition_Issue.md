---
title: "Ubuntu on USB: Partition Issue"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by karthikb23 on 2008-08-20
Hi,
I installed Ubuntu on my USB 4 GB USB drive, with the following partitioning (unlike the traditional approach):

1. Partition 1: 2 GB FAT32, so that windows would detect my USB as a RW partition, for regular file transfers.

2. Parition 2: 1.2 GB: This is the ext2 FS, 'casper-rw' partition, for persistence.

3. Partition 3: Approx 800 MB FAT16, where the CD ISO image is copied, and syslinux is installed.

When i boot off this pen drive, my BIOS (tried on 2 seperate PCs) fails to detect anything boot worthy, and continues to boot off my HD (IDE Drive).

Is this partitioning alright?
Does this pen-drive too, like a HD need the boot loader on the first partition, first sector?

If so, would this drive boot, if i installed GRUB on the 1st partition, and made it chainload syslinux on the 3rd partition?

Any help/attemp to help :lolflag: is welcome!

Thanks in advance!!!

---

### Post by Jeeeepers on 2008-08-20
just looking into running from a usb drive myself and found this that might help [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by prshah on 2008-08-20
> **karthikb23 said:**
> Hi,
I installed Ubuntu on my USB 4 GB USB drive, with the following partitioning (unlike the traditional approach):


Have you set the 3rd partition as active (for booting?) Give the command ```
sudo fdisk -l /dev/sdd
```, and check if there is a "*" (star) next to your 800Mb partition. (Replace /dev/sdd with the actual device for your usb pendrive).

If there isn't post back on how to make it "active".

---

### Post by karthikb23 on 2008-08-20
Thanks Guys.

I have marked my 3rd partition as active :)

fdisk shows me a '*' next to /dev/sda3.

Thasts why this boggles me, coz all guides would tell you to install the boot loader on the 1st partition, but i have done it on the 3rd.

So i want to know, if there can be an issue with this.

As i understand, BIOS always looks up at a predefined address (MBR on HD), for calling the boot loader.
But my first partition, i.e. which would have ideally been the MBR is empty.

Thereafter, the control should pass to the partition marked as active.

But it seems like this is not happening.

Any more help anyone?

Can installing grub on partition 1 help? Is there some other work around for this?

---

### Post by karthikb23 on 2008-08-23
Hi,
I have tried installing grub on /dev/sda1 as well as /dev/sda3. but to no avail.

as i understand, i shd create director for "boot/grub" and thereafter from grub prompt, run "setup (hd2)"
((hd2)-/dev/sda). On performing "embed ... fat_stage_1_5...", i get an error but with the text "not fatal".

I know that stage 1.5 is not mandatory and grub can work with stages 1 and 2.

I have tried this by having the grub files on /dev/sda1 as well as /dev/sda3.
But it does not work.

Also i am not sureif grub is writing to the MBR.
How can i verify this?

i want the stage 1 written to MBR of /dev/sda, and thereafer boot either using syslinux which is already installed on 
/dev/sda3 or grub.


Any suggestions anyone ???

---

### Post by prshah on 2008-08-23
> **karthikb23 said:**
> 
As i understand, BIOS always looks up at a predefined address (MBR on HD), for calling the boot loader.
But my first partition, i.e. which would have ideally been the MBR is empty.


I don't know about your problem, but your theories need a little adjusting. The MBR exists _before_ any partitions; partition 1, 2, 3 have nothing to do with the MBR.

Your setup looks fine to me. 

Try changing the emulation mode in the BIOS; Eg, from USB_Removable to USB-IDE (or similar option; it varies from BIOS to BIOS).

---

### Post by karthikb23 on 2008-08-23
Guys!

I finally managed to boot my USB!!!
i typed out the whole details of what i did, only to find that my reply was dropped n the thing never got posted!:mad:

So i will surely type the whole thing again  :)

But i now have 1 perplexing problem

On booting Kubuntu on my USB, after the booting screen, I am taken to the "initramfs" prompt.

I have replaced my initrd, but despite that the same thing happens i.e. I am taken to my initram file system. From there, ofcourse, i dont have much to do. its as if the booting has coem to a stand still.

I beleive for some reason, the change root and there after init is not getting executed.

Any inputs anyone???

---

