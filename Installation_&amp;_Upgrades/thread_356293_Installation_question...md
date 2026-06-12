---
title: "Installation question.."
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by Voodooengine on 2007-02-08
Im thinking about loading ubuntu on a 40 gig ATA drive. Im getting the ATA drive from my friend tomorrow, and before i install i plan on unplugging my C drive which is a SATA 250 gig, and my H drive which is a USB external drive which is also 250 gigs. Then i plan on connecting the 40 gig ATA drive.

My question is after i do this, and i install ubuntu will i be able to attach my C drive, and unplug the 40 gig drive and boot into windows? I'm unsure about this because my Windows MBR file would be on my C drive, and since that would be dettached, nothing would happen.

Thanks

---

### Post by bandie on 2007-02-08
If your fitting another hard drive (your 40Gb ATA) then you will have two separate bootable drives. One will have windows on it the other Ubuntu as they are two independant drives they will never meet each in your system so there cannot be any issues between them, simple fit one drive for windows - switch off and remove then fit the other drive for Ubuntu, 

Or install Ubuntu on the 250gb drive and they will both co-exixt together, then count how many times you boot in Ubuntu Vs Windows and after 1 month re-install Ubuntu using all of the drives capacity.

---

### Post by Voodooengine on 2007-02-08
> **bandie said:**
> If your fitting another hard drive (your 40Gb ATA) then you will have two separate bootable drives. One will have windows on it the other Ubuntu as they are two independant drives they will never meet each in your system so there cannot be any issues between them, simple fit one drive for windows - switch off and remove then fit the other drive for Ubuntu, 

Or install Ubuntu on the 250gb drive and they will both co-exixt together, then count how many times you boot in Ubuntu Vs Windows and after 1 month re-install Ubuntu using all of the drives capacity.

 Alright thanks. I was reading that it might be a good idea to unplug all other hard drives, then force ubuntu to install onto my IDE drive, and then enter my bios and set it to boot off my IDE drive first.

Would grub automatically recognize my windows install, and list the option to boot into it, or would i have to edit some files first?

I dont have a floppy disk drive, and i heard that the super grub loader must use a floppy.

---

### Post by aberry5555 on 2007-02-08
If I were you I would keep to the way you are thinking of now, as it will mean no hicc-ups for booting. Also, because sata is recognised as the first drive by most motherboards when it's plugged in, all you will have to do is plug in your sata, and not bother removing the 40 gig ATA. If you try Ubuntu and decide you like it enough to have dual boot then read up alot on dual booting as, unfortunately, it is barely ever as simple as just adding Ubuntu to your system, you have to do a few edits to either grub or the NTLDR system on windows to make it load up seemlessly.

---

### Post by bandie on 2007-02-08
No No No you don't need a floppy ( does anyone still use them?) install Ubuntu on the same drive as your windows partition all will be well and no disc swapping would be required. 

Or you could add the ATA drive as a slave and install Ubuntu onto that drive, however I recall some issues using SATA and ATA drives on the same motherboard.
With a dual boot system your PC will boot to the laoder screen giving the option of Ubuntu or Windows.

---

### Post by Voodooengine on 2007-02-08
Oh alright. Thanks alot for your help.

Right now i have a MA111 Netgear Wireless adapter, and i was reading about NDISwrapper.

I dont think i should have any problems with Ubuntu, or adding a couple of lines to dual boot, right now im running linux in VMWare so im getting the hang of it day by day.

My only concern is my graphics card, i have  X1600 Pro from ATI and i heard that Linux has problems with ATI cards, but i could just use the opensource driver from Automatix right?

---

