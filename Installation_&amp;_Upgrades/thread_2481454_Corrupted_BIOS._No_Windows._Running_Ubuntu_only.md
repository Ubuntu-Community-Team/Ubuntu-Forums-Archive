---
title: "Corrupted BIOS. No Windows. Running Ubuntu only"
date: 2022-11-30
forum: Installation &amp; Upgrades
---

### Post by lets-go-brandon on 2022-11-30
I have an HP Pavilion 23-q118 (SKU. NOA37AA#ABA). AMD A8. ID 2B42. 
I installed Ubuntu 22.04LTS over top of the Windows 10 OS. All was fine until I realized my BIOS was corrupted (found this out from the blinking light code). In order recover the Bios I need to re-install windows. I have a brand new Windows install disk, no problem right? The system won't run the install disk until the BIOS issue is resolved. As I stated before I need Windows to recover the BIOS.      I'm going in circles. If any one knows what to do I would be forever grateful. I haven't been able to find anything online that helps.

Thank y'all for listening

---

### Post by yancek on 2022-11-30
Can you still boot Ubuntu?  
Do you get any information when you try to boot the windows install medium and if so, what is it?
You have set the DVD/USB set to first boot priority?
When you installed Ubuntu, did you overwrite the entire drive or do you still have a windows Recovery partition?  If you have it, are you able to access it?
When you boot, are you not able to access the BIOS firmware at all?
Is your computer still under warranty?

---

### Post by MAFoElffen on 2022-11-30
As an HP, Dell, and Lenovo Certified Warranty Service Tech there was a combination of USB thumb drives that I would take on onsite service calls. Besides specific Diagnostics and Branding tools, I would take an Ubuntu LiveCD and Windows To Go.

If you dl previous version Rufus 2.0, if you have a Windows ISO, it will offer to create a Windows to GO USB. Later versions, this option was taken out. If I couldn't burn a BIOS image from the onboard UEFI BIOS or Diagnostics tool, then I would reburn it from WinToGo.

Not all USB Thumbdrives will work with this. I used a Lexar USB3.2 128GB thumbdrive. Lexar has a utility to turn their USB thumb drives to USB Storage... And you need a fast drive.

---

