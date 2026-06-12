---
title: "Installation questions re: HP Win8 laptop"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2013-12-29
So I bought my wife a new HP 2000 laptop with Windows 8 installed. She's been accustomed to ubuntu 12.04 and I wouldn't think of trying to adapt her to Windows - she'd probably have a virus on it the first day. So my intention was to install ubuntu on it.

When I ran the installation media (12.04.3 64 bit), all I saw was a black screen, so thinking there was some incompatibility (there really wasn't, the stupid thing just came up with the brightness turned all the way down), I called HP tech. support. They told me I had to turn off secure boot and enable legacy support. So I did that and got the same result. Then I stumbled on the brightness thing and proceeded with installation. All was fine until I booted - it would only boot into Windows. Further research yielded a way into ubuntu, but only after booting into Windows! So now I have some questions which also might help others:

1. Should I really have installed ubuntu with secure boot off and legacy support enabled? Is that the source of my problem?
2. If not, can I reinstall with the original bios settings?
3. Can I use some boot manager (grub, elilo, etc.) to create a bootable usb stick that will boot into my HDD installed ubuntu?
4. Would removing Windows help, and if so, could I later restore it from the restore partition?
5. Perusing the HP documentation, I noticed a reference to models with linux installed. Any idea where to get such an animal?

---

### Post by mettlewk on 2013-12-29
How did you get into Ubuntu after going into Windows.

I had Ubuntu working on my HP and then last night while working on bookkeeping in Win8 (one of two legacy programs I need Win. for) I got a message from HP saying they had an Urgent Bios upgrade.  I allowed it to install..
I tried booting into Ubuntu 12. after that and got error messages such and such a call was disabled by the Bios... over and over again. then black screen.  I tried going in to the Bios and resetting the boot order function 10, then booting from the install CD I used when I successfully installed the system a month ago.... 
It refuses to boot from the CD.

HP hacked the Bios so that Ubuntu no longer runs on my machine.

---

### Post by oldfred on 2013-12-29
@bilkay
Best to backup efi partition and Windows.
Then post this:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

@mettlewk
My BIOS updates have always reset BIOS to defaults. Probably HP did the same with your UEFI. So you need to turn secure boot off, turn fast boot off and see it then it shows a ubuntu entry in UEFI boot choices or one time boot key.

If secure boot is on and you have installed Ubuntu in UEFI but not secure boot or installed in BIOS mode, those will not be shown as boot options. Only secure boot options are shown with secure boot on.

---

### Post by bilkay on 2013-12-30
> **mettlewk said:**
> How did you get into Ubuntu after going into Windows.

I have to go to shutdown from Windows, then click on "Restart" with the shift key held down. That give several options, one of which is something like "Boot from device". I click on that and it presents another page with "Ubuntu" as an option.

> **mettlewk said:**
> I had Ubuntu working on my HP and then last night while working on bookkeeping in Win8 (one of two legacy programs I need Win. for) I got a message from HP saying they had an Urgent Bios upgrade.  I allowed it to install..
I tried booting into Ubuntu 12. after that and got error messages such and such a call was disabled by the Bios... over and over again. then black screen.  I tried going in to the Bios and resetting the boot order function 10, then booting from the install CD I used when I successfully installed the system a month ago.... 
It refuses to boot from the CD.

HP hacked the Bios so that Ubuntu no longer runs on my machine.

Wow! And that's why I don't want my wife anywhere Windows.

---

### Post by bilkay on 2013-12-30
> **mettlewk said:**
> ... I had Ubuntu working on my HP ...

How did you install it, i.e., is it installed on your HD or is it running on a usb stick? Did you disable secure boot before installation?

---

### Post by bilkay on 2013-12-30
> **oldfred said:**
> @bilkay
Best to backup efi partition and Windows.
Then post this:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)...

Does it have to be run from a livecd or liveusb? What would happen if I installed and ran it from an HDD installed system?

---

### Post by oldfred on 2013-12-30
Normally you run Boot-Repair from the Ubuntu live installer or download it as a full install/repair ISO.

But I run it from inside my Ubuntu install just to backup boot files and document system. But then you should not need it to resolve boot issues as you have booted?

---

### Post by bilkay on 2013-12-31
> **oldfred said:**
> Normally you run Boot-Repair from the Ubuntu live installer or download it as a full install/repair ISO.

But I run it from inside my Ubuntu install just to backup boot files and document system. But then you should not need it to resolve boot issues as you have booted?

I downloaded and ran it and it worked perfectly except for one hitch: I got the start-up black screen. It must be something with this model computer.

Thanks much!

---

### Post by oldfred on 2013-12-31
Many systems need nomodeset for video driver issues or Intel video needs other settings.
What video card/chip?
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by bilkay on 2014-01-02
acpi=off did the trick. Thanks again!

p.s. acpi=off solved the brighness problem but disabled the battery monitor. Used 'acpi_os=' instead.

---

