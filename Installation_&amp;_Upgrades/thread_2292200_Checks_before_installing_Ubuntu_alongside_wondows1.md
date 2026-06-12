---
title: "Checks before installing Ubuntu alongside wondows10"
date: 2015-08-26
forum: Installation &amp; Upgrades
---

### Post by gauravchauhan on 2015-08-26
Hello there,

I am Gaurav Chauhan. I got new laptop(Lenovo with AMD A8,4GB,500 GB) with Windows 8.1 which is upgraded to windows 10. Now i would like to install ubuntu along side windows. Please note i have installed ubuntu with windows many times and i am familiar with the installation procedure. I am not asking about procedure to set dual boot system. 

What i would like to know is what are the checks i need to perform to see if things will be fine. 

For example After searching and reading i found one thing. I have to check if UEFI is enable or not. In windows 10 power shell i used " Confirm-SecureBootUEFI" and got "False" as a output. (I don't know it is good thing or bad!!!). I am very much confused in thin UEFI things and i heard stories of people who mess things up.

Earlier i have experience with assembled computers and older laptops which came with free dos. For those cases dual boot was most simplest thing. Now in this branded laptop i am not able to get idea what i should do.

Thanks for reading. I appreciate your help. 
Have a nice day.

---

### Post by dino99 on 2015-08-26
'oldfred' help a lot , try to search its posts/threads as he has a great knowledge

---

### Post by Bucky Ball on 2015-08-26
Welcome. Was the previous Windows installed in EFI? Just check the BIOS to see whether it is installed in EFI mode or legacy. Also, you can boot from Ubuntu install media, launch gparted and look for a small FAT partition. That will be the EFI partition. 

What you need to do to install alongside a Win EFI install (if Win7 or above came pre-installed in the machine it will be EFI) is to boot into Windows and switch off faststart (or fastboot it might be) and hibernate. If these are on, Ubuntu will not see your Win partition during the install. Problem. 

In the BIOS, switch off secureboot. BIOSs vary, you may need to set the machine to boot the install media in EFI, but apart from that you should be good to go.

You will find lots of information on how to do all this online. If you run into issues, just ask.  

When you reach the partitioning section of the Ubuntu install, choose 'Something Else' and manually partition. You need free, unallocated space to install to as, as you say you've done this bit many times, you probably know. If you need to shrink the Win partition, do it in Win and using Win software, NOT using Gparted. Conversely, resize Linux partitions using Linux software, not Win (which doesn't have much idea what they are anyway). 

Good luck and hope that helps.

---

### Post by kagashe on 2015-08-26
> **gauravchauhan said:**
> Hello there,

I am Gaurav Chauhan. I got new laptop(Lenovo with AMD A8,4GB,500 GB) with Windows 8.1 which is upgraded to windows 10. Now i would like to install ubuntu along side windows. Please note i have installed ubuntu with windows many times and i am familiar with the installation procedure. I am not asking about procedure to set dual boot system. 

What i would like to know is what are the checks i need to perform to see if things will be fine. 

For example After searching and reading i found one thing. I have to check if UEFI is enable or not. In windows 10 power shell i used " Confirm-SecureBootUEFI" and got "False" as a output. (I don't know it is good thing or bad!!!). I am very much confused in thin UEFI things and i heard stories of people who mess things up.

Earlier i have experience with assembled computers and older laptops which came with free dos. For those cases dual boot was most simplest thing. Now in this branded laptop i am not able to get idea what i should do.

Thanks for reading. I appreciate your help. 
Have a nice day.If Lenovo pre-installed Windows 8.1 it has to be UEFI  but since you got false I am confused. Forget about it for this moment. Since you are going to install Ubuntu you must be having a Live CD or Live USB, if you don't have you need to create one. There must be some way to get the Boot Menu. On new Lenovo Laptops there is NOVO button on left side. After putting Live CD or USB you need to press the NOVO button on a shutdown machine to get the Boot Menu. From Boot Menu you select the Live CD or USB and boot into Ubuntu Live session.

In Ubuntu Live session you can type following in the terminal:
```
sudo gdisk -l /dev/sda
```
If the output of the above command shows like this,then you have MBR disk,
```
Partition table scan:
MBR: MBR only
BSD: not present
APM: not present
GPT: not present
```

If the output shows like this then you have GPT disk,
```
Partition table scan:
MBR: protective
BSD: not present
APM: not present
GPT: present
```

NB: Please use Ubuntu 14.04 or later.
Kamalakar

---

### Post by gauravchauhan on 2015-08-27
So what i understood here is, disable hibernate, disable secureboot and faststart. I enable legacy mode than UEFI mode. Then in windows i make a partition for ubuntu and install it from live USB.

---

### Post by kagashe on 2015-08-27
> **gauravchauhan said:**
> So what i understood here is, disable hibernate, disable secureboot and faststart. I enable legacy mode than UEFI mode. Then in windows i make a partition for ubuntu and install it from live USB.If your Windows is in UEFI you have to install Ubuntu also in UEFI and there is no need to enable legacy mode at all. If you are not sure about Windows (whether in UEFI or not) do as I suggested i.e. boot from live USB and find out from the command "sudo gdisk -l /dev/sda"

Kamalakar

---

### Post by Bucky Ball on 2015-08-27
> **gauravchauhan said:**
> So what i understood here is, disable hibernate, disable secureboot and faststart.

You have that part right.

> I enable legacy mode than UEFI mode.  

Don't quite understand this bit. If you have a EFI Windows install legacy mode has nothing to do with it. You don't want legacy mode at all. You want the previously mentioned things switched off and the BIOS set to boot the USB and install in EFI.

I think what you're trying to say is you enable legacy mode, then EFI mode. Impossible and no. You want one or the other, I presume EFI. As I think I mentioned earlier, unless you have manually and explicitly installed Windows in Legacy mode it will be in EFI. This is a certainty if Win7 or above came pre-installed. 

> Then in windows i make a partition for ubuntu and install it from live USB.

No. As I also think I mentioned, do NOT create Ubuntu partitions in Windows. You can't anyhow. Create free space to create partitions in during the install with Ubuntu and choose 'Something else' when you get to the partitioning section of the install to manually partition and do that.

---

### Post by kagashe on 2015-08-27
@Bucky Ball
I think his Windows is on MBR. This is India:D
Kindly let him give the output of the command I suggest.

Kamalakar

---

### Post by Bucky Ball on 2015-08-27
> **kagashe said:**
> 
Kindly let him give the output of the command I suggest.

Kamalakar

What gives you the impression I'm stopping him? The user had some questions, some suppositions which are wrong. I helped answer them. Kindly back the the problem at hand. Thanks.

PS: One look at Gparted for a small EFI partition will answer whether this is EFI Win install or not. As I said, if Win was preinstalled Win7, it is EFI unless that has been manually and specifically changed by the user when reinstalling Windows; a full, clean install, not an upgrade (which won't change the install from EFI to Legacy).

---

### Post by kagashe on 2015-08-27
> **gauravchauhan said:**
> In windows 10 power shell i used " Confirm-SecureBootUEFI" and got "False" as a output

shows that it may not be UEFI.

To confirm while in Windows please type following in the Run dialogue.
```
msinfo32
```
and see the entry next to BIOS Mode: (whether it is Legacy or UEFI)

Kamalakar

---

### Post by gauravchauhan on 2015-08-27
Lots of help guys. Thanks a lot.@[[COLOR=#000000]kagashe[/COLOR]]("http://ubuntuforums.org/member.php?u=27293")[COLOR=#000000] [/COLOR], @[[COLOR=#C61919]Bucky Ball[/COLOR]]("http://ubuntuforums.org/member.php?u=504316")[COLOR=#000000] .... from MSINFO32 secure boot is OFF and BIOS mode is UEFI. So i believe i will install ubuntu in UEFI mode.[/COLOR]

---

### Post by kagashe on 2015-08-27
> **gauravchauhan said:**
> Lots of help guys. Thanks a lot.@[[COLOR=#000000]kagashe[/COLOR]]("http://ubuntuforums.org/member.php?u=27293")[COLOR=#000000] [/COLOR], @[[COLOR=#C61919]Bucky Ball[/COLOR]]("http://ubuntuforums.org/member.php?u=504316")[COLOR=#000000] .... from MSINFO32 secure boot is OFF and BIOS mode is UEFI. So i believe i will install ubuntu in UEFI mode.[/COLOR]You can see in my signature that I use Lenovo G50-45 Laptop with Ubuntu in dual boot with Windows 8.1 with UEFI Secure Boot on and I think you can do that too on your Lenovo Laptop.

I am not sure why secure boot is OFF on your Laptop but you can turn it ON in the BIOS and see whether Windows boots normally. Ubuntu live as well as installed Ubuntu can also boot with secure boot ON.

There are not many cases of successful Ubuntu dual boot with Windows 10 and although you can install Ubuntu don't panic if Grub fails to detect Windows 10 installation if it happens there are workarounds.

Remember the advice of Bucky Ball and resize NTFS partitions while in Windows. I had taken one more precaution. I created ext4 partition with gparted on live Ubuntu and reboot Windows so that Windows accepted the ext4 partition then installed Ubuntu on that ext4 partition. I could not mount the NTFS partition on live Ubuntu and solved that too before installing Ubuntu.

You may face problem while resizing NTFS partition on Windows like it may not allow beyond certain size. If that happens there are workarounds in Windows.

Kamalakar

---

### Post by Bucky Ball on 2015-08-27
Okay. Secure boot off, hibernate and fastboot (or start) off (you need to boot to Windows to do this) and you should be good to go. Make sure you have created free space in Windows using Windows partitioning software prior to starting and you have a plan for what partitions to create and where they're going. Good luck and if you hit a brick wall just ask.

---

### Post by gauravchauhan on 2015-08-28
Up and running...Thanks a lot for help...@[COLOR=#DD4814][COLOR=#000000][kagashe]("http://ubuntuforums.org/member.php?u=27293") [SIZE=2]and[/SIZE] @[/COLOR][/COLOR][Bucky Ball]("http://ubuntuforums.org/member.php?u=504316")[COLOR=#000000]. this is what i did to get a dual boot system running.

In windows:

- Disable hibernate , faststart
- from windows 10, click on start menu>settings>update and recovery> advanced start up. 
- it restarted a system and presented me a menu from which i logged in to UEFI settings. (not bios, it`s UEFI)
- My UEFI manufacturer iss lenovo. this can very. i just enabled usb boot. secure boot is on!!!
- Again booted to windows 10
- created unallocated space for ubuntu in windows
- Downloaded rufus ([/COLOR]https://rufus.akeo.ie/[COLOR=#000000]) and created EFI bootable disk for GPT. Yes it is GPT.
- same procedure to boot to bios as above via update and recovery.
- there is a option to boot from usb/dvd
- selected that and it booted to live ubuntu.
- installed ubuntu 14.04.03 amd64..

thanks once again much appreciated the help.[/COLOR]

---

### Post by kagashe on 2015-08-28
> **gauravchauhan said:**
> Up and running...Thanks a lot for help...@[COLOR=#DD4814][COLOR=#000000][kagashe]("http://ubuntuforums.org/member.php?u=27293") [SIZE=2]and[/SIZE] @[/COLOR][/COLOR][Bucky Ball]("http://ubuntuforums.org/member.php?u=504316")[COLOR=#000000]. this is what i did to get a dual boot system running.

In windows:

- Disable hibernate , faststart
- from windows 10, click on start menu>settings>update and recovery> advanced start up. 
- it restarted a system and presented me a menu from which i logged in to UEFI settings. (not bios, it`s UEFI)
- My UEFI manufacturer iss lenovo. this can very. i just enabled usb boot. secure boot is on!!!
- Again booted to windows 10
- created unallocated space for ubuntu in windows
- Downloaded rufus ([/COLOR]https://rufus.akeo.ie/[COLOR=#000000]) and created EFI bootable disk for GPT. Yes it is GPT.
- same procedure to boot to bios as above via update and recovery.ubuntu1.
- there is a option to boot from usb/dvd
- selected that and it booted to live ubuntu.
- installed ubuntu 14.04.03 amd64..

thanks once again much appreciated the help.[/COLOR]Good that it all worked. Now when you are booting you must be getting Grub Menu as follows:
```
GNU GRUB version 2.02~beta2-9ubuntu1.3

Ubuntu
Advanced options for Ubuntu
Windows Boot Manager
System setup
```I hope you have checked that you are able to boot Windows by selecting the entry "Windows Boot Manager"

If you select the last entry "System setup" you will get the BIOS which has all system menus, UEFI Boot Menu etc. You can have a look and just exit without saving changes.

While in Ubuntu please check whether all hotkeys (Volume up/down, Brightness up/down etc) are working.

If you have time you can search for "System Testing" on Dash and do a complete test of how your hardware is working on Ubuntu and post separate thread if something does not work.

Please mark this thread as "SOLVED"

Kamalakar

---

### Post by Bucky Ball on 2015-08-28
Good news. Enjoy. :)

---

