---
title: "Ubuntu 14.04 on brand-new Windows 8.1 computer, desktop"
date: 2015-02-09
forum: Installation &amp; Upgrades
---

### Post by andrewallison2012 on 2015-02-09
I'm having problems installing Ubuntu 14.04 on my computer.
I'm using a USBlive boot so far I have tried it with 
1. Universal-USB-Installer-1.9.5.9
2. creating a startup USB from another Ubuntu computer
3. UNetbootin
I've gotten the same results every time
-either a totally blank screen
-or a black and white text screen that says "kernel panic-not sinking: fatal exception in interrupt"

I have configured my UFEI BIOS as well.
-I have turned off safe mode
-changed the boot order ect
-changed SATA to IDE
-configured the CSM to only use legacy
-ran the installation with all the different F6 boot options
I do not know what to do now

---

### Post by cassialeilani on 2015-02-09
Did you make sure that you downloaded the right bit version? If so, the only other suggestion I have is that the download may have gone wrong and that you could try to re-downloading it. For UNetbootin did you use a disk image or just use the drop menu?

---

### Post by oldfred on 2015-02-09
You want Windows fast boot or always on hibernation off, but some UEFI also have a fast boot setting which you need to turn off or change to allow you to get into UEFI to reset things if needed.

Better to keep UEFI on and CSM/BIOS mode off. You can only dual boot from grub menu with both Windows & Ubuntu installed in UEFI mode. If Ubuntu is in CSM/legacy boot mode, you can only dual boot from UEFI boot menu.

You must download 64 bit version, best to verify ISO downloaded correctly with md5sum. 
If everything else ok, then issue may be related to video.
What brand, model computer and what video card/chip does it have?

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tachanchachi on 2015-02-09
I had a similar problem during the installation a couple of weeks ago, and I solved editing the partition table by hand. 
The Ubuntu installation went good afterwards. 

However, I have experienced the same black console-like window with the kernel-panic message afterwards. It appears without apparent reason whilst I was surfing on the Internet, last time. 
I was also connected to a server via ssh, using the console and doing diff -qr /path1/  /path2/ localy on a different console. 

Does somebody know why do I get it just like that, after being working for hours in Ubuntu? I rarely use Windows, although I decided to keep it in a very small partition... 

Thanks in advance

---

