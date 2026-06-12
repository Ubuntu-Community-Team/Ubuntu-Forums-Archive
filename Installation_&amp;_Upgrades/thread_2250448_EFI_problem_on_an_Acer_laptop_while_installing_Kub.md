---
title: "EFI problem on an Acer laptop while installing Kubuntu next to Windows 8"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by atti84it on 2014-10-28
I have an Acer Aspire E1-522 with Windows 8 preinstalled. I tried to install Kubuntu twice, and do boot-repair once but it keeps booting windows. This is exactly what I did:


[LIST=1]
[*]Installing Kubuntu as I was used to do a few years ago: resize win partition, create 2 new partitions (one for swap, one for / ), then do manual partition choice and assign / to the big new partition. This didn't work; it was booting windows.
[*]I read a lot about efi and learnt about this new crap technology; then I ran boot-repair first time; it failed and said to disable secure boot.
[*]I disabled secure boot and ran boot-repair again. It failed with "unable to mount /dev/sda3" error. This partition on gparted appears labeled as "Microsoft reserved partition" and is unknown type partition (color black)
[*]On [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) I read that if you do the manual partitioning ("Something else") you have to mount your efi partition on /boot/efi, while if you "Install Ubuntu alongside others" it chooses the correct settings; so I did this last "automagic" option... but nothing! still booting win8...
[/LIST]

What shall I do now?!

In case you need to know I have a AMD64bit processor. The kubuntu I was trying to install is the latest stable: 14.10 utopic plasma 4.

---

### Post by oldfred on 2014-10-28
From Boot-Repair run the summary report and post link:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

      [/URL]
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)


 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

 
    [URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by atti84it on 2014-10-29
Here is the summary report: [http://paste.ubuntu.com/8732064/](http://paste.ubuntu.com/8732064/)

I was using boot-repair for "saucy" version because there are not repositories for "utopic" ( [http://askubuntu.com/a/449836/11627](http://askubuntu.com/a/449836/11627) )

Also, for information, when I boot the liveusb it starts with efi screen (not bios/legacy/purple)

---

### Post by oldfred on 2014-10-29
I do not see anything specific wrong with your install.

Do you have secure boot on? But it looks like you have the signed versions of kernel installed so it should even boot with secure boot on. But there was  a bug where you could not boot Windows in secure boot mode from grub menu only from UEFI menu. Better to have secure boot off.

Can you boot ubuntu entry directly from UEFI menu? 
Or do you have a one time boot key often f12 or f10 but varies by vendor? And does it let you boot Ubuntu.

       [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

Different model Acer was able to rename bootx64.efi which is the hard drive boot entry to be grub and select hard drive in UEFI and boot that. Some vendors modify UEFI to only boot Windows entry.


 acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)

      
 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

---

### Post by atti84it on 2014-10-29
I have secure boot off.

I tried as you said: on startup press F12, then choose ubuntu... IT WORKS!!! It's not the best solution (I was expecting an old style grub, with 10 seconds timeout) but IT'S ENOUGH. I don't want to spend more time on it! thank you very much!

---

