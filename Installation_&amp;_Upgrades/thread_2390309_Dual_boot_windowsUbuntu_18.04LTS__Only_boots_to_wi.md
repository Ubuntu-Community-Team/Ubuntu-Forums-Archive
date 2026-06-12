---
title: "Dual boot windows/Ubuntu 18.04LTS  Only boots to windows"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2018-04-27
Dual boot windows/Ubuntu 18.04LTS  Only boots to windows.  I've installed ubuntu 18.04LTS and windows boots fine, it just doesn't show the grub at start up to choose the operating system.  I only get Windows.

HP Pavilion laptop with windows 10

Thanks,

Dennis

---

### Post by oldfred on 2018-04-27
HP is not particularly dual boot friendly.
Can you boot Ubuntu from UEFI boot menu. Some that only boot Ubuntu occasionally live with that.

Otherwise there are many work arounds depending on configuration.
One is to boot fallback or hard drive boot entry in UEFI. Boot-Repair will now copy shimx64.efi to be /EFI/Boot/bootx64.efi which is a fallback entry.
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

[/URL]
 HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)
HP 8470p 
[https://ubuntuforums.org/showthread.php?t=2379728](https://ubuntuforums.org/showthread.php?t=2379728)
HP Z240 Tower Workstation XEON E5 UEFI & hard drive issues, manual chroot & reinstall of grub-efi-amd64
[https://ubuntuforums.org/showthread.php?t=2376227](https://ubuntuforums.org/showthread.php?t=2376227) 

[URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by timsdeepsky on 2018-04-27
Greetings claven123....
I fought with this exact issue all day, except i have windows 8.1....
My laptop is an "HP-ENVY-17-Laptop"....
Here is how i fixed my dual boot issue....

First I went into my Bios and made sure that Ubuntu was on top of the list under:
Bios
System Configuration
UEFI boot loader
OS boot manager

Second i started Ubuntu from the live disk, navigated to, and followed the instructions from this site....
[https://sites.google.com/site/easylinuxtipsproject/6]("https://sites.google.com/site/easylinuxtipsproject/6")

_If_ this works for you, you may still have to press "esc" at startup, and hit "F10" and choose Ubuntu instead of Windows....

This worked for my system....
Here is my system info....

Ubuntu 18.04 LTS
Linux 4.15.0-20-generic (x86_64)
Intel Core i7-4720HQ CPU @ 2.60GHz
HP-ENVY-17-Notebook-PC

Thank you....

---

### Post by claven123 on 2018-04-28
Please write on a paper the following URL:
[http://paste.ubuntu.com/p/hCdzrDVKSh/](http://paste.ubuntu.com/p/hCdzrDVKSh/)


Tim...I'm not sure of the first part of your reply, the second seems reasonable, however I'll stick with Oldfred's advice first.

Dennis

---

### Post by timsdeepsky on 2018-04-28
Greetings,
You have an HP....
Did you boot into the BIOS, (hit "esc" at startup and choose "F10") and then navigate here:

-Bios
-System Configuration
-UEFI boot loader
-OS boot manager

and make sure Ubuntu was on top of the list above Windows..?

If this works for you, you may still have to press "esc" at startup, and hit "F10" and choose to start Ubuntu instead of Windows....
Thank you....

---

### Post by claven123 on 2018-04-28
My last laptop, I had to hit F12 every boot to get the option to boot into grub.

I'll give it a try with this one using esc or F10.... couldn't remember the key.  

D

---

### Post by oldfred on 2018-04-28
I think HP is escape f9 for boot menu.

Have you tried turning Secure Boot off? 

If you run Boot-Repair it will copy shimx64.efi to the fallback /EFI/Boot/bootx64.efi. Then you may be able to boot a hard drive entry (not the ubuntu entry).

timsdeepsky suggestion is a full chroot. You still manually can do that, but Boot-Repair does the same thing and is a bit easier.

But with HP Boot-Repair sees all the .efi HP files in the ESP. And then it creates a 25_custom entry so you have all those as entries in grub. Generally not required, and many remove or turn off 25_custom or edit out most of those boot entries in grub menu.

 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by claven123 on 2018-04-28
I was able to push esc on start up and was given options for boot order, I chose F9, which got me to grub, was able to then boot ubuntu.

I'll try to turn off secure boot, then i'll try boot repair.

D

---

### Post by claven123 on 2018-04-28
No change with secure boot off.

I then ran boot repair, did the recomended repair, no change.

Here is the summary url.

[FONT=arial]Boot successfully repaired.[/FONT]

[FONT=arial]Please write on a paper the following URL:[/FONT]
[http://paste.ubuntu.com/p/nVmwXw5mmR/](http://paste.ubuntu.com/p/nVmwXw5mmR/)


[FONT=arial]In case you still experience boot problem, indicate this URL to:[/FONT]
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL][FONT=arial] or to your favorite support forum.[/FONT]

[FONT=arial]You can now reboot your computer.[/FONT]
[FONT=arial]Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file![/FONT]

[FONT=arial]If your computer reboots directly into Windows, try to change the boot order in your BIOS.[/FONT]
[FONT=arial]If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.[/FONT]
[FONT=arial]For example you can boot into Windows, then type the following command in an admin command prompt:[/FONT]
[FONT=arial]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi



D[/FONT]

---

### Post by oldfred on 2018-04-28
Separately, you need to have Windows fast start up off which is just hibernation.
The Linux NTFS driver will not mount nor then see hibernated Windows. And then grub will not boot a hibernated Windows. Note that Windows updates (which may be in background) will turn fast start up back on.

> Windows is hibernated, refused to mount.
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Does the internal hard drive boot entry boot Ubuntu now.
Boot-Repair copied shimx64.efi to this, since there is a backup of it. The backup probably is just a copy of Windows .efi boot file.

 /EFI/Boot/bootx64.efi 

Line 1074 in report:
      
```
 BootOrder: 0002,2001,2002,0001,3001,2004
Boot0000* Internal CD/DVD ROM Drive (UEFI) (hp      DVDRW  DA8AESH)	PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)/CDROM(1,0xe02b3,0x1240)RC
Boot0001* Windows Boot Manager	HD(1,GPT,a1bbcbde-629f-42ab-9581-29b075006f72,0x800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* ubuntu	HD(1,GPT,a1bbcbde-629f-42ab-9581-29b075006f72,0x800,0x82000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3001* Internal Hard Disk or Solid State Disk	RC 


```


Boot entry 3001 or internal hard drive may now boot Ubuntu.

---

### Post by claven123 on 2018-04-28
I turned off fast start up.

Hibernate is off.

I shut down and turned back on twice.  Still boots directly to windows.


Dennis

---

### Post by timsdeepsky on 2018-04-28
Greetings,
If i read correctly,,you were able to find and boot Ubuntu....This is good....
But you need it to boot Ubuntu by default....
If i were you, i would try what i said in my first reply:

Restart your machine and hit "esc" at startup....
Then you should be able to choose "F10" (not "F9")....
This should take you to the BIOS....

Go to System Configuration
Then to UEFI boot loader
Then to OS boot manager
Make sure that Ubuntu was on top of the list, and Windows is second in the list....
Save this in the Bios....

This may fix it....

Then if it does not boot Ubuntu by default,,you can always install "Grub Customizer"and tweak it from there....
Thank you....

---

### Post by claven123 on 2018-04-28
Yes, it boots fine if I choose F9, then I get an option to boot ubuntu.

I want the option at initial boot up to choose either windows or ubuntu, not just directly to ubuntu.  Unfortunately, I still require windows.

I'll give it a try....


D

---

### Post by claven123 on 2018-04-28
Oh my, I didn't know I could change that.  I looked for what you were saying the other day and didn't find it.  Then I noticed the triagle indicator next to the OS in the boot order.  I then clicked it and I saw the two options, windows/ubuntu.  I changed ubuntu to first and save exit.  Then booted and it booted directly into grub2!!!

So, that worked, also the other stuff as well.

Which one is the best option to boot into windows from the list of options, I see windows boot manager on sda, I assume that one would work.

Thanks,

D
[ATTACH=CONFIG]279474[/ATTACH]

---

### Post by timsdeepsky on 2018-04-28
You are correct....
When the grub 2 screen comes up, you choose the Windows boot manager to boot into Windows.... 
Thank you....

---

### Post by pirulo-gmail on 2018-05-03
(I found this elsewhere, this is just to share experience. Anyway, thanks to the community!)

I had the same symptom with an HP Envy 17 (i7-4700).
In the EFI partition, 
- in the "Microsoft\Boot" directory, I renamed the "bootmgfw.efi" to something else,
- then I copied the "grubx64.efi" from the "ubuntu" directory to the "Microsoft\Boot" directory and renamed it to "bootmgfw.efi"
I had to do it again after a substantial update of Windows.

---

### Post by oldfred on 2018-05-03
While the copy of grub or shim to be the Windows boot file, it is not now recommended.
As you found Windows updates will keep overwriting that file.
And grub updates will not update that file but the copy in /EFI/ubuntu.

Better to use one of the other work arounds.
Can you directly boot the ubuntu entry in UEFI boot menu?

       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)


 HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663) 

Older HP threads where users manually copied file, before Boot-Repair did it. But then you boot hard drive or fallback entry, not ubuntu entry.
       
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by f(fanta) on 2018-07-27
I have the same issue with Ubuntu 18.04.01 on a custom-built desktop. After installing Ubuntu Server (on RAID 0), the GRUB menu doesn't show at boot time, and I can switch between Win 10 and Ubuntu only by changing the boot order under UEFI BIOS. I run boot repair, also issued 
[FONT=arial]**bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi**
under Win 10, but no change. That doesn't happen with Ubuntu 16.04.
[/FONT][FONT=arial] [/FONT]

---

### Post by oldfred on 2018-07-27
@f(fanta)
Please start your own thread. This one is solved and if solutions here do not work, then you need your own thread.
Most boot issues are unique as users have different configurations and hardware.
Also post link to summary report from Boot-Repair.

---

