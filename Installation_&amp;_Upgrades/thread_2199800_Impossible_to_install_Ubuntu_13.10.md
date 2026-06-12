---
title: "Impossible to install Ubuntu 13.10"
date: 2014-01-15
forum: Installation &amp; Upgrades
---

### Post by gerapa on 2014-01-15
Hello all, 

I cannot install Ubuntu, and don't find any solution. 

I can run a live USB or CD, and Ubuntu seems to work well. Problems begin when i try to install Ubuntu. Installation is going well until i want manually create partitions. I can choose the size of / and /home, but when i try to check the little box in front of them to format the partitions, the installation freezes and i cannot apply the changes. 

I have verifyied md5 sum and have tryied with an USB stick and a CD. Linux mint 16 has been installed without problem. 

Do you know why that happens, and how to solve that ? 

Thanks in advance for the help.

---

### Post by mastablasta on 2014-01-16
strange, you could try preformating them by running gparted in liveboot and then just perform the install without formating the drive.

---

### Post by chkneater on 2014-01-16
yeah, preformat them with gparted and set your mount and swap points and whatever partitions you want to add.  Do this one process at a time though.

After you have the partitions how you want and you've set your mount points and boot flag, I have been able to use the desktop Icon to install as long as everything else was out of the way.  

When the prompt asks if "you want to erase *** or install alongside ***", at the very bottom choose "something else".  This lets you be absolutely sure that the OS only installs to the partition you want.  From there it's pretty self explanatory.

---

### Post by gerapa on 2014-01-16
Thank you very much for your help. I'll try that.

---

### Post by Larry_Penny on 2014-01-16
I have tried to run Live DVD on Kubuntu and Linux Mint KDE 13.10 and get the same results a blank screen. I get to 2nd menu/screen with Start..... options if I click on the Backspace key during countdown.  I have also click on Tab during 2nd menu/screen and tried to add one of the modset=0 then when I Click on Ctrl+X it will not do anything. Clicking on Enter key is the only thing that will start the boot and then Blank screen with flashing cursor

I am running:
[SIZE=2]Windows 8.1 Professional (x64) (build 9600)
Install Language: English (United States)
System Locale: English (United States)
Installed: 10/18/2013 3:24:03 PM
Boot Mode: BIOS [/SIZE]
 [SIZE=2]2.80 gigahertz AMD Phenom II X6 1055T
768 kilobyte primary memory cache
3072 kilobyte secondary memory cache
6144 kilobyte tertiary memory cache
64-bit ready
Multi-core (6 total)
Not hyper-threaded
[SIZE=2]Board:  890FXA-GD70 (MS-7640) 1.0
Bus Clock: 200 megahertz
BIOS: American Megatrends Inc. V1.15 10/31/2012[/SIZE][/SIZE]

 I was so in hopes that linux is finally to the point where most could install it and start learning how to use it.

Thanks for any help

---

### Post by Bucky Ball on 2014-01-16
Add 'nomodeset'. I am presuming you have it installed on the hard drive and are talking about booting to the grub menu with a list of cursors?

---

### Post by Bucky Ball on 2014-01-16
Add 'nomodeset'. I am presuming you have it installed on the hard drive and are talking about booting to the grub menu with a list of cursors? If so, 'e' to edit the kernel line and add 'nomodset' after 'quiet splash' or 'splash quiet'.

If you are still at the booting from the install media stage, when you get to 'Try Ubuntu' 'Install Ubuntu' hit F6 and choose 'nomodeset' from the popup list.

[QUOTE=Larry_Penny]I was so in hopes that linux is finally to the point where most could install it and start learning how to use it.[/QUOTE]

It is. ;)

---

### Post by mastablasta on 2014-01-17
linux is easy to install (especially if it's not a dual boot). also if Mint 16 works well use that instead. just use what works... Mint is a very good distro. ;-)

---

### Post by Larry_Penny on 2014-01-17
It is. ;)[/QUOTE]

[QUOTE=Bucky Ball;12902470]Add 'nomodeset'. I am presuming you have it  installed on the hard drive and are talking about booting to the grub  menu with a list of cursors? If so, 'e' to edit the kernel line and add  'nomodset' after 'quiet splash' or 'splash quiet'.

If you are still at the booting from the install media stage, when you  get to 'Try Ubuntu' 'Install Ubuntu' hit F6 and choose 'nomodeset' from  the popup list.

Here is the steps I have taken/done.
I have downloaded and burned linuxmint-16-kde-dvd-64bit.iso
I have opened the DVD and it does show many folders and files.
I have put the DVD disk in my DVD drive and restarted my 
computer.
I have tried to Boot the LiveDVD and I end up with a Blank white 

screen with a blinking cursor. I have not gotten to the screen 

where you have a choice to install. I only get to the screen in 

Linux Mint where you click on "Start Linux Mint".
When I click on "Start Linux Mint" a few seconds later I end up 

with a Blank White Screen with blink cursor. 
I have also tried this with Kubuntu 13.10 and the results is the 

same. I need help getting past the Blank screen.

---

### Post by Larry_Penny on 2014-01-17
I have now downloaded Ubuntu 13.10, burned using ImgBurn. After setting BIOS to boot using DVD I restart computer and now I go directly to Blank screen with flashing cursor. I do not get to the Welcome screen. Is there something in Windows 8.1 that is not allowing Linux to boot? I have regular BIOS.

---

### Post by Bucky Ball on 2014-01-17
Probably explains it. Did it come preinstalled on the machine? If so, it is an EFI install on an EFI disk with secureboot and fastboot enabled. 

You need to boot to Win8 and switch off faststart, get into the BIOS, leave the disk as UEFI, switch off fastboot and secureboot. Boot the Ubuntu install media. If you can now install ...

When you get to the partitioning section of the install, choose 'Something Else' and manually partition. Win8, if it is booting in EFI, will have created an EFI partition. Grub goes there, but as you are installing Ubuntu in EFI mode, it should see that partition and install grub there 'automagically' without you doing anything. (Incidentally, Ubuntu may not label the EFI partition but it should be a small partition somewhere between 100-500mbs.)

---

### Post by Larry_Penny on 2014-01-17
> **Bucky Ball said:**
> Probably explains it. You never mentioned Win8. Did it come preinstalled on the machine? If so, it is an EFI install on an EFI disk with secureboot and fastboot enabled. 

You need to boot to Win8 and switch off faststart, get into the BIOS, leave the disk as UEFI, switch off fastboot and secureboot. Boot the Ubuntu install media. If you can now install ...

When you get to the partitioning section of the install, choose 'Something Else' and manually partition. Win8, if it is booting in EFI, will have created an EFI partition. Grub goes there, but as you are installing Ubuntu in EFI mode, it should see that partition and install grub there 'automagically' without you doing anything. (Incidentally, Ubuntu may not label the EFI partition but it should be a small partition somewhere between 100-500mbs.)

Hi Bucky Ball,

Back on Post #5 I gave full description. Where I am confused is my motherboard does not have UEFI. So Does this still apply the fastboot and secureboot? I will boot into my BIOS and see if there is any way to turn it off and get back
Thanks

---

### Post by Larry_Penny on 2014-01-17
> **Bucky Ball said:**
> Probably explains it. Did it come preinstalled on the machine? If so, it is an EFI install on an EFI disk with secureboot and fastboot enabled. 

You need to boot to Win8 and switch off faststart, get into the BIOS, leave the disk as UEFI, switch off fastboot and secureboot. Boot the Ubuntu install media. If you can now install ...

When you get to the partitioning section of the install, choose 'Something Else' and manually partition. Win8, if it is booting in EFI, will have created an EFI partition. Grub goes there, but as you are installing Ubuntu in EFI mode, it should see that partition and install grub there 'automagically' without you doing anything. (Incidentally, Ubuntu may not label the EFI partition but it should be a small partition somewhere between 100-500mbs.)

I just check my BIOS and there is no Faststart or SecureBoot. I don't know what else to do other than pull my c: drive and install another drive to use only for Linux. I still may have the same problem and if I can't get Linux to install I sure can't run it.

Waiting for another idea.

---

### Post by chkneater on 2014-01-17
No, Windows doesn't have priority over BIOS settings...  This happens sometitmes, it sounds like you just had a couple of bad burns.  When you download the ISO to burn check the MD5 sum (there's plenty of text on how to do this) and be sure to burn your ISO at the LOWESt possible speed if the MD5 is correct.

Also., have you checked to see if the LiveDVD boots in another windows machine?

Also another option that works in other circumstances is 'grub-imageboot' you can d/l with the livedvd and copy to your /etc/grub file and your root file.

---

### Post by Larry_Penny on 2014-01-18
> **chkneater said:**
> No, Windows doesn't have priority over BIOS settings...  This happens sometitmes, it sounds like you just had a couple of bad burns.  When you download the ISO to burn check the MD5 sum (there's plenty of text on how to do this) and be sure to burn your ISO at the LOWESt possible speed if the MD5 is correct.

Also., have you checked to see if the LiveDVD boots in another windows machine?

Also another option that works in other circumstances is 'grub-imageboot' you can d/l with the livedvd and copy to your /etc/grub file and your root file.

The burn is good. I have an old MSI-1036 notebook running Windows 7 that  the Linux Mint 16 would load and run as LiveDVD. I have just now finished  installing it on the HDD. 
My desktop has a MSI 890 fxa gd70 motherboard and I  ran MSI Live Update 5 and all drivers are up to date including BIOS. So  unless someone has another idea on how to get Linux Mint to run as  LiveDVD or to be installed then I guess it has to do with Windows 8.1.  Windows 8.1 has a software bug that causes the computer to freeze for no  reason and may just restart or you may have to warm boot. This will  happen anywhere to several times a day to once a week. I would reinstall  Windows 8.0 if it did not take many hours to get all software loaded  that I use. 

How do you d/L with LiveDVD if I can not get the LiveDVD to load and run? Then I don't understand where to copy /etc/grub file? Does anyone know how to use EasyBCD to set a dual boot and force Linux Mint 16 to load and run?

I was hoping to be able to install Linux on another  drive and slowly get it running with all my software then switch to  Linux. So it looks like I may have to dual boot windows 8.1 with Windows  7 then install Linux Mint on its own drive with Windows 7.

---

### Post by Bucky Ball on 2014-01-18
Just to reiterate. If Win8 is installed in EFI mode, Ubuntu MUST be installed that way for a smooth ride and you MUST choose 'Something Else' at the partitioning section.

If Win is installed in EFI (which Win8 probably is) and you are attempting to install Ubuntu in non-EFI (Legacy) then that's your issue I'd think. The Ubuntu install will NOT see the Windows partitions, or in fact anything that was installed in EFI, and will treat it as an empty drive and use the whole thing, wiping Win in the process.

---

### Post by Larry_Penny on 2014-01-18
> **Bucky Ball said:**
> Just to reiterate. If Win8 is installed in EFI mode, Ubuntu MUST be installed that way for a smooth ride and you MUST choose 'Something Else' at the partitioning section.

If Win is installed in EFI (which Win8 probably is) and you are attempting to install Ubuntu in non-EFI (Legacy) then that's your issue I'd think. The Ubuntu install will NOT see the Windows partitions, or in fact anything that was installed in EFI, and will treat it as an empty drive and use the whole thing, wiping Win in the process.

When you use EFI do you mean  *Extensible Firmware Interface? *If so my computer motherboard does not have a choice of UEFI or BIOS. I only have regular BIOS setup no other option. Please explain what you mean by "installed in EFI or non-EFI. What I have tried to explain is my computer will not even allow Linux to start up. Until Linux is started and you get to a screen to where you have a choice of Try or Install Linux has not loaded yet so My computer will not do anything other than give a blank screen.

---

### Post by gerapa on 2014-01-19
Hi all, 

I have finally been able to install Ubuntu. I have run gparted from live USB like suggested by Mastablasta and Chkneater to preformat the HD. I  have seen a message mentionning a problem with GPT Table. I have answered "no" when  asked if it was GPT table. So installation have been possible. 
Thanks again, you've been very helpful.

---

### Post by Bucky Ball on 2014-01-19
Please mark as solved by following the instructions in my signature so your thread may continue to help others. ;)

Enjoy!

---

