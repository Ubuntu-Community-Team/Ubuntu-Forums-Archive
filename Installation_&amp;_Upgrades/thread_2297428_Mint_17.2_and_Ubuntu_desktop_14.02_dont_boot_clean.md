---
title: "Mint 17.2 and Ubuntu desktop 14.02 dont boot cleanly"
date: 2015-10-03
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2015-10-03
[LIST=1]
[*]Hello, I am using UEFI boot with WIndows Mint 17.2 Ubuntu  14.04 desktop and Kali Linux version 2.0. I upgraded Mint Kernel to the  latest version. To boot Mint I have to go to recovery option in Grub and  continue. Without recovery option it will not boot. When I try to  backup with clonezilla, this partition isnt recognized hence I can not  back it up.  Can I know what may be the problem ?
[*][COLOR=#BF0000][FONT=Lucida Grande][/FONT][/COLOR][FONT=Lucida Grande]The boot.log file for Mint has the following entry [/FONT][COLOR=#BF0000][FONT=Lucida Grande].* Starting Read required files in advance [fail][/FONT][/COLOR]
[*]For Ubuntu 14.04 I tried to move /home to another partition. I messed it up and had to create another user . This system does not shut down completely and hangs. How to tackle this issue?
[/LIST]
 
Thank you in advance

---

### Post by oldfred on 2015-10-03
Do you have Mint, Ubuntu and Kali all installed?

Or are you using just Mint and Kali. Mint is not an official version of Ubuntu, but based on Ubuntu.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

With multiple Linux installs often better not to have separate /home but separate /mnt/data partition where you move all the data but none of the configurations from /home. Then data can be shared without conflicts.

Did you miss a step in this process?

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by deepakdeshp on 2015-10-05
> [COLOR=#000000]Post the link to the Create BootInfo summary report. Is part of Boot-Repair:[/COLOR]
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


Here is the boot infocan be booted. . I have installed Mint 17.2 in partition 13 but it can be booted in recovery mode only. Normal boot fails. All the Grub entries are proper and there is no problem
[http://paste2.org/ehHG89vy](http://paste2.org/ehHG89vy)
[COLOR=#BF0000][FONT=Lucida Grande][/FONT][/COLOR][FONT=Lucida Grande]The bootlog file for Mint has this entry when I boot with recovery mode[/FONT][COLOR=#BF0000][FONT=Lucida Grande]. * Starting Read required files in advance [fail][/FONT][/COLOR]

> [COLOR=#000000]Do you have Mint, Ubuntu and Kali all installed?[/COLOR]
[COLOR=#000000]Yes all are installed on a single disk. 

[/COLOR]> [COLOR=#000000]With multiple Linux installs often better not to have separate /home but separate /mnt/data partition where you move all the data but none of the configurations from /home. Then data can be shared without conflicts.[/COLOR]
[COLOR=#000000]

Very true and a great suggestion[/COLOR]

---

### Post by oldfred on 2015-10-05
It looks like you left Windows fast start up on, which is always on hibernation.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

HP is not UEFI friendly to anything but Windows. It modifies UEFI to also use description and only valid description is "Windows". That is not UEFI standard.

Most copy /EFI/Ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi and boot a hard drive entry with UEFI. You may have to add the hard drive entry which is often called a fallback entry in UEFI.
I think some with HP have been able to change boot order with efibootmgr. but others have reported that newer Windows likes to reset boot order.
And some have used the suggested entry in BCD that Boot-Repair suggests.

Also more details in link in my signature below.
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
      [/URL]
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886
      [/URL]Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by deepakdeshp on 2015-10-06
Thank you so much for your response.

> It looks like you left Windows fast start up on, which is always on hibernation.
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials...ndows-8-a.html]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")
[http://www.kapilarya.com/how-to-enab...p-in-windows-8]("http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8")

HP is not UEFI friendly to anything but Windows. It modifies UEFI to also use description and only valid description is "Windows". That is not UEFI standard.


I get the option to boot Ubuntu,Mint,Kali or WIndows when I press F9 while system boots. I can boot any of the systems with this option. Since I can boot all the systems, I feel I wont experiment much with EFI
> Most copy /EFI/Ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi and boot a hard drive entry with UEFI. . 

May be I did not install Mint in EFI mode but there is no /EFI directory.
The problem is that I can boot Mint only with recovery option from the Grub menu. Somehow I am not able to find out the meaning of . * Starting Read required files in advance [fail] which happen during the normal boot of Mint. Though it looks a minor problem, I am not able to back the Mint partition using Clonezilla backup software. When I try Clonenzilla , the Mint partition is not recognized. I searched a lot for the status Starting Read required files in advance [fail] but have not been successful. 

> Most copy /EFI/Ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi and boot a hard drive entry with UEFI. . 
May be I did not install Mint in EFI mode but there is no /EFI directory in Mint.

---

### Post by oldfred on 2015-10-06
It looks more like Mint never installed a boot loader. You do not show any grub installed to a MBR or PBR which would be from a BIOS boot, nor a bios_grub partition. Perhaps installing in BIOS mode without bios_grub partition crashed the grub install?

And you do not have an UEFI entry, nor a efi folder with Mint. Not sure if Mint uses Mint as folder name or not, though.

Ubuntu's grub may just be finding the Mint kernels and booting those. If install is otherwise ok, then it would boot. 
Not sure what your error message is then, either, but perhaps related to missing boot loader.

---

### Post by deepakdeshp on 2015-10-20
This is my boot information about my device. [http://paste2.org/VpsO12nN](http://paste2.org/VpsO12nN).  I had edited /boot/grub/grub.cfg file for proper mounting of partition for at /.  [http://ubuntuforums.org/showthread.php?t=2299301](http://ubuntuforums.org/showthread.php?t=2299301) .Since with  recovery option of grub for my Mint partitions is working properly, should I keep the same value for normal boot option as that of recovery option by changing the grub.cfg value? Or is there any other option?

---

### Post by oldfred on 2015-10-20
I missed you had two threads on same issues. I would have merged them.

But I would boot into Mint, add an efi partition mount in fstab (you can copy the one from Ubuntu) and then install the efi version of grub. Then you should have an UEFI entry for Mint. But you will only be able to have one of you Mint installs boot from UEFI. I have several Ubuntu installs and latest install overwrites my ubuntu folder in /EFI/ubuntu.  I now have good backup of efi partition and just restore the correct grub.cfg to have configfile for my main working install.
sudo apt-get install grub-efi-amd64     

I also use 40_custom and turn off os-prober. It cleans up grub menu a lot, and you then can have what ever description you want in menu. Details in your other thread.

---

### Post by deepakdeshp on 2015-10-20
> **oldfred said:**
> I missed you had two threads on same issues. I would have merged them.
.
 The issues were really different. 
[LIST=1]
[*]Partitions not mounting correctly as ../
[*]Partitions not booting correctly.
[/LIST]
Following is again a new issue 
I was getting Cinnamon crashed msg on my sda10 partition. sda13 is my grub controlling partition. To solve this problem I tried following steps.
[LIST=1]
[*]Boot from sda13. chroot to sda10.
[*]Remove old versions of Kernel from sda10. I had 2 versions 3.16* and 4.2*
[*]Reinstall 4.2 kernel on partition sda10 . run update-grub from sda13.
[/LIST]
But this gave error and sda10a is not able to boot. I get initramfs> prompt and system hangs.  The code below lists the commands I tried. Sorry for the long list in the code.  How can I fix this issue now?

```
sudo su[sudo] password for uma: 
Sorry, try again.
[sudo] password for uma: 
uma-HP-Notebook uma # sudo su
uma-HP-Notebook uma # mount /dev/sda10 /mnt
uma-HP-Notebook uma # mount -t proc proc /mnt/proc
uma-HP-Notebook uma # mount -t sysfs sys /mnt/sys
uma-HP-Notebook uma # mount -o bind /dev /mnt/dev
uma-HP-Notebook uma # df -k /
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda13      40185208 31823408   6356700  84% /
uma-HP-Notebook uma # cp -L /etc/resolv.conf /mnt/etc/resolv.conf
uma-HP-Notebook uma # chroot /mnt /bin/bash
root@uma-HP-Notebook:/# 
root@uma-HP-Notebook:/# df -k .
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda10      62943156 52832316   7160276  89% /
root@uma-HP-Notebook:/# sudo rm -rf /lib/modules/kernel_version
root@uma-HP-Notebook:/# sudo rm -f /boot/vmlinuz-kernel_version*
root@uma-HP-Notebook:/# sudo rm -f /boot/initrd.img-kernel_version*
root@uma-HP-Notebook:/# sudo rm -f /boot/config-kernel_version*
root@uma-HP-Notebook:/# sudo rm -f /boot/System.map-kernel_version*
root@uma-HP-Notebook:/# cd /boot
root@uma-HP-Notebook:/boot# ks
ks: command not found
root@uma-HP-Notebook:/boot# ls
abi-3.16.0-38-generic         memtest86+.bin
abi-4.2.0-040200-generic     memtest86+.elf
config-3.16.0-38-generic     memtest86+_multiboot.bin
config-4.2.0-040200-generic     System.map-3.16.0-38-generic
efi                 System.map-4.2.0-040200-generic
grub                 vmlinuz-3.16.0-38-generic
initrd.img-3.16.0-38-generic     vmlinuz-4.2.0-040200-generic
initrd.img-4.2.0-040200-generic  vmlinuz-4.2.0-040200-generic.old
root@uma-HP-Notebook:/boot# pwd
/boot
root@uma-HP-Notebook:/boot# df -k .
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda10      62943156 52832316   7160276  89% /
root@uma-HP-Notebook:/boot# sudo rm -rf /lib/modules/kernel 3.16*
root@uma-HP-Notebook:/boot# sudo rm -rf /lib/modules/kernel 3.16*
root@uma-HP-Notebook:/boot# sudo rm -f /boot/vmlinuz-kernel_3.16*
root@uma-HP-Notebook:/boot# sudo rm -f /boot/initrd.img-kernel 3.16*
root@uma-HP-Notebook:/boot# sudo rm -f /boot/config-kernel_3.16*
root@uma-HP-Notebook:/boot# sudo rm -f /boot/System.map-kernel 3.16*
root@uma-HP-Notebook:/boot# ls
abi-3.16.0-38-generic         memtest86+.bin
abi-4.2.0-040200-generic     memtest86+.elf
config-3.16.0-38-generic     memtest86+_multiboot.bin
config-4.2.0-040200-generic     System.map-3.16.0-38-generic
efi                 System.map-4.2.0-040200-generic
grub                 vmlinuz-3.16.0-38-generic
initrd.img-3.16.0-38-generic     vmlinuz-4.2.0-040200-generic
initrd.img-4.2.0-040200-generic  vmlinuz-4.2.0-040200-generic.old
root@uma-HP-Notebook:/boot# df -k .
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda10      62943156 52832316   7160276  89% /
root@uma-HP-Notebook:/boot# sudo rm -rf /lib/modules/kernel 4.2*
root@uma-HP-Notebook:/boot# sudo rm -f /boot/vmlinuz-kernel_4.2*
root@uma-HP-Notebook:/boot# sudo rm -f /boot/initrd.img-kernel 4.2*
root@uma-HP-Notebook:/boot# sudo rm -f /boot/config-kernel_4.2*
root@uma-HP-Notebook:/boot# sudo rm -f /boot/System.map-kernel 4.2*
root@uma-HP-Notebook:/boot# cd /tmp
root@uma-HP-Notebook:/tmp# ls kernel*
ls: cannot access kernel*: No such file or directory
root@uma-HP-Notebook:/tmp# ls
linux-headers-4.2.0-040200_4.2.0-040200.201508301530_all.deb
linux-headers-4.2.0-040200-generic_4.2.0-040200.201508301530_amd64.deb
linux-image-4.2.0-040200-generic_4.2.0-040200.201508301530_amd64.deb
mintUpdate
pulse-PKdhtXMmr18n
screenlets
screenlets-daemon.py.log
ssh-ssAPs7unhits
VMwareDnD
vmware-root
WaterMarkScreenlet.py.log
root@uma-HP-Notebook:/tmp# xs /boot
xs: command not found
root@uma-HP-Notebook:/tmp# cd /boot
root@uma-HP-Notebook:/boot# ls
abi-3.16.0-38-generic         memtest86+.bin
abi-4.2.0-040200-generic     memtest86+.elf
config-3.16.0-38-generic     memtest86+_multiboot.bin
config-4.2.0-040200-generic     System.map-3.16.0-38-generic
efi                 System.map-4.2.0-040200-generic
grub                 vmlinuz-3.16.0-38-generic
initrd.img-3.16.0-38-generic     vmlinuz-4.2.0-040200-generic
initrd.img-4.2.0-040200-generic  vmlinuz-4.2.0-040200-generic.old
root@uma-HP-Notebook:/boot# cd /tmp
bash: cd: /tm[: No such file or directory
root@uma-HP-Notebook:/boot# cd /tmp
root@uma-HP-Notebook:/tmp# ls *deb
linux-headers-4.2.0-040200_4.2.0-040200.201508301530_all.deb
linux-headers-4.2.0-040200-generic_4.2.0-040200.201508301530_amd64.deb
linux-image-4.2.0-040200-generic_4.2.0-040200.201508301530_amd64.deb
root@uma-HP-Notebook:/tmp# dpkg --force -i *deb
dpkg: error: unknown force/refuse option '-i'


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
root@uma-HP-Notebook:/tmp# dpkg -i *deb
(Reading database ... 257321 files and directories currently installed.)
Preparing to unpack linux-headers-4.2.0-040200_4.2.0-040200.201508301530_all.deb ...
Unpacking linux-headers-4.2.0-040200 (4.2.0-040200.201508301530) over (4.2.0-040200.201508301530) ...
Preparing to unpack linux-headers-4.2.0-040200-generic_4.2.0-040200.201508301530_amd64.deb ...
Unpacking linux-headers-4.2.0-040200-generic (4.2.0-040200.201508301530) over (4.2.0-040200.201508301530) ...
Preparing to unpack linux-image-4.2.0-040200-generic_4.2.0-040200.201508301530_amd64.deb ...
Done.
Unpacking linux-image-4.2.0-040200-generic (4.2.0-040200.201508301530) over (4.2.0-040200.201508301530) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
Setting up linux-headers-4.2.0-040200 (4.2.0-040200.201508301530) ...
Setting up linux-headers-4.2.0-040200-generic (4.2.0-040200.201508301530) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
Error! Bad return status for module build on kernel: 4.2.0-040200-generic (x86_64)
Consult /var/lib/dkms/vboxguest/5.0.0_RC3/build/make.log for more information.
Setting up linux-image-4.2.0-040200-generic (4.2.0-040200.201508301530) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.2.0-040200.201508301530 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.2.0-040200.201508301530 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
Error! Bad return status for module build on kernel: 4.2.0-040200-generic (x86_64)
Consult /var/lib/dkms/vboxguest/5.0.0_RC3/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-040200-generic
Warning: No support for locale: en_IN
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-040200-generic
Found initrd image: /boot/initrd.img-4.2.0-040200-generic
Found linux image: /boot/vmlinuz-4.2.0-040200-generic.old
Found initrd image: /boot/initrd.img-4.2.0-040200-generic
Found linux image: /boot/vmlinuz-3.16.0-38-generic
Found initrd image: /boot/initrd.img-3.16.0-38-generic
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sda11
Found Linux Mint 17.2 Rafaela (17.2) on /dev/sda12
Found Linux Mint 17.2 Rafaela (17.2) on /dev/sda13
Found Kali GNU/Linux 2.0 (2.0) on /dev/sda9
Adding boot menu entry for EFI firmware configuration
done
root@uma-HP-Notebook:/tmp# sudo apt-get purge virtualbox*
Reading package lists... Done
Building dependency tree        
Reading state information... Done


You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cinnamon-control-center : Depends: cinnamon-control-center-data (= 2.6.0-20151015013040-trusty) but 2.6.0-20151001013040-trusty is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@uma-HP-Notebook:/tmp# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  cinnamon-control-center cinnamon-control-center-data
  libcinnamon-control-center1
The following packages will be upgraded:
  cinnamon-control-center cinnamon-control-center-data
  libcinnamon-control-center1
3 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
99 not fully installed or removed.
Need to get 3,052 kB of archives.
After this operation, 544 kB disk space will be freed.
Do you want to continue? [Y/n] y
Err http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu/ trusty/main cinnamon-control-center amd64 2.8.0-20151018013046-trusty
  404  Not Found
Err http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu/ trusty/main cinnamon-control-center-data all 2.8.0-20151018013046-trusty
  404  Not Found
Err http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu/ trusty/main libcinnamon-control-center1 amd64 2.8.0-20151018013046-trusty
  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu/pool/main/c/cinnamon-control-center/cinnamon-control-center_2.8.0-20151018013046-trusty_amd64.deb  404  Not Found


E: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu/pool/main/c/cinnamon-control-center/cinnamon-control-center-data_2.8.0-20151018013046-trusty_all.deb  404  Not Found


E: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu/pool/main/c/cinnamon-control-center/libcinnamon-control-center1_2.8.0-20151018013046-trusty_amd64.deb  404  Not Found


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@uma-HP-Notebook:/tmp# 


Warning: No support for locale: en_IN
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-040200-generic /boot/vmlinuz-4.2.0-040200-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-040200-generic
Found initrd image: /boot/initrd.img-4.2.0-040200-generic
Found linux image: /boot/vmlinuz-4.2.0-040200-generic.old
Found initrd image: /boot/initrd.img-4.2.0-040200-generic
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sda11
Found Linux Mint 17.2 Rafaela (17.2) on /dev/sda12
Found Linux Mint 17.2 Rafaela (17.2) on /dev/sda13
Found Kali GNU/Linux 2.0 (2.0) on /dev/sda9
Adding boot menu entry for EFI firmware configuration
done
root@uma-HP-Notebook:/tmp# 
root@uma-HP-Notebook:/tmp# 





```

---

### Post by oldfred on 2015-10-20
Try running Boot-Repair.
It has in Advanced a full uninstall/reinstall of grub and you can check to update kernel. You need at least one working kernel before starting to experiment with very new kernels.

---

### Post by deepakdeshp on 2015-10-21
[[FONT=times new roman][SIZE=2]QUOTE=oldfred;13376361]Try running Boot-Repair.
It has in Advanced a full uninstall/reinstall of grub and you can check to update kernel. You need at least one working kernel before starting to experiment with very new kernels.[/QUOTE]

Thank you for the prompt reply. There is no problem with the kernel as such. I am using same kernel on the other Linux partitions without a problem. There doesnt seem to be any any problem with grub as all the OS are detected. The kernel was built on other partitions without any error but the Kernel build on sda10 threw an error.[COLOR=#000000]**The make.log error contents are listed in code.  So I feel that I need to solve this problem first**. It is not a grub problem but I need to fix this first. Please share your expert opinion. and I dont have any idea on how to proceed.[/COLOR]
[/SIZE][/FONT]
```
  /var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/dirops.o  CC [M]  /var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.o
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c: In function &#8216;sf_follow_link&#8217;:
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:43:5: error: implicit declaration of function &#8216;nd_set_link&#8217; [-Werror=implicit-function-declaration]
     nd_set_link(nd, error ? ERR_PTR(error) : path);^M
     ^
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c: In function &#8216;sf_put_link&#8217;:
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:49:5: error: implicit declaration of function &#8216;nd_get_link&#8217; [-Werror=implicit-function-declaration]
     char *page = nd_get_link(nd);^M
     ^
LD [M]  /var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxguest/vboxguest.o
  LD      /var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/built-in.o
  CC [M]  /var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/vfsmod.o
  CC [M]  /var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/dirops.o
  CC [M]  /var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.o
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c: In function &#8216;sf_follow_link&#8217;:
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:43:5: error: implicit declaration of function &#8216;nd_set_link&#8217; [-Werror=implicit-function-declaration]
     nd_set_link(nd, error ? ERR_PTR(error) : path);
     ^
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c: In function &#8216;sf_put_link&#8217;:
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:49:5: error: implicit declaration of function &#8216;nd_get_link&#8217; [-Werror=implicit-function-declaration]
     char *page = nd_get_link(nd);
     ^
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:49:18: warning: initialization makes pointer from integer without a cast [enabled by default]
     char *page = nd_get_link(nd);
                  ^
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c: At top level:
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:57:5: warning: initialization from incompatible pointer type [enabled by default]
     .follow_link    = sf_follow_link,
     ^
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:57:5: warning: (near initialization for &#8216;sf_lnk_iops.follow_link&#8217;) [enabled by default]
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:59:1: warning: initialization from incompatible pointer type [enabled by default]
 };
 ^
/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.c:59:1: warning: (near initialization for &#8216;sf_lnk_iops.put_link&#8217;) [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf/lnkops.o] Error 1
make[1]: *** [/var/lib/dkms/vboxguest/5.0.0_RC3/build/vboxsf] Error 2
make: *** [_module_/var/lib/dkms/vboxguest/5.0.0_RC3/build] Error 2
make: Leaving directory `/usr/src/linux-headers-4.2.0-040200-generic'


]
```

---

### Post by oldfred on 2015-10-21
Cannot help on compiling kernel.

But most do not attempt to compile themselves, but use ppa.
       Ubuntu Kernel Mainline PPA use
[URL="http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1"]http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1
[http://www.phoronix.com/scan.php?page=news_item&px=MTY1NTU](http://www.phoronix.com/scan.php?page=news_item&px=MTY1NTU)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
[/URL]

---

### Post by deepakdeshp on 2015-10-22
Is there a way of reinstalling Ubuntu or Mint on the partition sda10 where the kernel is broken? It mean an install in which the software installed does not get wiped out on sda10. Npndestructive install. I am interested in only backing up applications like vmware and the images

---

### Post by oldfred on 2015-10-22
Software or your settings?

Do not think there is a way to reinstall without overwriting software install. If you have not housecleaned and the .deb are still there you can do a "dirty" install where you do not reformat partition. Then reinstall apps. But all your settings will be changed to the defaults for any standard app & the system when installed as it still recreates all the new files it needs.

       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

If just all your settings then your normal backups of /home can just be restored into the new install & the list of installed apps you create as part of a backup process can be used to reinstall them.

       discussion of alternatives/strategy backups
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem
[/URL]
 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)[URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL]

---

### Post by deepakdeshp on 2015-10-22
ok I got it. :)  I am able to boot from my sda10 partition,


I was getting the error ***Errors encountered while checking hard disk at /*** I followed advice in following link and edited the entry for sda10 in GRUB menu by pressing e. But the edit is not permanent. When I reboot I need to follow the same process again. How do I solve the issue? The partition which has the GRUB entry is sda13 which appears as the first choice in GRUB.


[http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted](http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted)

Now I have 2 queries please.
1.How to make sda10 as my grub control partition. That is the GRUB enttries in sda1o are the entries I should see when I boot.
2.How to make the above process work across reboot? That is I need not go to GRUB entry , press e and change ro to rw for sda10 partition?

Thank you

---

### Post by oldfred on 2015-10-22
If you are to change an entry to rw, it seems it may have some issue. Best to run fsck on all your ext4 partitions.

If a partition that is not mounted, then you can run from another install. Just do not click in Nautilus or it will auto mount.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

You can quickly install grub to the MBR from any working install.
      
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

    
But each install may have remembered where to reinstall grub on major updates. Best to turn that off on all other installs.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates for BIOS
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by deepakdeshp on 2015-10-22
Thank you. I did grub-install /dev/sda from sda10 and that has become the grub controlling partition now.
I ran fsck on sda10 after booting sda13. It reported errors. Then I ran fsck -y /dev/dsa10 and the partition is clean now.

But I still can not boot from sda10 unless I make the ro to rw change while in GRUB menu.. :(

---

### Post by oldfred on 2015-10-22
Run the Boot-Repair Summary report and post the new link.
Just to see if anything shows up that does not look correct. 
So many installs makes it a bit more difficult to tell what is where. But I have several and turn off os-prober so only those I want to see are in grub menu.

---

### Post by deepakdeshp on 2015-10-22
The boot-repair is at [http://paste2.org/Zjh6dNwh](http://paste2.org/Zjh6dNwh)

---

### Post by oldfred on 2015-10-22
I do not think I see anything.
I checked my entries in grub and they all use ro, and only after you boot does it then use the fstab entries (I think).

Are you booting recovery mode?
> BOOT_IMAGE=/boot/vmlinuz-4.2.0-040200-generic root=UUID=afc80bf2-4b55-4455-acae-bd4711ea8c3b rw recovery nomodeset

It does look like you left Windows fast start up on. As it still shows hibernation. You probably only can only boot Windows directly from UEFI or one time boot key.

---

### Post by deepakdeshp on 2015-10-22
> **oldfred said:**
> I do not think I see anything.
I checked my entries in grub and they all use ro, and only after you boot does it then use the fstab entries (I think).

Are you booting recovery mode?

It does look like you left Windows fast start up on. As it still shows hibernation. You probably only can only boot Windows directly from UEFI or one time boot key.

Thank you. I was not able to turn off OS-PROBER. Added GRUB_DISABLE_OS_PROBER=true entry in /etc/grub/grub.cfg and also made the 30_os-prober_proxy non executable but that did not stop the OS-PROBE for boot-repair.

Yes I had seen that all entries use ro for my other partitions. 

BTW I am using GRUB customizer too

I am booting in recovery mode because if I boot in the normal mode, the system hangs. That was the subject of the original post but so far there is no solution. At least this work around is available to boot in recovery mode.

I hardly use Windows. Hence if I am not quick to change the boot order, Windows boots. I just switch the machine off rather than let Windows repair its partition and then a clean shutdown. I want to make ubuntu as the default boot. Need to read about it though.

Was trying to add background image to GRUB but it looks quite involved. Thats not so important.

---

### Post by oldfred on 2015-10-22
All the proxy files are from grub customizer. That sometimes causes other issues, and I have always manually configured grub. Some do like the gui Customizer, but it use of modified grub scripts can cause other issues as it then is not standard.

If you want to uninstall grub customizer, you also need to use Boot-Repair and do a full uninstall/reinstall of grub. If you did make any settings changes yourself, you have to recreate those. Good backups always recommended.

Recovery mode also has nomodeset. Have you manually added that to first grub entry. And then if nVidia or AMD you need to install proprietary video driver. But some with AMD seem to be having issues. I have nVidia, so have not followed AMD issues.

---

### Post by deepakdeshp on 2015-10-23
Thanks for the update . 

[COLOR=#333333][FONT=Lucida Grande]I was able to remove Virtual Box add ons, I was able to install Kernel 4.2. aftere following the commands below[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]VB addons removal procedure[/FONT][/COLOR]

CODE: [SELECT ALL]("http://forums.linuxmint.com/viewtopic.php?f=46&t=207841#")cd /opt/VBoxGuestAdditions-5.0.0_RC3
./uninstall.sh
There are 2 important issues pending now. 

Changing to rw from ro when in Kernel mode. This is not persistent across reboots. There must be a file which I should be able to change so that the change is persistent across reboots.

1.I have to use recovery mode booting. Is there any way I can try? If I know the direction , I will.
2.Unless I boot in recovery mode on my Mint partitions I can not boot. Is there any way to solve this?

Some lesser issues:-

The boot process I follow is:- Power on laptop, press F9 and go to change boot priority. Here Windows is listed first then Ubuntu folder. I want to move Ubuntu folder at the top.Windows appears as first entry in BIOS mode when I boot.

Use background image for GRUB.

> **oldfred said:**
> 

If you want to uninstall grub customizer, you also need to use Boot-Repair and do a full uninstall/reinstall of grub. If you did make any settings changes yourself, you have to recreate those. Good backups always recommended.

Recovery mode also has nomodeset. Have you manually added that to first grub entry. And then if nVidia or AMD you need to install proprietary video driver. But some with AMD seem to be having issues. I have nVidia, so have not followed AMD issues.

I will not uninstall grub cstomizer. Manually editing should be tried by and expert otherwise, your computer may not boot  I just want to do manual config where ever it is a must. Otherwise the convenience of grub  customizer is nice .As long as all the systems are booting, it is good.

I havent added nomodeset or anything else to first grub entry.

---

### Post by oldfred on 2015-10-23
You should not change the recovery mode's entry, but fix the issues with the normal boot entry.

You have an HP, and they are not UEFI boot friendly for anything but "Windows"
See details in link in my signature for copying /EFI/ubuntu to /EFI/Boot. (or which ever system you want to default boot). Then rename /EFI/Boot/grubx64.efi to /eFI/Boot/bootx64.efi. Best to fully backup ESP partition first. Not sure if your Min works like Ubuntu, but the grub that is renamed is hard coded to only find the grub.cfg in /EFI/ubuntu. That is a three line configfile entry to the real grub.cfg in the install.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
 Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
      
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886
[/URL]
 HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
      [/URL]
 Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)      [ ]("http://ubuntuforums.org/showthread.php?t=2260681")  [ ]("http://ubuntuforums.org/showthread.php?t=2131886")

---

### Post by deepakdeshp on 2015-10-23
Thank you oldfred for so many excellent posts and so much knowledge shared. I will do some homework and report back. 

I have 13 partitions now if I delete some of them like say 11,12 etc I guess again there will be mismatches of UUIDS with fstab, and grub entries. So best bet would be to delete the files in these partitions and keep a minimal size partition like 10 MB etc. That way there wi;; not be any nasty things like mismatches etc.

---

