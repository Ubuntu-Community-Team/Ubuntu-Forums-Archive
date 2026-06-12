---
title: "Intalling Hardy via PXE"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by bstempi on 2008-05-04
Hi group,

I recently decided to upgrade my 12 machines (of various Ubuntu versions) to 8.04 using a Nuke-And-Pave method.  Instead of simply upgrading, I'd like to wipe the machines and start fresh.  I chose PXE to do so.

So, here's my setup:  I have a machine with 2 nics:  one to the LAN, and one to a private network for machine imaging.  This machine runs DHCP + TFTP + Apache 2.  I have the 8.04 ISO mounted and shared as http://<imagingmachine IP>/hardy.

I also copied to PXE images from the ISO into my TFTP folder.

I can get my machines to boot via PXE, and to start the installation.  For the mirror selection, I choose manual, and point it to my imaging server's http server.  All seems to go well up until it goes to grab packages.  The installer attempts to grab packages from Hardy-Updates directory, where the CD only contains a Hardy directory.  

I don't want to mirror an entire repo...that's just silly.  I want to install the software that's contained on the ISO, and then let machine update itself once it's connected to my regular LAN (which will give each machine internet access).  I would no like to connect these machine to the internet until the initial installation is complete.

Any ideas on how I can accomplish this?

Thanks,
Brian

---

### Post by Slim Odds on 2008-05-04
Does your DHCP server provide a gateway address and a default route through the gateway?

Otherwise, your machines won't see the package servers on the net.

---

### Post by bstempi on 2008-05-04
Well, I want to be able to do the installation while isolated from the internet (ie, maybe reuse the setup for a Installfest).  

I guess I'm having a hard time with the fact that I can install the content of the CD while off-line, but I can't do a net-install without being connected to the 'net or without mirroring an entire repo.

---

### Post by gsker on 2008-06-06
> **bstempi said:**
> Well, I want to be able to do the installation while isolated from the internet (ie, maybe reuse the setup for a Installfest).  

I guess I'm having a hard time with the fact that I can install the content of the CD while off-line, but I can't do a net-install without being connected to the 'net or without mirroring an entire repo.

You do not need to be connected to the 'Net.  Mount the Alternate CD iso in your http server directories and then when it asks you for a mirror, scroll to the top of the list to find Manual.  Then you can tell it where your ubuntu is.

HTH

---

### Post by Divan Santana on 2008-06-24
This doesn't work for me either.
I tried a kick start file telling it where the installation is but when the installation begins it fails because it has no network IP.
Its looking for the installation medium on the cdrom when it should get it over the LAN. If I check the terminal there is no eth0 at this point with no IP hence it cannot load the KS http:// file because it has no network configured.

Looked at all PXE docs can't get ubuntu-server or alternate network booted :(

---

