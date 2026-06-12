---
title: "Can't install Ubuntu on HP machine"
date: 2018-05-30
forum: Installation &amp; Upgrades
---

### Post by arashaga on 2018-05-30
I have been trying to no avail for couple of days to install ubuntu server on a machine stand alone overriding the windows. I went trough the installation many times and I can't boot to ubuntu. I tried nonmodeset, apci=off all of that. Also, when computer boots up the system allows me to choose an option "Run UEFI Applications". When I do that I see a menu as FAT File System -> Boot and then under boot there is a fie called boot. I also tried to do a manual partitioning according to t[his article]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode") but it does not detect /boot/efi and only shows boot. So I am confused if it does not detect boot/efi that means it is not going to install on UEFI mode. So if it's not installing on UEFI mode why it's not booting normal. I also get an error message whee ubuntu is initializing. I have included the screen shot of my bios options and the error below. I i tried both installating from USB and DVD by the way. I would appreciate any help on this.

[IMG]https://s3-us-west-1.amazonaws.com/amosharraf-mydata/public/IMG_0864.jpg[/IMG]


[IMG]https://s3-us-west-1.amazonaws.com/amosharraf-mydata/public/IMG_0865.jpg[/IMG]

[IMG]https://s3-us-west-1.amazonaws.com/amosharraf-mydata/public/IMG_0866.jpg[/IMG]

---

### Post by cmcanulty on 2018-05-30
Have you tried this simple fix? I have a bunch of HPs and some will only boot with a DVD not a flash drive, which is very weird. Some will also install if you pick try not install then click install from the desktop live environment.

---

### Post by arashaga on 2018-05-30
I did try DVD. The server be soon doesn’t have the try option.

---

### Post by oldfred on 2018-06-01
How you boot install media, UEFI or BIOS is then how it installs.
Have not done an UEFI server install, but with desktop installer you do not see nor mount the ESP - efi system partition. It just is used.

Do not confuse the ESP which must be FAT32 with boot flag and the /boot partition which must be Linux formatted, if you have a separate /boot partition. It is often ext2 since smaller, not often updated , so journal does not add much that ext4 would add.

HP has not been UEFI boot friendly. It likes Windows.
Generally have to do a work around to make HP work.

Also in link in my signature below:
 Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

