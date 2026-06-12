---
title: "Install Challenge - No CD, No bootable USB, No ethernet"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by kmull on 2006-12-01
I have Ubuntu Edgy happily installed on my IBM T42 Thinkpad. My roommate has a really old Gateway Solo laptop sitting around with Windows XP on it. It is having your typical issues - spyware, adware, possibility of a virus, runs slow, etc.

I told him I would try to load Xubuntu on the laptop, but quickly ran into these issues:
[LIST]
[*]CD-ROM does not function
[*]USB is not bootable (old hardware, option not in BIOS)
[*]No Ethernet port (phone jack only)
[/LIST]
It does have a floppy drive, but I have not confirmed if it is working or not because I do not have any floppies, nor do I have a computer around here with a functioning floppy drive to install that way.

He also has a plug and play Wireless card that functions under Windows.

I tried [this]("http://marc.herbert.free.fr/linux/win2linstall.html"). Got Edgy's linux kernal and initrd.gz loaded into C:\Boot\, loaded Grub. Going through Grub the config starts and tries to get me to link up to the US mirror, which of course fails because it doesn't recognize the wireless card.

The USB drive works, just not as a bootable option. It also doesn't power up under normal startup (it is a brand new 2GB and seems to need to be recognized before working -- works under Windows and my Ubuntu install).

So, is it possible to get Xubuntu/Ubuntu loaded on this machine, other than physically removing the drive and connecting it to a machine with a working CD drive? I am willing to do just about anything reasonable... but if it is too much hassle we may just throw it up on eBay and forget about it.

Thanks in advance!

---

### Post by milton1 on 2006-12-01
You might be able to get a bios update that would enable boot from usb. Most manufacturers have bios updates available for download.

---

### Post by kmull on 2006-12-01
Any other ideas?

---

### Post by Doppelbock on 2006-12-01
> **kmull said:**
> I tried [this]("http://marc.herbert.free.fr/linux/win2linstall.html"). Got Edgy's linux kernal and initrd.gz loaded into C:\Boot\, loaded Grub. Going through Grub the config starts and tries to get me to link up to the US mirror, which of course fails because it doesn't recognize the wireless card.

The USB drive works, just not as a bootable option. It also doesn't power up under normal startup (it is a brand new 2GB and seems to need to be recognized before working -- works under Windows and my Ubuntu install).

I'm not sure how to interpret the last sentence but could you maybe boot to Grub as mentioned and then have it look to the USB drive instead of the mirror?

---

