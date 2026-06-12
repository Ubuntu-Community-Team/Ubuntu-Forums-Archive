---
title: "Tried live disk, now no OS"
date: 2015-06-09
forum: Installation &amp; Upgrades
---

### Post by raheny on 2015-06-09
Hi guys,
I have an ACER laptop running windows 8 and wanted to test ubuntu 14 so ran the live disk via usb. Turned off the boot uefi so i could boot from the usb and then tested ubuntu. All seemed fine but i ran into the no wifi found issue and decided i would try again another day. So i shutdown and rebooted hoping to get back into my windows OS but i now get the message "Operating not found" when i try booting with the usb removed. When i try to boot with the usb inserted and choose to boot from the HDD i get get the "Booting...." message but nothing else.

---

### Post by oldfred on 2015-06-09
Did you turn UEFI back on and choose the Windows entry in UEFI boot tab?

You should not boot Ubuntu live installer in BIOS mode if your Windows install is UEFI.

---

### Post by raheny on 2015-06-09
As simple as that, thank you so much :D. 

I do run ubuntu on 2 desktops at home but my work laptop runs on windows. Now i just need to work out how to enable wifi on the live disk (the laptop has no ethernet port) and then i can wave bye bye to windows forever.

---

