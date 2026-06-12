---
title: "ubuntu won't boot"
date: 2019-10-16
forum: Installation &amp; Upgrades
---

### Post by cryxus on 2019-10-16
Yesterday I tried to install ubuntu 18.04. I followed a tutorial how to burn the DVD, then I followed a tutorial from youtube (the first one I saw) on how to install ubuntu because i didn't had the "Install allong windows" option. I think it installed successful, but the Efi partion didn't created like it should and after a restart I can not access ubuntu, even after I selected ubuntu from GRUD menu. What can I do?

---

### Post by yancek on 2019-10-16
Posting link to tutorials you use to perform some action is always useful.  That way, members here who often know quite a lot about a specific topic can point out errors to us.  I will say that I don't think Youtube tutorials are the best source of information although many are very good.  THe link below is the official Ubuntu documentation on dual booting with windows 10.  You don't indicate whether you have windows installed or which version of windows if you do.  Since you refer to the install alongside windows option, we will guess you do have windows, which release?  WHile reading through the pages at the Ubuntu site below, compare the instructions to what you did.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you do have an installation of windows and it is an EFI install, there would already be an EFI partition and a new one would not need to be created by Ubuntu as the installer would create a separate directory on the EFI partition for the Ubuntu EFI files.

Provide some information on your hardware, name of computer manufacturer at least.  Can you access the BIOS firmware on boot?  Do you have options to select different EFI boot files.

If you don't resolve this after reading the documentation you may need to get the boot repair software and run it to post more details here.  You can do that from the Ubuntu usb you used to install.  Use the 2nd option described on the page.  Do NOT try to make any repairs but select the Create BootInfo Summary option.  WHen it finishes it will give you a link which you can post here for others to view.

---

### Post by twily2018 on 2019-10-17
Try to access your boot menu in your BIOS. Do you see an entry for ubuntu? If you see it then just change the boot order so it boots ubuntu first so that way you'll have the grub menu everytime you boot.

---

### Post by slickymaster on 2019-10-17
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by cryxus on 2019-10-17
So, I have an pc with an intel i5 4690 3.5GHz, a nvidia geforce gtx 960 4gb GDDR5, 8 gb ram DDR3, 1TB hard disk and a 128 SSD on which is the windows. with windows 10 version 1803, I can access the BIOS on boot, and I have the option to access different EFI boot. I entered the boot menu from BIOS and selected ubuntu, but it still boot on windows. I created the ubuntu partion on the hard disk while the windows is on the SSD.

---

### Post by kmarsajith on 2019-10-19
Try running the boot repair software on ubuntu 19.10 live boot and post the Create BootInfo Summary report. that will enable us to help you better..

---

