---
title: "Live USB not bootable under 15.04"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by rjbownes on 2015-08-24
Hi There! 

I made the jump entirely to Linux recently and chose Ubuntu 15.04 and I have run into a problem. I have for a long time liked flipping ROMS on my phone and wanted the same flexibility in distros, but I can't for the life of me get off Ubuntu now.
I made a live USB for linux mint 17.2 Cinnamon, booted into bios (UEFI) changed my boot order, saved and exited and nothing, booted back into ubuntu. 
I tried using different tools to create the live disk, UNet etc, but after that it was no longer visibile in bios. I reformatted the USB a number of times to ensure it was FAT 32 and GPT but nothing, can't even see it in the boot order. Any one else running into this problem? If so, any advice?

---

### Post by oldfred on 2015-08-24
Many UEFI have settings you have to change to specifically allow booting from flash drives. You may have to turn off secure boot, but keep UEFI on and CSM off. Or whatever settings those are and it varies. Some also require a supervisory password to enable changing some or all of those settings.

My system just does not like to recognize my press of f8 so it takes several trys, and then just shows flash drive twice as "English". I believe one is BIOS & the other UEFI but have to try several times with that before I get it to work.

---

### Post by rjbownes on 2015-08-24
I ran a dual boot before this, but never changed that partition, I got fed up with Win 10 hence the total move. 

I have turned off secure boot, and fast boot, enabled boot from USB and have no passwords set, what is the f8 functionality?

---

### Post by oldfred on 2015-08-24
f8 was my Asus motherboard, Most systems use f10 or f12 and it directly shows just the boot options or the same UEFI boot tab. It is for a one time boot like when you want just DVD or flash drive. Or have a second install on sdb with its own loader in the MBR or ESP.

 BIOS Setup Utility Access Keys for Popular Computer Systems
[http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm](http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm)
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

