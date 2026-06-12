---
title: "downloading the ISO file directly?someone better help me!"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by lordvolo on 2006-10-02
If I download the xubuntu ISO file directly, can i install it like that with out having to make a CD-ROM?

---

### Post by unco on 2006-10-02
My understanding is:

If installing into a VMWare image (virtualisation) then yes you can use ISO direcly by configuring the CDROM dirve of the virtaul machine to point to your ISO file.

However if you are trying to install to an actual physical machine then you will need to burn the ISO to a physical CD and then update your BIOS to BOOT from CD.

---

### Post by randell6564 on 2006-10-02
> **lordvolo said:**
> If I download the xubuntu ISO file directly, can i install it like that with out having to make a CD-ROM?

'unco' is right, and if indeed you ARE trying to install via Virtual machine, I suggest that you dont. You dont get the real deal that way! It's hard to evaluate a distro this way, in my opinion.

---

### Post by Aquila62 on 2006-10-03
> **randell6564 said:**
> 'unco' is right, and if indeed you ARE trying to install via Virtual machine, I suggest that you dont. You dont get the real deal that way! It's hard to evaluate a distro this way, in my opinion.

Hi all, I disagree in part with the above statement as I find Virtual Machines to be invaluable for testing & exploring  A new OS. I have been running Ubuntu 64bit in a virtual machine on my WinXP-(32bit) Conroe box which is testament to how far virtual machines have come in the past 2 years. It is able to grab the hardware directly, recognise my dual core 64 bit processor, bypassing the 32bit limitation of windows & runs very smoothly with all the eye candy on.

On another note RE: VMware Installs.  I have a 5 gig USB2 drive with a 4.5gig partition & 500meg swap. I have been able to install Ubuntu 64bit directly on the USB drive (no virtual disk), from the downloaded ISO & after a BIOS adjustment, reboot directly into this without any probs. Almost like a HD install with USB2. I had to do this as my Asus P5B Deluxe Wifi has problems with Linux (JMicron , ICH8 stuff).

Just my 2c worth

---

