---
title: "PXE, the Final Fronteer"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by IndigoRage on 2012-02-02
This will be the 3rd and final time I attempt to post this. The previous two attempts acted like they posted, but the threads do not exist... so...

I'm trying to build a working PXE server, and I've gotten it to 99% working but here's the problem I've run into:

DHCP works perfectly, no problems getting addesses.
TFTP on the other hand... it's mostly doing what it's supposed to, until the pxelinux.0 file, then things take a turn for the stupid.

Using version 2.08 of pxelinux.0, I see

pxelinux.cfg/HE-X-OF-IP-AD-DR-ES-S
pxelinux.cfg/HE-X-OF-IP-AD-DR-ES
and so on, down to
pexlinux.cfg/default

then I get "cannot find kernel: linux"
boot:

at the boot: prompt, I can type memdisk initrd=floppy.img keeppxe

and it boots the image file just fine and everything works from there on out.

the default file living in my /tftpboot/pxelinux.cfg/ is:

DEFAULT NBD

LABEL NBD
KERNEL memdisk
APPEND initrd=floppy.img keeppxe

Yes, I need the keeppxe.

So, deciding to experiment a little, I removed the default file from pxelinux.cfg directory, figuring this would give me an error, and... it did not. It went through the whole process of looking in all the various directories that aren't there for a file that isn't there, and gave me the same "cannot load kernel: linux"/boot: prompt.

I figured this must be a bug in 2.08 of pxelinux.0, so I grabbed a fresh copy of pxelinux.0 version 4.05 and replaced the pxelinux.0 in my /tftpboot directory, and restored the default file.

Rebooted the pxe server, tried a new PXE boot and this time I get "Cannot locate configuration file. Press any key to try again or wait for restart."

Except... there is a /tftpboot/pxelinux.cfg/default file, but 4.05 acts like there isn't.

I've been looking for other versions of pxelinux.0 to try, but have had the same issue.

Only 2.08 ACTS like it's looking for this file, even though it doesn't bother reading or using it.

Any other version acts like the /tftpboot/pxelinux.cfg/default does not exist.

So that brings me here, asking for some explanation as to what I need to do to make this thing work without human interaction.

---

### Post by lykwydchykyn on 2012-02-02
Logically it seems like there are two possibilities:

 - a permissions problem on the configuration file
 - a configuration problem for tftpd

Which tftp server are you using?  

What are the permissions on /tftpboot and /tftpboot/pxelinux.cfg/?

---

### Post by IndigoRage on 2012-02-02
Bingo! Your logic is flawless.

Turns out, despite having set the owner for /tftpboot to Nobody and given full access, this did not propagate downward like I'd expected.

Turns out the pxelinux.cfg directory was still access restricted, as was the default file.

Modified permissions on both and we're booting fully automatically without any human intervention.

Much appreciated!

I'll write up a guide for (re)creating a PXE server in this same style when I've some extra time - as it stands now I have 731 new machines that need images pushed to them, and I'll be pushing them PXE style!

---

### Post by lykwydchykyn on 2012-02-02
Good to hear; PXE is a load of fun once you get it working, isn't it?

---

### Post by IndigoRage on 2012-02-02
Fun? Maybe, in a hard-core geeky kind of way... but then, that is what we are lol

But it's certainly extremely useful, especially for IT support people. Our PXE server allows us to:

Boot to a PE Boot image of the diagnostic utilities we use.
Boot to a Dell diagnostic image.
Boot to Symantec Ghost boot image for creating or restoring images.

It's a HUGE time-saver for us to be able to PXE boot and do these things, especially when dealing with some of the older machines in the field that have no or broken CD ROMS/Floppy drives.

And being able to run Ghost on multiple machines at the same time saves us around 75-100 man hours a month now.

---

### Post by lykwydchykyn on 2012-02-02
> **IndigoRage said:**
> Fun? Maybe, in a hard-core geeky kind of way... but then, that is what we are lol

Is there another kind of fun??? :)
> 
But it's certainly extremely useful, especially for IT support people. Our PXE server allows us to:

Boot to a PE Boot image of the diagnostic utilities we use.
Boot to a Dell diagnostic image.
Boot to Symantec Ghost boot image for creating or restoring images.

It's a HUGE time-saver for us to be able to PXE boot and do these things, especially when dealing with some of the older machines in the field that have no or broken CD ROMS/Floppy drives.

And being able to run Ghost on multiple machines at the same time saves us around 75-100 man hours a month now.

Absolutely.  I've got one booting g4l, parted magic, WinPE, various diagnostic utilities, and just about any Linux live Cd/installer that we need.  So nice to do away with that stack of CDs and floppies.

---

