---
title: "Ubuntu 14.04 won't boot, Toshiba Satellite L15W-B1302"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by pwsiegel on 2015-02-01
Hi,
Forgive me if this question has been settled already on this forum - I couldn't find any other threads describing my problem, but I may not have searched comprehensively.

I just bought a Toshiba Satellite L15W-B1302 laptop, and I have been trying to install Ubuntu 14.04 on it (after erasing a particularly vicious piece of malware called "Windows 8.1").  The problem I keep having after numerous attempts at reinstalling is that I keep getting a message beginning with "Reboot and select proper boot device" when I try to boot the system from the hard drive.

**What I've tried**
-I disabled the security in my BIOS
-I erased and rebuilt the USB stick from which I am installing Ubuntu
-I used boot-repair and got this message:

"Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/9995297/](http://paste.ubuntu.com/9995297/)


In case you still experience boot problem, indicate this URL to:
<e-mail address> or to your favorite support forum.

You can now reboot your computer."

**Results**
None of these attempts have solved the problem entirely, but I have made some interesting observations.  

-When I freshly install the system and reboot, if I remove the USB drive at the moment when the "Toshiba" label is on the screen (i.e. when hitting F12 would load the BIOS settings) then Ubuntu boots just fine and works perfectly.  However, as soon as I restart the system after the first successful boot it's back to the "Reboot and select proper boot device" message and I have not found away to get back into Ubuntu without reinstalling.  If I remove the USB drive at any other moment then I cannot boot the system even once.
-When I ran boot-repair and restarted, Ubuntu booted just fine.  But again, as soon as I restarted the computer after the first boot it was back to "Reboot and select proper boot device".
-I can boot Ubuntu from the USB stick (indeed, that is how I am writing this post).

Thanks in advance!

---

### Post by yancek on 2015-02-01
You have Ubuntu installed in UEFI mode so you should have a setting in the BIOS to set boot in EFI.  I don't use it myself, so can't be any more specific and each manufacturer has a somewhat different method.  You might check the BIOS options or your Toshiba manual for the correct method.

---

### Post by pwsiegel on 2015-02-01
I strangely could not find the UEFI setting anywhere in the BIOS (I checked all of the menus), and the laptop did not ship with a manual (and I can't find one online).  Any suggestions?

---

### Post by oldfred on 2015-02-04
It seems that Toshiba now is just like HP & Sony. 
They all modify UEFI to only boot Windows by UEFI description. That is against UEFI standard and Ubuntu policy statement. I assume Microsoft is giving a discount if they make it difficult to boot anything but Windows.

Since you only have Ubuntu you may just be able to change the description from ubuntu to Windows.
You still are booting grub or shim.
       
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

     
Or you can create /EFI/Boot folder and add the hard drive boot entry. System still have to allow hard drive to boot. Hard drive uses bootx64.efi which we really make to be grub or shim.

 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
sudo mount /dev/sda1 /mnt
#only if not already existing, 
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by Jim Link on 2015-03-25
I just bought one of these computers as an emergency laptop replacement during a business trip.  I was wondering if oldfred's  advice, or if you had figured this out in general... I think this little multi-platform laptop would perform greatly on linux!  Thanks in advance...

---

### Post by wum46 on 2015-07-23
I had the same problem ('reboot and select proper boot device') with ubuntu 15.04 and a Toshiba Satellite CL 10W-B-100. What oldfred suggested solved the problem for me. Thanks for the good advice!

---

