---
title: "Differing partition layouts depending on drive size 12.04"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by ntgamers1 on 2014-07-24
Hello everyone so I have a computer that is running SeaBios/Coreboot which does not support booting from UEFI partitions, the system came with a 16gb SSD originally and I am trying to get 12.04 up and running on a 256GB replacement drive. 

16GB drive brand is Sandisk and the 256GB drive is Crucial both are msata drives.

I am trying to install Ubuntu from my Lenovo laptop onto the 256GB drive to swap into the other machine since it lacks an optical drive and has some usb boot issues at the moment, when I do this with the 16GB drive and tell Ubuntu to install to the entire drive it creates everything perfectly for the other system, it will boot and run flawlessly even if i create the partitions manually including a 1gb swap partition however for some reason when I go to do this with the 256GB drive Ubuntu wants to create a UEFI boot partition of 512mb, manually trying to create the partitions isn't working.

I can go and manually make the following with the 16gb drive and it works fine.

/swap 1gb
/ 15gb 

if i try to do the following with the 256gb drive it doesn't work and throws the UEFI boot partition warning and then refuses to boot on restart

/swap 16gb
/ 240gb

even doing 

/boot 100mb
/swap 16gb
/ 240gb

doesn't work.


This leaves me with a few questions, why is Ubuntu enforcing UEFI boot only when the larger drive is present but not the 16gb drive? I even attempted to boot into the live cd and manually set / with the boot flag using gparted and no dice.

The 16gb drive will boot from both systems, the 256gb drive will not boot from any system and will only boot from my laptop if i let it make the UEFI partition, disabling EFI from bios causes the Ubuntu install to behave very oddly and doesn't allow me to even select the partition setting it complains about not being able to load some EFI module. 


I want my 256gb drive to work with the other system, if i install windows 7 of all things to the 256gb drive the other system will boot that but it won't boot Ubuntu?

---

### Post by ntgamers1 on 2014-07-24
Bump, hoping someone has some information regarding this

---

### Post by Bucky Ball on 2014-07-24
Welcome. Please wait at least a few hours or longer before bumping threads. We are an international community and it can sometimes take awhile for the person who can help you to see your thread. 

Think you need to boot to BIOS and make sure it is not set to boot in UEFI to start with, if you don't want UEFI. You might be able to force it to not use it.

Is there a particular reason you don't want to install UEFI on the larger drive?

PS: Have you wiped the larger drive, including partition table and MBR? That might be the issue. You can boot to Gparted from a Live DVD/USB and kill it, then reformat as EXT4 (or whatever). Or you can format it with 'Something Else' during install, which sounds like what you want.

---

### Post by ntgamers1 on 2014-07-24
> **Bucky Ball said:**
> Welcome. Please wait at least a few hours or longer before bumping threads. We have an international community and it can take time for the person who can help you to see log on. 

Think you need to boot to BIOS and make sure it is not set to boot in UEFI to start with, if you don't want UEFI. You might be able to force it to not use it.

Is there a particular reason you don't want to install UEFI on the larger drive?


My apologies, yes as stated in the beginning of my original post the system the drive is going to will not boot from a UEFI partition, it will however boot from Windows 7 on the larger drive and boot with the 16gb drive with Ubuntu, I tried 12.04 and 14.04 neither of which create the partition layout correctly when using the larger drive. 

Just to clarify what the issue is Ubuntu will install to the 16GB drive without trying to make a UEFI partition and since it doesn't try to do that it works flawlessly in both systems, it however wants to force me to make one with the larger drive. Also disabling UEFI in bios before loading Ubuntu installer causes the Ubuntu installer to fail by throwing an error regarding unable to load amd-64-uefi something and if i press continue it doesn't take me to the partition layout section nor does it display any information once i get past the setting timezone/username section so there is no indication that it's actually installing.

---

### Post by Bucky Ball on 2014-07-24
Is Windows 7 already on the larger drive? I don't understand this:

> ... the drive is going to will not boot from a UEFI partition, it will however boot from Windows 7 

Boot Ubuntu from Windows 7? If you are dual-booting you will be booting Windows and Ubuntu using Grub or UEFI (there are others, but these are the most common).

---

### Post by ntgamers1 on 2014-07-24
> **Bucky Ball said:**
> Is Windows 7 already on the larger drive? I don't understand this:



Boot Ubuntu from Windows 7? If you are dual-booting you will be booting Windows and Ubuntu using Grub or UEFI (there are others, but these are the most common).


I am not dual booting, the point I was making is that I can wipe the drive entirely and install windows 7 to it with my laptop and swap it over and windows 7 will boot but Ubuntu refuses to by doing the same process, I just tried your suggestion of using gparted to format the drive to ext4 then letting ubuntu try to install to the freshly formatted drive will post an update shortly letting you know the results.

---

### Post by Bucky Ball on 2014-07-24
Okay. Now I think I have you. I'll forget about the small drive cos that works. You are deleting Windows 7 from the large drive and installing Ubuntu on that. Well, I'm guessing Windows 7 was installed UEFI and therefore, when you try to do anything with it, it will respond accordingly. Let us know how you go after deleting everything on it and starting again. If it has an EFI partition on it (FAT and small) then that is probably the issue.

After wiping you should boot into the BIOS and make sure the machine is NOT booting UEFI mode before proceeding with the Ubuntu partition/install.

---

### Post by ntgamers1 on 2014-07-24
So it appears what I need Ubuntu to do is create a MBR partition layout and currently it wants to create a GUID partition layout

This is how Ubuntu partitions the 256gb drive 

[ATTACH=CONFIG]254980[/ATTACH]


and this is how it partitions the 16gb drive

---

### Post by Bucky Ball on 2014-07-24
Got me stumped. If you've wiped the drive, booted to the BIOS to make sure you're not booting in UEFI and it is still doing it, I don't have any suggestions for now. I'll dwell on it and in the meantime someone who does have an idea may arrive.

Please attach large pics rather than inserting into the body of your post by using 'Adv Reply' or 'Go Advanced' and using the paperclip icon. I've done one of them as an example. ;)

---

### Post by ntgamers1 on 2014-07-25
> **Bucky Ball said:**
> Got me stumped. If you've wiped the drive, booted to the BIOS to make sure you're not booting in UEFI and it is still doing it, I don't have any suggestions for now. I'll dwell on it and in the meantime someone who does have an idea may arrive.

Please attach large pics rather than inserting into the body of your post by using 'Adv Reply' or 'Go Advanced' and using the paperclip icon. I've done one of them as an example. ;)


No problem so the issue i figured out when trying to install 12.04 with UEFI disabled is that ubi-partman fails to run which means i can't partition the drive and the install hangs, there seems to be some solution to go into f6 advanced mode from the boot screen and use the nodmraid option but when i press esc or f6 from the install screen neither of those options are present do I have to use the live cd to get this option? Pretty frustrating experience so far seeing as different Ubuntu releases depending on it being the live cd or not may or may not have this option and Ubuntu seems to be unable to run the install normally if UEFI is disabled. I'll try again when i get some free time using the live cd of 12.04 and 14.04 and will update.

---

### Post by oldfred on 2014-07-25
How you boot install media is how it installs.
Or if you boot in UEFI mode it will only install in UEFI mode, or if you boot in BIOS mode it will only install in BIOS mode. But Boot-Repair can convert one type of install to the other if you have gpt partitioning and correct supporting partition. With UEFI you have to have an efi partition and with BIOS you must have a bios_grub partition.

With Ubuntu you have to have gpt partitioning with UEFI.
With Ubuntu only you can have either gpt partitioning or MBR(msdos) partitioning and boot in BIOS mode. 
Windows only boots in BIOS mode from MBR drives. And only in UEFI mode from gpt drives.

I only create gpt partitioned drives now, and add both an efi partition even though I do not have UEFI, so I could convert drive to UEFI later when I get my new system. And then with BIOS I have to have the bios_grub partition. I use gparted to partition in advance but still use Something Else to install.

Since UEFI & BIOS work differently, some systems need different boot parameters to boot in different mode.

While for a flash drive, the procedure is the same for any install and you do not have to make it both.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by ntgamers1 on 2014-07-25
Yeah that doesn't help, I think you missed the point I was making I don't want to install to a USB drive either. The Ubuntu installer fails with UEFI disabled using the latest 12.04 ISO, when you boot and try to install it will throw an error saying ubi-partman failed with error 10 check syslog. Since the partition manager fails to run with UEFI disabled it won't allow me to install to the ssd the installer simply hangs, now as far as boot-repair goes I already attempted to use that with the freshly formatted and installed 256gb ssd, when i use boot-repair the MBR option is greyed out even after deleting the UEFI partition, having it reinstall grub and upon reboot what happens is it gets stuck in a boot loop where it will try to boot and then return to the bios splash screen over and over.

What the instructions on the site say is that I should be able to go into the boot menu and click f6 or esc to view advanced options but that isn't the case, there are no advanced options presented.


When i create the bios_grub partition, be it 100mb , 10mb, 1mb (tried all 3) and run boot-repair what I end up with in the end in gparted is a red explination mark saying that the partition is broken or unusable even after using boot-repair and it won't boot with UEFI disabled.

The screenshots here show a fancy ubuntu start menu, what i get is an ugly cmos style blue/black bars when i go to the boot menu. [http://nixsos.com/ubi-partman-failed-with-exit-code-10-error/](http://nixsos.com/ubi-partman-failed-with-exit-code-10-error/)

---

### Post by oldfred on 2014-07-25
Was drive ever RAID? That leaves meta-data on drive that interferes.
Or are you trying to install in BIOS with MBR when left over gpt data is one drive. Then you need to remove backup gpt partition table.

Instructions for flash drive are just instructions for install to any drive whether flash or not, whether internal or external.

What model Lenovo?
One user posted this:
 > Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.
      
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

---

### Post by ntgamers1 on 2014-07-25
Hmm the drive should have never been in raid mode, I've wiped the partitions using gparted before the model is Lenovo y580 which has the hm76 mobile chipset which has raid functionality disabled so I highly doubt it has raid data on it. F2 is my bios access key, In fact I'm running a custom unlocked bios that opens up quite a few options for me but I have set everything accordingly as far as I can tell, I will try once more this afternoon and put the drive in IDE mode before trying the install again.

---

### Post by oldfred on 2014-07-25
Some more Lenovo links.

  [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

This is now older:
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

---

### Post by ntgamers1 on 2014-07-25
So first of all I want to say thank you for trying to help me solve this both of you. I finally fixed it.

So here is what I had to do, boot into windows and recreate my usb key using the linux live usb creator and not unetbootin, if you use unetbootin you cannot access the advanced options and thus cannot boot with nodmraid flag.

Once booted in I tried installing (UEFI disabled) and the installer froze while trying to load ubi-partman again, so this time i set the drive into IDE mode only, rebooted using 14.04 and not 12.04 and booted with nodmraid and I was able to manually create a 100mb grub bios partition, a 8gb swap partition and a 240gb / ext4 partition, then I had the installer install, made sure it booted from my laptop with UEFI disabled and swapped it over, upon boot it said it needed to fix some errors I pressed F and wala I'm now in!  :guitar:

---

