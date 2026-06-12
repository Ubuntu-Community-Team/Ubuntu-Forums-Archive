---
title: "[How to] Multiboot USB from Linux ISOs/Windows Installer"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by rafabr4 on 2013-02-25
Hello! I just suscribed to this forum to post this, since I couldn't find this information over the forum (I hope it is in the right section).

[SIZE="4"]**What will I be able to do?**[/SIZE]

Basically what we want to achieve is to be able to boot almost any Linux ISO (with the traditional loopback method) as well as being able to boot a Windows 7/8 installation from a USB.

Summarizing the process, we will make 2 FAT32 partitions in a USB, get the Windows Installation in the first partition (through syslinux with Universal USB installer). Then install grub2 to the second partition and modify the grub.cfg file to boot Linux ISOs and chainload to the Windows installation

[SIZE="4"]**Requirements**[/SIZE]

[LIST]
[*]Pendrive of at least 8GB (Not sure if you can make this with an external hard drive, the process should be similar though)
[*]Working windows installation
[*]Working linux installation
[*]Linux ISOs
[*]Windows 7/8 ISO
[*][[COLOR="Blue"]Universal USB Installer[/COLOR]]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.9.2.5.exe")
[/LIST]

[SIZE="2"]**DISCLAIMER**[/SIZE]
I'm not responsible for any damage that you could cause to your devices or information loss.

[SIZE="4"]**Process**[/SIZE]

[LIST=1]
[*]Backup any information on your USB because we will format it. Boot into your linux installation (I will be using Ubuntu 12.10) and open gparted (if you don't have it, install it). At the top right corner, switch to your usb device, in my case it is /dev/sdb but it will vary in each computer. MAKE SURE IT IS THE CORRECT DEVICE, you can do this by going into the disk utility.
Proceed to unmount it. Now delete the USB partition and make a new one with this arguments: FAT32 filesystem, primary partition, at least 5GB (this will be Windows partition, it should be the first one). If you want to keep using this USB as a normal one, you should consider in adding more space since this will be the partition that windows will recognize. Then make another partition with the same specs, but with the rest of the space.

[*]Boot into your windows installation. Download Universal USB Installer from the link I gave (or a newer version if any), open it and from the dropdown list scroll to the bottom and you should see "Windows 7 Installer" (or Windows 8 Installer). Select it and then search for the corresponding ISO. Select the correct drive letter (it should only be listing the first partition that we made) and choose NOT to format it. Click create and wait for it to finish, it will take some time.

[*]Get back to your linux installation, make sure your second partition of the USB is mounted and check the directory (in my case it is /media/USER/usb2). We will now install grub2 in the device. Open a terminal and run this command as root:
```
grub-install --force --no-floppy --root-directory=/media/[COLOR="red"]2nd_partition_directory[/COLOR] /dev/sd[COLOR="Red"]X[/COLOR]
```
NOTE: replace "2nd_partition_directory" and the "X" for your own specific.

In my case it ended up like this:
```
grub-install --force --no-floppy --root-directory=/media/USER/usb2 /dev/sdb
```

[*]Now that grub2 is installed we should place the grub.cfg file in the usb. Navigate to the second partition and inside "/boot/grub" place the grub.cfg file which you can download by typing this command in the terminal:
```
wget pendrivelinux.com/downloads/multibootlinux/grub.cfg
```
Now a very important step is to modify the grub.cfg file in order to load the isos from the correct location. In my case, I created a folder in the root of my usb (2nd partition) called "iso" and I placed in it both the Ubuntu 12.10 i386 and amd64 isos. Then I edited the configuration file to look like this:

[HTML]# This grub.cfg file was created by Lance http://www.pendrivelinux.com
# Suggested Entries and the suggestor, if available, will also be noted.

set timeout=10
set default=0

menuentry "Ubuntu 12.10 i386" {
 loopback loop /iso/ubuntu-12-10-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-12-10-i386.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.10 amd64" {
 loopback loop /iso/ubuntu-12-10-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-12-10-amd64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Windows 8 Installer" {
 set root=(hd0,1)
 chainloader +1
}[/HTML]
You should replace "[COLOR="Red"]/iso/ubuntu-12-10-i386.iso[/COLOR]" and "[COLOR="red"]/iso/ubuntu-12-10-amd64.iso[/COLOR]" with the correct path and name of your ISOs. You have to replace **BOTH**, the one that goes after "[COLOR="red"]loopback loop[/COLOR]" and the one that goes after "[COLOR="red"]iso-scan/filename=[/COLOR]". You should use as much entries as number of ISOs that you have.

Also a very important step is to add the Windows 7/8 installer entry by chainloading it. Again the "[COLOR="red"](hd0,1)[/COLOR]" will vary depending of each computer. When it comes to drives, the first one will be "0". And when it comes to partitions, the first one will be "1". So theorically, by booting with your USB it should always be hd0, and since we put windows in the first partition, you should use (hd0,1). It should work like that, if not... well, try to play with the numbers until you get it.

[*]Finally, open gparted again and make sure that the second partition has got the "boot" flag. If not, set it.
[/LIST]

[SIZE="4"]**DONE!**[/SIZE]

Congratulations! You have just finished setting up your USB to boot Linux ISOs or Windows Installer. I hope the guide is clear enough and feel free to make any questions/critics. Again, I'm not sure this is in the right section.

---

### Post by Steve6375 on 2013-03-14
[COLOR=rgba(0, 0, 0, 0.8)][FONT=Helvetica Neue]You may like to look at the Easy2Boot project from RMPrepUSB. The V1 BETA version allows you to simply copy all or any of your ISOs onto the USB Flash drive. This includes standard unmodified  Windows WinXP/Vista/7/8/SVR2K8R2/SVR2012 install ISOs and **all linux LiveCD ISOs**. As many as you have room for!

Nearly all linux ISOs work even if there are no cheat codes available for direct ISO booting for them!

[http://www.rmprepusb.com](http://www.rmprepusb.com) - see Easy2Boot Tutorial and see **V1 BETA** download for details.[/FONT]

---

