---
title: "Can not reparig GRUB after it dissappeared"
date: 2014-07-31
forum: Installation &amp; Upgrades
---

### Post by Augusto_Ramterdini on 2014-07-31
Hello all,

I've tried everything... no luck so far.

I have a Toshiba laptop it came with Windows 8 preinstalled. I installed ubuntu it worked perfectly during months.
Yesterday I removed the hard drive and battery, and put another HD to see if that hd was working. After that I put
back my original hard drive with ubuntu and windows. Turned on the computer and to my surprise the grub menu was gone
and I was directed straight to windows 8. Even the touchpad stopped working. I checked the bios and found the touchpad
was disabled from an option right there, which seems very strange to me.

Now I followed many tutorials online about repairing grub with EFI, etc but none did work. I have also ran boot repair, here-s the
log, it-s giving me an error. BTW, I have disabled hibernation and fast boot in my windows 8:

Boot repair log: 
[COLOR=#000000][FONT=Arial]http://paste.ubuntu.com/7918388/

THank you so much in advance for your time and help,
Augusto[/FONT][/COLOR]

---

### Post by Augusto_Ramterdini on 2014-07-31
Hello all,

I've tried everything... no luck so far.

I have a Toshiba laptop it came with Windows 8 preinstalled. I installed ubuntu it worked perfectly during months.
Yesterday I removed the hard drive and battery, and put another HD to see if that hd was working. After that I put
back my original hard drive with ubuntu and windows. Turned on the computer and to my surprise the grub menu was gone
and I was directed straight to windows 8. Even the touchpad stopped working. I checked the bios and found the touchpad
was disabled from an option right there, which seems very strange to me.

Now  I followed many tutorials online about repairing grub with EFI, etc but  none did work. I have also ran boot repair, here-s the
log, it-s giving me an error. BTW, I have disabled hibernation and fast boot in my windows 8:

Boot repair log: 
[COLOR=#000000][FONT=Arial]http://paste.ubuntu.com/7918388/

THank you so much in advance for your time and help,
Augusto[/FONT][/COLOR]

---

### Post by oldfred on 2014-07-31
Not sure error in Boot-Repair is important. I think it checks names of grub files and grub-efi has changed to grub-efi-amd64 or grub-efi-amd64-signed.
It says grub reinstalled correctly as 0 for exit code is no error.

       Reinstall the GRUB of sda5 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

Have you gone back into UEFI to set Ubuntu as first in boot order. Plugging in another drive probably reset UEFI to defaults or whatever that drive required.
And Windows updates, changes, or repairs will have Windows send a command to make it first in boot order.

      
 # from liveDVD or flash and use efibootmgr
sudo efibootmgr -v

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

      
 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.)

It does look like it says you have ubuntu first?

 BootOrder: [COLOR=#ff0000]0000[/COLOR],2001,0004,2003,2002
Boot0001* EFI Network 0 for IPv4 (08-9E-01-4E-E8-0D)
Boot0002* EFI Network 0 for IPv6 (08-9E-01-4E-E8-0D)
Boot0004* Windows Boot Manager
Boot0005* EFI USB Device (KingstonDT 101 G2)
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
[COLOR=#ff0000]Boot0000* ubuntu.[/COLOR]

---

### Post by oldfred on 2014-07-31
Merged duplicate threads. Please do not post two threads with same issue.
We all are volunteers here and need to know if someone else has already answered your question, so we do not waste time repeating similar info in another thread.

---

