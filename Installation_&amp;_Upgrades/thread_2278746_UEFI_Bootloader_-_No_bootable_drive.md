---
title: "UEFI Bootloader - No bootable drive"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by Nathan_Callister on 2015-05-18
I have an intel NUC installation that has been running Ubuntu 14.04.1 without a problem for some time now. It is a single OS installation (no windows etc). After a recent `apt-get upgrade` the BIOS has started reporting that no bootable drive is detected.

I have booted it using a Ubuntu live USB and ran boot-repair but that didn't help. The report can be found here: [http://paste.ubuntu.com/11180095/](http://paste.ubuntu.com/11180095/)

I have some experience with grub and the old boot loaders but I have never worked with UEFI before so I have no idea what might be wrong or how to fix it. I've been reading through forums & wikis but they all seem to point to running boot-repair which I've already done. Any assistance would be appreciated.

Edit: If it is any help for context on what might have gone wrong this is the script that I use to update my system: [https://github.com/ncallister/castle/blob/master/home/scripts/aptupdate.sh](https://github.com/ncallister/castle/blob/master/home/scripts/aptupdate.sh)

Edit:
The BIOS output is:
> Could not open "\EFI\BOOT\fallback.efi": 14
Failed to open \EFI\BOOT\grubx64.efi - 8000000...00E (Not positive on the number of 0s here)
Failed to load image
Failed to open \EFI\BOOT\MokManager.efi - 8000...000E
Failed to load image

Edit: Some success but no time to post now will post in the morning. This for the record: [http://paste.ubuntu.com/11228046/](http://paste.ubuntu.com/11228046/)

---

### Post by oldfred on 2015-05-19
Not sure if this is only work around.
The fix for those systems looking for fallback is to create one and make it be grub or shim. So copy grub or shim into /EFI/Boot and rename it fallback.efi.

Did you also change any UEFI boot parameters? Turn on or off secure boot?

       Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)
fallback should be bootx64.efi not a file named fallback.efi, but vendors may have used the name fallback.efi?

---

### Post by Nathan_Callister on 2015-05-19
Ok, so I figured the files seemed to be in the wrong place so I backed them up then wiped sda1 (the EFI partition) and copied the following from the backup into sda1:

 /EFI/ubuntu/MokManager.efi -> /EFI/Boot/MokManager.efi
                       /EFI/ubuntu/grubx64.efi  -> /EFI/Boot/grub64.efi
/EFI/ubuntu/shimx64.efi -> /EFI/Boot/shim64.efi

Then I ran boot-repair again.

Now I have a very strange situation. I can boot from my HDD into Ubuntu, I get the grub options with ubuntu default and some weird ones (I can put up with that). The problem is that now I can only boot from my HDD if the live USB is inserted. If I take out the live USB then I don't even get grub, I just get "No bootable device detected".

I am baffled.

I've booted into my HDD Ubuntu then ejected and removed the USB. Then I ran boot-repair (thinking maybe the config was referring to files on the USB). It didn't help but the resulting report is here: [http://paste.ubuntu.com/11228046/](http://paste.ubuntu.com/11228046/)

---

### Post by Nathan_Callister on 2015-05-19
I haven't changed any BIOS settings since it was first working.

It looks like boot-repair preserves the EFI files. I would like to know how to re-create them from scratch but if I remove them all then boot-repair doesn't even show EFI options.

---

### Post by oldfred on 2015-05-19
There is a small grub.cfg that script does not show in /EFI/ubuntu. That controls which partition an UEFI boot loader for the grub.cfg with boot menu.

Post that grub.cfg. 
If booting live installer, you may have to mount efi partition to find it. If from your booted install, fstab mounts the efi partition in /boot/efi or you find it in /boot/efi/EFI/ubuntu/grub.cfg.

If you boot Boot-Repair in UEFI mode you can do a full uninstall/reinstall of grub. But if you are booting into your install you can just reinstall grub-efi-amd64. You also have either signed versions for secure boot or standard versions without secure boot.

---

### Post by Nathan_Callister on 2015-05-19
There is currently a file /boot/efi/EFI/Boot/grub.cfg where /boot/efi is sda1 so its relative location is sda1/EFI/Boot/grub.cfg :

> search.fs_uuid 939c91a0-fff8-4b67-b3af-06252039ec46 root hd0,gpt2 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

uuid 939c91a0-fff8-4b67-b3af-06252039ec46 matches sda2, currently mounted at /boot

---

### Post by Nathan_Callister on 2015-05-19
Ok, so following what you said about re-installing grub to re-generate the efi files I ran the following

> mkdir ~/tmp/bootbackup
sudo cp -r /boot/efi/* ~/tmp/bootbackup
sudo rm -rf /boot/efi/*
sudo apt-get purge grub-efi*
sudo apt-get install grub-efi-amd64-signed

That all ran without a problem but my /boot/efi directory is still empty. How the hell do I create *NEW* efi files????

Edit: I was able to run boot-repair starting with an empty /boot/efi directory and select an EFI install.. The resulting report is here: [http://paste.ubuntu.com/11236367/](http://paste.ubuntu.com/11236367/)

Rebooting now, wish me luck :p

---

### Post by Nathan_Callister on 2015-05-19
Ok so after that I was unable to boot from the HDD by any means, I booted into live and copied all files from /EFI/ubuntu to /EFI/Boot and now I'm back to being able to boot from the HDD only if the live USB is present.

---

### Post by Nathan_Callister on 2015-05-19
Hooray... it seems to be fixed (I hope). Following advice from here: [https://communities.intel.com/message/219578#219578](https://communities.intel.com/message/219578#219578)

I copied /boot/efi/EFI/ubuntu/grubx64.efi to /boot/efi/startup.nsh and now I can boot from my HDD without the USB!

I have absolutely no idea how or why that works... but it does.

---

