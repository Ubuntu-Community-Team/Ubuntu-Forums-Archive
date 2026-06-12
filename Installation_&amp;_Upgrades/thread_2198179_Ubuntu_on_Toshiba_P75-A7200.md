---
title: "Ubuntu on Toshiba P75-A7200"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by ram_saa on 2014-01-07
Some days ago I was trying to install Ubuntu (12.04 or 13.10 on 64 bits) in this Toshiba, but I failed. Sincerely I didn't know what was the UEFI Boot and the dificulties in the installation of Ubuntu in a computer with pre-installed Windows 8. I read a lot of posts until the laptop started to read the USB with Ubuntu, but nothing changed; first the screen gone purple, like when Ubuntu is initiating, but then the screen gone black, like when the laptop is off, and finally I heard a beep.


After that, I read that I have to disable the Secure Boot and enable the Legacy Emulation and the CSM Boot, at the same time I put the USB in the priority of the Boot Menu. With this I got a screen similar to [this]("http://thirderror.com/wp-content/uploads/2008/07/install_ubuntu.png"), but with a purple background; however, when I selected any option, again I got a black screen. I thought that maybe I have to wait, so I left the computer on all night, with the hope that the typical installation screen would appear, but it wasn't the case.


Then I become desperate, just a little, and with Gparted installed in a USB I deleted all the partitions that the computer have: all of them. However, I still have the same problem, I can only get the typical screen of try or install Ubuntu. As we can see, I don't have a clear idea about what I'm doing, and I don't know how damaging was having erased all the partitions of the laptop. So I post this in order to know how I can install Ubuntu under this situation. I know that probably I need to create the partitions in some way, but I don't know how. At most, I created a partition with 300 MB, with "EFI" label and in FAT32, because supposedly I read that is necesary; however, I still have the same result. I hope you can help me on the configuration because I'm a little upset about this situation xD


By the way, in almost all posts I read how to do a dual boot, but I'm not interested. Actually, I deleted all partitions because I don't want Windows at all. Also, I don't think to sell this computer, so I don't worry if I can't recover the partitions; I only want to do a clean Ubuntu install, either versión 12.04 or 13.10. I hope that with this it would be more easy to fix it.


Finally, the Toshiba specifications:
-Intel Core I7-4700QM procesador
-8 GB of Ram DDR3L
-1 TB of HD
-Intel HD 4600 graphics


Thank you!


P. D. Sorry for my writing.

---

### Post by sudodus on 2014-01-07
Welcome to the Ubuntu Forums :-)

I have another (simpler) Toshiba with Intel i5, possibility to run Windows 8 and a possibility to select between UEFI and CSM (alias old-style BIOS mode).

Maybe I can help you. With help from the real gurus oldfred here at the Ubuntu Forums, I could (just for the sport of doing it) make a dual boot system with Windows 8 and Ubuntu 12.04.3. But &#341;ight now I have disconnected that disk and use the computer in CSM mode. Then things are simple and it is easy to install Ubuntu and other linux operating systems.

Let us hope that you can enter the UEFI-BIOS menu system and switch off secure boot, fast boot and UEFI. Then it should be straight-forward to install any Ubuntu flavour and version 12.04.3 with long time support or the newest version 13.10.

But first you should try to boot a live session, 'Try Ubuntu without installing anything'.

There might be a secondary problem with drivers for the graphics chip and wifi chip. In that case I suggest that you use a boot option. Start with nomodeset, and then try to install a proprietary driver. See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ram_saa on 2014-01-07
Precisely I did that and if I click on "Try Ubuntu..." I only get a black screen; I think is because I deleted the partitions, buy I'm not sure : (

---

### Post by sudodus on 2014-01-07
No, 'Try Ubuntu' does not use the internal drive. I think you might have a problem with the graphics chip. Do you know what chip it is? Try some boot options (as I suggested in post #2).

---

### Post by ram_saa on 2014-01-07
[TABLE="width: 600"]
[TR]
[TH="bgcolor: #F6F6F6, colspan: 2"]Display[/TH]
[/TR]
[TR]
[TD]**Display size**[/TD]
[TD]17.3 inches[/TD]
[/TR]
[TR]
[TD]**Touchscreen**[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]**Aspect ratio**[/TD]
[TD]16:9[/TD]
[/TR]
[TR]
[TD]**Resolution**[/TD]
[TD]1920 x 1080 pixels[/TD]
[/TR]
[TR]
[TH="bgcolor: #F6F6F6, colspan: 2"]Graphics[/TH]
[/TR]
[TR]
[TD]**Graphics Type**[/TD]
[TD]Integrated[/TD]
[/TR]
[TR]
[TD]**Primary Graphics Chipset**[/TD]
[TD]Intel HD 4600[/TD]
[/TR]
[/TABLE]

So, did I need to try other boot options with the F6 key?

---

### Post by sudodus on 2014-01-07
I have good experience with Intel graphics. They usually work with the built in drivers in Ubuntu. (They are not as powerful as nvidia and amd/ati/radeon, but those are harder to get running and often need proprietary drivers). But I don't know about the 4600 version. Let us hope someone who knows about it will chip in an tell us about it.

---

### Post by cincibluer6 on 2014-01-07
Do you know if your flash drive with Ubuntu on it is even working correctly? How did you flash it?

The proper method for 13.10 is using PowerISO in Windows (sorry, unetbootin gives errors for some reason) or just use the dd command in Linux (dd if=path-to-file.iso of=/dev/sdx where x is the flash drive (as can be shown in gparted or with blkid.))
Also, make sure you do a valid md5sum on the downloaded iso.

I would start right at the source first off. Heck, find another computer and just try to boot Ubuntu on that one via the flash drive and then we can narrow it down to your computer and certain things.

---

### Post by sudodus on 2014-01-07
> **cincibluer6 said:**
> Do you know if your flash drive with Ubuntu on it is even working correctly? How did you flash it?

The proper method for 13.10 is using PowerISO in Windows (sorry, unetbootin gives errors for some reason) or just use the dd command in Linux (dd if=path-to-file.iso of=/dev/sdx where x is the flash drive (as can be shown in gparted or with blkid.))
Also, make sure you do a valid md5sum on the downloaded iso.

I would start right at the source first off. Heck, find another computer and just try to boot Ubuntu on that one via the flash drive and then we can narrow it down to your computer and certain things.

+1 

Good basic advice. I'll add this link [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ram_saa on 2014-01-07
I used Ubuntu Live USB Creator and it works fine, I tested the live USB that I created and it works well in others laptops, except this Toshiba : (

---

### Post by ram_saa on 2014-01-07
I could solve the problem following this post: [http://www.ubuntizando.com/2012/04/23/como-resolver-el-problema-de-la-pantalla-en-negro-en-linux/](http://www.ubuntizando.com/2012/04/23/como-resolver-el-problema-de-la-pantalla-en-negro-en-linux/)
However, I get this message when the system loads:

> [drm:drm_pci_agp_init] *ERROR* Cannot initialize the agpgart module.
DRM: Fill_in_dev failed.

Any idea?

---

### Post by sudodus on 2014-01-08
Are you running 12.04 LTS or 13.10? With a new computer, chances are better with a new version, that there are suitable hardware drivers. You might even try the future version Trusty Tahr, that is to become 14.04 LTS, but beware, it is still experimental, and you can expect that something might not work.

---

### Post by cincibluer6 on 2014-01-08
> **sudodus said:**
> Are you running 12.04 LTS or 13.10? With a new computer, chances are better with a new version, that there are suitable hardware drivers. You might even try the future version Trusty Tahr, that is to become 14.04 LTS, but beware, it is still experimental, and you can expect that something might not work.

Honestly, considering this is an LTS, I would expect that coming into January that 14.04 would be pretty ready for release at this point. Mainly it should be small bugfixes, etc. at this point.

---

### Post by ram_saa on 2014-01-09
I'm using 12.04 because I had a lot of problems with 13.10 on others computers...

---

### Post by sudodus on 2014-01-10
It is a good idea to stay with the LTS release, but sometimes you need the newest version to manage new hardware. So if you have already downloaded 13.10, try it live in this computer :-)

---

