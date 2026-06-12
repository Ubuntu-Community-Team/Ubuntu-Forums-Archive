---
title: "Run Ubuntu from an external drive"
date: 2014-01-22
forum: Installation &amp; Upgrades
---

### Post by GrouchyGaijin on 2014-01-22
I have a question about running Ubuntu from an external drive.
Can you plug the drive with Ubuntu installed into a Windows 8 machine and boot Ubuntu or will you run into the secure boot problem?


The thing is I'm thinking of getting a new PC and setting up dual boot with Windows 8.1 seems pretty daunting.
(I really need to run EndNote, which does not work in WINE.)


If I had a USB 3 port which is pretty fast, could I just run Ubuntu from an external drive?

---

### Post by jp734 on 2014-01-22
Yes you can. It shouldn't be a problem. Just make sure you edit your bios setup to boot from external drive first. I had that setup for a while when I could not use my sata connections, until I updated my bios.

---

### Post by GrouchyGaijin on 2014-01-23
Cool!  I'm so glad to hear that works.

---

### Post by ndiniz on 2014-01-23
Unfortunately, I don't have a BIOS update for my Lenovo H430. The BIOS was setup on September 9th of 2012 (I think that's correct, I'll have to go back into my BIOS to be sure)

---

### Post by GrouchyGaijin on 2014-01-23
@ndiniz
I think he meant set the boot order in the BIOS not update the BIOS.

---

### Post by sudodus on 2014-01-23
> **jp734 said:**
> Yes you can. It shouldn't be a problem. Just make sure you edit your bios setup to boot from external drive first. I had that setup for a while when I could not use my sata connections, until I updated my bios.

+1

Yes it works in most computers. But if Windows is installed in UEFI mode (and I think so), you must either

- install Ubuntu in UEFI mode too
- or change in the BIOS/UEFI menu system every time you switch between Ubuntu and Windows.

Search the internet for ***ubuntu uefi*** to find links like this one [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by GrouchyGaijin on 2014-01-25
Thank you Sudodus.
Is installing Ubuntu in UEFI mode simply an option presented during installation?
I wonder, can you simply turn off UEIF for WIndows?

This option is a last resort actually.  I'm taking a trip to the US this summer and plan on buying a PC from Zareason.
I emailed them and they will make an empty partition for Windows and give me some instructions on how to install Windows to make the machine dual-boot.

---

### Post by sudodus on 2014-01-25
I think Ubuntu 64-bit install drives will find automatically if UEFI is needed and select that. Unfortunately several computers are equipped with UEFI systems that do not conform with the standard, and it makes it tricky to install dual boot systems. Often ***Ubuntu Boot Repair*** will help, otherwise *oldfred* is often checking calls for help at the megathread [[Boot-Repair] Graphical tool to repair the PC boot in one click]("http://ubuntuforums.org/showthread.php?t=1769482")

If you buy Windows on a DVD disk, you can probably install version 8 without UEFI, at least it was possible with early versions and also the 'developers preview'. But if it comes pre-installed, I think you are stuck with UEFI. This is a way for Microsoft and the manufacturer to control (limit) how you use the computer.

---

