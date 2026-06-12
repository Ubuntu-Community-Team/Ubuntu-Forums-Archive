---
title: "Install Error Ubuntu 12.10: Unable To Find A Medium Containing A Live File System"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by Loose2009 on 2013-02-16
Hi All,

I am new to Ubuntu. I decided to give it a test drive since I am not all the fond of Windows 8. I have a brand new system that I built and have been trying to install 12.10 (the 64bit version). There is currently no OS installed, nor have I been able to install/update device drivers as of yet.

System Specs
AMD FX-8350
GigaByte 970A-D3
G.Skill Ares 16Gb DDR-3-1600
Samsung 840 Series 250Gb SSD
Sapphire 2Gb Radeon 7850

I am using a USB stick to install Ubuntu as my optical has not yet arrived. I select "Install Ubuntu" and get the screen with Ubuntu on it and the scrolling dots. After that I always get this message:


BusyBox v1.19.3 (Ubuntu 1:1.19.3-7ubuntu1) built-in shell (ash) 
Enter &#8216;help&#8217; for a list of built-in commands.
 
(initramfs) Unable to find a medium containing a live file system.


I have tried different kernel boot options, and searched pretty extensively and have not found a solution. I've also used a couple different programs to create the bootable USB drive including the one posted on the tutorial on the Ubuntu site, with no luck. Any help would be much appreciated, as I would like to try the OS out.

---

### Post by kc1di on 2013-02-16
I've found this to work before. it may work for you;
```
Goto SATA Settings in your Bios and use AHCI instead of IDE.
```
Also usb 3.0 ports give trouble sometimes.

---

### Post by oldfred on 2013-02-16
+1 on kc1di suggestions.

Since it is a new system is it UEFI with compatibly mode or BIOS/Legacy/CSM?

Do you want the new UEFI or the known, but old BIOS install.

Also related is the choice of formatting of drive. If planning on Windows you have to use BIOS with MBR partitioning or UEFI with gpt partitioning. 
Ubuntu will install with the new gpt partitioning whether BIOS or UEFI, but needs an extra partition either way. bios_grub for BIOS or efi for UEFI booting.

---

### Post by Loose2009 on 2013-02-16
Tried changing the SATA settings to no avail, and I am already using USB 2.0 ports. 

I can use either UEFI or Legacy. I have tried booting with either option and end up with the same message.

---

### Post by oldfred on 2013-02-16
Then I would suspect that either download is not correct or install was not correct.

You can verify download
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
    
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
   
Some have better success with 
       [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by kc1di on 2013-02-16
I would go with Oldfred's suggestion of checking the download and
us unetbootin to make the usb stick.
Good Luck

---

### Post by Loose2009 on 2013-02-16
I have tried Unetbootin, LinuxLive USB Creator, and Universal USB from Pendrive Linux. I have booted all of those in both UEFI and Legacy. All give the same message.

As far as my Ubuntu download, it is directly from the Ubuntu's site. I would assume that would make it okay, correct? Though I will go ahead check that just to make sure.

UPDATE: Used MD5SUM and came up with different sums. So looks like you are correct. If I download from the same source would I come up the same problem or is this just some random error?

---

### Post by grahammechanical on 2013-02-16
I also built my own machine - 5 years ago. Until a few months ago I was able to run the live session for every Ubuntu from 7.04 to 12.10 but when I try with Raring Ringtail 13.04 I get that Busybox prompt as you do. The answer?

1) At the first purple screen press Enter
2) At the second (language screen) press Enter - English is the default.
3) Press F6 and from the menu select acpi=off and press Enter
4) Press Esc to close the menu
5) Put irqpoll in between initrd.lz and quiet splash in the boot parameter line.
6) Press F10 to boot.

That gets me and 13.04 to a live session. It might do the same for you and 12.10.

Regards.

---

### Post by oldfred on 2013-02-16
Sometimes is just happens that download is not good.

Do you know about zsync? With the alpha or beta the ISO is changing daily so we do not download the entire thing but just the changes.

Your local mirror has the zsync also.

sudo apt-get install zsync

change to the directory you have your iso in. I have mine in /home/fred/ISO

```
cd ISO
fred@A105-Precise:~/ISO$ zsync http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/12.04/ubuntu-12.04.2-desktop-amd64.iso.zsync
#################### 100.0% 211.3 kBps DONE     

reading seed file ubuntu-12.04.2-desktop-amd64.iso: **********

verifying download...checksum matches OK
used 728760320 local, fetched 0
fred@A105-Precise:~/ISO$ 

```You will have to find your local mirror. and change to exactly the name of the ISO you have. I had just downloaded 12.04.2 so I was able to run it against that as above.
Click thru to your nearest down load mirror.
[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

Change path to where yours is at.
This is a USA mirror fro 12.04.
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/12.04/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/12.04/)

---

### Post by Loose2009 on 2013-02-16
I downloaded a new copy, but this time tried the "ubuntu-secure-remix-12.10-64bit." Not sure if there's any difference besides the whole secure boot thing with Windows 8, but figured I'd try it anyways...Same outcome.

grahammechanical:
I am going to try to boot via UEFI, since I will probably eventually load Windows in that way when I get my optical drive in. As such, I am not sure how to implement what you suggest when booting in UEFI as it different.

oldfred:
I get what you are saying about zsync being able to update the file without downloading the whole iso. However, I am currently working from a windows machine, do you know how to this from windows? Also, would it necessarily matter if I have a slightly older verison of Linux, I would think that it should install regardless.

---

### Post by oldfred on 2013-02-16
I think zsync only works from Linux.

With UEFI you need 12.10, but they very new 12.04.2 has been updated to work with UEFI also. 

Some of the slightly older versions started to work with UEFI but there have been major updates with each version. So I cannot recommend any older versions for use with UEFI.

Windows has very specific partition requirements which you should plan for if dual booting with Windows and installing yourself.

You will not have the vendor recovery partition but should end up with all the others. The efi partition is used by all operating systems so only one is allowed.

       Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.

---

### Post by LosButcher on 2013-02-18
Sharing frustration:
I have been trying to fix this exact problem all weekend using different images on the USB stick. The I realized that it could't find the stick at all, so I gave up and dug up a writable DVD and burned the image.

Then I couldn't figure out how to get it to boot from the DVD so now I'm booting from the USB but installing from the DVD. Now it seems to install though, although my mousepad is not working.

Will report back in a little while when the install is done.

Edit: So everything seems to work fine :) Really glad to be out of that Windows 8 trap.

---

### Post by st4 on 2013-04-18
I'm having that problem, too.

---

### Post by mörgæs on 2013-04-18
You need to provide more information. 

Which hardware? 
Exactly which error?
What have you tried to solve it? 
Which results did you get?
- and so on.


[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by st4 on 2013-04-18
> **mörgæs said:**
> You need to provide more information. 

Which hardware? 
Exactly which error?
What have you tried to solve it? 
Which results did you get?
- and so on.


[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)I'm getting the "Busybox Unable to find a live file System" error message, and I have an HP Pavilion zd7160 laptop from 2003. The laptop also has a hardware problem, it shuts off when there is too much HD activity. That's why I wanted to try Ubuntu, to see if it would stay on longer with the less demanding OS than Windows XP.

I tried Puppylinux and it installed okay except for all of the missing icons and text.

Oh, and it's a 32 bit system.

And I'm installing from the DVD drive in the laptop.

---

### Post by matt1x on 2013-04-18
I had the same problem with my new Sony Vaio SVT1313 trying to install Ubuntu 12.10 64bit.

I though I tried everything until desperetaly plugged the usb stick to a USB3.0 port and got it working. UEFI is enabled.

-Matti

---

### Post by st4 on 2013-04-18
Maybe Xubuntu would be a better choice for my messed up laptop.

---

### Post by mörgæs on 2013-04-18
Most likely, and booting from USB is also a good idea, if your BIOS supports it.

---

### Post by st4 on 2013-04-19
> **mörgæs said:**
> Most likely, and booting from USB is also a good idea, if your BIOS supports it.I didn't know about Lubuntu, that one works pretty well on my laptop. Thnx for the tip.

---

### Post by mörgæs on 2013-04-19
You're welcome. Please pass it on.

---

### Post by st4 on 2013-04-19
> **mörgæs said:**
> You're welcome. Please pass it on.I will.

---

