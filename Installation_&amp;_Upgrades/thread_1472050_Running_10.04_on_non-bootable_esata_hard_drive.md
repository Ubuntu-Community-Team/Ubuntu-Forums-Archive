---
title: "Running 10.04 on non-bootable esata hard drive?"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by slawek_zachcial on 2010-05-04
Hello,
 
I have a laptop (hp 8530w) with Vista and disk encryption software installed on the internal hard drive. As I cannot touch the internal hard drive, I would like to install and run Ubuntu from an external hard drive (500 hitachi in an enclosure with USB and eSata port). The idea being that when the drive is connected I run Ubuntu and when it is not the internal HDD is used to boot.
 
I already installed Ubuntu 10.04 LTS on this external hard drive. I would like to run it using eSata interface and not USB as the former offers better performance.
 
Unfortunately, as it turns out my BIOS does not allow me to boot directly from eSata disk. I can however boot from USB.
 
I thought it would be possible to install a boot loader on a USB stick and tell it somehow that Ubuntu is installed on the eSata disk and load the system from there. 
I installed GRUB on a USB stick without grub.cfg. This allowed me to load GRUB and get to its shell. Here I discovered another issue. Using GRUB "ls" command the eSata drive is not listed - I can see the USB stick (hd0) and the internal drive (hd1) but no eSata drive.
 
Not being an expert I don't know when in the boot process the eSata disk is detected. If I load Ubuntu completely from USB stick I can see it listed with "fdisk -l" command.
 
At this point, knowing that I can boot from USB, I'm wondering if there is any way to have a hybrid solution with USB stick storing only what's required to bootstrap Ubuntu, and then have everything else stored on and mounted to my external drive. 
 
 
**Does anyone know how to do that?**
 
**Is there any other, better way (assuming I cannot do anything on the internal hard drive like repartitioning it, etc ...) to get to what I'm after?**
 
 
I know that I could boot and run Ubuntu using USB interface only but as I stated above I would like to use eSata as it offers better performance.
 
I suppose I'm not the only one trying to do that. Unfortunately my web research did not reveal any solutions. Any help would be greatly appreciated.
 
Thanks,
/Slawek

---

### Post by slawek_zachcial on 2010-05-09
It seems the solution may be to use "kexec-loader" ([http://www.solemnwarning.net/kexec-loader/](http://www.solemnwarning.net/kexec-loader/)) which, based on its description, was designed for exactly what I'm trying to do.

Does anyone have any experience with "kexec-loader"?

I'm not giving up yet...

/Slawek

---

### Post by slawek_zachcial on 2010-05-16
[COLOR=#000000][FONT=Arial]With great help from  Daniel Collins, the creator of "kexec-loader", I'm now able to boot from  USB key into Ubuntu installed on external hard drive connected with  eSata.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Below are the steps I  followed to get there. It may not be the simplest way but it worked for  me.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]IMPORTANT: If you  decide to follow the steps below always make sure that you work on the  right disk (i.e. external) to not wipe out the data from your internal  drive. Also doing a backup of your internal disk is a good idea in case  things don’t go as expected.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]0. Prerequisites[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]- Ubuntu on Live USB  stick with some presistent storage[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- Small USB key which will be used for  booting[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]-  External hard drive connected though eSata[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]1. Ubuntu installation  on external disk[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]This  is done using Live USB. Go through the installation steps until you  reach the screen about partitioning. Here I had to used the “advanced”  option (the radio button at the very bottom) as none of the others  seemed to be able to work with the external disk. Once you get to the  next screen it should show partitions on the internal disk but also on  the external disk. Let’s say my external disk is “/dev/sdb”.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Here I selected my  external disk and created 2 primary partitions: swap - with 2x the size  of RAM in my laptop, ext4 - using the remaining space and mounted to  “/”.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Go to through the  following screen(s) until you reach the summary with “Advanced” button.  Hit this button and uncheck the box about updating the boot record  - I  didn’t want to do it as my BIOS does not support eSata booting anyway  (otherwise I would specify it should boot from my external disk, i.e.  /dev/sdb instead of /dev/sda).[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Review the changes to make sure that any disk  changes will only be done on the external drive. And then GO - Ubuntu  should be installed in your external drive.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]2. “kexec-loader” ISO  preparation[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]While running Ubuntu  from the Live USB key go to  [http://www.solemnwarning.net/kexec-loader/download.cgi](http://www.solemnwarning.net/kexec-loader/download.cgi) and download from  there kexec-loader-2.2.1-cdrom.tar.gz and modules-2.6.30.5-1.tar.gz.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Unpack both of them.  From the modules copy “sata.tlz” and “ext4.tlz” into  “kexec-loader-2.2.1-cdrom/iso-modules” directory. Note that if you used  another file system than “ext4” to install Ubuntu you should take the  appropriate module for your installation.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]In  kexec-loader-2.2.1-cdrom run “mkiso.sh kexecloader.iso”. This will  create ISO image that we will use for boot.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]3. Bootable USB  preparation[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Plug the 2nd USB key  that we will use for boot. With GParted format it to FAT32 and label the  partition as KEXECLOADER. The label is important as “kexec-loader”  during boot will look for a partition with that name to read its  configuration file from there.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Get access to the files in the created ISO  image using the following commands:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ mkdir /mnt/kexecloadercd[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ mount -o loop  path/to/iso /mnt/kexecloadercd[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Download UNetBootin tool used to create  bootable USB. If you run plain Ubuntu, it will complain about missing  “p7zip-full”. I don’t know if this is really needed but I installed it  following one of the “to do list after installing Ubuntu 10.04” posts.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Run UNetBootin. Select  “Custom”. In “Kernel” open the one in  /mnt/kexecloadercd/isolinux/vmlinuz. In “Initrd” open the one in  /mnt/kexecloadercd/isolinux/initrd.img. In the USB dropdown make sure  you select the one that we just formated above and that will be used for  boot. In my case it was visible as “/dev/sdd” device. Hit OK.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]If used as-is the  UNetBootin USB stick will show a menu at start up. If you want to avoid  that backup “syslinux.cfg” present there and replace it with one  containing just this line:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]default /ubnkern initrd=/ubninit[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]4. “kexec-loader.conf”  configuration file[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The  final step is to tell kexec-loader about the external disk Ubuntu is  installed on.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]In  the root directory of the USB boot disk create file called  “kexec-loader.conf” with the following content:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]timeout 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]title Lucid Lynx on  eSata[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]root  sdb3[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel  /vmlinuz[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]cmdline  root=/dev/sdb3[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]initrd /initrd.img[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]... and replace “sdb3” with the device name  for the partition of your external disk where Ubuntu is installed.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Alternatively, you can  use UUID instead of “sdbN”. To get UUID execute in terminal “ls -l  /dev/disk/by-uuid” and then in “kexec-loader.conf” file use:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]root UUID=<your  uuid>[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]cmdline  root=UUID=<your uuid>[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]...[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial](“=” is present twice in cmdline)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Note that  “kexec-loader” has a shell that you can use for troubleshooting. Its  commands are documented at  [http://www.solemnwarning.net/kexec-loader/readme.html](http://www.solemnwarning.net/kexec-loader/readme.html) in “Shell” and  “Shell Reference” sections.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]5. BIOS boot order[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]If you want to  automatically boot from your USB key when it’s plugged in you’ll need to  change the boot order in BIOS and put the USB hard drive above internal  hard drive.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Doing  all the above I’m now able to boot into Ubuntu installed on my external  drive when my USB stick is plugged in, and into my internal drive when  the boot stick is not connected. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Hope others will find this useful.  Enjoy![/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]/Slawek[/FONT][/COLOR]

---

### Post by frostschutz on 2010-05-16
there's no need for a kexec-loader really, all you have to do is install grub on the usb stick, and put your /boot partition and kernels on the usb stick as well.

when you boot from usb, grub can then load the kernel normally (from hd0 == usb), detect your devices, mount the root partition (from /dev/sdx == esata), and start the system init process...

---

### Post by slawek_zachcial on 2010-05-17
What you describe is somewhat close to what I wanted to do (see my initial post). Unfortunately I haven't found any documentation or posts about such a setup and I decided to try kexec-loader which worked pretty well for me.

Where can I find more information about the setup you highlight?

Thanks,
/S

---

