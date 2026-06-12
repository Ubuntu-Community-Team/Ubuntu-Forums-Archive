---
title: "Another No Booting Device Error (Ubuntu 14.04 on Acer Aspire V3 371-58BP)"
date: 2015-02-16
forum: Installation &amp; Upgrades
---

### Post by Marfi on 2015-02-16
Hello everybody, I recently bought an Acer Aspire V3 371 58BP.
I eliminated Windows 8, disabled the secure boot, and installed Ubuntu
 formatting the SSD (I replaced the HD 500gb with a SSD 250 gb).

The boot failed and gave me the "no booting Device" error. All
 the booting sequence on bios is correct, with SSD at the first place, and
 then USB devices.

After having run Boot-repair (with this entry: [http://paste.ubuntu.com/10242098](http://paste.ubuntu.com/10242098)) the booting sequence is very odd.


First, as I turn on, there is this blue screen error: "default boot
 device missing or boot failed. Insert recovery media and hit any key. Then
 select boot manager to choose a new boot device or boot recovery
 media". I can press "ok".

Then, it comes a screen with Boot manager, with two choices:
1 unknown device (samsung ssd 850 evo 250 gb)
2 windows boot manager  (samsung ssd 850 evo 250 gb)

I choose 1.

Finally it comes out Grub and I can start Ubuntu.

Now, Ubuntu runs fine and I am happy, but the booting sequence is a little
 annoying and odd, definitely ankward. 

Besides, why there is still the windows boot manager if I have removed the original
 hard disk with windows? I can't understand, it is like the Windows Boot manager is still hidden in there somewhere..

How can I fix this without go mad? Could you help me?
Thanks!

---

### Post by efonde on 2015-02-16
when you changed the HDD with new SSD, off course it will tell you "No booting device". Since the SSD probably don't have any OS installed yet (assuming it was a new SSD). 
If  you have a bootable usb stick with Ubuntu in it, the boot sequence in BIOS should be USB devices in the first place. 
In the first place, you don't need boot repair. No wonder you have windows boot manager. I could only think that you have boot-repair installed windows boot manager.

Oh and in the bios option, you would have to disable secure boot and have the Boot Mode: Legacy instead of UEFI. Since you said you previously have Windows 8.

---

### Post by oldfred on 2015-02-16
It looks like you originally installed Ubuntu in BIOS/CSM mode as you have grub in MBR and a bios_grub partition.
But then either reinstalled or repaired install in UEFI mode as you have UEFI boot files in efi partition and entry in fstab to mount efi partition.
So system is now configured for UEFI boot.

Many vendors are modifying UEFI to only boot the Windows entry by description.
Some with only Ubuntu change (or add) a new entry with Windows as description but actual boot file as grub or shim to boot into grub menu.
Others have changed the hard drive boot entry which is in /EFI/Boot as bootx64.efi. They rename that file and copy grub or shim into the folder and rename to bootx64.efi. Then boot hard drive entry in UEFI menu.
You may also need to remove Windows folder in efi partition and remove current Windows entries in UEFI menu with efibootmgr.

Alternative workarounds for many systems.
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019

[/URL]
 
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

If above does not work or you want hard drive boot entry:

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

 
     
[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by Robert_Vertesi on 2015-08-17
Hi,
I made a clean install of Ubuntu 14.04 and hit the very same problem. The solution was to disable secure boot.
By default one cannot change that option, so what to do was the following:

- Keep pressing F2 during bootup to enter the Setup utility
- Go to the Security tab, set an arbitrary password and confirm it
- Go to the Boot tab, then disable Secure boot
- Go back to the Security tab to clear the password (hit enter on the empty field) if you wish.

---

