---
title: "Booting anything from UEFI USB - packard Bell ENME69BMP InsydeH2O"
date: 2013-11-24
forum: Installation &amp; Upgrades
---

### Post by ukoepping on 2013-11-24
Hi,

I got a Packard Bell easy note ME69BMP (ENME69BMP). I am trying to get it to boot ***anything*** from USB at all. The goal would be to put some kind of Linux / Ubuntu on it but i got much less ambutious. It comes with Win8 , with secure boot eneabled. The BIOS is a InsydeH20 (InsydeH2O) Rev 5.0 showing upper right corner. 

I am aware of the BIOS / EFI / UEFI and the secure boot situation. 

Here is what I tried so far:
- trying to set the BIOS to legacy (CSM?). But the BIOS menu does not offer anything like this. The manufacturer support told me to press F6 to switch to legacy mode - which the Netbook does not have. :-) 
- all I can do is swtiching secure boot on and of (after setting the bios password). 
- when rebooting Win8 (holding the shift key) I can select an USB stick to boot from. However: when having added nothing to the NVRAM , the BIOS complains that it does not have an USB boot option (?). This changed when adding s.th. to the UEFI secure boot menu. 
- I can also add a trusted boot file to the NVRAM (a.g. bootx64.efi from an Ubuntu distribution). This results in the disk/file show up in the boot manager when pressing F12. However, the BIOS still does load Win8. 
- I tried different USB sticks. I tried FAT formatted and FAT32 formatted sticks. I tried Ubunto 64bit 12.04.2 13.04 and latest. I booted these sticks on a (non UEFI) PC, they work (in no UEFI and non secure mode though). I tried UNetbootin, LinuxLiveCreator and also putting the files from Win8 directly from an .iso to the stick. 
- I converted an USB stick from MBR to GPT. neither booted.
- I tried getting into the advanced options of the BIOS by: pressing A after / before pressing F2. By pressing Ctrl-F1 in the BIOS. No success. 
- I tried connecting a USB CDROM. It does also not boot from there (but here the CDs are most likely NOT UEFI compatible)

Here are my questions: 
1) what might I have done wrong preparing a UEFI bootable (secure) USB stick? In other words: what is a ***foolproof*** way to create a UEFI capable stick (to make sure this is not a source of faults)?
2) what could I do to get the BIOS to offer legacy / CSM mode / advanced options? (flashing a modyfied BIOS might work, but I didnot find a suitable one yet)
3) any other suggestions?

I really read a lot: newspaper, Internet... I just am out of ideas. 

Bye & thanks for any help!! Uli

---

### Post by ubfan1 on 2013-11-24
Booting from USB should be pretty straightforward, but with all the machine differences who knows what problems you will encounter.  On the USB (remote media in UEFI terms), have a 300M FAT32 partition with the boot flag set.  In this partition, have a directory EFI.  In this directory, have directories Boot and ubuntu.  In the /EFI/Boot directory, have a copy of shim.efi named bootx64.efi, and the signed copy of grubx64.efi (from /usr/lib/grub/efi (something like that?).The signed copy there is named grubx64.efi.signed, so copy and rename it.  Now, in the /EFI/ubuntu directory, have your grub.cfg file.  The file may be a full grub.cfg file or one that just pulls in the maintained one in /boot/grub (like 13.04 and later releases do).
That's it.  No nvram changes needed, since the usb boot should already be present.  No hard disk EFI partition changes needed.  Maybe set a password on the bios supervisor, and you might get more boot choices.

---

### Post by ukoepping on 2013-11-24
OK! I got all the files already in that places and am pretty sure they are allright, since I got them from the distribution. , I will just look through the grub.cfg to see if anything is all right there. **Thanks**! Uli

---

### Post by ubfan1 on 2013-11-24
The location for the signed grub is /usr/lib/grub/x86_64-efi-signed/grubx64.efi.signed.  You can tell it is the right one by the size.  The setup I described was for Secure Boot enabled.  I guess without Secure Boot enabled, you could copy the unsigned grubx64.efi to the EFI/Boot/bootx64.efi instead of shim.efi.  With the right uuids in the grub.cfg, you can even boot Ubuntu on the internal hard disk instead of the USB.  Good Luck.

---

### Post by fabien-3 on 2013-12-02
Hi all,

I'm planning to buy this laptop. Since my last laptop was "Win7" age, i've never had to deal with this secure boot stuff. I'll google it, but i'm wondering if there're easy tool to create a bootable USB key.
@ukoepping, have you tried to open it? I've got this spare 64go SSD and would like to install it. Is it easy to open ?
And what about the battery? How long does it last ?

Thanks!

---

### Post by fabien-3 on 2013-12-02
Ok there's a long tutorial here in French : [http://doc.ubuntu-fr.org/uefi](http://doc.ubuntu-fr.org/uefi)

The Packard Bell is the European clone of the **Gateway LT41P04u. **For the hdd and memory here's a bit of info in a Amazon.com comment : 

[I][COLOR=#000000][FONT=verdana]I just got it today. I like it so far. The price is right. It has Windows 8. The Haswell chip has good battery life (and good Linux support). It's small and light.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I was a little surprised to see no wired Ethernet... but I guess that's like the Mac "Air" or a cell phone, so I can get a USB Enet adapter for a few bucks if I need to. Progress.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I like look under the hood, so found out how to get the "door" off (I didn't find service manuals on the Gateway site, unlike Dell or Lenovo) : undo the clips at the top of the keyboard and then remove the 5 "door" screws. There is one socket for memory, so it's upgradeable. There is only one wifi antenna. The disk is easy to remove at this point.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I'm trying to load Linux so I can dual boot it, but I'm struggling with the "secure boot".

**Here : **[/FONT][/COLOR][/I]**[http://www.amazon.com/gp/cdp/member-reviews/A2BSTBUIS9AAH/ref=cm_pdp_rev_title_1?ie=UTF8&sort_by=MostRecentReview#RR4AKCAUKCEEE](http://www.amazon.com/gp/cdp/member-reviews/A2BSTBUIS9AAH/ref=cm_pdp_rev_title_1?ie=UTF8&sort_by=MostRecentReview#RR4AKCAUKCEEE)**

---

### Post by oldfred on 2013-12-02
I think the link to the UEFI instructions on the French site are essentially the same as this first link.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Both are by Yannubuntu who is the creator of Boot-Repair and is from France.

---

### Post by davidlukas.m on 2013-12-07
Hi!
I've just bust this netbook yesterday and run into the same problems

... until I figured it out and it was not fun.

The underlying problem is that, although it's a 64 bit cpu, the EFI (and windows) are both 32 bit. So, even if you do the "usual" procedure:
- enable secureboot
- select a trusted file to boot 
- press f12 on boot to choose the bootloader
It will always return to the windows bootloader, because a 32bit EFI will not load the 64bit grubx64.efi on your installation medium (found in /efi/boot/grubx64.efi )

After some research I found out that 32bit EFI grub/linux is not easy to get by. Ubuntu doesn't provide anything like that (with good reason)... but some years ago there were 32bit efi macbooks, so it's not impossible.
I basically used my 64 bit pc to compile a 32bit, efi-supporting grub1.99 (use this as a guide: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) ), though you will have to manually change some Makefiles (disable -Werror ; and there is another error involving gets - just googling it will get you a one line sed-patch) - probably any newer version of grub will also work, but I've tried to stick to the instructions.

Then, you will have to put your newly compiled 32bit-efi-grub (grub.efi and its modules) somewhere onto your usb-installation medium. Then choose this file in the EFI (with secureboot enabled, otherwise you won't be able to select anything) and reboot, pressing F12 and selecting the grub bootloader. 

Once I was in, I had to manually enter (i guess you could do that in some grub.cfg, but I don't know which path you would have to put that file in, so stick to manual control) the kernel & initrd path and load the (64bit) kernel.

One thing: You will have to use the netboot kernel (get it from here: [http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/netboot.tar.gz) )

So, your "EFI USB Stick" just has to contain:
- 32 bit grub.efi + grub modules ( [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) )
- netboot 64-bit linux-kernel (filename "linux") (in here: [http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/netboot.tar.gz) )
- netboot 64-bit initrd (in here: [http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/netboot.tar.gz) )

This is (probably) because ehci_hcd does not work, so once you boot your kernel, it won't recognise the usb-stick (or any other usb devices)
I am currently compiling a new kernel so I can blacklist ehci_hcd (because in the default ubuntu kernel, it's built-in), if that won't work I will give the 32 bit kernel a try.

I also experienced some problems with booting probably because of gfxmodes not set correctly. Just use some of the commands of the default ubuntu.iso's grub.cfg, if you don't know your grub commands (I don't and I will probably never like the new grub).

Once you're in ubuntu, just install it but make sure you copy your own grub.efi into the EFI partition; then you have to choose the grub.efi file (now on your hd) in this less-than-useful efi and make it your default bootloader.
You can always use your 32bit-efi-grub to load any kernels on your disks on any partition.

Now, the only thing I have to figure out is how to get USB to work. 
It always gives me this error: device not accepting adress error -110

lsusb only shows the main usb hub. since I've already tried changig most of usbcore-kernel options and some other (noapic, nolapic nomsi, noefi, ...) I'm waiting for the netbook to finish compiling a new kernel with ehcd_hci as a module.

Please try to make it work, too, so you can help me with this damn usb thing...

---

### Post by davidlukas.m on 2013-12-07
PS once you have your 32bit grub, it doesn't matter at all wether you enable secureboot or not.

---

### Post by davidlukas.m on 2013-12-07
you have to use the netboot kernel image, unless you get USB to work. Just in case I wasn't clear enough.
Oh, and I did resize the NTFS partition from within windows.

---

### Post by davidlukas.m on 2013-12-07
just rebooted with a 32-bit netboot image, usb problems still persist. So don't bother trying that. back to compiling a removable ehcd_hci...

---

### Post by oldfred on 2013-12-07
Is this what you have?
 New Intel Atom - Nov 2013 x86 secure boot can be turned off, but only 32 bit UEFI which no one else has.
 Intel Atom SoC systems that ship with Windows 8/8.1 32-bit provide 32-bit UEFI-only firmware with no BIOS compatibility option (no CSM). In UEFI terms these systems are called Class 3 systems (this term is not specific to 32-bit), ie. UEFI-only with no BIOS CSM.
Windows with Atom 
[http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux](http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux)

      
 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

---

### Post by davidlukas.m on 2013-12-07
I am not really up to date concerning the cpu naming schemes intel uses nowadays... 
As far as I can tell, it's not an Atom, at least it says it's a Celeron N2805 / Silvermont cpu, dual core, 64 bit (released about a month ago, I think). And it's running Ubuntu amd64 perfectly fine except for the USB controller. 
But I don't really know if it's just an Atom relabeled for marketing purposes, I guess not.

But yes, it's got a 32bit UEFI only firmware with no CSM and SecureBoot enabled by default but that doesn't really matter. 
Dual boot with Windows 8 32bit, Ubuntu 13.10 32/64 kernels both work in conjunction with Grub 1.99 32Bit+EFI support, works just fine.
Intel ValleyView VGA/SATA/PCIe/SMBus and Qualcomm Atheros QCA9565 all work fine and out-of-the-box. But the USB (ValleyView rev0a) with ehci-pci doesn't work with neither 32 nor 64 bit kernels.
EFI is v2.03 by INSYDE corp, although the kernel tells me its v2.31 (plus the message: No EFI runtime due to 32/64-bit mismatch with kernel)

I read somewheres (about another problem) though, that I could try to disable USB2.0 (ehcd_hci) and only use USB1.1 (which would be better than no usb at all)..

---

### Post by davidlukas.m on 2013-12-07
BTW, I can sign that: [http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html) ([COLOR=#000000]Don't ship 32-bit UEFI firmware on x86)[/COLOR]

---

### Post by oldfred on 2013-12-07
I do not comprehend that they would offer a 32bit UEFI on a 64 bit chip??? I do not even see how that saves any money unless the nvram can be a bit smaller. It sounds more like a Microsoft thing on only letting you boot Windows.

---

### Post by fabien-3 on 2013-12-08
It seems there's a new bios but it doesn't fix the issue.

2013/11/28
1. Fix Modify show boot fail dialog behavior issue.
2. Fix S4 RTC wake up issue.
3. Fix Retry 5 times for PXE Boot fail issue.

---

### Post by fabien-3 on 2013-12-08
@[**[COLOR=#000000]davidlukas.m[/COLOR]**]("http://ubuntuforums.org/member.php?u=1888164")
So, did you finally manage to install ubuntu?
I'm planning to buy this computer and get rid totally of windows i won't use. I'm able to tinker the boot and everything but does it worth it?

thanks

---

### Post by fabien-3 on 2013-12-08
For the same price, almost same CPU, 2go of ram more and a bit more heavy there's this one : Toshiba SATELLITE NB10-A-103  (Amazon description here : [http://www.amazon.fr/Toshiba-Sat-NB10-A-103-Ordinateur-CN2810/dp/B00G327PMU#productDetails](http://www.amazon.fr/Toshiba-Sat-NB10-A-103-Ordinateur-CN2810/dp/B00G327PMU#productDetails))
But, in the technical document you can find on the Toshiba website it claims the battery last 3,5h... So basically 2,5h...

---

### Post by davidlukas.m on 2013-12-08
> **fabien-3 said:**
> @[**[COLOR=#000000]davidlukas.m[/COLOR]**]("http://ubuntuforums.org/member.php?u=1888164")
So, did you finally manage to install ubuntu?
I'm planning to buy this computer and get rid totally of windows i won't use. I'm able to tinker the boot and everything but does it worth it?

thanks
Yes, but USB does not work and I cannot recommed it at all. 

If you really want to buy this computer and want to install ubuntu on it, make sure that you at least
- know how to compile grub, how to edit Makefiles and how to google for compile errors (& how to fix them)
- know how to manually load a kernel from inside the grub shell
- know how to install a ubuntu-netboot image (no graphical installer)

---

### Post by fabien-3 on 2013-12-08
Thanks for your awnser! I'm not sure i'll buy it... I need the usb...

---

### Post by simon58 on 2014-10-04
Sorry for picking up this thread again. I also consider buying this Piece of Hardware. Is there a Workaround to get USB to work ? Perhaps Ubuntu 14  could solve some Problems. Has anyone tried?

---

### Post by oldos2er on 2014-10-04
Please start a new thread for your question.

---

