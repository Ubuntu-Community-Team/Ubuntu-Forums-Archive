---
title: "Improperly burnt Alternate Install USB ? 12.04 Pangolin"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by RAM SEN on 2012-07-06
1. Not being confident about optical drive quality, I burnt my Alternate iso (md5 was verified) for 12.04 into a 8GB HP usb stick via pendrivelinux UUI - 

2. I have GAG installed to my MBR as I'd rather use that than GRUB in MBR 
I'll put Lilo in '/' 

3. BIOS boot order is set to make Hard disk as last option 

4. BTW I used the same steps in as in 1. to also burn a simple Desktop 12.04 Live to another 8GB HP usb stick via pendrivelinux UUI - this one boots nicely and allows me Live sessions with persistence. 

5. But my Alternate USB is stuck in the main menu "Install Ubuntu / Test Memory ...etc  " i pressed Enter to boot & got this message 
"Could not find kernel image: /casper/vmlinuz"

What do I do ?

---

### Post by oldfred on 2012-07-07
I like to boot ISO directly with grub2's loopmount. It works fine for Desktop, but does not work for alternate or server versions as something in ISO is missing.

I think you have to use the standard unetbootin to create flash drive.

Grub does not loopmount alternate
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926)

You can add to the bug even if it is not grub2 just to wake up the developers. It really needs 5 or more complaints before they really look at something, but not enough users boot any other way than standard.

---

### Post by RAM SEN on 2012-07-07
Tks Fred 
or shud i say RightsaidFred!!

---

