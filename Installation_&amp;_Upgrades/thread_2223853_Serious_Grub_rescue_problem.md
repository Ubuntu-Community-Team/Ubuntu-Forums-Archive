---
title: "Serious Grub rescue problem"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by peter110 on 2014-05-13
I have done something pretty stupid - and there are complicating factors which mean this is not a run-of-the-mill grub rescue issue. 

I had a dual boot setup on my netbook - Windows XP and Ubuntu 14.04.  I deleted the Ubuntu partitions (using a utility within Windows), with the intention of reinstalling Ubuntu after I'd reconfigured the partitions.  But when I did so I clearly messed up Grub, because when it rebooted I get a "grub rescue" message.

I'm aware of the instructions to boot to Ubuntu from grub rescue, but they don't help me because Ubuntu isn't there anymore - only Windows.  Nor can I boot onto a recovery CD/USB.  There are three avenues that I've tried that don't help me:


[LIST=1]
[*]This being a netbook, there is no optical drive to boot from.
[*]I can't boot from USB, even when BIOS is configured to check the USB drives first - I just get a "NTLDR is missing" message.
[*]I do have a recovery partition for XP, but when I try to enter recovery at startup time nothing happens (it says "press F4 to enter recovery" but pressing F4 it doesn't actually work).
[/LIST]

When I use the "ls" command, this is what I get:

(hd0) (hd0,msdos2) (hd0,msdos1)

I think those are the XP recovery and XP OS partitions.

Help!

---

### Post by sudodus on 2014-05-13
Welcome to the Ubuntu Forums :-)

I think you can boot from USB. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

For example, try

>  **Note: with some motherboards you have to select 'hard disk/USB-HDD0' to choose the USB flash disk**.  It may work like this because the system sees the USB drive 'a mass  storage device' as a hard disk drive, and it should be at the top of the  boot order list. 


So  you need to edit the Boot Order. Depending on your computer, and how  your USB key was formatted, you should see an entry for "removable  drive" or "USB media". Move this to the top of the list to make the  computer attempt to boot from the USB device before booting from the  hard disk. 



---

### Post by oldfred on 2014-05-13
If you are getting ntldr missing that is a Windows XP error. 

Better to just use a Linux repair flash drive to boot and install a Windows boot loader to the MBR. Always install boot loader for system you are keeping before deleting other systems, whether Windows or multiple Linux installs.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Some systems if rebooted many times get locked up as BIOS settings may be corrupted. A cold reboot may work. If a laptop remove battery and hold power switch for a few seconds to drain capacitors.

---

### Post by peter110 on 2014-05-13
Thank you for the replies - but unfortunately I don't think either method will help, since both methods require me to have access to a flash drive (as far as I can tell).

But I don't have that access - the BIOS boot order is already set to boot from USB, but it doesn't.  

I have access to the grub rescue command prompt, but nothing else.  I really need a way to either access/load either the XP partitions, or Ubuntu on a flash drive - but I need to do that from the grub rescue prompt I think.  

I've read about 'grub-n-iso' which might help?

---

### Post by oldfred on 2014-05-13
Then the flash drive is not configured correctly to be a bootable device. BIOS only shows or boots from a bootable device then defaults to hard drive.
But if you are getting a ntldr error you have booted with Windows boot loader as that error is from the Windows partition boot sector which is after the MBR. Windows in MBR jumps to Partition with boot flag. If you have multiple NTFS partition did boot flag get moved from Windows partition to a data partition. 
But to fix just about anything you have to boot from a CD or flash drive.
Or install hard drive into another system that you can boot to make repairs to this hard drive.

---

### Post by peter110 on 2014-05-13
Thanks for that.  I'll try an alternative method of making a bootable USB - perhaps the application I'm using isn't doing something right.

Otherwise I suppose I'll have to try to use grub rescue to boot from the USB (though I'm not sure if that can be done).

I don't really want to go down the route of removing the hard drive - that's definitely beyond my skill set.

---

### Post by peter110 on 2014-05-14
Problem solved - thank you to those who helped.  It turned out that the programme I was using to create live USBs was not doing a great job - Unetbootin to the rescue.  I was able to boot from a Ubuntu live USB and reinstall from there.

---

