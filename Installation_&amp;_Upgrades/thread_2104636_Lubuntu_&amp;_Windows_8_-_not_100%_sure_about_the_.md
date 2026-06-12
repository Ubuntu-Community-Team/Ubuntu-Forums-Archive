---
title: "Lubuntu &amp; Windows 8 - not 100% sure about the process."
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by kero4 on 2013-01-13
Gentlemen,

It's time for me to replace both laptops for both the wife and I. I have plenty of linux experience and have been using it for years, particularly lubuntu and other flavors with the LXDE desktop.

We all know the new problem with windows 8 and secure boot and all that malarkey.

I went to look at new laptops today and was able on several models to disable secure boot. 

I would like to install lubuntu 12.10 on both machines but I am not 100% understanding the process.

I have read several articles on SHIM which I am also not 100% sure about.

[B]In addition, I brought with me to the store a usb boot flash drive with lubuntu 12.10. Works at home and on all my computers. Made sure of this before leaving. On the laptops I am interested in, I disabled secure boot and disabled fast boot. Was not able to get any of the laptops to boot from the USB flash drive. I usually do this to make sure what I buy, all the hardware works correct with lubuntu. 

I was at a loss at the store to figure out why I couldn't get lubuntu to load up from the USB flash drive like I do on all pre windows 8 machines.

I have 32bit version of lubuntu 12.10 on the flash drive, not sure if that has anything to do with above.
[/B] 
What is the most affective and straight forward way to install lubuntu on a windows 8 laptop.

I would prefer to not have windows on the laptops at all but have a feeling it's needed based on my readings thus far.

In additions the laptops I am looking at have AMD processors and no CD/DVD drives so I would have to install through a USB boot flash drive, which I do on all my other machines anyway.

Please advise as it's time to replace my old heavy laptops with something more modern and would like to do this soon.

Thanks in advance for any help.

---

### Post by kero4 on 2013-01-14
Please someone help me with some guidance.

---

### Post by oldfred on 2013-01-14
I think you were close but have to have the 64 bit version as that is the only one with the efi files. All new computers are 64 bit capable so there is no reason for 32 bit.

You have to from UEFI menu boot UEFI mode. UEFI menu should show both an efi and a BIOS/legacy/CSM/AHCI or something as two boot options. How you boot flash drive is how it will install.

Not sure of AMD systems, but depending on video you may have to add nomodeset of other boot parameters to get system to boot. Also the new Intel based systems that are Ultrabooks have a small SSD that somehow uses RAID which then adds another level of complication. And dual video systems with nVidia need special handling.

New systems can be real fun. :)

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vitial for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
When you do install you will need Boot-Repair to fix a grub bug on chain loading to Windows and on some systems backing up &  changing file names as they only boot from the Windows file. For those the work around is to copy either grub2's efi file or the shim file to Windows efi folder and name it to the Windows file. Then from grub menu chain back to the renamed Windows file.

We are finding some systems just work, some have issues and a few have really major issues that may or may not be resolvable.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

     
Several different brands, some issues, and most at least were finally able to boot in UEFI mode.
       Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

---

### Post by kero4 on 2013-01-14
Okay and thank you for chiming in, some quick questions:

#1 You will need to use the 64 bit version of 12.10 and from the UEFI menu  boot the flash drive in UEFI mode. That way it will install in UEFI  mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vitial for some systems - [B]Lubuntu does indeed have a 64bit install, however, this is what their website says. "This release of Lubuntu does not support [UEFI Secure Boot]("http://en.wikipedia.org/wiki/UEFI_Secure_Boot"), unlike [Ubuntu 12.10]("http://en.wikipedia.org/wiki/Ubuntu_12.10"), which would have allowed it to run on hardware designed for [Windows 8]("http://en.wikipedia.org/wiki/Windows_8"). This feature will likely be included in the next release of Lubuntu.[[73]]("http://en.wikipedia.org/wiki/Lubuntu#cite_note-Lubuntu1210relnotes-73") _In the meantime Lubuntu can be run on UEFI secure boot hardware but turning off the secure boot feature. - does this mean I can or cannot use this version at this time?_

[/B]#2 You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode - [B]So, once I create the bootable USB flash drive, I use unetbootin, I have to boot the flash drive in UEFI mode on the laptop. How is that done or how do I tell the laptop to boot the flash drive in that mode?

[/B]#3 If lubuntu is not ready yet for windows 8 machines, can I install ubuntu 12.10 and then install LXDE into ubuntu 12.10. I like lubuntu much better and it's very low resource, which even on a new machine is nice as it runs ultra quick. If so, will LXDE installed into ubuntu 12.10 resemble LUBUNTU itself or will their be core differences, etc.

**#4 I would simply love to wipe out windows 8 and simply use lubuntu 12.10. Does this make life easier and change the steps at all other than disabling secure and fast boot, etc?**

#5 I just saw on dell business website they sell both a celeron dual core and I3 laptop that comes preinstalled with ubuntu (no windows whatsoever) price ranges from $266 yo $369. This could be a nice option since I would assume they would not even have UEFI on them.

Thank you.

PS - I haven't purchased a laptop yet. This is why I wanted to try and test them in the store with a bootable flash drive to check for hardware issues. If I create the bootable USB drive as normal, and want to boot from the USB flash drive, on the laptops in the store, I would have to disable fast boot and secure boot, after that how do I get the USB flash drive to load up?

---

### Post by oldfred on 2013-01-14
Not sure what Lubuntu is based on. But UEFI has worked (before secure boot) on older systems with Windows 7, but each update to grub2 has improved UEFI support.

I think secure boot has to be off for just about all systems to boot anything other than Windows to install. UEFI menu should have two entries one UEFI and the other BIOS along with all the other boot options. Every vendors UEFI seems to be different, so there is not just one way to get to UEFI menu and how menu looks. UEFI is a standard, but like most standards can be implemented many ways.

       The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
sudo apt-get install ubuntu-desktop
    
You can also install just desktop enviroments.
       Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
All Desktops in one:
[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)
    
Boot-Repair does have an option where if you install Ubuntu by mistake in BIOS mode, it can convert to UEFI mode by uninstalling grub-pc & installing grub-efi.  But I think Lubuntu may not have the correct kernel. The 32bit Lubuntu was one that could be used with old systems that did not support PAE.

I would not uninstall Windows at this time. Some systems with fast boot only can get into UEFI menu from Windows and they can be bricked if fast boot not off and Windows not working. Reinstall UEFI/BIOS about only fix if possible.

All Windows 8 systems are now secure boot. I would think vendors will eventually use UEFI for all systems but perhaps Dell is selling older systems with Ubuntu to unload them as they cannot run Windows 8?

---

### Post by kero4 on 2013-01-14
Here is what I was thinking of getting since I don't give two craps about windows whatsoever and the specs are pretty nice for the price

[http://configure.us.dell.com/dellstore/config.aspx?oc=bqctf2n&model_id=vostro-2420&c=us&l=en&s=bsd&cs=04](http://configure.us.dell.com/dellstore/config.aspx?oc=bqctf2n&model_id=vostro-2420&c=us&l=en&s=bsd&cs=04)

$369 is a good price

Thoughts?

Comes with ubuntu pre-installed, then can simply remove that install and install any distro i want, thus, avoiding the issue all together for now and the future until the laptop kicks the bucket

---

### Post by oldfred on 2013-01-14
I might add the extra RAM, 4GB would be better, but do not know enogh about this system to know how good it is.

If it has only 2GB it may be only 32bit anyway. With 4GB you can run the 64 bit version without issue. 

I am running 64 bit Ubuntu on my 6 year old Toshiba with only 1.5GB of RAM but it goes to swap if I try to open too much.

---

### Post by kero4 on 2013-01-14
I am running older pentium 4 laptops right now with 1 gig of ram and with lubuntu, they all run like champs.

I primarily use these for emergencies and web surfing and watching a movie here and there on VLC.

The dell comes with an I3 processor, hard to find a laptop with that for $369. Don't forget windows does not come with the laptop so I am saving that money.

2 gigs of ram is more than sufficient to run lubuntu, especially with an I3.

I never have installed a 64bit version as the 32bit versions always run very well. And this is on very old pentium 4 machines, with my pc's have.

So, I might grab that dell and never have to worry about all this stuff we have been discussing.

Plus the 14" screen is a perfect size for home use and or grab and go.

---

