---
title: "Tutorial for UEFI installation?"
date: 2015-12-18
forum: Installation &amp; Upgrades
---

### Post by Dorian_Mode on 2015-12-18
Hello, I am planning a dual-boot,Windows 8.1 & Ubuntu (or possibly Mint). I have no experience doing this with UEFI and GPT partitions. However since both have been around for awhile now, I am hoping there is a tutorial. Some reading beforehand usually eliminates a lot of trial and error. Suggestions anyone?

---

### Post by sudodus on 2015-12-18
Welcome to the Ubuntu Forums :-)

Maybe you can start with this link and the links about UEFI from this link,

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

> There is a good wiki page about [booting with UEFI](https://help.ubuntu.com/community/UEFI), and a good tutorial thread, [UEFI Installing - Tips](http://ubuntuforums.org/showthread.php?t=2147295). 

and ask when you need more direct help.

---

### Post by yancek on 2015-12-18
The links below should help.

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Dorian_Mode on 2015-12-18
Thank you both.

---

### Post by grahammechanical on 2015-12-18
Are you planning to upgrade Windows 8.1 to Windows 10 in the future? Better to do the upgrade before installing Ubuntu. You will find several posts on this forum about the problems that people get when upgrading Windows 8.1 to 10 in a dual boot with Ubuntu. From those threads you will learn what to expect and possibly what to do to fix things.

Regards.

---

### Post by oldfred on 2015-12-18
What brand & model system?
 Some just work, but many have unique issues.
Most Dells seem to just work, Acer requires UEFI password and setting "trust" on ubuntu/grub boot files. HP & Sony and now many others require major work arounds.

Microsoft said they were auto upgrading everyone to Windows 10. Then retracted that. 
Latest I just saw was they were turning auto update to Windows 10 again and you have to turn that off if you do not want it now.

---

### Post by Dorian_Mode on 2015-12-26
> **oldfred said:**
> What brand & model system?
 Some just work, but many have unique issues.
Most Dells seem to just work, Acer requires UEFI password and setting "trust" on ubuntu/grub boot files. HP & Sony and now many others require major work arounds.

Microsoft said they were auto upgrading everyone to Windows 10. Then retracted that. 
Latest I just saw was they were turning auto update to Windows 10 again and you have to turn that off if you do not want it now.

Thank You for the input oldfred and thanks to everyone else as well, since I plan on upgrading to windows 10, I will do that first. However regarding the UEFI and GPT, I have inadvertently solved that by using Diskpart, whereby I rendered my windows unbootable. I had to reformat and reinstall Windows 8 (I have the
install media). My hard disk is now partitioned MBR and Linux Mint 17.3 is on an extended with Windows 8 on a primary. I will probably have to reinstall Mint after the upgrade to Windows 10, but that won't be a problem. This solves my dual boot issues but unfortunately I still have no experience installing a dual system in  UEFI & GPT mode, which is what I was hoping for, perhaps at some point in the future. after I have read up on it, and become more proficient with
Diskpart. Thanks again.

---

### Post by Geoffrey_Arndt on 2015-12-26
Dorian,  or, you can just run Linux as the sole/host OS and run Win 7, 8 or 10 in Oracle's Virtual Box VM.    For a decent PC, this usually works well (unless you're a high-end gamer).    Worth looking into so you have soft-switch ability to run guest OS in secure containers.

---

