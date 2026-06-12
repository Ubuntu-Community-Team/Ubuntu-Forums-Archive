---
title: "Non dual 16.04 install: asking for force uefi install. Uefi or bios?"
date: 2017-04-24
forum: Installation &amp; Upgrades
---

### Post by anm898989 on 2017-04-24
Installing 16.04 from usb. The computer  came stock with ubuntu 14.04 and i have wiped that and am now installing  from usb and want a solo boot with 16.04. When  i go to install it asks me if i want to force uefi installation. Not  sure which option i need here and most similar questions i can find are  relating to dual boot.




My  intuition is that i choose a uefi installer image when i created the  usb but the computer has no uefi boot partition. Does that sound right  given that it is asking the force uefi question? So  should i continue with force uefi? If i do this do i need to create a  uefi partition. If so how do i do that? If not is the solution something  related to checking "allow legacy boot options?  Or do i need to make a new ubuntu boot usb that is configured for bios?

Ha,  im so lost. I really dont want to bork this machine and im not  knowledgable about this stuff at all. any help would be sincerely  appreciated.

Attached a pic of my partitions for reference. There is one extra one off screen that says free space

[ATTACH=CONFIG]274746[/ATTACH]

---

### Post by oldfred on 2017-04-24
The installer is configured for both UEFI or BIOS install.
It just is how you boot from UEFI boot menu. If you boot installer in UEFI mode it installs in UEFI mode.
And if you currently have a BIOS/MBR install the conversion to UEFI/gpt will erase drive.
Make sure you have good backups whatever you do.

You show the typical LVM type install with BIOS. That is a bit more advanced, but required with encryption. Did you have or want encryption?
With UEFI the LVM install has both the ESP - efi system partition, Boot partition and rest of drive is a partition for the LVM.

If you totally install in UEFI mode, it will automatically create an ESP, / (root) & swap using gpt partitioning.
If you want other partitions you can add some during install or use gparted before or after your install.

I only install with gpt, since about 2011, even when I had a BIOS only system.
But if you use gpt, then Windows can only boot in UEFI mode if later you also want Windows.

More info on UEFI in link below in my signature.

---

