---
title: "can't boot Ubuntu OS (always boots only to Windows OS)"
date: 2017-07-18
forum: Installation &amp; Upgrades
---

### Post by pyrko on 2017-07-18
Hello. Computer: Acer E5-575G
1. Installed windows 10 64x from UsbFlash  
2. then installed ubuntu 16.04.02 from USB drive
3. but after reloading comp always loads only to Windows.
4. So i tried to make Boot-repair buy using USBFlash using Boot-repair Disc like here: [https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/)
after making Boot Repair achieved a message:
 You can now reboot your computer.
 Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file!   (BUT i cant see this kind of file in Priority boot loader)
 If your computer reboots directly into Windows, try to change the boot order in your BIOS.  (Question: to change to What?)
 If your Bios does not allow to change the boot order, change the default boot entry of the Windows bootloader. (Question, what is that, don`t undestand?)
 For example you can boot into Windows, then type the following command in an admin command prompt:
 bcdedit/set{bootmgr}path\EFI\ubuntu\shimx64.efi

5. But still cant choose the OS beetween UBUNTU AND Windows before loading the OS. Always boots only to Windows

Please, help me. I don't know what to do( 
**paste.ubuntu.com/25119016/**

---

### Post by johndough2 on 2017-07-18
Hi

The shim thing I have used with opensuse, and it is a form of security signing I believe, that makes the Linux install a trusted OS.

I remember it as a CLI thing sudo supper install shim, so zypper is apt-get not supper as this stupid predictive text says.

---

### Post by ubfan1 on 2017-07-18
Acer computers need to set "trust" on the Ubuntu bootloaders (shimx64.efi and grubx64.efi) before you can boot them.  In the UEFI settings (also known as BIOS), set a supervisor password, then additional options, like setting trust, should be displayed.  Then when trust is set, you should see the shimx64.efi in the choice of bootloaders, put that one first.   Shimx64.efi just boots grubx64.efi, and can be used with secure boot either enabled or disabled.  Without secure boot enabled, you could boot grubx64.efi directly.  When grub's boot menu displays at boot, try to boot Ubutu.  Next try to boot Windows from grub -- some machines with secure boot enabled cannot do this.  If your machine cannot boot windows from grub, either turn off secure boot, or use the efi menu (some function key at power up) to boot Windows directly.

---

### Post by pyrko on 2017-07-18
ubfan1, thank A LOOOOT for some explanation!!!
now, when i added "trusted" efi file shrimx64 to bootload, i should always press, when starting computer, a key F12 to get bootmenu, and to choose beetween windows boot manager and grub loader.If i choose grub, i will have a possibility to choose beetween Linux and windows.

But one more question, how can i put this Grub to load itself after turning On a computer, without pushing F12 key and choosing special loader?

---

### Post by oldfred on 2017-07-18
You should in UEFI be able to change boot order.

Or you can use efibootmgr.

sudo efibootmgr -v
 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr 

But grub only boots working Windows. That is Windows that is not hibernated (fast start up) nor needs chkdsk. 
Best to have Windows repair recovery flash drive. 
Windows will on updates reset itself to first in boot order and turn back on fast start up which then prevents grub from booting Windows. 
      
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 

[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

### Post by pyrko on 2017-07-18
a huge THANKS to all, just after making things that ubfan1 adviced, i`ve got a one more new device in boot priority device, which was Grub loader, so i put it on first in priority, and now i don`t need to press F12 to load boot menu for choosing special loader.
Thank you all!! now it`s time to look and find how to find, install and set all drivers and updates on Ubuntu OS))

---

### Post by pyrko on 2017-07-18
You can make it Solved)

---

### Post by oldos2er on 2017-07-18
*You* can mark it Solved under Thread Tools at the top of the page.  :)

---

