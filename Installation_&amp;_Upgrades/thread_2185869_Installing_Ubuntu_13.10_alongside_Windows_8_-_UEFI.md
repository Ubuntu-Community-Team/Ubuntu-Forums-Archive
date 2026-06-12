---
title: "Installing Ubuntu 13.10 alongside Windows 8 - UEFI issues"
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by Thomas Oliveira on 2013-11-04
Hi,

I am trying to install Ubuntu 13.10 on a HP Envy 17-j20us that has come with Windows 8 pre-install.

I have followed the instructions on [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

However, after rebooting, the computer **loads Windows 8 directly and cannot make the dual-boot work**.

Some information that may be relevant:
- Windows FastStartup is disabled
- my BIOS does not have any option related to QuickBoot/FastBoot or and Intel Smart Response Technology (SRT)
- I had to add this option to GRUB when booting and installing from the LiveCD so X would load: acpi=off
- I have run YannUbuntu's **Boot-Repair** with **SecureBoot on**. The result is here: [paste.ubuntu.com/6354744]("http://paste.ubuntu.com/6354744/")
- I have also run YannUbuntu's **Boot-Repair** with **SecureBoot off**. The result is here: [paste.ubuntu.com/6354809]("http://paste.ubuntu.com/6354809")

Thank you very much for you help!

---

### Post by fantab on 2013-11-04
The last two links for Bootinfo-Summary are NOT working. Its important that we have look at the boot-summary.

---

### Post by ubfan1 on 2013-11-05
@fantab, cut and paste the url, looks like an extra "ubuntuforums.org/" got prefixed.
@Thomas, can you boot ubuntu through the efi - boot menu?  The one you get listing the devices and oses when you type a function key early in the boot process.  If you can, you should see grub, select ubuntu and see if it runs.  Then try again to see if you can run Windows through the grub menu.  If you can, you can make the ubuntu choice the boot default using efibootmgr.  Unfortunately, not every machine can boot windows through grub, so in that case, leave things like they are, and just use the efi boot menu to choose (or change the default to ubuntu, and use the efi boot menu to choose Windows.)

---

### Post by Thomas Oliveira on 2013-11-05
I have just edited the links to take the extra "ubuntuforums.org/" out.

@ubfan1, during the boot process, I can press ESC and then F9 to reach a menu. From this menu, I can boot Windows and grub. From grub, I can load Windows and Ubuntu.
I will try using efibootmgr.

[EDIT] @ubfan1: to have an idea of which would be the effect of using efibootmgr, I have tried to set the timeout from 0 to 20 seconds, as shown below.
However, the Timeout variable does not change. Does this behaviour mean anything?

thomas@dv7:~$ sudo efibootmgr
BootCurrent: 003D
Timeout: 0 seconds
BootOrder: 0002,3002,0001,2002,2001,2003
Boot0000* Internal CD/DVD ROM Drive (UEFI)
Boot0001* Ubuntu
Boot0002* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk

thomas@dv7:~$ sudo efibootmgr -t 20
BootCurrent: 003D
Timeout: 0 seconds
BootOrder: 0002,3002,0001,2002,2001,2003
Boot0000* Internal CD/DVD ROM Drive (UEFI)
Boot0001* Ubuntu
Boot0002* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk

thomas@dv7:~$ sudo efibootmgr
BootCurrent: 003D
Timeout: 0 seconds
BootOrder: 0002,3002,0001,2002,2001,2003
Boot0000* Internal CD/DVD ROM Drive (UEFI)
Boot0001* Ubuntu
Boot0002* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk

---

### Post by oldfred on 2013-11-05
In your UEFI can you change boot order from 0002 or Windows to 0001 or ubuntu?

BootOrder: [COLOR=#ff0000]0002[/COLOR],3002,0001,2002,2001,2003
Boot0001* Ubuntu
Boot[COLOR=#ff0000]0002[/COLOR]* Windows Boot Manager

You should also be able to change from a UEFI command line with efibootmgr.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
-o | --bootorder XXXX,YYYY,ZZZZ,...     explicitly set BootOrder (hex)

---

### Post by Thomas Oliveira on 2013-11-05
@oldfred, I can't change boot order:

```
thomas@dv7:~$ sudo efibootmgr  
 [sudo] password for thomas:  
 BootCurrent: 0001  
 Timeout: 0 seconds  
 BootOrder: 0002,3002,0001,2001,2002,2003  
 Boot0001* Ubuntu  
 Boot0002* Windows Boot Manager  
 Boot2001* USB Drive (UEFI)  
 Boot2002* Internal CD/DVD ROM Drive (UEFI)  
 Boot3000* Internal Hard Disk or Solid State Disk  
 Boot3002* Internal Hard Disk or Solid State Disk  
 Boot3003* Internal Hard Disk or Solid State Disk  
 
 thomas@dv7:~$ sudo efibootmgr -o 0001,3002,0002,2001,2002,2003  
 boot entry 2003 does not exist  

 thomas@dv7:~$ sudo efibootmgr -o 0001,3002,0002,2001,2002  
 BootCurrent: 0001  
 Timeout: 0 seconds  
 BootOrder: 0002,3002,0001,2001,2002,2003  
 Boot0001* Ubuntu  
 Boot0002* Windows Boot Manager  
 Boot2001* USB Drive (UEFI)  
 Boot2002* Internal CD/DVD ROM Drive (UEFI)  
 Boot3000* Internal Hard Disk or Solid State Disk  
 Boot3002* Internal Hard Disk or Solid State Disk  
 Boot3003* Internal Hard Disk or Solid State Disk  
 
 thomas@dv7:~$ sudo efibootmgr  
 BootCurrent: 0001  
 Timeout: 0 seconds  
 BootOrder: 0002,3002,0001,2001,2002,2003  
 Boot0001* Ubuntu  
 Boot0002* Windows Boot Manager  
 Boot2001* USB Drive (UEFI)  
 Boot2002* Internal CD/DVD ROM Drive (UEFI)  
 Boot3000* Internal Hard Disk or Solid State Disk  
 Boot3002* Internal Hard Disk or Solid State Disk  
 Boot3003* Internal Hard Disk or Solid State Disk
```

Anyway, it seems I have managed to solve the problem, and I will soon describe here what I had done.
Thank you all very much for your help!

---

### Post by Thomas Oliveira on 2013-11-23
@oldfred, please consider adding the link I mention below to the rich collection you have compiled on [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)


It seems that some HP notebook having UEFI will only boot from the file /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

 In order to circumvent this limitation HP is imposing for their users, you can manually replace this file with /boot/efi/EFI/ubuntu/grubx64.efi.

 I had successfully followed the instructions from Rod Smith found on [http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
more specifically the topic &#8220;Do the job manually&#8221;.
 
 Using shimx64.efi did not work for me.

 One of the steps is &#8220;modify your GRUB configuration to enable it to launch the Windows boot loader in its new location&#8221;.
 Those that had never done that should know that is not advisable to edit the grub config file (e.g. /boot/grub/grub.cfg) directly.
 
 As you can read on the warning in the beginning of this file:
 &#8220;It is automatically generated by grub-mkconfig using templates from /etc/grub.d and settings from /etc/default/grub&#8221;. It can also be generated by running update-grub.
 
 So, it is better to edit the files inside /etc/grub.d and run update-grub after that.

---

### Post by oldfred on 2013-11-23
Thanks for update.

I did add some more info and the link. 
My only concern of late is the process and explanation has gotten so long most may not read it or just give up.
In many cases if Windows is backed up, and specific Windows settings like fast boot and secure boot are turned off, Ubuntu now will just install to standard UEFI systems. Ultrabooks still are more complicated. And everyone may have issues with video drivers.

---

### Post by andrei.cimpoca on 2013-12-27
Just wanted to share this piece of information with anyone who has had troubles with efibootmgr because of faulty/crapy implementations from the good guys at Lenovo who probably coded the firmware using child labor in a mental asylum.
Hint: The UEFI thing looks for the default EFI/BOOT/BootX64.efi binary, regardless of what is in it's eprom so skip efibootmgr altogether; You pointlesly risk bricking your laptop.
[FONT=courier new]mount /dev/sda1 /mnt
cd /mnt/efi
cp -rfv ubuntu boot
cd boot
mv grubx64.efi bootx64.efi
[/FONT]
Edit boot order so it boots from the hard drive first.

Reboot and enjoy!

If you're using kubuntu and the installer failed, apt will nag you because it cannot finish configuring grub properly. The solution is:
[FONT=courier new]sudo mv /usr/bin/efibootmgr /usr/bin/efibootmgr.lol #you must use .lol or else you run the risk of copyright infringement
sudo touch /usr/bin/efibootmgr
sudo chmod +x /usr/bin/efibootmgr
sudo apt-get install grub-efi #will pass and stop nagging
[/FONT]
PS: If you use like me for instance a Lenovo Ideapad 205, suspend/shutdown will not work in EFI mode because of the poor quality of the rice the programmers were payed with. Additionally, the laptop won't wake up from suspend because of a bios bug. In this case, all you need to do is install a windows for a little while, upgrade your bios to the latest version (if it's below 21), then install ubuntu in bios mode.
The idea is that you can make a bootable usb using the nifty Startup Disk Creator, then mount it and rename the EFI folder to OLDEFI. It will then boot in bios mode and it will create a MBR partition table instead of GPT and it will install grub-bios or whatever it's alias is. Everything will work flawlessly, at least in 13.10

PS PS: Don't even bother with ati/amd/radeon drivers. Keep the default dri/glx thing. Frglx is pure crap and it's crash patterns are a better source of entropy then /dev/random. RSA should use ati drivers to regain it's customer's trust.

---

