---
title: "Can't Enter Into BIOS"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by gopusridhar on 2012-12-25
Hi 

I have installed Ubuntu 12.10 On a brand new fujitsu Lifebook A552/SL. I have wiped away the whole harddisk and i only have Ubuntu on it now. 

Now when i power-up the notebook and press F12 i can't get the Boot menu to boot from CD/DVD or USB or Network boot.. The boot menu is replaced with 1.Ubuntu. 

I know Ubuntu can't change anything in BIOS, But strange i can't enter into BIOS even using F2 on start, Tried with multiple keyboards during 3 days without sucess, Did i screwed up my Laptop now ?! 

Any help would be appreciated 

thanks in advance 

Best Regards,
Sridhar.

---

### Post by Frogs Hair on 2012-12-25
When building my desktop I installed the mother board software(bios utility)onto the hard-drive prior to the operating system,so the Asus screen appears prior to the boot loader and allows entrance into the bios.

This of course would have been by the manufacturer in your case. Did you have a page with the manufactures name and does it still appear prior to the boot loader ?

---

### Post by oldfred on 2012-12-25
Is this a new UEFI system. 

Some say if you do not turn off fast boot then you use Windows to get back into the UEFI menu.

This Windows pages has info on booting into UEFI menu for most systems. Edit - it looks like it does not include your Fujitsu, so you may have to try all the alternatives unless your manual or vendors web site has more info.

       UEFI/BIOS Boot keys - about halfway down on this page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

    
There are also UEFI shell. Some UEFI include the shell, but Intel has one. Not sure how it really works.
Some discussion of shell from grub2:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by gopusridhar on 2012-12-26
Thanks Frags for your reply, 
The Phoenix Screen does appear before Grub2, The screen says F2 for BIOS settings and F12 for Boot menu. If i press F2 nothing happens, But when i press F12 it takes me to Another boot menu where i can choose only Ubuntu and nothing else.. I still didnt get how can Linux replace boot menu

---

### Post by gopusridhar on 2012-12-26
Thank you for your reply Oldfred, 

Yeah it is New EFI system ( Just noticed it), The Hotkeys are F2 and F12 and are displayed on Phoneix first screen. This is weired situation, I have helped many people before boot related problems, But now i m totally lost and don't know what to do. 

If i can boot from CD/DVD or USB then i can install windows and Flash bios, Is there anyway to add CD/DVD boot to Grub2?! 

thanks again

---

### Post by Frogs Hair on 2012-12-26
I am unfamiliar with the new boot loader, but there are some related threads on the forum. I would check there first.

---

### Post by grahammechanical on 2012-12-26
Might I suggest that we stop and think about what is actually happening?

The machine has a boot menu that comes up when F12 is pressed and the only option is to boot Ubuntu. That is correct because Ubuntu is the only OS on the machine.

You expect this menu to also show options to boot from CD/DVD and other areas. And it does not. This situation does not mean that you have screwed up the laptop. 

Is the laptop still working? Do you need to press F12 and then select Ubuntu or can you not power up the laptop and will it load Ubuntu straight away?

Have you tried putting a Ubuntu live DVD into the drive and then powering up the machine? Does the machine boot from the live DVD? Or from USB?

Is there a user guide or manual that explains about UEFI/BIOS settings? May be it will also explain about editing this boot menu to direct the UEFI/BIOS to look towards the DVD drive or the USB drive?

Check all options before risking flashing the BIOS. That also is a new area for these types of machines. If all else fails there may be a method of re-setting the machine to factory defaults.

Please read what is happening when we install 12.10 on a mchine with UEFI and Secure Boot.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

> Netboot support is currently nonexistent. The major blocker seems to be that unlike in BIOS booting we can't rely on the firmware's PXE stack, and in practice GRUB2's tftp support doesn't seem to be very robust yet. Once we have a working GRUB2 image that successfully reads files over tftp, we can evaluate signing it for Secure Boot as well.

So, that is why the Ubuntu first-stage UEFI boot loader does not have an option for Network booting.

Regards.

---

### Post by gopusridhar on 2012-12-26
Hi Grahammechanical, 

Thanks for taking your time and asking some valuable questions 

Before installing Ubuntu when i press F12 i used to get a menu with different boot options such as Boot from HDD,CD/DVD,USB and Network boot etc.. The laptop originally came with Windows 7 but i booted with a windows 8 DVD and installed Windows 8 on first power up, So basically it never had Windows 7 completely configured on it. After installing windows 8, I used Windows Installer to Install Ubuntu 12.10 but i couldn't start Linux, So I made a bootable USB of 12.10 64Bit and booted from it ( Chose the first option i.e.wipe away all partitions ). 

Now the machine works perfectly and boots directly into 12.10, I added some time delay in Grub2 to stop booting directly. The problem is now, i can't boot from live CD/DVD Or USB or any other device except HDD

all i can do is just use Ubuntu 12.10 on HDD..Now Ubuntu is installed on HDD.. I expect the F12 key to show a device to boot from (Just like before) not an OS on HDD.. I don't understand how could Ubuntu change bios settings?! Now i know that it didn't wipe away the BIOS but the Menu which i see on pressing F12 is some intermediate Menu created by Ubuntu..How can i see the original boot menu.. The Manual which came with the laptop  is useless, It just has 2 pages of description in 20 different languages 

Did you get the problem?! Just want to know if there is any secret key which can bring back the original Bios boot menu?!!

---

### Post by gopusridhar on 2012-12-26
Just an addition, I removed HDD and Inserted Bootable USB, the system doesn't Boot from USB.  Removed HDD,USB and inserted bootable DVD, the system doesn't boot either..It ends up in Intermediate Boot menu..

All i want is to run Windows 8 and Ubuntu 12.10 side by side, When i installed Ubuntu 12.10, it couldn't recognize that there is Windows 8 on HDD, thats why i chose to to wipe away everything, Now i can't install Windows 8 because i don't have option to Boot from Windows DVD..Is there any other option to install Windows 8 without booting from USB or DVD ..for example like from Ubuntu 12.10 ?! 

Thank you very much Graham !

---

### Post by gopusridhar on 2012-12-26
This is how looks my paste from boot-repair 

[http://paste.ubuntu.com/1468293/](http://paste.ubuntu.com/1468293/)

whats the code to add "Boot from USB" to Grub2 ?! I m going to use Grub customizer to make an Entry. Thanks a lot for your help

---

### Post by gopusridhar on 2012-12-27
Finally after 10 hours of work i found out to boot from CD/DVD. 
 
I have used grub command line something like below 
 
grub> set root='(cd0)'
grub> chainloader /EFI/microsoft/boot/bootmgr.efi 
grub> boot 
 
thats it, the system booted from cd/dvd 
 
I've learnt something new and Ubuntu Rocks !! 
 
I still need some research on dual booting windows 8 and Ubuntu 12.10 because i can't install them side by side in straight manner. 
 
But thank you very much Graham,Oldfred and Frogs for your support and ideas 
 
Best Regards,
Sridhar.

---

### Post by sugame on 2013-01-12
I have the same issue.

I need add "Boot from DVD" to grub2, because to enter the BIOS menu is troublesome.

Thanks in advance for your help.

---

