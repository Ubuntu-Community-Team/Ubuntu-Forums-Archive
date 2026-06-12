---
title: "UEFI on gigabyte motherboard(GAH77-DS3H) and Ubuntu and XP"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by Dennis McClary on 2013-11-18
I am building a new computer using the above motherboard. It will have two hard drives, one with Windows XP and the other with Ubuntu 12.04 LTS. I want to install 32 bit Ubuntu as I have had better luck with getting citrix receiver to work on on 32 bit. I use Citrix receiver to access my company's network and to do some work from home. From my research, I believe I should turn off UEFI in the bios and set it to legacy bios. I am going to back up data on both hard drives which are now in an old Dell and then attempt to boot in the new computer. If not possible, I will re-install both operating systems. Also, my new computer will have 4 gb of ram. My understanding is that if am able to boot my existing Ubuntu installation I will need to manually enable PAE as it was originally in a computer with 2 gb of ram. If make a new installation it should automatically be enabled in a system with 4 gb of ram. Correct? 

I am sticking with Windows XP as the wife has a few old arts and crafts programs that run on XP and my son has a RC plane simulator. 

Thanks in advance for any advice.

Dennis

---

### Post by fantab on 2013-11-18
Yes, reinstalling OS is a good idea. As the System has different hardware, the OS installed and configured to older computer, will not. XP definitely won't, Ubuntu too may cause issues.

What version of Ubuntu do you have? As the newer Ubuntus support a more hardware than the older versions your citrix reciever may work on newer version of Ubuntu.
So I suggest go for 64bit Ubuntu, if possible.

You are right about 'disabling UEFI' if you want to use 32bit ubuntu. 32bits does NOT support EFI booting. However, with 32bits you won't be able to utilize the full power for your processor. By the way, what processor do you have?

Windows7 has XP compatibility layer and you can run 'older' software on Win7 (I don't know how Win8 treats older software). XP will be phased out [end support] in March/April 2014. I guess its time to move on.

I am not sure, but the newer CPS's support [PAE]("https://help.ubuntu.com/community/PAE"), so I don't think you have to enable it, it will be done by the Kernel.

---

### Post by Dennis McClary on 2013-11-19
Thanks for the info. I am going to disable UEFI and use legacy bios. I just discovered there is a new version (13.0) of Citrix receiver for 64 bit. I installed Ubuntu 12.04 LTS in Virtualbox on my wife's Mac and then Citrix receiver. It worked great. I will install 64 bit Ubuntu on the computer I am building. As to Window XP being outdated, I am not overly concerned. The programs I want to run do not utilize the internet and XP will not be used for surfing. Also, no sensitive information will be on the XP hard drive. Processor is Intel I3-3240.

Dennis

---

### Post by oldfred on 2013-11-19
If Windows is not and will not be on Ubuntu hard drive I might suggest using gpt. With gpt you could later convert to UEFI if desired without having to totally reformat hard drive.

But XP cannot read gpt partitioned drives at all, so if you wanted a NTFS shared data partition on new drive you would have to stay with MBR(msdos). Newer Windows will read gpt drives, but only boot from gpt partitioned drives with UEFI.
Ubuntu will boot from gpt drives with UEFI or BIOS if an extra partition is on drive. With UEFI you need an efi partition at/near start of drive and if booting with BIOS you need a small 1 or 2MB  unformatted partition with the bios_grub flag.

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by fantab on 2013-11-19
Like oldfred points out in the post above, if you keep XP on the machine, you will be forced NOT to utilize the full potential of your hardware. Since XP does NOT really work with newer firmware and configurations.
For instance, XP will not work if the SATA is set to AHCI in BIOS and XP cannot work with GPT, which means you will be forced to use 30yr. old 'msdos'... In other words, with XP on board, you will have to work with 'lowered' hardware configuration.

If you want Windows then get yourself a 'modern' version, like Windows7 or 8. If I were, you I would go with 7.

My two cents....

---

### Post by Dennis McClary on 2013-11-19
I appreciate the advice about Windows as it the operating system I know the least about. If I planned to install Windows 7 on one hard rive and Ubuntu 12.04 LTS on the other would you recommend disabling uefi or not?

Dennis

---

### Post by oldfred on 2013-11-19
It is your choice. 
BIOS and MBR is well known, but has been the way PCs have booted since the first hard drive for a PC. BIOS has had to have a lot of fixes to try to work with newer hardware.
UEFI is new, both vendors, Windows & Linux all are making lots of improvements so it works well but still some issues (not that BIOS is prefect either).

A standard Windows 7 DVD has to be copied to flash drive and converted to work with UEFI.
       Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Ubuntu 64 bit installer for new versions is both BIOS & UEFI. And how you boot it is how it installs.
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by fantab on 2013-11-19
No, I wouldn't advice it.
The following webpage will explain how to install Windows 7 in UEFI mode.
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

By the way, only 64bit Windows will install in UEFI mode, same with Ubuntu.

---

### Post by Dennis McClary on 2013-11-26
After reading all the above advice, I think I will install Ubuntu 12.04 LTS 64 bit in UEFI mode and then give running XP in Virtualbox a try. I found posts on a RC forums that some have gotten Phoenix RC to work in this manner. If this fails, I will probably purchase Windows 7. I just want to be able to run what few Windows programs I have and not spend more on Windows operating systems and software. Over the last few years I have found that Ubuntu meets most of my needs Thanks.

Dennis

---

### Post by Dennis McClary on 2013-12-15
I finally got my computer built and my two operating systems installed. I installed Ubuntu 12.04.3 LTS on one hard drive utilizing UEFI and Windows XP on the other hard drive utilizing legacy bios. For each installation I had only one hard drive connected at a time to eliminate any possibility of something being installed in the wrong place. For the Ubuntu UEFI installation I selected "EFI" for PCI ROM priority and disabled CSM support. For the Windows XP installation I selected "Legacy" for PCI ROM priority and enabled CSM support. Both installations went well. I then changed back to EFI for PCI ROM priority but left CSM support enabled. I can boot from either hard drive and both operating systems work well on the computer. 

I know that support for XP will soon stop. However; I only have a few programs I want to run and Windows XP will be used only for these programs. Any activity where security is a concern will be handled with Ubuntu or the wife's Mac. I use Citrix receiver in Ubuntu to connect to applications on my company's network and it works great on Ubuntu. Gaming is mostly Minecraft and this was easily installed and works well on Ubuntu.

I wrote this follow-up to say thanks for advice given and to perhaps let some other novice know that with this motherboard you can have both both an UEFI and legacy installation as long as they are on different hard drives. I initially thought that the bios setting would have to be adjusted each time to boot from the other hard drive. I didn't realize that once set up properly that one could simply hit F12 on start up to select which hard drive to boot from. 

Dennis

---

### Post by oldfred on 2013-12-15
Glad you got it working. :)

It seems a lot of the newer UEFI will auto switch from UEFI menu. Some have specific settings with one mode only and for those you might have to switch in UEFI/BIOS to turn on/off CSM or UEFI.

---

