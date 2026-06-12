---
title: "Boot Ubuntu"
date: 2016-11-08
forum: Installation &amp; Upgrades
---

### Post by xhafa on 2016-11-08
Hello,
I have just installed ubuntu 16.04 on external driver but I cant boot it. 
I have windows 10 install on my hp elitbook.
Can someone help me?
Thank you

---

### Post by yancek on 2016-11-08
Can't help with the limited info you posted.  Did you have windows installed EFI?  Did you install Ubuntu EFI?  lGo to the site below on dual booting windows 10 and Ubuntu and compare the instructions to what you did.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If that doesn't help, go to the site below from the Ubuntu installation media and download and run the boot repair.  Select the options to Create Bootinfo summary and post a link to it here.  Do not try to make any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by RobGoss on 2016-11-09
Are you using the F-12 key to boot from the external hard drive? This will give you access to the external drive so your machine knows we're to boot from

---

### Post by oldfred on 2016-11-09
If HP was UEFI, you may have installed in UEFI mode to external.
But full install to external with UEFI does not correctly install grub.
Full install only installs grub to ESP - efi system partition on sda in /EFI/ubuntu.
HP does not like to boot anything but as it uses description as part of boot.

And external drives only boot from ESP on external drive from /EFI/Boot/bootx64.efi which is not normally created.
       Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244) 
            UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 
    
You do have to manually partition external drive with gpt partitioning and include the ESP - FAT32 formatted partition 200 to 500MB with boot flag.
       One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
            [http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by C.S.Cameron on 2016-11-10
My EliteBook, (8560w) sorta sucks at booting off USB drive also.
Boots faster and works better when plugged into USB2 slot than USB3 slot.
Not sure if the Ubuntu USB3 drivers work when booting an external drive.

On this work station, F12 is used for Network Boot, F9 is used for Boot device Options.

---

### Post by oldfred on 2016-11-10
Ubuntu USB3 drivers must be ok, as I UEFI boot flash drives from USB3 ports on two different systems. One Asus motherboard and the other Gigabyte.

---

### Post by xhafa on 2016-11-16
Hi,
I have just instal ubuntu on my external disk and when I want to boot it shows:
" error:attempt to read or write outside of disk 'hd0' 
  Enterng rescue mode...
  grup rescue>
"
On my laptop I have installed windows10.
My external disk is 160gb and I have 2 particions on it, one where I have my file and the other where is installed ubuntu.
Thank you

---

### Post by xhafa on 2016-11-16
Thank you all for your support.
I try to install again and follow some step from a tutorial and the the problems seem to be that I didn't create a particion from swap area.
Now when I try to boot it show :
"error:attempt to read or write outside of disk 'hd0' 
Enterng rescue mode...
grup rescue>
"
Can someone help?
Thank you again

---

### Post by sudodus on 2016-11-16
Welcome to the Ubuntu Forums :-)

We know too little about your computer and about what you have done so far. We can only guess, so please give us more information to help us help you!

1. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

2. Which version of Ubuntu are you trying to install?

3. Did you install from a DVD drive or a USB drive?

4. Which tool did you use to create an Ubuntu install drive?

---

### Post by slickymaster on 2016-11-16
Threads merged.

Please do not create duplicate threads, it dilutes the community’s efforts to provide support and causes confusion.

---

### Post by xhafa on 2016-11-16
I have a Elitebook 8470p with 8gb ram and i5cpu.
I installed ubuntu 16.04 from DVD drive. When i create partion on my external, I make 2 particions, at first I chose "swap area" and the other "ext4".
I have made some searching and most of than says that on bios should be a option "Boot Secure" which I have to disable but I cant find it on my bios

---

### Post by sudodus on 2016-11-17
Is this the graphics: Intel hd graphics 4000 1696MB ?

Ubuntu should work well with Intel graphics. But there were some issues with 16.04 LTS. The first point release contains a lot of bug-fixes, so I suggest that you download and try **Ubuntu 16.04.[COLOR="#cc0000"]1[/COLOR] LTS** ('amd64' alias the 64-bit version).

But if you have another graphics chip (nvidia or AMD/ATI/Radeon), you may need the boot option nomodeset, and after that install a proprietary driver.

Does the computer boot well from the DVD, 'Try Ubuntu'? See this link,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

-o-

Secure boot is only 'active' in UEFI mode, not in BIOS mode (sometimes called CSM). Are you booting and installing in UEFI mode or BIOS mode?

---

### Post by oldfred on 2016-11-17
If Windows is UEFI on gpt drive best to have external drive with gpt partitioning.
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

