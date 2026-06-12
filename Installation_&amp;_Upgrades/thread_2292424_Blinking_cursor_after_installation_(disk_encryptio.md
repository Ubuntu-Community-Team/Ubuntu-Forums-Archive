---
title: "Blinking cursor after installation (disk encryption)"
date: 2015-08-27
forum: Installation &amp; Upgrades
---

### Post by petey2 on 2015-08-27
I'm a beginner. I installed Ubuntu and selected disk encryption. After the installation completes, the computer reboots to a black screen with a blinking cursor. I tried to enter the password and nothing happens. I can't do anything on that screen.

I reinstalled and did not select encryption and the installation completed just fine. 

I decided to reinstall yet again, and selected disk encryption again, and I'm back to the problem in the first step - black screen with blinking white cursor.

I used the installation CD to boot into a live environment and ran boot repair. It said it fixed my boot loader, but I still can't boot. Here's the link: [http://paste.ubuntu.com/12209782/](http://paste.ubuntu.com/12209782/)

I tried installing on my SSD (sdb). The other two drives are internal, but used for storage (they are currently empty). 

Any help?

Thanks!

---

### Post by Petro Dawg on 2015-08-27
Is your bios set to boot from the SSD instead of one of the other drives?  I would try unplugging the other two drives and see if it boots from the SSD by itself.

---

### Post by yancek on 2015-08-27
The reason you can't boot is shown at the very top of the boot repair output.  You don't have any bootloader installed on any of the drives.  You have Ubuntu installed on the 128GB drive but boot repair doesn't show any the expected Grub boot files, particularly the grub.cfg file which contains the boot menu you see on screen when you boot.

You should see an option in the Installation Type windows for "Device for bootloader installation" during the install.  What did you select?  If you want it installed to the master boot record of the drive to which it is installed, that would be /dev/sdb according to your output.  You would then need to set that drive to first boot priority in your BIOS when you reboot.  Might be easier to reinstall and make the correct selection for the bootloader install.  I don't use encryption so I don't really know what options you get but the problem is simply that you don't have any bootloader.

---

### Post by petey2 on 2015-08-28
> **yancek said:**
> The reason you can't boot is shown at the very top of the boot repair output.  You don't have any bootloader installed on any of the drives.  You have Ubuntu installed on the 128GB drive but boot repair doesn't show any the expected Grub boot files, particularly the grub.cfg file which contains the boot menu you see on screen when you boot.

You should see an option in the Installation Type windows for "Device for bootloader installation" during the install.  What did you select?  If you want it installed to the master boot record of the drive to which it is installed, that would be /dev/sdb according to your output.  You would then need to set that drive to first boot priority in your BIOS when you reboot.  Might be easier to reinstall and make the correct selection for the bootloader install.  I don't use encryption so I don't really know what options you get but the problem is simply that you don't have any bootloader.


Thanks for your help. I reinstalled, but this time I used the custom option (I forget what the exact name is) where you manage your partitions prior to the installation. On that screen, there was the option for the device bootloader. I changed the drive, hit the back button, and then selected my original install settings and everything worked. I know that's not too clear, but I don't remember the exact options I had to choose. Thanks for your help!

---

