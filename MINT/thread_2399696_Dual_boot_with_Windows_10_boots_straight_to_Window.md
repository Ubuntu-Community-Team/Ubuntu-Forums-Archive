---
title: "Dual boot with Windows 10 boots straight to Windows. No option for Ubuntu in BIOS"
date: 2018-08-28
forum: MINT
---

### Post by snathans on 2018-08-28
Hi, I'm new to Linux so any help is much appreciated.

I'm trying to dual boot Linux Mint 19 on an Acer Spin 5 laptop that came with Windows 10 OEM pre-installed. I used Mint's automatic "install alongside Windows" and I can see that it created a partition called /dev/sda5.

However, instead of booting into Grub my laptop boots straight into Windows Boot Manager. What's more, even when going into the BIOS boot order there's no option for Ubuntu.

This seems to be an issue with Acer laptops and I've tried the methods in this thread:
[URL="https://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot"]https://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot

[/URL]And yet on step 39, after pressing enter on "grubx64.efi" or "shimx64.efi" it just says "Null Character!!".

I've also tried all the steps in this:
[URL="https://www.lifewire.com/fix-uefi-bootloader-issues-when-dual-booting-2200655"]https://www.lifewire.com/fix-uefi-bootloader-issues-when-dual-booting-2200655

[/URL]And it still doesn't work. Here's my boot-repair log:
[http://paste.ubuntu.com/p/rcGCjCHr8r/](http://paste.ubuntu.com/p/rcGCjCHr8r/)

Thanks in advance for any help. Let me know if there's any other information I can provide.

---

### Post by jeremy31 on 2018-08-28
What is the result from the Mint Live USB for ```
efibootmgr
```

---

### Post by snathans on 2018-08-28
> mint@mint:~$ efibootmgr

 BootCurrent: 0001
 Timeout: 0 seconds
 BootOrder: 2001,0000,2002,2003
 Boot0000* Windows Boot Manager
 Boot0001* USB HDD: PNY     USB 2.0 FD
 Boot0002* USB HDD: PNY     USB 2.0 FD
 Boot0003* ubuntu

 Boot2001* EFI USB Device
 Boot2002* EFI DVD/CDROM
 Boot2003* EFI Network


When I change the order, it's reset the next time I boot.

---

### Post by yancek on 2018-08-28
Recent Acer computers require that you set "trust" somewhere in the BIOS so you will have to take a look at your BIOS and make that change.  Your efibootmgr output clearly shows an ubuntu option.  I don't use Acer myself so can't give you any more details.

---

### Post by oldfred on 2018-08-29
Some more examples of trust setting.
But many with Acer have also had to update UEFI from Acer to have it work correctly.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392

      [/URL] Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
    [URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by littlefoot505 on 2018-08-29
Dang. I just had to buy a new computer, and this makes me glad I didn't get an Acer. I had no issues at all with Ubuntu on my HP, and I did have issues booting into Q4OS, but it was noting that disabling Safe Boot or whatever setting in the BIOS doesn't allow obscure OS's couldn't fix.

---

### Post by oldfred on 2018-08-29
From what I have seen, Acer's trust setting is relatively easy, once you know you have to do it.

Many other systems violated UEFI spec that says NOT to use description and only valid boot is "Windows Boot Manager". And then we have to install, modify or change various settings & files to make system work.

If an HP worked, that is new as many HP only booted Windows and needed one of the several work arounds.

---

### Post by snathans on 2018-08-29
Thanks for the suggestions, but when I try to set the trust settings it just says "Null Character!!    " and doesn't do anything.
I'm going to try reinstalling Mint to my USB. Maybe it should be MBR and I did GPT, or vice versa?

---

### Post by oldfred on 2018-08-29
If UEFI, it should be gpt.
And Windows is very particular about partitioning. It only uses MBR with BIOS boot and gpt only with UEFI boot. All new systems since Windows 8 was released are UEFI.
Ubuntu should be in same boot mode as Windows.

---

