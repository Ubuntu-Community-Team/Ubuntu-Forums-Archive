---
title: "Problems to install ubuntu aside windows (usb cable bad / grub prb)"
date: 2018-08-12
forum: Installation &amp; Upgrades
---

### Post by totog1nger on 2018-08-12
Hello everyone,


I am trying to install ubuntu 18.04 aside windows on my computer.
My computer is an ASUS GL553VD.


For now, I shrinked my ssd and made a 30Go partition for Ubuntu.
I am following this french tutorial : [https://www.youtube.com/watch?v=hTIIx9-ZAyw&t=665s&index=19&list=PLBI40N1MjTOCVe4eBRopUOVGI9Pv7YdcV](https://www.youtube.com/watch?v=hTIIx9-ZAyw&t=665s&index=19&list=PLBI40N1MjTOCVe4eBRopUOVGI9Pv7YdcV)


Also the fast boot is disabled as well as secure boot.
I also disabled the hibernate option on windows with the command ```
powercfg -h off
``` (as a first try to solve my problems).


I can boot on my Ubuntu USB key, but half of the time it says me something like "Maybe the USB cable is bad?", and I can't remember what was before.
The other half of the time it stays stuck on the Ubuntu splash screen.
And by half the time, I mean it is like really one case after the other one...


Also I tried to to do the disk analysis (below "try ubuntu" and "install ubuntu") and it stayes stuck on something like "/...uefi/...grub".
I am sorry not to be precise on my description :(


Also, I searched for few solution to correct that.
One of the most viewed answer was to do some commands on the linux terminal.
It said I could have access to the terminal by doing ctrl + alt + f1 or f2 or f3.
I tried every f options and also del and escape without any result.
To be honest, I don't know if I was doing it at the right moment.


I am a student in computer science so I have some knowledge but I am stuck here and I don't fully understand how the installation of linux works.
I just want to have ubuntu on my computer so I can stop using windows for work.


If you need some more precision don't hesitate to tell me, I can also try again to install it in order to have the precise error messages.


Thank you a lot for your help and time,
Thomas.

---

### Post by yancek on 2018-08-12
You neglected to mention which version of windows you are using which is an important factor.  If you are using windows 10, read the information at the Ubuntu site below on dual booting with windows 10 using UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You might try booting again and try getting more details on the messages you see as that might help someone to help you.  Also, what software did you use to create the bootable usb and are you able to try booting it on another computer?  Did you do a checksum on the iso after the download to verify the download?

---

### Post by totog1nger on 2018-08-12
First thank you for your help yancek.
Yes my computer was peinstalled with windows 10.
I did my bootable USB key with rufus and the Ubuntu 18.04 iso image downloaded from here [http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/).

So I tried again to do what I tried yesterday :
So I pluged my USB key, and went into the bios to set the key as first boot, before windows.
I saved and restart the computer. Then I got the following messages :
```
ACPI Error : [PRT0] Namespace lookup failure, AE_ALREADY_EXISTS (20170831/dswload-378)
ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20170831/psobject-252)
ACPI Exception: AE_ALREADY_EXISTS, (SSDT:SataTabl) while loading table (20170831/tbxgload-228)
ACPI Error: 1 table load failures, 10 successful (20170831/tbxfload-246)
usb usb2-port1: Cannot enable. Maybe the USB cable is bad?
usb usb2-port1: cannot disable (err = -32)?
usb usb2-port1: Cannot enable. Maybe the USB cable is bad?
usb usb2-port1: cannot disable (err = -32)?
```


I forced the computer to restart.
There it stucked on the Ubuntu splash screen.

I forced the restart again, get stuck on acpi pb and usb bad cable, restart again and try to "Check disk for defects".
It stucked on "Checking ./boot/grub/*86_64-efi/pbkdf2_test.mod".

Since there are a multiple problems at the same time I really have no idea on which one to correct first and even how.
Does it precise my problems and help you to understand the way to correct that ?

Thomas

---

### Post by yancek on 2018-08-12
I'm not familiar with those errors and am not sure why it reports "Cannot enable. Maybe the USB cable is bad?".  Might be that usb port is bad so if you have multiple usb ports, try another.

Did you read the info in the link I posted on UEFI dual booting?  Is your BIOS set to boot UEFI?  I would expect that.  Reading through that documentation should tell you what to expect to see when booting UEFI with Ubuntu.

---

### Post by totog1nger on 2018-08-13
I verified and yes my windows is set on EFI.

For the "maybe cable is bad", I think it is an issue with linux.
My computer has been repaired 2 weeks ago and they changed the motherboard.
Also, it does the same thing with all my three ports.
Moreover, I already have had something like that when I tried to install ubuntu few months ago with the previous motherboard that was 4 months old.

Yes, I began to read your link but I didn't find any real solution.
I understood that I should install Ubuntu on EFI mode since my windows is on EFI too,
It says that they can both use the same EFI System Partition and that I don't have to create one.
But it doesn't solve my problems especially for my "[COLOR=#000000]Checking ./boot/grub/*86_64-efi/pbkdf2_test.mod[/COLOR]" issue.

I will try to solve that in the following days.
Thank you for your help,
Thomas

---

### Post by mo3az014 on 2019-02-25
I had the same problem while installing ubuntu 18.04 aside with windows 10.
I was using this tutorial: [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)
and I solved the same problem by following this tutorial:
- for disable fast startup: [https://itsfoss.com/solve-ntfs-mount-problem-ubuntu-windows-8-dual-boot/](https://itsfoss.com/solve-ntfs-mount-problem-ubuntu-windows-8-dual-boot/)
- for disable secure boot: [https://itsfoss.com/disable-uefi-secure-boot-in-windows-8/](https://itsfoss.com/disable-uefi-secure-boot-in-windows-8/)

---

### Post by slickymaster on 2019-02-25
Thread moved to **Installation & Upgrades** for a better fit

---

