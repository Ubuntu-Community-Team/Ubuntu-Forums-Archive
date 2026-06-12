---
title: "USB boot error"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by sebastian-weil on 2015-08-22
I have tried several different USB sticks, different ports, made sure checksum of image is correct. I am trying to install Ubuntu Gnome on Windows laptop. But whenever I boot from USB I get the following error:

```
Could not get fio for li->DevIceHandle: 2
Failed to find fs
Failed to load image
Failed to find fs
Failed to load image
Press any key to continue...
```

What is the problem?

---

### Post by sudodus on 2015-08-22
Welcome to the Ubuntu Forums :-)

There can be many problems. If you tell us more about your computer, it will be easier to help. Otherwise we can only guess. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- Are you running Windows in the computer now? In that case, which version, and do you want to keep it and install Ubuntu alongside Windows, dual boot?

- Are you running in UEFI or BIOS mode?

- Which version of Ubuntu Gnome are you trying to install?

- How did you copy from the iso file to the USB stick?

- Please read the following links and links from them for more details,

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by sebastian-weil on 2015-08-23
> - Brand name and model
Fujitsu Siemens Lifebook S761
> - CPU
Intel Core i5-2520 M 2.50Ghz
> - RAM (size)
4 GB
> - graphics chip/card
Intel HD Graphics 3000
> - wifi chip/card
It is either Intel 82579LM Gigabit Network Connection, Intel Centrino Advanced-N 6205 or Sierra Wireless (I'm unsure which one it is with disk manager)

> - Are you running Windows in the computer now? In that case, which version, and do you want to keep it and install Ubuntu alongside Windows, dual boot?
I am running Windows 10 and would like to dual boot.

> - Are you running in UEFI or BIOS mode?
I have no idea how to check this. There are no UEFI settings in my BIOS as far as I can see. I have played around with having ACHI on or off though.

> - Which version of Ubuntu Gnome are you trying to install?
15.04

> - How did you copy from the iso file to the USB stick?
I have tried with unetbootin, linuxliveusbcreator and win32diskimager.
I have tried having the three different USB sticks in FAT32 and FAT16 modes.

> - Please read the following links and links from them for more details,

[Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it

I have read through these but nothing helps. I cant even boot and try from the USB.

---

### Post by sudodus on 2015-08-23
> **sebastian-weil said:**
> Fujitsu Siemens Lifebook S761

- Intel Core i5-2520 M 2.50Ghz
- 4 GB RAM
- Intel HD Graphics 3000
- It is either Intel 82579LM Gigabit Network Connection, Intel Centrino Advanced-N 6205 or Sierra Wireless (I'm unsure which one it is with disk manager)

- I am running Windows 10 and would like to dual boot.

This computer is definitely powerful enough to run any Ubuntu flavour. There might be problems with UEFI, that it does not allow you to boot anything but Windows. 
> 
- I have no idea how to check this. There are no UEFI settings in my BIOS as far as I can see. I have played around with having ACHI on or off though.

Run a command line according to [Test if running in UEFI mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode)

```
test -d /sys/firmware/efi && echo "booted via EFI (UEFI)" || echo "booted via BIOS (legacy boot)"
```
> 
Ubuntu Gnome 15.04

I have tried with unetbootin, linuxliveusbcreator and win32diskimager.
I have tried having the three different USB sticks in FAT32 and FAT16 modes.

I have read through these but nothing helps. I cant even boot and try from the USB.

You must turn off hibernation and fast startup in Windows. Otherwise UEFI will boot directly into Windows. You do that via Windows's control panel:

***All apps -- Windows system -- Control panel -- System and security -- Power options -- Choose what the power button does***

scroll down and untick (they should be 'off')

- Turn on fast startup
- Hibernate

-o-

*If your computer runs in UEFI mode:* It will also be easier if you turn off secure boot in the UEFI settings (if possible).

Have a second look internet links about UEFI, for example those you find at [FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by sebastian-weil on 2015-08-23
> This computer is definitely powerful enough to run any Ubuntu flavour. There might be problems with UEFI, that it does not allow you to boot anything but Windows. 

Run a command line according to [Test if running in UEFI mode]("https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode")

```
test -d /sys/firmware/efi && echo "booted via EFI (UEFI)" || echo "booted via BIOS (legacy boot)"
```

I can't very well run a linux command on my laptop when it is using Windows 10 - remember, I cannot even "try" linux from the USB stick. It won't boot.

> 
You must turn off hibernation and fast startup in Windows. Otherwise UEFI will boot directly into Windows. You do that via Windows's control panel:

***All apps -- Windows system -- Control panel -- System and security -- Power options -- Choose what the power button does***

scroll down and untick (they should be 'off')

- Turn on fast startup
- Hibernate

-o-

Allright, those were already turned off. :(
> 
*If your computer runs in UEFI mode:* It will also be easier if you turn off secure boot in the UEFI settings (if possible).

Have a second look internet links about UEFI, for example those you find at [FromUSBStick#UEFI]("https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI")

I checked using MSINFO and appearently my BIOS is labelled as "older" and not "UEFI".

---

### Post by sudodus on 2015-08-23
So the problem is somewhere else (not UEFI).

Have you tried to boot another computer with your USB sticks?

How far does the boot continue - can you tell if the computer boots at all from the pendrives, or if they are not recognized at all. I don't recognize the output you described in post #1.

You could also try version 14.04.1 LTS with long time support. It is well debugged and polished, and the drivers might work better with your hardware.

-o-

According to some web pages describing Fujitsu Siemens Lifebook S761, there is a DVD burner. Maybe it works better to boot from DVD. If you want to try, I suggest that you burn at the lowest speed possible and the you 'burn an iso file'. Do not create a data DVD with the iso file. After burning you should see several files and directories, when you insert the DVD disk.

---

### Post by sebastian-weil on 2015-08-23
> **sudodus said:**
> So the problem is somewhere else (not UEFI).

Have you tried to boot another computer with your USB sticks?

How far does the boot continue - can you tell if the computer boots at all from the pendrives, or if they are not recognized at all. I don't recognize the output you described in post #1.

You could also try version 14.04.1 LTS with long time support. It is well debugged and polished, and the drivers might work better with your hardware.

-o-

According to some web pages describing Fujitsu Siemens Lifebook S761, there is a DVD burner. Maybe it works better to boot from DVD. If you want to try, I suggest that you burn at the lowest speed possible and the you 'burn an iso file'. Do not create a data DVD with the iso file. After burning you should see several files and directories, when you insert the DVD disk.

Let me start by thanking you for trying to help me first. :)

The boot goes like this:
* computer starts
* I hit key to choose what device to boot from (F10 for me).
* I choose the device I would like to boot from (the USB).
* The screen goes black with a blinking prompt in the upper left corner.
* Then the code in my first post is printed

---

### Post by sudodus on 2015-08-23
I have confidence in unetbootin and win32diskimager. They work for me.

It seems the computer boots into the pendrive(s). It might be a problem with the graphics, but Intel graphics of the kind you have should work without problems.

- There might be problems with the wifi driver. Is there a hardware switch (button) to turn off wifi?

- There might also be problems that can be fixed with one or several boot options. Try those available at boot, for example nomodeset, acpi=off ...! See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sebastian-weil on 2015-08-23
> **sudodus said:**
> I have confidence in unetbootin and win32diskimager. They work for me.

It seems the computer boots into the pendrive(s). It might be a problem with the graphics, but Intel graphics of the kind you have should work without problems.

- There might be problems with the wifi driver. Is there a hardware switch (button) to turn off wifi?

- There might also be problems that can be fixed with one or several boot options. Try those available at boot, for example nomodeset, acpi=off ...! See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I can turn off the wifi with a button - should I do that before burning the ISO to the USB or when booting?

I will tro the suggested boot options and then return here.

---

### Post by sudodus on 2015-08-23
Turn off wifi and try booting (when wifi is turned off).

---

### Post by sudodus on 2015-08-23
I will soon be busy and away from the keyboard. Other people are welcome to chip in and help :-)

---

### Post by sebastian-weil on 2015-09-02
> **sudodus said:**
> I will soon be busy and away from the keyboard. Other people are welcome to chip in and help :-)

Allright. I still won't work on my laptop. The USB sticks will, however, work on other computers I have. I can only conclude that there is something wrong with the BIOS - but I cannot for the life of me figure out what could be wrong.

---

### Post by sudodus on 2015-09-02
Now that we know that your USB sticks work in other computers, I suggest that you try some other linux distro, that might work, for example Knoppix, which is known to be good at recognizing hardware.

---

### Post by sebastian-weil on 2015-09-02
I will, I have tried the following distros already though:
Ubuntu
Ubuntuo Gnome
Linux Mint
Manjaro
Karora

and not one of them works... :-(

---

