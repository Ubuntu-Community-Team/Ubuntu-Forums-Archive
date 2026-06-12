---
title: "grub/install fatal error when installing Ubuntu 20.04 in Macbook Pro 15"
date: 2022-02-17
forum: Installation &amp; Upgrades
---

### Post by jefazo92 on 2022-02-17
Hi everyone, 



I'm trying to install Ubuntu 20.04 on a Macbook Pro 15 as my host OS  (no dual-boot). I have been following the tutorial from this website: [URL="https://www.macworld.co.uk/how-to/how-install-linux-on-mac-3637265/#:%7E:text=Shut%20down%20the%20Mac%20you,Try%20Ubuntu%20and%20Install%20Ubuntu"]https://www.macworld.co.uk/how-to/how-install-linux-on-mac-3637265/#:~:text=Shut%20down%20the%20Mac%20you,Try%20Ubuntu%20and%20Install%20Ubuntu

[/URL]

 I selected "Erase disk and install Ubuntu" and clicked install. During the stage <<Running "grub-install/dev/nvme0n1"...>> of the installation process, I get the error <<Executing 'grub-install/dev/nvme0n1'  failed. This is a fatal error.>> See screenshot:


                                                                                                                                      [https://ubuntuforums.org/attachment.php?attachmentid=290059&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290059&stc=1)                                                                                                                                [URL="https://drive.google.com/file/d/1EYuZIwamY4K0dsievsnKE0McAFkDceL-/view?usp=sharing"]

[/URL]

 Before that when I had to choose the EFI Boot from the startup screen  I was being given 3 UFI Boot options which I already found strange. The  only one that has been working has been the icon to the far right in  the screenshot: [URL="https://drive.google.com/file/d/1u5C5EpiJdn4ZLLtikniAGOTiytOcJn7g/view?usp=sharing"]https://drive.google.com/file/d/1u5C5EpiJdn4ZLLtikniAGOTiytOcJn7g/view?usp=sharing

[/URL]

 I have read online that it could have to do with System Integrity  Protection. I tried to access it by holding command + R at power on but  instead it started internet recovery. I tried reinstalling the Mac  Mojave OS from there but I when I want to install I cannot select the  drive on which I want the OS to be installed and I am not allowed to  continue. Also on the suggestion from another forum I tried 

[COLOR=#1A1A1B]to boot  into Ubuntu usb, select "Try Ubuntu", open gparted from app menu,  select the disk, create partition table and choose gpt, then open "install ubuntu" from app menu and proceed with the installation using "erase disk & install". However, it didn't work for me.

[/COLOR]

 


What can I do from here on? I would like to install Ubuntu but if I  can have MacOS again and do a dual-boot from there that'd be fine by me  too. Any help would be very much appreciated.

---

### Post by oldfred on 2022-02-17
Please do not post screenshots or photos in line, just attach.
Not all users have high speed Internet.

Are you booting in UEFI mode?
Is drive gpt partitioned?
Do you have an ESP - efi system partition on the drive?

Post this:
sudo parted -l

---

### Post by MAFoElffen on 2022-02-18
@oldfred...

MAC Hardware,for over a decade, will only boot to a disk that is partitioned with GPT, and via UEFI. Remember that I have an old MacBook, that I picked up to test the 'system-info script on, for testing.

That tutorial is over 5-1/2 years old... Ubuntu 14.04 LTS. LOL. No mater. On the advice of the other forum you visited, you may have left some steps out... Unless you installed a new drive in that notebook, it should have been fine and already have had a GPT Partition table. Creating a new one, you deleted the old EFI directory on the drive...No matters.Ubuntu on erase and use all the disk should have created another. The installer is now a lot easier than the one in that tutorial. It's a fairly straight forward installation on Intel based MAC's.

Yes , post the results oldfred asked for...

---

