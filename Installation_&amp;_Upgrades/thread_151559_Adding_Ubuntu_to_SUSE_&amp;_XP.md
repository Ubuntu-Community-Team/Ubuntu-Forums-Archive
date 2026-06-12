---
title: "Adding Ubuntu to SUSE &amp; XP"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by Vulpus on 2006-03-28
I have SUSE 10 and XP installed on a dual boot system. This has had various distros installed in recent months, my favourite is SUSE but I, and other family members, still have some affection for Ubuntu. Mandriva is still 'installed' on one partition (SDA5) but that didnt work (couldnt detect my SATA HD) so it is just taking up space and is NOT in the grub menu.lst. 

I would like to overwrite the Mandriva instal with Ubuntu but KEEP SUSE and KEEP the SUSE Grub menu. If I install Ubuntu 5.04 (that is the disk I have) will it give me the option writing to SDA5 and will it automatically add itself to the existing Grub menu or is the latter best done manually?

I do not want to just 'try it and see what happens' as I dare not take any risks with this as certain other members of the family have totally lost patience with my constant tinkering. So it is essential that SUSE, XP and the existing Grub menu remain untouched.

---

### Post by wjp.reg on 2006-03-28
Vulpus;

Like you, I am a tinkerer and get very much the same response from family members ](*,) 

My experience has been that Ubuntu will ask to replace grub with it's own menu.lst setup and write it to the MBR.

I too like the SuSE boot menu, so what I have done in the past after installing any other distro ( FC5 most recently), is to boot SuSE, go into YaST | System | Boot Loader, and select "Other", and let SUSE **Propose New Configuration**.  Once you confirm the proposed scheme, SuSE will reinstall it's own grub, with all distros included in menu.lst.

If you want to modify how the menu reads, change the order, or set boot options, you can do so before confirming the reinstallation.

Hope this helps

---

### Post by Vulpus on 2006-03-28
That sounds like an ideal solution!  Thanks very much. :p

---

### Post by Vulpus on 2006-03-28
[QUOTE=wjp.reg]Vulpus;

I too like the SuSE boot menu, so what I have done in the past after installing any other distro ( FC5 most recently), is to boot SuSE, go into YaST | System | Boot Loader, and select "Other", and let SUSE **Propose New Configuration**.  Once you confirm the proposed scheme, SuSE will reinstall it's own grub, with all distros included in menu.lst.
[/QUOTE]

SUCCESS!  Isnt it great when something just WORKS!  I did exactly as you suggested and I now have a triple boot system using the SUSE boot menu, excellent! :p 

I must say it is nice to have Ubuntu back.  I really like SUSE and it is my preferred distro but somehow Ubuntu has a bit more 'character'.  If they were cars, SUSE would be a BMW 5 series and Ubuntu would be a Volvo 740 Estate.

---

### Post by wjp.reg on 2006-03-28
[QUOTE=Vulpus]SUCCESS!  Isnt it great when something just WORKS!  I did exactly as you suggested and I now have a triple boot system using the SUSE boot menu, excellent! :p 

I must say it is nice to have Ubuntu back.  I really like SUSE and it is my preferred distro but somehow Ubuntu has a bit more 'character'.  If they were cars, SUSE would be a BMW 5 series and Ubuntu would be a Volvo 740 Estate.[/QUOTE]

Vulpus;

If you like gnome. check out FC5; looks fantastic.  Finding it a little more finicky than Ubuntu and SuSE, but their community forum is very good from what I've seen already.

Glad my suggestion worked out for you :-D

---

### Post by Vulpus on 2006-03-29
I have tried FC4 but it didnt seem to offer anything that Ubuntu didnt have.  Plus it didnt automatically mount my Windows drives, which I thought was a big negative in this day and age.

---

