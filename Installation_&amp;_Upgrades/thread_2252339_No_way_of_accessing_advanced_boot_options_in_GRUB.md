---
title: "No way of accessing advanced boot options in GRUB"
date: 2014-11-11
forum: Installation &amp; Upgrades
---

### Post by Idlewild1888 on 2014-11-11
Hi,

I'm experiencing a rather weird problem and I can't for the life of me figure out what's going on!

I'm trying to put Ubuntu, or one of its derivatives onto an old wall mounted screen with built in PC. Naturally I am experiencing the blank screen after trying to launch a live session or try an install. So I figured the next stop would be to try and launch with 'nomodeset' only this is where I have my issue...I can't seem to access any of the advanced kernel menus that will let me activate this setting!

When I boot from my usb stick (made using Universal USB Installer), I don't get the purplish sort of screen, nor do I see the little man icon with the sort of keyboard beside him - I am taken straight into the GRUB menu where I can select from Try Ubuntu, Install Ubuntu, Advanced, Mem Check, Help etc. When I land on this screen, the F key options do not appear along the bottom of the screen. When I try and press any of the F keys, all that happens is the screen flashes briefly and the menu resumes as normal. I don't know how to get out into terminal from here as pressing ctrl + alt+ Fn does nothing. If I press ctrl + c I get taken to a black screen with the word "boot:" and nothing else. If I try to launch live install or normal install I just get taken to the blank screen of doom!

I was worried that it might have been to do with the image I was using to boot, but am getting the exact same results from Elementary, LXDE and Lubuntu. The behaviour is exactly the same.

I was then concerned it was something to do with the old hardware I was trying to boot from, but then tried it on my nice shiny i7 Windows 8.1 machine and the behaviour was exactly the same, apart from the fact I could launch a live session or run an install ie no blank screen - which I would expect from a newer machine. However, even on this machine i still couldn't find a way to access the advanced boot menus or find any way of getting the F keys to do anything!

Does anyone have any idea how I can make my images boot with 'nomodeset' when I seem to have no way of getting the F keys to be recognised!?

Many thanks in advance!

---

### Post by oldfred on 2014-11-11
If you get grub menu on installer, then you are booting in UEFI boot mode.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You then add nomodeset or other boot parameters just like after you have installed to grub menu to test options.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Idlewild1888 on 2014-11-11
Thanks for the reply.

The machine I'm trying to install it on is pre-UEFI and when testing it on my Win 8.1 machine I am doing so with legacy boot and secure boot off, so again no UEFI.

When the machine boots to the USB stick I am taken straight to the options screen where I can choose Try unbuntu, install ubuntu, memory check, check drive for errors, advanced options and help. There is literally nothing between getting to that screen and the usb booting.

The e button doesn't do anything on either machine when this menu list is on the screen.

Any further advice would be great.

---

### Post by oldfred on 2014-11-11
When I directly boot ISO using grub, it just boots to live mode and I can install from that. Each mode is a boot option.

But I modify my grub menu to add nomodeset when booting ISO.

So how did you create flash drive? I might modify it with the nomodeset parameter.

       In /syslinux/txt.cfg
Where it has quiet splash on append line add nomodeset

---

### Post by Idlewild1888 on 2014-11-11
Ok maybe I'm getting confused with my nomenclature or something. Here are the steps I have carried out:

I downloaded the iso image from the ubuntu website.
I wrote it to my usb stick using the Universal USB Installer
I changed the boot order of my machine to boot straight to usb when I turn it on.

When the machine boots, it boots the usb and the very first screen I see is a menu screen with a Ubuntu background and a list of options.

The options are:

Try Ubuntu
Install Ubuntu
Memory Test
Check disk for errors
Advanced options (there's nothing under this menu item!)
Help

That is roughly what the list items say.

I can't press any of the Fn keys as they do nothing. I can't press e as it does nothing.

If I try to install or try ubuntu I'm just taken to a blank screen and can go no further.

What am I doing wrong here? :S

---

### Post by oldfred on 2014-11-11
The BIOS boot mode, you have to press the "any" key while the tiny icons are at bottom of screen. If not shown I might just try pressing keys right after BIOS.

If not grub menu e will not work.

You may have BIOS settings you need to change also.

You should be getting these screens.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

And if function keys do not work that may be your hardware?

---

### Post by Idlewild1888 on 2014-11-12
The problem is I don't get any tiny icons at the bottom of my screen!

I turn the Pc on, it is set to boot to USB and I am taken straight to the menu screen with nothing before it.

It looks like this except without the Fn key options at the bottom and then the e button doesn't do anything other than make the screen sort of refresh!

[IMG]http://cdn3.itzgeek.com/wp-content/uploads/2011/12/Ubuntu-11.10-CD-Options-.png[/IMG]

My hardware is fine, I have the same experience on both machines with different hardware set ups...one much more modern than the other. I have also tried various iso images and different derivatives of Ubuntu and get the exact same experience! I'm very confused.

---

### Post by grahammechanical on 2014-11-12
What you are seeing is not Grub therefore pressing "e" will not work. What you are seeing is the live session text menu. Grub is not used by the live session.

You should be able to press F6 and get Other Options and select from a menu or change the boot parameters of the live session. Look at this wiki page under the section Changing the CD's Default Boot Options. Go down to sub-section 6 - F6.

Now if the Functions keys (Fn or F1 to F12) do not work then perhaps it is because the keyboard is not being activated by the BIOS settings. My BIOS has a setting for Plug and Play OS and this is the description;

> When set to [No], BIOS configures all the devices in the system. When set to [Yes] and you install a Plug and Play operating system, the operating system configures the Plug and Play devices not required for boot.

If that setting is set to Yes, then the keyboard will not be active until the OS has loaded. But the live session loads instead of the installed OS. Perhaps the live session cannot activate Plug and Play devices. Certainly we have to choose either Try Ubuntu or Install Ubuntu before the lives session begins to investigate what hardware it is running on.

For similar reasons it is not possible to get to a Linux command line terminal at this stage because Linux has not been installed or loaded. By the way, Grub does not recognise Linux - Bash commands because it has its own set of special commands.  

Regards.

---

### Post by Idlewild1888 on 2014-11-13
Hi Graham,

Thanks for the clarification, that sheds some light on the direction I'm supposed to be heading in.

Unfortunately, I just cannot get into the advanced menu as there seems ot be no way of getting the function keys to, well, function! I don't seem to have any options like those you describe in your BIOS in mine and so there isn't really much I can change.

I'm thrown straight into the live session text menu and my only real option is to proceed with a normal boot to the live session or boot tio the installer, both of which, under normal circumstances give me the dreaded blank screen and I can proceed no further. Of course on my other windows 8.1 i7 machine, this isn't an issue as the video drivers load fine and I don't get the blank screen. Unfortunately the machine I need to get some linux distro or other running on is old and probably requires me to run nomodeset or some such.

I appreciate we are probably running out of options here, I just find it baffling that I can't seem to get into an advanced menu on any of the ISO that I have written to usb and it is really frustrating. I just need to get a web browser running in this machine haha I'm not asking for much. It used to run XP embedded but, unfortunately this is no longer an option either.

Any last suggestions would be most appreciated.

Thanks again!

---

### Post by Idlewild1888 on 2014-11-13
Is there any way I can make it boot to GRUB instead of the Live Session text menu?

I have followed the exact same steps as in [http://www.youtube.com/watch?v=FfEbsf06IwU](http://www.youtube.com/watch?v=FfEbsf06IwU) this video, but when they boot their usb stick from the BIOS, they get taken to GRUB ([http://youtu.be/FfEbsf06IwU?t=4m43s](http://youtu.be/FfEbsf06IwU?t=4m43s)) where as I am taken straight to the live cd text menu and have no way of getting to GRUB :-?

---

### Post by oldfred on 2014-11-13
I now install grub to flash drive, manually create my own grub.cfg and include extra boot parameters. That seems to boot directly into live mode where I can install from.

These all are examples of my install of grub to a flash drive.
 Multiple-Boot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

      
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

Examples of boot stanzas for different ISO.

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

My systems see flash drives as another hard drive, so examples for hard drive are similar.
Note: that drive & path are critical and flash drive's drive number if directly booted will be hd0 in all cases. But when installed it may be something else. If you use grub in another drive to boot then drive can vary.

---

### Post by Idlewild1888 on 2014-11-14
Really helpful thanks oldfred!

I did managed to get a bit further but ran into more issues related to video settings :(

I've all but given up although I'm planning on starting a thread to ask one final set of specific questions on video parameters, so maybe if you can see that you can offer some advice there too!

Thanks agin.

---

### Post by oldfred on 2014-11-14
Did you try the suggestion in post #4?
Directly adding nomodeset or even other settings to boot parameters.

---

