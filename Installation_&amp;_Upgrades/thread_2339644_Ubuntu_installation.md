---
title: "Ubuntu installation"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by marco139 on 2016-10-11
I have tried to install ubuntu.
All seems to work fine, until "Looking for other operations systems".


ubuntu ubiquity: find: '/toget/boot/efi/... Input/output error


ubuntu kernel: FAT - fs (sda2): error invalid access to fat (entry 0x...)


ubuntu kernel: FAT - fs (sda2): error invalid access to fat (entry 0x...)


and then the same loop. 


I have an HP laptop with WINDOWS 10 (I have disabled both the fast boot option and the secure boot one)


Thank you in advance

---

### Post by RobGoss on 2016-10-11
Your questions is a bit confusing please clarify what the problem is so we can help you

---

### Post by marco139 on 2016-10-11
I have tried to install ubuntu with a USB stick. At a certain point, the installation process goes into a loop (the one mentioned in the first point). As a result, I need to power off my laptop.

---

### Post by RobGoss on 2016-10-11
In order to help you we need to know a few things about your machine and hardware 

What are the specs for your machine Ram, Graphic card, so on

How did you try to install Ubuntu USB or DVD I know you mentioned USB how did you create it?

What distribution are you trying to install ?

Is your machine UEFI / Legacy / BIOS ?

---

### Post by marco139 on 2016-10-11
Thank you for your help

**A**

RAM: 8 gb

PROCESSOR: Intel(R) Core(TM) i-5-3230 M CPU @2.60 GHz 2.60 GHz

SYSTEM TYPE: 64-bit operating system, x64-based processor

GRAPHIC CARD: Intel(R) HD Graphics 4000, AMD Radeon HD 7600M Series

DISK SITUATION 

DISKPART> list disk


  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
* Disk 0    Online          465 GB   181 GB        *

 DISKPART> list partition


  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary            399 MB  1024 KB
  Partition 2    System             260 MB   401 MB
  Partition 3    Reserved           128 MB   661 MB
  Partition 4    Primary            185 GB   789 MB
  Partition 5    Recovery           898 MB   186 GB
  Partition 6    Primary             97 GB   186 GB


I want to install UBUNTU on those 181.20 gb unallocated.

[B]B
[/B]
I created my bootable USB drive with rufus. The distro is ubuntu-16.04.1-desktop-amd64

[B]C

[/B]My boot environment is EFI.

---

### Post by RobGoss on 2016-10-11
When dual booting and using UEFI you are going to have to install Ubuntu is the same way UEFI 

Turn off** secure boot** and disable** fast startup**

Then put the USB in your machine and begin the installation when you see the option to install along side Windows choose that option, unless ýou want to create another partition with a pacific amount of space

I'm on my mobile so I don't have all my notes with me...

---

### Post by marco139 on 2016-10-11
dual boot with Windows 10.

---

### Post by marco139 on 2016-10-11
*Turn off secure boot and disable fast startup*

Already done.

[I]When dual booting and using UEFI you are going to have to install Ubuntu is the same way UEFI 

[/I]
How can I do that ?


Anyhow, the installation works fine, until the step, which comes pretty at the end, mentioned in the first post. Is there a way to skip it?

---

### Post by RobGoss on 2016-10-11
This might help you with UEFI it explains in detail 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I'm not sure what you mean at the end are you referring to choose along side Windows? And are you even seeing this option

What is the branday name for your machine so new machines are harder to install Ubunt so it also depends on what brand you have / model  /  Dell, Acer, HP  so on

---

### Post by marco139 on 2016-10-11
Ok. I will read it.

[I]choose along side Windows

[/I]Yes, that is what I have chosen. Of course, in order to show you my disk partitions, I deleted the partitions that Ubuntu has created during the installation process.

---

### Post by Bucky Ball on 2016-10-11
You should be using the 'Something Else' option when you get to that part of the install, not 'Install alongside'. That's problematic. Manually partition the drive with 'Something Else'. [This link will explain the 'Something Else' install]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"). Windows will have an EFI partition already so you don't need to create another. Just leave whatever existing Windows (NTFS and FAT) partitions that already exist alone.

To install Ubuntu in UEFI you need to choose the USB device with [UEFI] next to it as first boot device in BIOS or hit F12 and that should get you to a boot device list where you can choose it from there. You should see two entries for the USB, one without UEFI next to it and one with. 

Note: You should be using the AMD64bit version of Ubuntu or its flavours to use UEFI, not the 32bit version. The AMD64bit is for both Intel and AMD processors.

---

### Post by marco139 on 2016-10-11
I am pretty sure that I am installing Ubuntu in the UEFI mode.

---

### Post by Bucky Ball on 2016-10-11
Please re-read my last post. I hadn't finished. :)

We need 'positive' not 'pretty sure'. :)

---

### Post by RobGoss on 2016-10-11
If you're choosing alongside Windows then Ubuntu will take care of any partitioning you will also be able to give the partition size at that point by sliding the arrow  to the correct partition size this will help you balance the amount needed for the new partition for Ubuntu

I'm not sure why you had to delete any partition 

You can also create a partition using Windows with unallocated space then run the live USB installer and choose that's unallocated space to install Ubuntu this gives you more control over the disk size. Just a suggestion

---

### Post by marco139 on 2016-10-11
@Bucky Ball
My version is [COLOR=#000000]ubuntu-16.04.1-desktop-amd64. 

Is it OK?[/COLOR]

---

### Post by Bucky Ball on 2016-10-11
Yep, that's the one. Are you ticking 'Install proprietary drivers' and 'update during install' during that part of the install? If so, don't. You can do that later as it can cause issues when done during install. (Plus you can end up with a bunch of stuff you don't need/want).

Just to confirm: the install runs fine and then when you get to 'Identify other operating systems' it hangs or can't find one? You're saying this happens *at the end* of the install? Doubt if you would have gotten that far if this was the case, but you have booted into Windows prior to the install and made sure it is not in hibernate? As in, when you shut it down it actually hibernates the drive (thus locking it and hiding Windows, and generally the drive, to any other OS).

---

### Post by marco139 on 2016-10-11
Now I will redo the installation with your suggestions and I will report you again in case of errors.

[I] it hangs or can't find one

[/I]It just says "fat-fs (sda2): invalid access to fat. And then it goes on forever trying to access the sda2. 

[I]but you have booted into Windows prior to the install and made sure it is not in hibernate?

[/I]No, I started the installation from the BIOS.

---

### Post by Bucky Ball on 2016-10-11
You need to boot to Windows and switch hibernation off. This error message

"fat-fs (sda2): invalid access to fat."

... suggests to me that the install can not access the EFI partition (which is the only FAT partition you probably have on the drive). This suggests Win has it locked. Some manufacturers make it very difficult and you need to jump through hoops to get (their mostly outside the standard) custom EFI setups to work.

You gave a description of your machine before. A desktop, yes? Could you boot to the BIOS and see what BIOS and version it is, please? The make of your motherboard would also be helpful if you know it.

---

### Post by RobGoss on 2016-10-11
You should also have a backup disk for Window's just incase something goes wrong I see a lot of new user wipe their entire systems out trying to dual boot it's better to safe then sorry

---

### Post by marco139 on 2016-10-11
The same problem, again.

My PC is a laptop.

>wmic bios get smbiosbiosversion
SMBIOSBIOSVersion
F.25

>wmic baseboard get product,Manufacturer,version,serialnumber
Manufacturer     Product  SerialNumber    Version
Hewlett-Packard  183E     PCSCN018J3Y6V8  56.32

I have also made a video, so that you can understand the problem better :)

[https://www.youtube.com/watch?v=mzp2RWpYC70](https://www.youtube.com/watch?v=mzp2RWpYC70)

---

### Post by RobGoss on 2016-10-11
I'm not really sure what happen at the end of that video it looks as though it was installing unless I miss something

---

### Post by marco139 on 2016-10-11
No, at the end of the video there's that loop I was talking about.

---

### Post by Bucky Ball on 2016-10-11
> **marco139 said:**
> No, at the end of the video there's that loop I was talking about.

+1. Did a search for that error and could find not much but [I did find this]("https://ubuntuforums.org/showthread.php?t=2301830&p=13387372&viewfull=1#post13387372"). Apart from that, few other ideas at this point, sorry.

Doubt you'd need to reinstall Windows, but perhaps try updating it then try again. As I mentioned, the EFI partition I think is the only FAT partition on there, so not being able to access that seems to be it. But then, the install USB is FAT also and maybe there's a damaged block or two on that. 

Have you tried different install media, another USB dongle or a DVD? Did you do a MD5SUM check on the install media? At the opening options when you boot from the USB, you should see something like 'check install media for defects'. Try that.

Have you selected the 'Try Ubuntu' option? If so, does that take you to a desktop and you can use Ubuntu fine? If you haven't tried that, please do and report back.

---

### Post by marco139 on 2016-10-11
Yes, Right now I am posting this message using the live distro.
I have also tried with a DVD, but the problem is the same

---

### Post by RobGoss on 2016-10-11
I know you mentioned something about the installation looping but is it just installing with out stopping?

---

### Post by marco139 on 2016-10-12
Well, yes it does not stop. But it gives the error message over and over again.
Anyhow, today I will perform a clean installation of Windows and report you back.

---

### Post by RobGoss on 2016-10-12
Was Windows working correctly before you tried installing Ubuntu? If it was I don't believe this issue is with Windows they are to totally different operating system 

It seems extreme to have to reinstall Windows not knowing what's causing this isses with Ubuntu

---

### Post by marco139 on 2016-10-12
@RobGoss Windows was working correctly

Wonderful! I have reinstalled Windows with the media creation tool ([https://www.microsoft.com/de-de/software-download/windows10](https://www.microsoft.com/de-de/software-download/windows10)). I have done a clean installation of w, deleting all the recovery partions that were created during the updates and removing all the pre-installed apps. 
And now everything works. Thank you!

---

### Post by RobGoss on 2016-10-12
> **marco139 said:**
> @RobGoss Windows was working correctly

Wonderful! I have reinstalled Windows with the media creation tool ([https://www.microsoft.com/de-de/software-download/windows10](https://www.microsoft.com/de-de/software-download/windows10)). I have done a clean installation of w, deleting all the recovery partions that were created during the updates and removing all the pre-installed apps. 
And now everything works. Thank you!

Were you able to install Ubuntu also you mentioned everything is working correctly does that include  Ubuntu?

---

### Post by marco139 on 2016-10-12
> **RobGoss said:**
> Were you able to install Ubuntu also you mentioned everything is working correctly does that include  Ubuntu?

Yes, of course :)

---

### Post by RobGoss on 2016-10-12
Glad  everything work out with the installation if your issue was solved would you mind marking this post as solved. You can do this by using the **Thread tools** tab from the drop down menu at the top of this post. Thank you

---

### Post by Bucky Ball on 2016-10-12
Excellent news, well done and thanks for marking as solved.

Enjoy. ;)

---

