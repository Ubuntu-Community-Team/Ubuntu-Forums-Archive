---
title: "USB Installation issues"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by taloravia on 2014-09-24
Hello,

I have been trying to install ubuntu on a 8GB flash drive. I am using the 64 bit ubuntu 14.04.1 LTS. I followed the intructions here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows). I am currently running 64 bit windows 8.1. I can run the 32bit 14.04.1 Ubuntu from a USB stick and I also can run 64 bit through a VM on my system. However, every time I try to run 64bit ubuntu off of a USB stick I get this error: [http://imgur.com/dWBKELQ](http://imgur.com/dWBKELQ)  Any ideas on how to fix this or why it is happening?

Hardware: 

CPU: AMD DX(tm)-8350 Eight core processor 4.00GHz
Ram: 16 GB

---

### Post by varunendra on 2014-09-25
Hello taloravia, Welcome to the forums!

Please clarify whether you want to actually "Install" ubuntu on the drive or make it "Live" bootable. The link you gave is about is making it "Live" bootable - something similar to an installation DVD which you use to "Install" the OS on other disks. The Live mode does give you a usable graphical environment, but is very different from a session running from an 'Installed' instance of the same OS. For now I am assuming you mean a "Live Bootable USB".

Depending on the version of syslinux used in the Live USB, the Universal USB Installer can cause problems with some systems. For example, the latest version of syslinux used in YUMI (a multiboot tool from pendrivelinux.com) does cause similar, if not the same, problem with some laptops while it works flawlessly with some others.

If you have setup VMs, I recommend to boot one with the Ubuntu ISO that you want to create USB from, then use its inbuilt "Startup Disk Creator" program to make the USB live bootable. I think VMware allows using USB drives without installing "VMware Tools" on the guest OS. If it is VirtualBox you are using, it may require you to install 'Extension Pack' to be able to use USB drives within the guest OS.

So far, I have found the inbuilt Startup Disk Creator to be most promising tool for creating Live USBs.

Be also aware that laptops that come with Windows 8 preinstalled usually have "FastBoot" and/or "Secure Boot" features enabled in their UEFI firmware. This may also be a reason for the error you got. But I don't know much about that and so am not sure. But you should disable "Secure Boot" as explained here : [https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)

---

### Post by taloravia on 2014-09-30
Running ubuntu in VMware fixed the issue that I was having, thank you for the help :)

---

