---
title: "Reboot and select proper boot device error"
date: 2015-09-21
forum: Installation &amp; Upgrades
---

### Post by cj55555 on 2015-09-21
I recently installed Ubuntu using a USB flash drive. The installation went well, except I'm having issues booting without the flash drive in. I get the error message "reboot and select proper boot device" every time I try to boot without the flash drive. I checked the BIOS settings, and my hard drive is the first priority to boot. Additionally I used the Ubuntu boot repair program and it didn't work. The URL I received was [http://paste.ubuntu.com/12517519/](http://paste.ubuntu.com/12517519/) 

Thanks in advanced for any help!

---

### Post by oldfred on 2015-09-21
You have a full drive install using LVM and encryption.
I do not really know LVM nor encryption. 

But you have a standard UEFI and /boot partition.
You show secure boot on, have you tried with it off.

But most Toshibas have needed a work around.
Since you only have Ubuntu installed you can rename it from ubuntu to "Windows" and then the Toshiba UEFI will be happy to boot.

Assumes ESP - efi system partition is sda1.
 
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Then you should be able to boot the "Windows entry" but it really is shim which also has the same signing key as Windows.

Other work arounds and in link below in my signature:
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by cj55555 on 2015-09-21
Hey I tried booting without secure boot and it gave me the me the message "Start PXE over IPv6" and then nothing happened. I also tried running the code you sent but it said the command wasn't found. I then looked into the files on the partition containing Ubuntu and found the epi folder to be empty (not sure if it should be).

---

### Post by oldfred on 2015-09-21
Per Summary report you have these in the ESP - efi system partition. That is where efi boot files are. Major parts of grub are in the /boot folder in your install. Some grub configuration files are in other folders in Ubuntu's / (root). 

>      Boot files:        /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi



---

### Post by cj55555 on 2015-09-21
I tried copying the grub.efi file to the /boot folder like the UEFI Installing Tips link says, but it gave me an error saying "permission is denied'. The same happens when I try to open the /root folder and when opening the /boot and efi folder they both appear empty.

I was able to access the root folder by sudo -i nautilus  and copied the grub.efi file and renamed it as bootx64.efi and still no luck.

---

### Post by oldfred on 2015-09-21
When you say no luck, exactly what happens.

What brand, model system and what video card/chip?

---

### Post by cj55555 on 2015-09-22
By no luck I meant it still did the same thing (message with "Reboot and select proper boot device"). It's a Toshiba Satellite 11.6" with an Intel HD Graphics card (I couldn't find more specific information). Last night I got the computer to boot Ubuntu without the flash drive by reinstalling without encryption or LVM, but as soon as the computer had to restart after updating software it went back to how it was (with the reboot and...message).

Thank you for all the help by the way, I appreciate it! It's frustrating that it won't seem to work but Ubuntu is well worth the trouble!

It's the L15-B1330 model by the way

---

### Post by oldfred on 2015-09-22
Most newer Toshibas also seem to need work arounds to boot the default  hard drive entry that we make as grub or shim. But some do not have the  default hard drive entry in UEFI, or take a couple of reboots to find  it.

If you reinstalled did you copy grub to /EFI/Boot/bootx64.efi again.
Do you have a hard drive boot entry? If not after a couple of reboots, we can use efibootmgr to add one.

---

### Post by cj55555 on 2015-09-25
I changed the shim efi file to bootx64.efi and it still didn't boot. I'm trying again with the grub file. How do I check if I have a hard drive boot entry?

My hard drive is mounted at /boot/efi and I have the bootx64.efi file in there. When I booted this time I got a screen saying "GNU GRUB...Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions."

Upon typing "exit" I'm returned to the original "Reboot and select proper boot device" screen.

---

### Post by oldfred on 2015-09-25
Did you just rename shimx64.efi or copy it into /EFI/Boot and then rename to bootx64.efi.
You have to have both /EFI/Boot with a bootx64.efi and all the Ubuntu boot files in /EFI/ubuntu.

With this you should have both a ubuntu entry and some default UEFI hard drive boot entry.
sudo efibootmgr -v

If not reinstall grub with Boot-Repair.
And/or add a specific hard drive entry.
this assumes efi partition is sda1.
# You may need new hard drive entry:
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
# confirm entries:
sudo efibootmgr -v

---

### Post by cj55555 on 2015-09-27
I have two separate directories in /EFI...Boot, and ubuntu. In /EFI/ubuntu there's several files (shimx64.efi, MokManager.efi, grubx64.efi, and grub.cfg) and in /EFI/Boot there's a copy of the shimx64,efi file renamed as bootx64.efi. I ran the code you sent in the last message, and the hard drive was first priority to boot. Still, I got the same "reboot and select proper..." message. I tried rebooting several times and still received the same message.

---

### Post by oldfred on 2015-09-27
Is Secure boot off?
Post this:
sudo efibootmgr -v

---

### Post by ubfan1 on 2015-09-27
How did you get the grub prompt?  That means you have dealt with all the system bits of boot, and are just left with loading the kernel.   Maybe try just typing in the configfile (hd0,2)/boot/grub/grub.cfg instead of "exit" and see if you get the menu?  At the grub prompt, try the suggested TAB completion to see what grub sees with the "ls" command:
ls (hd   TAB   to list the devices, or fill in if only one, the "0"), then
ls (hd0, TAB  to list the partitions (expect to see three of them), choose 2 then
ls (hd0,2)/  TAB and see if you see anything on the boot partition, like kernels and initrd ramdisks.
If you can see what's expected, you could try to look at a boot section for a kernel (starts with "menuentry") and type it in to see what happens.

---

### Post by cj55555 on 2015-09-27
Yes, secure boot is off. Upon entering sudo efibootmgr -v I get the following:
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0005,0004,0003,0003,2003,2001
Boot0000* ubuntu    HD(1,800,100000,498394fb-c5eb-4527-b573-2dff52c24e27)File(\EFI\ubuntu\grubx64.efi)
Boot0001* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(74852a32a640,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0002* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(74852a32a640,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot2001* EFI USB Device    RC
Boot2003* EFI Network    RC

I was getting the grub prompt before but now I've just been getting the "reboot and select proper..." message.

After re entering sudo efibootmgr -c -L"UEFI Hard drive"-l"\EFI\Boot\bootx64.efi" and running the code sudo efibootmgr -v again, I got this;
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0003,0000,0005,0004,0003,0003,2003,2001
Boot0000* ubuntu
Boot0001* UEFI: IP6 Realtek PCIe FE Family Controller
Boot0002* UEFI: IP4 Realtek PCIe FE Family Controller
Boot2001* EFI USB Device
Boot2003* EFI Network
Boot0003* UEFI Hard drive-l\EFI\Boot\bootx64.efi
c@waspcorp:~$ sudo efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0003,0000,0005,0004,0003,0003,2003,2001
Boot0000* ubuntu    HD(1,800,100000,498394fb-c5eb-4527-b573-2dff52c24e27)File(\EFI\ubuntu\grubx64.efi)
Boot0001* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(74852a32a640,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0002* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(74852a32a640,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0003* UEFI Hard drive-l\EFI\Boot\bootx64.efi    HD(1,800,100000,498394fb-c5eb-4527-b573-2dff52c24e27)File(\elilo.efi)
Boot2001* EFI USB Device    RC
Boot2003* EFI Network    RC

---

### Post by oldfred on 2015-09-27
You are missing some spaces in the command, and then entry in UEFI is not correct. Best to copy & paste.

sudo efibootmgr -c -L"UEFI Hard drive"-l"\EFI\Boot\bootx64.efi"
should be:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

And best to delete the incorrect one, currently 0003

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by cj55555 on 2015-09-30
I reinstalled once again (as I've been having to do every time I reboot my computer) and used the code you sent (copied and pasted it). The "UEFI Hard drive" boot I added last time was gone, so I didn't have to delete it. Now the correct files are in /EFI/Ubuntu and /EFI/Boot and the boot "Windows Boot Manager" is first priority. Upon restarting it appeared to work, however after shutting the whole computer down (not just restarting), I got the same "reboot and select proper boot device" error.

---

### Post by oldfred on 2015-09-30
You should not have to reinstall, perhaps re-install grub only with Boot-Repair's advanced mode.
Generally just reconfigure /EFI/Boot & add UEFI entry.

Can you use one time boot key, usually Toshiba uses f12 to give the same list as the UEFI boot tab as boot options? With your system the ubuntu entry will give the error, but Windows & the hard drive/fallback entry should work.

Is Windows turning on secure boot? Some with Windows 10 seem to have that issue?

---

### Post by ubfan1 on 2015-09-30
Do you also have /EFI/Boot/grubx64.efi along with /EFI/Boot/bootx64.efi (which is shim)?  You can get along with only a bootx64.efi if it is a grubx64.efi copy and you are not in secure boot.  shim needs grubx64.efi in the same directory it is run from.

---

### Post by cj55555 on 2015-09-30
Putting the grub file in with the renamed shim file worked!! Thanks so much!! I can now completely shut it off and the computer still boots Ubuntu without the flash drive.

---

