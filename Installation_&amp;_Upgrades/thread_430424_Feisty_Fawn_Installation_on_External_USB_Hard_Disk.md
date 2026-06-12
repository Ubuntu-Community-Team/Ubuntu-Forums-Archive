---
title: "Feisty Fawn Installation on External USB Hard Disk"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by neobe on 2007-05-02
I am a complete Newbie to Ubuntu coming from a Fedora background. I'm trying to install Ubuntu on an External USB Hard Disk with laptop capable of booting from USB. 

Here is my partition Layout:

/dev/sda1 (internal HDD of Laptop)
/dev/sda2 (Internal HDD of Laptop)

/dev/sdb  (Unpartitioned space)
/dev/sdb3 (NTFS partition on USB hard disk which I use to store files)

I'm trying to Install Linux on the unpartitioned space on the USB HDD, What I did so far was create an ext3 partition with '/' as mount point and a swap partition of 1024MB and install.

It is also important to note that I clicked 'Advanced' at the last page of installation Wizard and input (sdb0) instead of (hd0) since I didn't want to install grub on my laptop Hard Disk.

Everything went normal until it came to the installation of GRUB boot loader. The installation program gave me an error saying "Executing 'grub-install (sdb)' failed. This is a Fatal Error!"

Can someone tell me a solutiong for this problem please...?

---

### Post by neobe on 2007-05-02
ok I managed to install it successfully without errors by typing the full path to the device '/dev/sdb/'

but now Grub can't boot the partition...

i know it has to be root (sdb, 0) or sumthing...

any ideas ?

---

### Post by neobe on 2007-05-02
well got it...

it is hd0, 0

---

### Post by ernani on 2007-05-07
Hi neobe,

That's exactly the problem I faced. Since though I don't want to install grub on my laptop's hard disk but on the mbr of the external drive, I hesitated to proceed. My internal hard drive was also recognizes as /dev/hda and my external as /dev/hdb. So, by using (hd0,0) as a parameter for the boot loader installation, you are still refering to the external drive?

Also, please correct me if I'm wrong, but the second 0 refers to the boot partiton, right?

Thanks,

-- ernani

---

### Post by bulldog on 2007-05-07
> **ernani said:**
> Hi neobe,

That's exactly the problem I faced. Since though I don't want to install grub on my laptop's hard disk but on the mbr of the external drive, I hesitated to proceed. My internal hard drive was also recognizes as /dev/hda and my external as /dev/hdb. So, by using (hd0,0) as a parameter for the boot loader installation, you are still refering to the external drive?

Also, please correct me if I'm wrong, but the second 0 refers to the boot partiton, right?

Thanks,

-- ernani

Hi,
Your internal hdd would be (hd0) and the external hdd would be (hd1).and you're right the second number refers to the boot partition.
Keep in mind GRUB starts counting the first hdd as 0 and the first partition as a 0 as well.

---

### Post by CasperRed on 2007-05-26
I've been seeking a solution to this myself for some time. I've followed this (and other) threads on the matter and nothing worked. I even tried the hack in "Ubuntu Hacks" from OReilly Press. Nothing worked, until I tried a solution I saw online somewhere.

I'm booting a Dell Latitude D600 laptop. Dell is very friendly to optional boot sources. Just hit F12 at boot and it gives you options to boot to whatever possible sources the BIOS detects.

I took the hard drive out of the laptop (simple procedure) , hooked up the USB drive, and booted to the Ubuntu install disk in the CD drive. I then installed Ubuntu to the system. After the install, when Ubuntu wants to reboot, be sure to hit F12 and select the USB boot option. 

Then you can put the hard drive back in and keep your Windows install. And when you want Ubuntu, just plug in the external drive and hit F12 on boot. 

After all, it is all about choice. :p

---

