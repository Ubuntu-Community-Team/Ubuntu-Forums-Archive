---
title: "Cant Boot up from USB"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by lauraleesmith2012 on 2012-11-12
**[COLOR=purple]Hello. My name is Laura Smith. I recently bought a new Toshiba Satellite laptop. It came with Windows 8 preinstalled. I am not fond of it and want to try out the latest offering of Ubuntu, 12.10. I made a bootable installation on my USB, but the system wont allow it to boot, due to the 'secure boot" mechanism. How do I get around this issue? :( [/COLOR]**

---

### Post by Mr_JMM on 2012-11-12
Hello Laura Smith.
As you've discovered, it's not so simple with Windows 8. I had a quick search and found this article - [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

This should help you. Sorry I can't be more help. Like you, I couldn't find a definitive how-to on the forum but hopefully someone will be able to point us to one.

---

### Post by carl4926 on 2012-11-12
I think you need to access the UEFI boot menu in the BIOS

---

### Post by Cheesemill on 2012-11-12
There should be a setting in the BIOS to disable secure boot, you can enter the BIOS by pressing a certain key (usually F2 or F12) when you turn the computer on. Your laptop manual should have instructions on how to do this.

Please note that disable secure boot will leave you unable to boot Windows.

---

### Post by oldfred on 2012-11-12
Did you download the 64 bit version of Ubuntu? Only the 64 bit version has UEFI support and 12.10 with grub2 2.00 is supposed to work with secure boot. (Have not seen anyone do it yet though). Most just turn off secure boot. I think Windows still works as several have posted they have turned secure boot off to install Ubuntu.

You also may have video issues. What video card/chip do you have?

---

### Post by lauraleesmith2012 on 2012-11-12
> **Mr_JMM said:**
> Hello Laura Smith.
As you've discovered, it's not so simple with Windows 8. I had a quick search and found this article - [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
 
This should help you. Sorry I can't be more help. Like you, I couldn't find a definitive how-to on the forum but hopefully someone will be able to point us to one.
 
Thanks for the link Mr_JMM.  I will check out the link.

---

### Post by lauraleesmith2012 on 2012-11-12
> **carl4926 said:**
> I think you need to access the UEFI boot menu in the BIOS
 
Thanks carl, I will look into that.

---

### Post by lauraleesmith2012 on 2012-11-12
> **Cheesemill said:**
> There should be a setting in the BIOS to disable secure boot, you can enter the BIOS by pressing a certain key (usually F2 or F12) when you turn the computer on. Your laptop manual should have instructions on how to do this.
 
Please note that disable secure boot will leave you unable to boot Windows.
 
Thanks.  :)

---

### Post by lauraleesmith2012 on 2012-11-12
> **oldfred said:**
> Did you download the 64 bit version of Ubuntu? Only the 64 bit version has UEFI support and 12.10 with grub2 2.00 is supposed to work with secure boot. (Have not seen anyone do it yet though). Most just turn off secure boot. I think Windows still works as several have posted they have turned secure boot off to install Ubuntu.
 
You also may have video issues. What video card/chip do you have?
 
I am not sure what video card I have but will post that information shortly.  I downloaded the 64 bit version of Ubuntu.

---

### Post by lauraleesmith2012 on 2012-11-12
> **oldfred said:**
> Did you download the 64 bit version of Ubuntu? Only the 64 bit version has UEFI support and 12.10 with grub2 2.00 is supposed to work with secure boot. (Have not seen anyone do it yet though). Most just turn off secure boot. I think Windows still works as several have posted they have turned secure boot off to install Ubuntu.
 
You also may have video issues. What video card/chip do you have?
 
Here is my system information:

---

### Post by oldfred on 2012-11-12
Are you getting an error message on secure boot. 

From UEFI menu you have to boot USB flash drive in UEFI mode not BIOS or whatever other mode is called. Only UEFI mode will support secure boot.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

If issues is related to blank screen then it may be video, but I do not know AMD as I have nVidia.

Do not know if some of this applies to your version or not:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by lauraleesmith2012 on 2012-11-12
> **oldfred said:**
> Are you getting an error message on secure boot. 

From UEFI menu you have to boot USB flash drive in UEFI mode not BIOS or whatever other mode is called. Only UEFI mode will support secure boot.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

If issues is related to blank screen then it may be video, but I do not know AMD as I have nVidia.

Do not know if some of this applies to your version or not:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

Yes, there is a boot up error that is displayed,[COLOR=Red] " Boot failure:  a proper digital signature was not found. One of the selected files on the boot device was rejected by the Secure Boot feature. "[/COLOR] I have not yet turned of Secure Boot yet, because I wanted to make sure that's something I need to do.

---

### Post by oldfred on 2012-11-12
Someone in another thread posted that his system worked with either secure system on or off. So it should work.

Are you booting from UEFI menu and using UEFI mode from install CD or flash drive? Other mode is for BIOS and may be called BIOS/AHCI/Legacy or something.

---

### Post by carl4926 on 2012-11-12
Not all UEFI mobos have a legacy option

If I can, I'd like to point to a couple of well written articles in the openSUSE forum, hope that's OK

[http://forums.opensuse.org/content/102-booting-opensuse-uefi-bios-elilo-grub2-linux-only-multi-booting.html](http://forums.opensuse.org/content/102-booting-opensuse-uefi-bios-elilo-grub2-linux-only-multi-booting.html)

[http://forums.opensuse.org/content/105-booting-opensuse-uefi-bios-elilo-grub2-windows-dual-boot.html](http://forums.opensuse.org/content/105-booting-opensuse-uefi-bios-elilo-grub2-windows-dual-boot.html)

*Consider though, these were written for openSUSE 12.1 which used legacy grub

I post those to help with getting an understanding only

---

### Post by lauraleesmith2012 on 2012-11-13
Ok, here is my current status of installing Ubuntu.  I disabled the secure boot on my machine, and can still run Windows 8 with that feature off.  However, I still am having issues trying out the live USB.  When I boot from the drive, it lets me choose what mod of Ubuntu to go into, I select the regular version, not the compatibility mode, but after doing selecting the mode I want, it goes to a black screen, and sits there, does nothing.

---

### Post by lauraleesmith2012 on 2012-11-13
I assume my graphics card is the issue.  

AMD Radeon HD 6300 hraphics card

---

### Post by lauraleesmith2012 on 2012-11-13
Basically, its a black screen, but the computer screen is on, and there is no curser at all.

---

### Post by oldfred on 2012-11-13
I have nVidia so I have not followed all the AMD stuff. Some links to get you started.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

