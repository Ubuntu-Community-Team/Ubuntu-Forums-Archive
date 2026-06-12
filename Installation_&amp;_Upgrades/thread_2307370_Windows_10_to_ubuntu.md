---
title: "Windows 10 to ubuntu"
date: 2015-12-24
forum: Installation &amp; Upgrades
---

### Post by Anjela_Johnoson on 2015-12-24
I'm using Ubuntu 15.10 on my Lenovo Latop, and it seems it is runing OK. Now i want to install Ubutu in My Home PC with Woindows 10. Is there any difficulties in installing it together with windows 10?

---

### Post by brian-mccumber on 2015-12-24
Are you dual booting on your laptop too? 

Windows 10 is apparently utilizing a different type of bios and if certain steps are not followed it could potentially cause both operating systems to not be able to boot up without repairing the boot sector first. Another thing you might want to be worried about is if your hardware in your home pc is compatible with Ubuntu. But you can always make a bootable usb or dvd/cd and run the live version first to see if there would be any problems. I found this guide on dual OS installation that looks pretty promising -  [http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

---

### Post by grahammechanical on 2015-12-24
This is still applicable even though it does not mention Windows 10. Look at the section Installing Ubuntu in UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If this home PC came with Windows 10 pre-installed or it came with Windows 8 pre-installed and has been upgraded to Windows 10 then the Ubuntu wiki page really does have relevance.

If the PC came with Windows 7 pre-installed that has been upgraded to Windows 8 & then Windows 10 the situation might be different. Also, there are posts on this forum relating to problems people have had dual booting with Windows 10 both as regards installation and as regards loading Ubuntu after Windows 10 has had an update. Those posts are useful case studies.

Regards.

---

### Post by Frogs Hair on 2015-12-24
My desktop with a legacy bios was not a problem . installing with UEFI, depending on version and if modified by the OEM can be unique for each brand or model of computer.

---

### Post by Anjela_Johnoson on 2015-12-24
My home PC has UEFI.. Hardware amd  FX-8350 on Asus maiboaard with  16Gb ram and Radeon video card. I think that's quiet enough for ubuntu ;)

Ok. thanks for reply. I'll try ti install it. Hope my PC will not die.

---

### Post by oldfred on 2015-12-24
I have an Intel based Asus motherboard and had to make many setting changes in UEFI. Main one was to UEFI only for USB flash drive. Even UEFI & CSM/BIOS did not let me boot in UEFI mode. I also turned off UEFI fast boot, so I had time to get into UEFI until fully configured. And left fast boot off on cold boot. And on warm boot or reboot set to 3 sec delay, so I did have some time to get into UEFI if needed.

---

### Post by jean noel on 2015-12-25
OMG. I recently bought a Packard Bell ENT G71BM for work, with the idea of installing 14.04, which I use at home. It was a complete disaster. This is my first encounter with UEFI. First it would not boot from cd. Next, despite installation of 14.04 complete, there would be a "no bootable media" message shown on boot. I still trying to figure out how to tame UEFI. :-)

---

### Post by kurt18947 on 2015-12-25
> **Anjela_Johnoson said:**
> My home PC has UEFI.. Hardware amd  FX-8350 on Asus maiboaard with  16Gb ram and Radeon video card. I think that's quiet enough for ubuntu ;)

Ok. thanks for reply. I'll try ti install it. Hope my PC will not die.

If you haven't started yet, I would recommend creating a complete backup of your present system first. There are no or low cost ways to accomplish that. I believe it's also possible to create a Windows install disk from Windows though I haven't tried it. It sounds like UEFI is today where 'traditional' BIOS was years (decades) ago when each manufacturer did things a bit differently.

---

### Post by yoshii on 2015-12-25
I have an HP with UEFI, and I couldn't change the boot order until I enabled legacy boot mode (MBR boot mode).  Unfortunately, it wouldn't let me enable legacy boot mode until after I'd disabled secure boot and restarted.  After I disabled secure boot and restarted, then I could enable legacy boot mode.  And then after I rebooted after that, I could change the boot order to all the CD to boot first.  After each BIOS change saved you have to reboot.  Maybe this can help you.

---

### Post by jean noel on 2015-12-29
Sorry for being a bit late, as I was at work. I did a back up on a usb drive. My luck, since I was not provided with a Windows 10  disk. I guess you have to be careful when installing another OS in a UEFI mobo. I guess I will have to do some research before installing my beloved 14.04 on this laptop.
Regards
Jean Noel

---

### Post by kurt18947 on 2015-12-29
> **jean noel said:**
> Sorry for being a bit late, as I was at work. I did a back up on a usb drive. My luck, since I was not provided with a Windows 10  disk. I guess you have to be careful when installing another OS in a UEFI mobo. I guess I will have to do some research before installing my beloved 14.04 on this laptop.
Regards
Jean Noel

You can download a Windows 10 .iso direct from Microsoft if necessary, it's legitimate. You'd still need the activation key. There may also be a way to create Windows 10 install media from the installed Windows O.S; there was with Windows 8.x I believe.

---

### Post by jean noel on 2016-01-05
I was able to make a back up of the windows installation. The problem is that when the installation has completed, there is a "no bootable media" message. I installed Ubuntu just like I have always done. I guess you have to make a special procedure to enable dual booting.
Regards

---

### Post by oldfred on 2016-01-05
@ jean noel
If you need specific help with your system, please start your own thread.
This is Anjela_Johnoson's thread with a Lenovo system. Yours is not Lenovo, so issues may be greatly different even if boot issues. And trying to deal with two totally different issue in one thread gets confusing. Plus when issue is solved (hopefully) other users can search for your system. And you can only close & set [solved] on your own thread.

---

