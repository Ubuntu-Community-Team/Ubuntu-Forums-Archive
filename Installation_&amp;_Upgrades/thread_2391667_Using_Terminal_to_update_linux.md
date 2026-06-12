---
title: "Using Terminal to update linux"
date: 2018-05-12
forum: Installation &amp; Upgrades
---

### Post by turb03 on 2018-05-12
Hello guys,

I'm fairly new to the Linux community, so I'm not that familiar with all the commands. A few weeks ago I installed Lubuntu 17.04, but because my laptop is pretty old I had a lot of graphics card issues, mainly because of the drivers. So after talking with a few friends, I decided to update my Kernel to the newest one, and that fixed my graphics issue but made a new one, as the Kernel doesn't support my network card drivers. I asked in the forums again, and one guy suggested me I either update to Linux V. 18 or 16, so I was choosing is there  a way I can do this directly from the terminal? Because I don't want to waste space on CDs and make a bunch of linux disc copies. If anyone knows if that is possible and how to do it, please help me out. 

Thank you very much for your help,
-turb0

---

### Post by Impavidus on 2018-05-12
Lubuntu 17.04 reached end of life a while ago. 17.10 is close to end of life, 16.04 is has almost a year left and 18.04 has almost 3 years left, but is new and can be slightly buggy. I suggest Lubuntu 18.04 or, if you really want stability, 16.04.

You can upgrade your 17.04: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades). However, a fresh install is more reliable. Can your computer boot from usb? In that case you don't have to waste a dvd. It is possible to boot a live disk image sitting on your hard drive using grub, but it's a bit complex and comes with some limitation on how you can partition your hard drive. That would be my last resort.

Old hardware rarely needs the latest kernel, but if you give us some details about your hardware someone may know.

---

### Post by garvinrick4 on 2018-05-12
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
#Go to this site and scroll to bottom and select 4.16.1
#Open and select these 3 packages below note .deb means already built and ready to install
#after downloading open files icon on sidebar and select recent tab and drag the three downloads to desktop
linux-headers-4.16.1-041601_4.16.1-041601.201804081334_all.deb
linux-headers-4.16.1-041601-generic_4.16.1-041601.201804081334_amd64.deb
linux-image-4.16.1-041601-generic_4.16.1-041601.201804081334_amd64.deb
#ready to install run these below in terminal
> cd Desktop
> ls
#should see the 3 packages after ls
> sudo dpkg -i *.deb
#now new kernal is installed reboot and open terminal
> uname -a 
#will say new kernal.
#when booting you can go down to Advanced option and see installed kernels
  and select any kernels to boot from, hit exit to go back to boot page

---

### Post by garvinrick4 on 2018-05-12
Oh geezzz I read post wrong thought you wanted to use newer kernel. Sorry but highlight and copy and
save for use in future if needed or for helping others that need to fetch a new kernel.

---

### Post by SeijiSensei on 2018-05-12
> **turb03 said:**
> I was choosing is there  a way I can do this directly from the terminal? Because I don't want to waste space on CDs and make a bunch of linux disc copies. If anyone knows if that is possible and how to do it, please help me out. 
If you're migrating from 15.10 to 18.04, you should start with a fresh installation.  

You don't need to burn discs; use a USB drive instead.  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by deadflowr on 2018-05-12
The most convoluted way I've ever install/reinstall/fresh installed Ubuntu was to convert my swap partition into a normal (ext4) partition, put the downloaded new Ubuntu iso image into the new partition, setup grubisoboot booted into the aforementioned iso, then went about and installed the new version into the partition Ubuntu was on.
Then after the install, installed gparted and reset the swap partition back to swap and then edit the fstab to see it.
(in 17.10 and newer, there is no need to reset the swap partition, as Ubuntu now defaults to a swap file instead)

I did this because I had no usb sticks or dvds available at the time.
(And probably some other reason I forget)

Convoluted? Indeed.
Did it work? Yes


Ref:
[https://help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")
[https://help.ubuntu.com/community/Grub2/ISOBoot#Installing_Ubuntu_from_a_Menuentry_Boot]("https://help.ubuntu.com/community/Grub2/ISOBoot#Installing_Ubuntu_from_a_Menuentry_Boot")

I personally choose the swap partition to place it because it needs to be somewhere that won't be overwritten and swap was as good as any.

---

### Post by turb03 on 2018-05-26
Alright guys thank you very much! I will probably go with the 16.04 as it is also 32 bit and the new one is only 64! :)

---

### Post by Impavidus on 2018-05-27
Ubuntu 18.04 only has a 64 bit live disk image, but Lubuntu and Xubuntu (and maybe some other flavours too) still have 32 bit available. On old hardware you want one of the light flavours anyway. The light flavours of 16.04 have less than a year support left.

---

