---
title: "Can't install Ubuntu on Toshiba C55-A-1N1 Laptop - Windows 8 UEFI Blank Screen"
date: 2014-03-18
forum: Installation &amp; Upgrades
---

### Post by jflock on 2014-03-18
I recently bought a Toshiba C55-A-1N1 Laptop, and I can't get Ubuntu to install on it. It came pre-installed with Windows 8.

I have disabled fast boot in windows. Secure boot was already disabled in the BIOS (or UEFI or whatever it is). 

I have tried only with the Live CD as I do not have a USB key at the moment. I have tried 13.10 and 12.04.4, both 64 bit. 

After putting the disk in the drive, then starting the machine up, I do get to a GRUB screen. However before reaching grub, there are two screens. The first flashes up very quickly, and has some text in the top left which I cannot read. The second then stays up for about a second, and says:

error: variable root not set

Then GRUB loads. After selecting the option to try Ubuntu, or the option to install directly, the screen just goes black. I can hear the optical drive for a bit, but then that goes quiet. 

I have tried increasing the screen brightness using the buttons on the keyboard (both with and without holding down the FN key - just in case). 

The only thing that I can find online that seems similar is this [http://forums.linuxmint.com/viewtopic.php?f=90&t=161388](http://forums.linuxmint.com/viewtopic.php?f=90&t=161388) which although it is for LinuxMint is the only thread that I can find for my exact model of laptop. Other Toshiba Satellite C55 models can have different hardware, such as AMD chips. 

I have tried a few of the suggestions in that thread, such as adding options to the GRUB boot, but have had no results. I am not sure whether I am even applying them correctly. 

Can anyone help at all?

My computer specifications are :

Core i5 4200m 
8 GB Ram
Intel HD graphics 4600

Thank you in advance!

---

### Post by squakie on 2014-03-18
Try some of the boot options - I'd try nomodeset first.

---

### Post by jflock on 2014-03-18
I tried the ubuntu gone 14.04 beta 

That allows me to install, and to boot into the live CD. 

However, the computer will then  just boot straight into windows. There is no GRUB displayed, or UEFI boot choices or whatever. 

I then tried running boot-repair from the ubuntu live CD that I can boot into., 14.04. However boot repair has no trusty repo, so I had to change it to saucy. 

After doing that, and restarting, it still just boots straight into windows 8. 

Help please.

---

### Post by fantab on 2014-03-18
Post the link to 'Bootinfo Summary' file which Boot-Repair generates.

---

### Post by jflock on 2014-03-20
Thanks

[http://paste.ubuntu.com/7117553](http://paste.ubuntu.com/7117553)

It says that their were errors during the repair. 

Although, I then tried changing it to CSM boot in the BIOS. That didn't work, which I expected, however after I changed it back to UEFI boot, the next time that I turned on the computer GRUB appeared, thus allowing me to boot into Ubuntu. It has also appeared every time that I have rebooted since then. I haven't dared try booting into windows though, just in case I can't get into Ubuntu again!

What I am still unsure of is why I could install 14.04, but not 13.10 or 12.04 in the first place. 

Thanks.

---

### Post by fantab on 2014-03-20
Try to run the Boot-Repair again, this time use only the 'Recommended Repair'. Post back the boot info.

You current BRinfo is bloated, unusually lengthy... lets see if there is different Bootinfo this time.

---

