---
title: "Can't install on Dell optiplex 760"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by joelstitch on 2012-12-31
I am trying to install Ubuntu 12.04 LTS on my Dell Optiplex 760 but it always gets stuck on the loading screen. For some reason my computer does not shows me the BIOS or the Dell logo at startup so I cant see the Ubuntu menu when you boot from the CD. It goes straight to the Ubuntu name with the loading dots and at some point it gets stuck. I have tried using a CD and flash drive to boot from and I get the same problems. I know the cd and the USB work because I tested it on other computers sop I don' t know why it always gets stuck.

I am running Windows 8 and tried using the Windows installer but it gives me an error so I cant install it either.

---

### Post by oldfred on 2012-12-31
Is system in BIOS or UEFI mode?

If windows 8 is it hibernated?

What video card/chip does system have?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by joelstitch on 2013-01-06
So I figured out how to get to BIOS (I had to remove the 2 extra video cards) but the Ubuntu disk/usb still freezes. Is there anything I have to change in BIOS?

---

### Post by oldfred on 2013-01-07
What video do you have? Often with nVidia you need nomodeset. And that works with some others also. And/Or other boot parameters may be needed. 

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by xaegis on 2013-01-07
> **joelstitch said:**
> ... I am running Windows 8 and tried using the Windows installer but it gives me an error so I cant install it either.

So are you saying that windows will not reinstall either? Are you having a boot sector issue? Have you run HDD and RAM tests to make sure these are functioning properly? Is SMART running on the HDD in bios?

---

### Post by joelstitch on 2013-01-07
> **oldfred said:**
> What video do you have? Often with nVidia you need nomodeset. And that works with some others also. And/Or other boot parameters may be needed. 

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I have a NVIDIA Geforce 8400 GS and a NVIDIA Geforce GT 545

> **xaegis said:**
> So are you saying that windows will not reinstall either? Are you having a boot sector issue? Have you run HDD and RAM tests to make sure these are functioning properly? Is SMART running on the HDD in bios?

Is not a boot sector issue because it does boots to BIOS, I think there is some setting on BIOS that would make it show it on every video card but I dont know which.

---

### Post by oldfred on 2013-01-07
I have nVidia 9600GT and have had to use nomodeset on liveCD/DVD/Flash boot and on first boot after install, until I get nVidia driver downloaded from Ubuntu.

---

### Post by joelstitch on 2013-01-09
How am I going to install nomodeset if I cant boot Ubuntu? I cant even install it trough Windows with the Windows Installer because it gives me an error.

---

### Post by oldfred on 2013-01-09
If both Windows DVD and Ubuntu DVD do not work are you sure you do not have a hard ware issue. 
       How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html](http://members.iinet.net.au/~herman546/p27.html)

    
You should be able to get into BIOS first.
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by freewish on 2013-03-11
> **joelstitch said:**
> I am trying to install Ubuntu 12.04 LTS on my Dell Optiplex 760 but it always gets stuck on the loading screen. For some reason my computer does not shows me the BIOS or the Dell logo at startup so I cant see the Ubuntu menu when you boot from the CD. It goes straight to the Ubuntu name with the loading dots and at some point it gets stuck. I have tried using a CD and flash drive to boot from and I get the same problems. I know the cd and the USB work because I tested it on other computers sop I don' t know why it always gets stuck.

I am running Windows 8 and tried using the Windows installer but it gives me an error so I cant install it either.

I also have one Dell optiplex 760 machine. I can't install 12.04 at first, and this is how it works for me. 
When boot up, try to press F6 before the installation start and select the acpi=off option. 
Then after the installation is done, and right before your first reboot. Modify grub2 configuration and add acpi=off to make it permanently.

```

sudo vi /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

```
And
```

sudo update-grub

```

Hope it works for you :)

---

