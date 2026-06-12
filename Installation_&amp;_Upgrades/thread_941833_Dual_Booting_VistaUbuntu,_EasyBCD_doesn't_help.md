---
title: "Dual Booting Vista/Ubuntu, EasyBCD doesn't help"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by gopchandani on 2008-10-08
So I tried to look forum for similar problem, kindly help out and bear with me for the longer post.

I installed Vista and then installed Ubuntu and unchecked the box for installing bootloader in MBR (wanted to have Vista controlling things). After Ubuntu was installed, I plugged in EasyBCD (which helps to manipulate Vista's bootloader) and put an entry for Linux. (I tried it both ways, checking/unchecking the GRUB isn't installed to the bootsector checkbox) it doesn't work.

I do get the Linux options when Vista's bootloader shows up but when I choose to go in, instead of booting Ubutu, it takes me to grub> prompt. Here I have tried to use find /boot/grub/stage1 but I get an error 17. 

Then I tried to go about doing it using Ubuntu LiveCD and following this tutorial here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) - assuming that my Grub is not installed. But it doesn't work. Grub still shows an error 17.

I check /boot folder but there is no "grub" sub-directory so I am thinking that grub hasn't been installed at all. How should I do it now, is there any other tutorial than the one mentioned above? Can you think of stuff which I am doing incorrectly.


Thanks

---

### Post by caljohnsmith on 2008-10-08
> **gopchandani said:**
> 
I installed Vista and then installed Ubuntu and unchecked the box for installing bootloader in MBR (wanted to have Vista controlling things). 

If you unchecked the box to install the Ubuntu boot loader (Grub), then it doesn't install Grub at all, and you won't have a /boot/grub directory. If you want to use Vista's boot loader instead of Grub, one way is you can use the "NeoGrub" option in EasyBCD to boot Ubuntu; but then you will have to figure out the correct Ubuntu entries to put in the menu.lst. 

A better solution for using the Vista boot loader to boot Ubuntu is to install Grub to the boot sector of the Ubuntu partition, instead of the MBR. That way it is really easy to "chain load" Ubuntu from Vista's boot loader. Here is a tutorial:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

So if you don't mind reinstalling Ubuntu, when you get to the final stage of installing, click on the "advanced" button and you can tell Grub to install to your Ubuntu partition boot sector by using /dev/sdaX, where sdaX would be your Ubuntu partition, like /dev/sda2 for example. Make sure you use the Ubuntu partition, and not /dev/sda, as that will install Grub to the MBR of sda. 

Or it is possible to install Grub after you've done the installation, but it is more trouble. So if you can just reinstall, I would recommend doing that at this point. Let me know how it goes or if you need more info/details. :)

---

### Post by gopchandani on 2008-10-08
Yes, re-installing Ubuntu fixed it. But it is a lot of pain. I think it should be made more obvious with that checkbox that if you choose to un-check it then no boot-loader shall be installed.

Anyway. Thanks.

---

