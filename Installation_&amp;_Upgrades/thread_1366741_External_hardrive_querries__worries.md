---
title: "External hardrive querries / worries"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by thesavagedonkey on 2009-12-28
Hi firstly some background so you can understand where im coming from.

Im running a HP pavillion dv9000 with vista on it. I reccently found an old 80gb external hardrive (usb support) I would like run ubuntu from the hard drive and keep it seperate from vista so that i can run that aswell. 

Am i ok to just plug in my ext hard disk and install directly onto it, via my laptop. ?

Do i need to change the bios so that it will boot from usb to make ubuntu boot and then when i want vista will i have to change the bios back or will grub help me out there.?

When i install linux  will grub be installed to the external hard drive or to my laptop?

Thats all i can think of for now. Is there anything else i need to know / be concerned about?

Thanks in advance

---

### Post by HP dv4 on 2009-12-28
Hi, thesavagedonkey

If you are going to install Ubuntu on your external hard drive you first must make sure that your BIOS can support booting from a USB hard drive. All you need to do to check this is when you computer starts up, enter the BIOS setup (usually by hitting the f10 key i think) with your external drive plugged in and see if that is on your list of boot devices. It should be an option.
      One thing to MAKE SURE you do in the installation process is to install the GRUB on to your external hard drive instead of the laptop's drive. I made the mistake of installing GRUB (without knowing it) on my laptop's internal drive, as that is apparently the default. If GRUB is installed on the internal drive you can't boot from your external drive on another computer, and most importantly you can't boot your windows, or anything for that matter, without the external drive plugged in. This link should tell you how to install GRUB on to your external drive:[http://ubuntukids.org/blog/?p=69](http://ubuntukids.org/blog/?p=69)

I hope this helps,
HP dv4

---

### Post by presence1960 on 2009-12-28
As long as your machine's BIOS allows booting from USB you can put Ubuntu on the external disk.

When you install Ubuntu you must specify to put GRUB on the external disk's MBR. You can do this when you get to the Ready to install window by clicking the advanced button (see pic below). I am assuming you have only 1 internal disk and the external. If this is so you want to select /dev/sdb after clicking advanced. This will put GRUB on the MBR of the external disk. When the install is complete and you reboot go into BIOS and put USB/Removable ahead of hard disk in the boot order. Save changes to CMOS and continue booting. You should boot off the external and get GRUB. If so you are set, try booting into Ubuntu.

Doing it this way has an advantage. Your windows disk including MBR is untouched. If you boot with the external plugged in you get the GRUB menu and can boot either OS, if you boot without the external plugged in you go right to windows since the MBR of your internal disk was not altered. You won't have to play with BIOS this way.

One thing to consider that I just read on another thread: Is your external powered with a power cord or is it powered from USB? If it powered from USB port someone has reported being unable to boot from the external claiming the USB disk didn't spin up fast enough for BIOS to detect. I don't know if that is true just saying what I just read on another thread.

---

