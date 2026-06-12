---
title: "I broke grub when replacing mint with ubuntu"
date: 2015-11-21
forum: Installation &amp; Upgrades
---

### Post by janw-oostendorp on 2015-11-21
**The backstory**

For a few years I've played with Ubuntu. With Windows 10 I think it's time to take a more serious look.
So I've had dual boot Win8 + Ubuntu. After hearing a few things I decided to install Linux Mint.

So I installed Mint. Something that went horrible wrong. I broke Grub, Windows, Ubuntu and had no Mint.
I wiped the whole disk and reinstalled Windows 8 and then Installed Mint. Luckily I had a backup and a list of installed programs.
All was well except for a huge amount of time I spend on this.

But I didn't think Mint was better. Mainly the way Cinnamon plays with hotkey's switching monitors on my laptop and a few other things.
So I wanted to go back.

** What went wrong.**
So I had Mint dual boot with Win8. I wanted to install Unbuntu over Mint. After a search I found that in the installer I should just select the main (ext4) Mint partition, format it and mount it at `/`.
I did that but when done the grub booted in command line. Using the `exit` command did boot Into Windows. Luckily.
After that I tried a few other things. I tried Deleting the Ubuntu and swap partitions and a "clean" install rather then overriding an existing install.
I tried to reinstall Grub with the live USB. Nothing worked.
At this time I have deleted the Ubuntu and swap partitions. But in the Bios I see 2 boot options which both boot in identical (broken) grubs. But I can't see any partitions in the windows partition manager.
On a live USB I do see an extra partition.

How Can I fix this so I can install Ubuntu and a normal Grub?
Any idea what I did wrong?
Can I delete the two extra boot options? how?

Screenshots: [http://imgur.com/a/hjxIn](http://imgur.com/a/hjxIn)

---

### Post by oldfred on 2015-11-21
UEFI has its own NVRAM and retains entries. You have to delete those if not valid anymore. You can use efibootmgr for that.

Best to see details of what is still on drive. Boot live installer flash/DVD and add Boot-Repair and run its report.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2015-11-21
If we are not aware of this information then things can go wrong when trying to dual boot Windows 8/10 and Linux

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by janw-oostendorp on 2015-11-24
I ran the repair and it gave me this info:
[http://paste.ubuntu.com/13495123/](http://paste.ubuntu.com/13495123/)

The 2 entries still exist

---

### Post by yancek on 2015-11-24
All of the partitions you have on your hard drive are windows filesystems.  The only sign of Ubuntu or Mint are the two files in the EFI partitions which won't do anything since you do not have either Mint or Ubuntu installed.  That's why you can't boot them.  Another problem you have is that you have code from the Grub bootloader in the MBR.  You also have an efi partition and mixing UEFI and MBR BIOS is going to create problems so you need to decide which you want.  You should be able to choose which when you boot the Ubuntu/Mint install medium.   I don't use UEFI so you'll have to wait for someone else to give you more details.

---

### Post by oldfred on 2015-11-24
You need to always boot in UEFI mode.
Booting live installer in UEFI mode you will have efibootmgr.
Details on deleting extra UEFI entries are in the UEFI menu clean-up in the link in my signature below.

Best to review install procedures for UEFI. Since Windows is UEFI, you only want Linux in UEFI boot mode.

---

### Post by janw-oostendorp on 2015-11-29
I've read the [UEFI installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295") But I can't figure it out.
I have screenshot of my [Bios Tabs]("http://imgur.com/a/6DbAR").
Can you help me how to boot in EUFI?

---

### Post by yancek on 2015-11-29
It would probably be more useful if you posted an image of the Boot tab in the BIOS.  I would expect that would be where you would find the options.

---

### Post by oldfred on 2015-11-29
In your boot tab, you can select the Windows entry and move it to first in UEFI. 

You show this in your Boot-Repair Summary Report in the ESP or sda2. Delete the entire /EFI/ubuntu folder. You should be able to do this from live installer. In Windows you have to mount the partition as Windows hides it.

     Boot files:  /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 

You booted Boot-Repair in BIOS/CSM mode, so it did not directly show UEFI's entries.
ReBoot in UEFI boot mode and run this from a terminal:
sudo efibootmgr -v

Then you can run the efibootmgr commands to delete UEFI entries.
      
 Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

### Post by janw-oostendorp on 2015-12-01
I really feel I'm missing the last piece :(
I still don't understand the difference between normal boot and UEFI.

1a) When I put Windows at the top I can't boot from USB, is that correct?
1b) Is putting Windows on top the same as booting UEFI?

2) Should CSM be enabled? If I disable it the "USB DISK 2.0 PMAP" option disapears. The "UEFI: USB DISK 2.0 PMAP" stays. But It won't work when I try to boot from it. ([List]("http://i.imgur.com/MEGr10v.jpg"))
I made my usb with [http://www.linuxliveusb.com](http://www.linuxliveusb.com).

I'm having a hard time to understand it. Thanks for sticking with me so far.

---

### Post by oldfred on 2015-12-01
You should always be able to use the one time boot key, often f10 or f12 to choose what to boot. Check your manual on correct key.
What brand/model system?

When you have CSM/Legacy/BIOS on that allows BIOS boot. Only the UEFI: entry then is UEFI boot.

Are these new or left over & you deleted the Ubuntu install? You are showing the two standard ubuntu UEFI boot entries. One is shim for use with secure boot and the other is grub for use if secure boot is off. I only use grub.

I do not know about Lili, but many with Windows have posted Rufus works.
  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)

Please review install steps in link in my signature. There is a lot to absorb, but best to at least review it.

---

### Post by janw-oostendorp on 2015-12-02
My laptop is a Asus N56JN-CN035H ([Dutch specs]("http://tweakers.net/pricewatch/382522/asus-n56jn-cn035h/specificaties/")). The key to the one time boot is *'esc'* (at least I learned that).


With the knowledge I've gained here I've red your [footer post]("http://ubuntuforums.org/showthread.php?t=2147295") again.
My Original setup should be *'Windows 8 or 10 pre-installed & secure boot'*

So I should disable the CMS. And keep Windows at the top of boot. That should be UEFI boot, right?

The two Ubuntu entries in the boot menu are the result of an old (deleted) Ubuntu. The goal is to delete those two, right?

I tried Recreating the USB with Rufus. (it's faster and cleaner UI) But It still gave 1 unresponsive entry with CSM disabled. and 2 options with CSM enabled.


The problem is probably one of these two.
1) I'm not correctly booting in EUFI, which is why I can't start USB-ubuntu.
2) My USB-ubuntu is somehow wrong and therefore it won't start when booting in UEFI.

If I'm able too start the USB-Ubuntu in UEFI I should be able to do boot-repair and delete the defective Ubuntu boot options, right?

---

### Post by oldfred on 2015-12-02
Boot live installer in UEFI mode and use efibootmanger to delete old ubuntu entries in UEFI boot menu.

Every brand of system has different UEFI screens and how they work. UEFI is a standard, but everyone has implemented it differently.

Within brands and therefore brand of UEFI software, they usually are similar with just difference for the different options included in that specific model.

Some possibly similar UEFI, may have included details useful for you.
       Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus X205TA hardware support in Ubuntu
[http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)
Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)
Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
[URL="https://wiki.archlinux.org/index.php/ASUS_N550JV"]https://wiki.archlinux.org/index.php/ASUS_N550JV
[/URL]
 Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

[URL="https://wiki.archlinux.org/index.php/ASUS_N550JV"]
[/URL]

---

### Post by janw-oostendorp on 2015-12-08
I got it last weekend.

What I found out is quite simple..
I remade the USB with a newer Ubuntu version and 64bit.
I had *'ubuntu-15.04-desktop-i386.iso'* the newer was *'ubuntu-15.10-desktop-amd64.iso'*
Now the stick booted in UEFI without problems.
There I cleaned up the UEFI boot entries as suggested earlier and installed Ubuntu with normal settings.

Thanks for the help.

---

