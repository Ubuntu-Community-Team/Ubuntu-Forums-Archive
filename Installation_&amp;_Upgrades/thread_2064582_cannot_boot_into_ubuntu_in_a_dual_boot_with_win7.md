---
title: "cannot boot into ubuntu in a dual boot with win7"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by dawcha on 2012-09-29
I have my win7 on a SSD and installed ubuntu 12.04 (LTS) on my Hard Drive from a usb stick. I set up EasyBCD but cannot boot into Ubuntu from the boot menu (no problem booting into win7 there).

So now I have to go into BIOS and boot to the hard drive from there to get into ubuntu.

I wonder if I installed ubuntu wrongly - followed instructions online somewhere which said to have 4 partitions on the hard drive! These 4 partitions are /boot, /home, / and swap. When I installed ubuntu, I think I installed the bootloader on the /boot partition - is that the problem?

I'd like to be able to load either win7 or ubuntu from the boot menu.

---

### Post by darkod on 2012-09-29
Why don't you simply use grub2 on the MBR of one of the disks which can boot both OSs, unlike windows bootloader?

---

### Post by dawcha on 2012-09-29
By windows bootloader, do you mean EasyBCD?? If so, are you saying it would be simpler to remove EasyBCD and use grub2 instead?

Sorry if I sound naive - I'm new to ubuntu!

---

### Post by darkod on 2012-09-29
Yes, it would be much simpler to use grub2.

Boot your ubuntu, you can do that right now, yes?

Then open terminal, and first check which disk is /dev/sda and which /dev/sdb. You can do this by executing:
sudo fdisk -l (small L)

After you figure out the device name, you can install grub2 onto the MBR with simply:
sudo grub-install /dev/sda (or /dev/sdb depending which is the HDD)

Then reboot and make sure in BIOS it's set to boot from the HDD first.

In fact, maybe none of the above is necessary since you seem to say that if you boot from the HDD you get the grub2 boot menu, right? In that case grub2 is already on the MBR of the HDD. Just put the HDD before the SSD in BIOS and that's it.

---

### Post by dawcha on 2012-09-29
Actually, booting into the HDD will take me straight to ubuntu, there is no grub2 menu there which means I cannot boot into win7 from the HDD.

Checking the disk utility in ubuntu, it looks like both the SSD and the HDD have MBRs. 

I think perhaps it would be simpler for me to delete all the 4 partitions on the HDD and reinstall ubuntu again from usb stick with only 2 partitions - linux and swap? (especially as I do not know how to use the terminal).

---

### Post by darkod on 2012-09-29
First try to update the OSs detected by grub:
sudo update-grub

That should work if it sees the SSD correctly. If the SSD was disconnected during the ubuntu install it will not be in the grub boot menu since it wasn't there to be detected. In that case you need to run the update-grub to search for OSs again.

---

### Post by dawcha on 2012-09-29
I just realized you're right about the grub menu being on the HDD, so all I have to do is to change the boot order in BIOS from SSD to HDD! My apologies - I think it's bedtime for me!!

By the way, I suppose that means I can remove EASYBCD from the SSD without damaging the grub menu on the HDD?

---

### Post by darkod on 2012-09-29
Yeah, EasyBCD is just a third-party software that can write entries to the windows bootloader. If you want to remove it, it might be better to also remove any entries you tried to make with it so that windows bootloader doesn't show a boot menu with entries that don't work.
After that you can remove EasyBCD itself.

---

### Post by dawcha on 2012-09-29
Done!

Booting into win7 opens the windows boot manager - I guess that's because it sees 2 OS in the system even though there's only one entry on it (win7).

Gotta learn to use the Terminal.

Thanks Darko.

---

### Post by darkod on 2012-09-29
That's what I was talking about. If you have more than one entry, it will open a menu for you to select, even if the second entry never works. You need to delete it so that you don't see any "second" menu after you select win7 from the grub boot menu.

---

