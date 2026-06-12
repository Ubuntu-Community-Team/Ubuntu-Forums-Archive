---
title: "Another Can't boot into Ubuntu from Windows 8!"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by mvaranda on 2012-10-31
Same here... I tried EasyBCD 2.2, grub2 repair, boot-repair and windows boot manager always get control over.
At this point I would be happy if someone cold tell me how to boot my Linux partition from a grub2 loaded from the Installation disk. I can press "c" and get the grub2 shell but I was not able to figure out the commands needed.

when I try "boot (hd0,gpt7)/boot/(image... I guess it was vmlinuz-...)" it tells that no kernel was found.
image shows in ls (hd0,gpt7)/boot

---

### Post by oldfred on 2012-10-31
Moved to your own thread. but follow the adice from Yann in old thread. It gets confusing on who has what issue. And boot issues may seem similar but often details matter.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

If you have gpt partitioning with Windows you have UEFI booting. Did you download the 64 bit version of Ubuntu and boot it in UEFI mode. Both Windows & Ubuntu have to be in UEFI mode not one in BIOS and the other UEFI. If you installed Ubuntu 64 bit in BIOS mode, Boot repair can fix it by uninstalling the grub2 BIOS boot file grub-pc and installing grub-efi.

---

### Post by mvaranda on 2012-10-31
Thanks a lot. I reinstalled Ubuntu 12.04.1 with separated efi boot. /etc/fstab has an entry to /boot/efi as mounting point.
I also ran boot-repair: [http://paste.ubuntu.com/1322443/](http://paste.ubuntu.com/1322443/)

Now the BIOS shows 2 boot devices for my HD. They have the same name but behaves differently: one goes to Windows Boot Manager; The other shows a msg: "Reboot and select the proper boot device...".

---

### Post by oldfred on 2012-10-31
Is this the file you are booting from?

sda2/EFI/ubuntu/grubx64.efi

Boot-Repair says it fixed or reinstalled the efi boot loader.

---

### Post by mvaranda on 2012-11-01
Acer's BIOS does not have a field where I can set the EFI filename. It is a brand new box Acer AX3995-EF308 Intel based.

---

### Post by oldfred on 2012-11-01
Then it just should say Ubuntu.

One user posted this:

Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter.

---

### Post by mvaranda on 2012-11-01
There is no UEFI menu in that Acer's BIOS (unless hidden). Tonight I will check if there is any upgrade for that BIOS. Thanks.

---

### Post by mvaranda on 2012-11-01
Official Acer's BIOS downloader does not work with Win8 (says that the exe file is not valid). Tried to launch from a DOS terminal with Admin privilege and same crap.
I installed Ubuntu 64 in a USB Stick and boots fine. I am giving up for now in having Ubuntu in a partition aside Win8. I may get a USB-HD or try once again in a few weeks. New Machine and a new crappy Win8 could not be any different. Thanks for all your help.

---

