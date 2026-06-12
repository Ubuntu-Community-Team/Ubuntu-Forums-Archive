---
title: "Dual-Boot Ubuntu and WIndows"
date: 2016-07-03
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2016-07-03
Hi all.  I have a fairly new PC with Windows 10 on it.  I want to install Ubuntu 15.10 and configure it for dual-boot.  I created a free disk partition from the Windows side with 500 GB of space.  That is where I want to install ubuntu.  I rebooted the machine with an ubuntu install flash drive.  However, It complains about UEFI mode.  The message is something like this

```
This machine's firmware has started the installer in UEFI mode
but it looks like there may be existing operating systems already installed
using "BIOS compatibility mode".  If you continue to install Debian in UEFI
mode, it might be difficult to reboot the machine into an BIOS mode operating
system later.
```

I tried the search engines, but I could not find this error message.  I found a few web pages with Dual-Boot instructions, but I don't know if they apply to me because they don't mention the above warning.  So, what should I do?

Also, just out of curiosity, I tried to proceed anyway and I got as far as the disk partitioning section of the install process (I did not click 'install now' after that).  That page listed the existing Windows partitions, as well as the free 500 GB partition.  However, there was no way to partition the 500 GB space into smaller partitions (for /, /usr, swap, etc).  How should I proceed once I get to that step?

---

### Post by yancek on 2016-07-03
Don't bother creating multiple partitions as it will just further complicate things for a new user.  You can always create a separate data partition by shrinking the root partition after installing.  If you have windows 10, you need to determine whether it is an EFI install or an MBR install and install Ubuntu in the same manner.  Check the Ubuntu documentation at the link below for more information.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also, I wouldn't bother with 15.10 as support for it will end this month.  14.04 or 16.04 would be better options.

---

### Post by pfeiffep on 2016-07-03
I suggest reading here ... [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by UserJB on 2016-07-03
Yes, I've been reading the webpage on UEFI at help.ubuntu.com.  However, it doesn't explain how to tell if Windows 10 is an EFI or MBR install.  It only explains that for Windows 8, and those instructions don't work for Windows 10.  I need to know if my Windows 10 install is EFI or MBR.

UPDATE: Okay. my Windows 10 used BIOS for booting.  How do I install Ubuntu in BIOS mode?   The webpage on UEFI at help.ubuntu.com seems to only describe installing Ubuntu in EFI mode.  Should I go into the firmware and tell it to boot in BIOS mode?

---

### Post by UserJB on 2016-07-03
Also, why does support for 15.10 end this month?  It's only eight months old.  I'm fairly new to ubuntu.  Is each release only supported for eight months?

---

### Post by UserJB on 2016-07-03
My PC already has Windows 10 installed, and it boots in Legacy (BIOS) mode. I want to also install Ubuntu (15.10).  In order to make it dual-boot with the Legacy-Mode Windows, I need to install Ubuntu in Legacy mode.  But I don't know how to do that.  I read the UEFI article at help.ubuntu.com. but it doesn't explain how to force a Legacy-mode install.  It only says that you have to install Ubuntu in Legacy mode if your existing Windows is Legacy mode.

Does anyone know how I can force Ubuntu 15.10 to install in legacy (BIOS) mode?

Alternatively, can I easily convert my Windows 10 to boot in UEFI mode?  I know that's not within the scope of this community, it would also solve the problem because I could then install Ubuntu in UEFI mode.

---

### Post by grahammechanical on 2016-07-03
I do not have a UEFI boot system motherboard but I do believe that you enter the UEFI settings utility and change a setting. See the section: Set up the firmware in UEFI or BIOS/CSM/Legacy mode.

> Some recent computers (>2011) allow you to set up  the computer to boot either in UEFI mode or in BIOS/CSM/Legacy (not-EFI)  mode. The way to adjust this setting depends on the computers, but  generally this setting is located in the "Boot order" tab of the BIOS  (to access the BIOS screens, it is generally necessary to press a key  during the PC startup). It can also often be set on a per-boot basis by  hitting a function key (F8 and F10 are common choices) soon after you  power on the computer. 


Note:  Some UEFIs (e.g. American Megatrends' "Aptio", found on the Asus  vivobook series) call Legacy mode "Compatibility Support Module" or  simply "CSM". 


Remark: Some UEFIs enable one to set up the boot mode for the optical drive separately from the boot mode for the HDD.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by pfeiffep on 2016-07-03
[SIZE=3]Here's a quote from ... [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)[/SIZE][h=2]Case when Ubuntu must be installed in UEFI mode[/h] Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  

[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*][COLOR=#b22222][SIZE=5]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. [/SIZE][/COLOR]


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]

---

### Post by UserJB on 2016-07-03
Yes.  I agree.  I have to install in legacy mode because the existing Windows 10 installation was installed in legacy mode.  I said that in the first three sentences on my post.

The question is this: How do I install Ubuntu in Legacy Mode?

---

### Post by UserJB on 2016-07-03
I have already read the article at help.ubuntu.com/community/UEFI.   I'm trying to figure out how to install Ubuntu in Legacy Mode.  I tried everything I can think of in the PC firmware (Gigabyte UEFI Dual BIOS), but there does not appear to be an option to force the PC to boot off of the Ubuntu flash drive in Legacy mode.

---

### Post by grahammechanical on 2016-07-03
> Also, why does support for 15.10 end this month?  It's only eight months  old.  I'm fairly new to ubuntu.  Is each release only supported for  eight months?

The Ubuntu release schedule = a Long Term Support (5 years) release every 2 years and a 9 months supported release every six months during the 2 year period. The reason? Cost. Both in the hardware required to run quality assurance tests and the salaries of Canonical employees maintaining Ubuntu.

Would a moderator please merge these two threads as they seem to be covering the same situation?

[http://ubuntuforums.org/showthread.php?t=2329607](http://ubuntuforums.org/showthread.php?t=2329607)

---

### Post by UserJB on 2016-07-03
For future users, I'm posting my solution to forcing Ubuntu to boot in Legacy (BIOS) mode.

When I booted the PC, I immediately went into the firmware and tried every option, but I could not force the PC to boot off the USB flash drive in legacy (BIOS) mode.

Then, I tried the Boot Menu (as opposed to the full firmware menu) and that showed me several options for the USB flash drive.  Some options had a UEFI in front of the name.  Don't use that.  Other options had no UEFI in front of the name.  The first one booted the machine into Windows 10, even though the option claimed it was booting off the USB flash drive.  That didn't help.  The second option gave me an error and a prompt that looked like this

> Missing parameter in configuration file
keyword: path  gfxboot.c32 not a COM32R image

At the prompt for this, hit the TAB key.  Then type 'live-install', hit return, and then the Ubuntu boot install will happen in legacy (BIOS) mode.

---

### Post by wildmanne39 on 2016-07-03
Please do not post duplicates, it dilutes community effort. Threads merged

---

