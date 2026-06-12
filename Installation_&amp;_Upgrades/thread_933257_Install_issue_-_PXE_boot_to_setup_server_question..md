---
title: "Install issue - PXE boot to setup server question..."
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by Tancor on 2008-09-29
Hi all,

I've got a tinsy problem that I'm hoping I can get worked out.  ok - I have a blade server, no CDRom, which means I'm pretty much stuck using a PXE boot install.  Now, my blade server has 6 blades in it with a variety of HD sizes.  One of the servers I intend on being a DNS only server, it has a small hard drive (1 gig (kinda low on 68 pin scsi drives atm)) and 2 gigs of ram.  The ubuntu server install CD has a fairly small install footprint of if I recall correctly from one of my other servers somewhere around 600 megs (that was with web server, email, dns and something else, but can't remember which off hand, might be FTP).

Now, since I need to do pxe boot and subsequent install, from everything I've read - it appears I need to use the desktop alternate - can that be customized enough to be the equivilent of the server install?

I pretty much just want the base OS + DNS and that's it.

And for those that might question the install method, I'll explain this:

*This is a Dell 1655 blade chassis which means:
  1) It will only boot with an external device from either special Dell usb cdrom, or a special Dell USB floppy drive, neither of which I have.  
  2) a USB stick is not able to be booted
  3) A no-name CDRom drive won't boot

The CDRom drive that is bootable is no longer in production 
(I haven't found it on EBay either, and the only places that claim to have it are in europe, and I don't have the ~$200 atm to buy one =( ).  They gave me a part number for a replacement (which was just as expensive as the original at $165) which I ordered which didn't work (the "replacement" requires 2x usb ports, and is not recognized by the individual blades)  

Any tips would be most appreciated.  

-Tony

---

