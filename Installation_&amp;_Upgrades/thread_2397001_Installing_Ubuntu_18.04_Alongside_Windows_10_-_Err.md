---
title: "Installing Ubuntu 18.04 Alongside Windows 10 - Error Grub Failed"
date: 2018-07-24
forum: Installation &amp; Upgrades
---

### Post by mk2080 on 2018-07-24
I'm getting a grub failed to install error while trying to install Ubuntu 18.04 alongside Windows 10. While googling for answers I came across something called UEFI and legacy and that both windows and ubuntu would have to boot using the same mode. My Windows Bios says it is legacy when i look up system information but while booting from the USB drive i'm getting the Ubuntu UEFI dark screen  with white text. Also in the bios boot options there is only 'UEFI:Sandisk' option for my usb drive. Also during the install process , I chose 'something else' and created a swap and an ext4 partition as there was no option to 'Install Ubuntu alongside Windows'. I tried tuning off fast boot but the install still fails. Here is my pastebin [http://paste.ubuntu.com/p/nSjqrJwZxM/](http://paste.ubuntu.com/p/nSjqrJwZxM/)

---

### Post by yancek on 2018-07-24
The boot repair output shows that windows is installed with windows boot code in the MBR.  If you want to boot Ubuntu from the windows bootloader, it is possible to do following the instructions at the link below.  This will only work if Grub is properly installed on sda6 and that partition does not seem to have the necessary Grub files, no grub.cfg menu file shows.

 [https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

I don't know why you are getting the UEFI screen on Ubuntu.   The installation of Ubuntu was not done in UEFI as there are no EFI files showing but it also does not look like it was successful.   According to the Ubuntu docs, if you are installing Legacy, you should see the purple Ubuntu screen and you report you do not so I'm not sure what the problem is there.  Re-check the BIOS for Legacy/CSM options to enable

---

### Post by mk2080 on 2018-07-25
> **yancek said:**
> The boot repair output shows that windows is installed with windows boot code in the MBR.  If you want to boot Ubuntu from the windows bootloader, it is possible to do following the instructions at the link below.  This will only work if Grub is properly installed on sda6 and that partition does not seem to have the necessary Grub files, no grub.cfg menu file shows.

 [https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

I don't know why you are getting the UEFI screen on Ubuntu.   The installation of Ubuntu was not done in UEFI as there are no EFI files showing but it also does not look like it was successful.   According to the Ubuntu docs, if you are installing Legacy, you should see the purple Ubuntu screen and you report you do not so I'm not sure what the problem is there.  Re-check the BIOS for Legacy/CSM options to enable

I'm completely stumped as to what I should do. The specific error i'm getting is ```
grub-efi-amd64-signed package failed to install
```

Legacy option is enabled in the bios but there is no CSM option, Also I couldn't find any secureboot option to disable and the installation was done with internet on and third party software checked, but i still get the grub failed error. I saw someone mention in another website to remove the EFI folder but once I did that the USB wouldn't even boot.

Also on the paste url i can see that [COLOR=#000000]**/sys/firmware/efi/** is present, because i read on some website that if that efi folder is present that means the install was done in UEFI?. And yes, I do get the UEFI screen when the USB boots.[/COLOR]

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

---

### Post by roadrawts on 2018-07-25
Finally go Ubuntu to boot alongside Windows 10.  Used comment 13 about setting up Trust of the OS.  Thank you all for your advice.

---

### Post by mk2080 on 2018-07-27
Ok, I finally managed to solve this problem. What I did was instead of using the USB, i burned the ISO onto a DVD, and once I did that I had two dvd boot options, UEFI and non UEFI. Not sure why I didn't get two options like this when booting from USB. Anyway it's solved.

---

