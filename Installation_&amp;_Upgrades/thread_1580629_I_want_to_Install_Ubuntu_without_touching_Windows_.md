---
title: "I want to Install Ubuntu without touching Windows bootloader"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by Delgo Thex on 2010-09-23
So here's the skinny, I have Windows 7 home Premium installed on my Touchsmart PC. I have a 60 GB partition I want to use for Ubuntu. Can I install Ubuntu to that partition so that it doesn't change how my computer boots up already?

Example:

I press the power button. The POST test processes and then boots into windows no questions asked, as if it's the only OS on the system.


[COLOR="Red"]I want to keep it that way even after Ubuntu is installed.[/COLOR]


I want Ubuntu ONLY accessible by using the BIOS boot menu as soon as the PC starts up. Can this be done, and how?

---

### Post by plucky on 2010-09-24
> **Delgo Thex said:**
> So here's the skinny, I have Windows 7 home Premium installed on my Touchsmart PC. I have a 60 GB partition I want to use for Ubuntu. Can I install Ubuntu to that partition so that it doesn't change how my computer boots up already?

Example:

I press the power button. The POST test processes and then boots into windows no questions asked, as if it's the only OS on the system.


[COLOR="Red"]I want to keep it that way even after Ubuntu is installed.[/COLOR]


I want Ubuntu ONLY accessible by using the BIOS boot menu as soon as the PC starts up. Can this be done, and how?

The only way it can be done this way is if you install a second drive and write the Grub2 boot to the Master Boot Record of the second drive.Then the BIOS can pick up the MBR for the second drive and boot Ubuntu.

That would leave the first drive MBR to boot Windows 7.

Clear as mud.Hope this helps.:)

Good Luck

---

### Post by Rubi1200 on 2010-09-24
I am not quite sure why such a stringent stipulation?

The other alternative I can suggest is to install Ubuntu into the partition you created and let it also install its bootloader.

Then, after the installation go into Ubuntu and edit the bootloader configuration files so that the default boot is into Windows (assuming that is the whole point of what you want).

But plucky's suggestion is probably better as far as keeping the option to choose the default OS directly from BIOS (except that it seems to me like a lot of hassle and for what?).

Anyway, if you have any other questions, feel free to ask here.

---

### Post by Delgo Thex on 2010-09-24
Well the reason for this, is because every single time I've ever installed Linux on my personal computer It always overwrites and the MBR. I don't like GRUB, or LILO or any of the Linux bootloaders because I don't understand how to set them up. And because of that everytime I end up losing access to my Windows partition no matter what I do. And I simply can't have that happen this time. I have to much stuff on my computer to backup right now, and I don't want to spend the time restoring after that happens.

Because I've done this kind of setup with two installations of windows before. But I do believe it was with two seperate hard Drives like what was stated. 


Thanks for your suggestions though, I'll probably go buy an external SATA drive for this purpose. Because the Touchsmart PC doesn't have an easy way to install an additional drive.

---

### Post by lukeiamyourfather on 2010-09-24
> **plucky said:**
> The only way it can be done this way is if you install a second drive and write the Grub2 boot to the Master Boot Record of the second drive.Then the BIOS can pick up the MBR for the second drive and boot Ubuntu.

That would leave the first drive MBR to boot Windows 7.

Clear as mud.Hope this helps.:)

Good Luck

That's how I do it. :)

---

### Post by entropy1 on 2010-09-24
Have you ever used "startupmanager"?  After an ordinary dual-boot installation, in Ubuntu, use synaptic to install "startupmanager".  Then select System > Administration > StartUp-Manager.  This provides a GUI that makes it easy to select the default OS.  That way, you can make Windows the default OS.

---

