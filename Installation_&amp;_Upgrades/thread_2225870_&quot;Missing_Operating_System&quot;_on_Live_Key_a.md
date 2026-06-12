---
title: "&quot;Missing Operating System&quot; on Live Key and Virtual Box?"
date: 2014-05-23
forum: Installation &amp; Upgrades
---

### Post by phil32 on 2014-05-23
Hello, I am trying to install Ubuntu 14.04 on a USB. I have already got this to work with 14.04 and past versions, on the same key and computer.

But now every time I install 14.04 on this key I get the "Missing Operating System" error upon booting from Virtual Box or the computers bios.

I have found no answers online. I have try'd both x64amd and Intel versions (amd worked previously), created in LiLi, Yumi, and Pendrive. With varying persistence's, and with or without Virtual Box.

With the UEFI CMS on and Fast Boot off.

Am I missing something here?

---

### Post by oldfred on 2014-05-24
If UEFI only the 64bit version will work.

Is this an installer or a full install? 
Do not know about Virtual box but if booting 64 bit version, UEFI should offer both a UEFI boot and a non-UEFI or CSM/BIOS/Legacy boot.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


Known good flash drive? some just do not work.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
Howto help USB boot drives - sudodus
A tool that helps boot some computers from [other] USB boot drives - Chainloader
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by phil32 on 2014-05-30
Hey thank you for the info!

No conformation on this but, it was just a hardware issue. Works on a separate usb.

Just anecdote but right before it stopped working I installed a Win8.1 .iso on the key. Key works great for everything else, maybe it just messed up its ability to boot an os...

---

