---
title: "Ubuntu installation without external media"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by z33 on 2007-04-25
**Issue:**

I want to install ubuntu on a laptop that does not have floppy or cd-rom. I want to install the required files for installation onto the Harddrive so that it install on its own.

**My Proposed Solution:**

I remove the harddrive and put it in a usb enclosure. Plug it into my windows machine and use the installation method shown here [link to ubuntu installation guide]("https://help.ubuntu.com/community/Installation/FromWindows")

**What I want from you:**

Will this work if i put the required files on the drive and then plug it back into the laptop? Or does it have to be connected to my windows machine? Please let me know if i am not clear on what i need.

---

### Post by jda1701 on 2007-04-25
The only big problem I find with this is that the ubuntu installer will only initialize the hardware it finds on your windows machine.  So even if you get the OS installed via the USB enclosure, putting it back into your laptop will probably cause it not to boot (firstly since grub will be looking for something other than hd(0,0) and secondly because some of your hardware wouldn't have been probed and might need to be setup manually.

I'm all for you trying it if you have the time though.  You could try to edit the grub menu item line at your first boot to reflect which partition to boot to according to your laptop's setup.  If you can get it to boot at least to a console login you can edit /boot/grub/menu.lst to reflect that change and reboot.  

Its possible that the bootup hardware probing will be able to find all your hardware and you should be fine.  The biggest concern is whether or not grub will be setup correctly to find the kernel image on that first boot.

If you do decide to try it, post a reply with if and how you got it working.

Good luck!

---

### Post by Ambimom on 2007-04-25
Here's a suggestion....why not download VMWare Server (it's free). [I also recommend Parallels for Llinux very highly, but that costs about $70].  Then download an iso for Ubuntu.  

You can boot Ubuntu in the VMWare Server using the iso file only without the need for hard drive or flash drive.  You may have to tinker around a bit to get the wireless to work but there's plenty of help here on NDIS wrapper et.al.  Another issue might be that your webcam and microphone might not be useable in VMWare, but everything else will work.  Oh, and you can't use Beryl or Compiz, but that's just eye candy anyway.

As long as you have at least 512 RAM, you should be good to go.  Ubuntu hums along on only 256 RAM. 

In my experience virtualization is the best of both possible worlds....you are not rebooting constantly as in a dual boot system; and you have access to both operating systems to optimize your productivity.

---

### Post by rich.bradshaw on 2007-04-25
Is that anything to do with his question?

You can do it I think over a network - you might need to boot from a floppy though to get started...

---

### Post by z33 on 2007-04-25
I tried a floppy drive i had (USB) however it did not get detected. (Tried a USB CD-ROM also) Before I explore the issues with why the floppy isnt working I was wondering if I could just get it done on a different machine. (I did enabled usb device bootup on the BIOS) 

BTW it is a pentium 3 fujitsu lifebook. No CD-ROM and no Floppy onboard. I am not even sure it can do a network boot.

I hope that was helpful.

---

### Post by z33 on 2007-04-25
I tried doing my solution mentioned in my first post but it didnt really work out.

The scenario i want is to copy installation files to the harddrive and also a copy of grub. So that once i plug the drive back into a laptop where it is hd0, grub will pick up and boot the installation of ubuntu.

---

### Post by metromari on 2007-04-25
Try installing from USB flash drive. This can get you started:

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-usb-files.html)

---

### Post by z33 on 2007-04-26
If a usb floppy and a usb cd-rom dont get detected will a usb flash drive get detected?

---

### Post by z33 on 2007-05-06
I am having no luck with this issue can anyone help with some direction?

---

